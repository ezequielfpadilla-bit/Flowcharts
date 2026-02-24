\`\`\`mermaid  
\---  
title: "S-1 Production Flowchart \- Oil & Gas MLP IPO"  
\---  
flowchart TD

%% \============================================================  
%% PHASE 1: S-1 Input Assembly  
%% \============================================================  
subgraph P1\["Phase 1: S-1 Input Assembly"\]

    subgraph P1A\["VDR Readiness"\]  
        Milestone\_IPOTrigger(\["TRIGGER: Sponsor decides to pursue IPO"\])  
        Issuer\_EstablishVDR\["Issuer: Establish & populate VDR folders\<br/\>(Financials, Reserves, Ops, Legal,\<br/\>Governance, Risks, Tax)"\]  
        Issuer\_RunChecklistComparison\["Issuer: Run VDR index against\<br/\>S-1 checklist"\]  
        Issuer\_FlagVDRGaps\["Issuer: Flag missing or incomplete\<br/\>VDR items"\]  
        Issuer\_ConfirmPhysicalComplete\["Issuer: Confirm physical completeness\<br/\>of VDR folders"\]  
        Decision\_VDRReady{"VDR ready for S-1 drafting?"}  
    end

    subgraph P1B\["Section Assignment & Kickoff"\]  
        Issuer\_AssignSectionOwners\["Issuer: Assign S-1 section owners\<br/\>(Counsel→1/1A/3; Acctg→7/8;\<br/\>Bankers→UoP/Cap/Dil; Ops→reserves)"\]  
        Issuer\_HoldOrgMeeting\["Issuer: Hold organizational meeting\<br/\>(style guide, drafting\<br/\>timeline, gun-jumping rules, comps)"\]  
    end

    subgraph P1C\["Direct Input Production"\]  
        ResEng\_PrepareReserveReport\["Reserve Engineer: Engage reserve engineer\<br/\>for SEC reserve report\<br/\>from VDR\>Reserves per Reg S-X 4-10(a)"\]  
        Acct\_CommenceAudit\["Accountants: Commence audited FS\<br/\>from VDR\>Financials\<br/\>(3yr non-EGC / 2yr EGC; pro forma)"\]  
        CompCounsel\_ReviewMatlContracts\["Company Counsel: Review material contracts\<br/\>from VDR\>Legal"\]  
        CompCounsel\_ReviewRelPartyTxn\["Company Counsel: Review related-party\<br/\>transactions (current \+ 3 prior yrs)"\]  
        CompCounsel\_ReviewLitigation\["Company Counsel: Review litigation,\<br/\>environmental & regulatory\<br/\>from VDR\>Risks"\]  
        CompCounsel\_FlagDDGaps\["Company Counsel: Flag DD gaps;\<br/\>counsel reviews findings"\]  
        Issuer\_CompileOpsData\["Issuer: Compile acreage, drilling locations,\<br/\>infrastructure from VDR\>Ops"\]  
    end

end

%% Phase 1 Connections  
Milestone\_IPOTrigger \--\> Issuer\_EstablishVDR  
Issuer\_EstablishVDR \--\> Issuer\_RunChecklistComparison  
Issuer\_RunChecklistComparison \--\> Issuer\_FlagVDRGaps  
Issuer\_FlagVDRGaps \--\> Issuer\_ConfirmPhysicalComplete  
Issuer\_ConfirmPhysicalComplete \--\> Decision\_VDRReady  
Decision\_VDRReady \--\>|No| Issuer\_RunChecklistComparison  
Decision\_VDRReady \--\>|Yes| Issuer\_AssignSectionOwners  
Issuer\_AssignSectionOwners \--\> Issuer\_HoldOrgMeeting  
Issuer\_HoldOrgMeeting \--\> ResEng\_PrepareReserveReport  
Issuer\_HoldOrgMeeting \--\> Acct\_CommenceAudit  
Issuer\_HoldOrgMeeting \--\> CompCounsel\_ReviewMatlContracts  
Issuer\_HoldOrgMeeting \--\> CompCounsel\_ReviewRelPartyTxn  
Issuer\_HoldOrgMeeting \--\> CompCounsel\_ReviewLitigation  
Issuer\_HoldOrgMeeting \--\> Issuer\_CompileOpsData  
Issuer\_HoldOrgMeeting \--\> CompCounsel\_PrepareIndemAgt  
ResEng\_PrepareReserveReport \--\> CompCounsel\_ExtractGovTerms  
Acct\_CommenceAudit \--\> CompCounsel\_ExtractGovTerms  
CompCounsel\_ReviewMatlContracts \--\> CompCounsel\_FlagDDGaps  
CompCounsel\_ReviewRelPartyTxn \--\> CompCounsel\_FlagDDGaps  
CompCounsel\_ReviewLitigation \--\> CompCounsel\_FlagDDGaps  
CompCounsel\_FlagDDGaps \--\> CompCounsel\_ExtractGovTerms  
Issuer\_CompileOpsData \--\> CompCounsel\_ExtractGovTerms

%% \============================================================  
%% PHASE 2A: S-1 Exhibit Document Drafting  
%% \============================================================  
subgraph P2A\["Phase 2A: S-1 Exhibit Document Drafting"\]  
    CompCounsel\_ExtractGovTerms\["Company Counsel: Extract governance terms\<br/\>from VDR\>Governance"\]  
    CompCounsel\_DraftUnitholderRights\["Company Counsel: Draft unitholder rights\<br/\>& GP powers provisions"\]  
    CompCounsel\_DraftIDRSubord\["Company Counsel: Draft IDR tier structure\<br/\>& subordination period mechanics"\]  
    CompCounsel\_DraftFiduciary\["Company Counsel: Draft fiduciary duty\<br/\>modifications & conflicts provisions"\]  
    CompCounsel\_ReviewLPADraft\["Company Counsel: Review & negotiate\<br/\>complete LPA draft"\]  
    CompCounsel\_DraftContribAgt\["Company Counsel: Draft Contribution Agreement\<br/\>from VDR\>Governance\<br/\>(sponsor assets → MLP)"\]  
    CompCounsel\_DraftOmnibusAgt\["Company Counsel: Draft Omnibus Agreement\<br/\>from VDR\>Legal\<br/\>(indemnification, non-compete, ROFO)"\]  
    CompCounsel\_DraftServicesAgt\["Company Counsel: Draft Services Agreement\<br/\>from VDR\>Governance"\]  
    CompCounsel\_DraftRegRightsAgt\["Company Counsel: Draft Registration Rights Agreement\<br/\>from VDR\>Governance"\]  
    CompCounsel\_DraftLTIP\["Company Counsel: Draft LTIP\<br/\>from VDR\>Governance"\]  
    TaxCounsel\_ObtainTaxOpinion\["Tax Counsel: Obtain tax opinion from VDR\>Tax\<br/\>(qualifying income, pass-through,\<br/\>disguised sale rules)"\]  
end

%% Phase 2A Connections  
CompCounsel\_ExtractGovTerms \--\> CompCounsel\_DraftUnitholderRights  
CompCounsel\_ExtractGovTerms \--\> CompCounsel\_DraftIDRSubord  
CompCounsel\_ExtractGovTerms \--\> CompCounsel\_DraftFiduciary  
CompCounsel\_DraftUnitholderRights \--\> CompCounsel\_ReviewLPADraft  
CompCounsel\_DraftIDRSubord \--\> CompCounsel\_ReviewLPADraft  
CompCounsel\_DraftFiduciary \--\> CompCounsel\_ReviewLPADraft  
CompCounsel\_ReviewLPADraft \--\> CompCounsel\_DraftContribAgt  
CompCounsel\_ReviewLPADraft \--\> CompCounsel\_DraftOmnibusAgt  
CompCounsel\_ReviewLPADraft \--\> CompCounsel\_DraftServicesAgt  
CompCounsel\_ReviewLPADraft \--\> CompCounsel\_DraftRegRightsAgt  
CompCounsel\_ReviewLPADraft \--\> CompCounsel\_DraftLTIP  
CompCounsel\_DraftContribAgt \--\> TaxCounsel\_ObtainTaxOpinion  
CompCounsel\_DraftOmnibusAgt \--\> TaxCounsel\_ObtainTaxOpinion  
CompCounsel\_DraftServicesAgt \--\> TaxCounsel\_ObtainTaxOpinion  
CompCounsel\_DraftRegRightsAgt \--\> TaxCounsel\_ObtainTaxOpinion  
CompCounsel\_DraftLTIP \--\> TaxCounsel\_ObtainTaxOpinion  
TaxCounsel\_ObtainTaxOpinion \--\> CompCounsel\_PullOpsData

%% \============================================================  
%% PHASE 2B: S-1 Prospectus Drafting  
%% \============================================================  
subgraph P2B\["Phase 2B: S-1 Prospectus Drafting"\]  
    CompCounsel\_PullOpsData\["Company Counsel: Pull acreage, drilling\<br/\>& reserve data from VDR\>Ops"\]  
    CompCounsel\_DraftCompStrengths\["Company Counsel: Draft competitive\<br/\>strengths narrative"\]  
    CompCounsel\_DraftBizStrategy\["Company Counsel: Draft business strategy\<br/\>& midstream advantage sections"\]  
    CompCounsel\_DraftReserveDisc\["Company Counsel: Draft reserve disclosure\<br/\>per Reg S-K Subpart 1200"\]  
    CompCounsel\_VerifyReserveConsist\["Company Counsel: Verify Item 1 consistency\<br/\>with reserve engineer report"\]  
    CompCounsel\_AssistItem1\["Company Counsel: Assist Item 1 narrative\<br/\>(tone, reserve\<br/\>report consistency)"\]  
    Issuer\_AnalyzeProdPriceCost\["Issuer: Analyze production, price\<br/\>& cost trends from VDR\>Financials"\]  
    Issuer\_DraftMDANarrative\["Issuer: Draft MD\&A narrative\<br/\>(liquidity, capital resources,\<br/\>known trends)"\]  
    Issuer\_MgmtVerifyMDA\["Issuer: CFO/management verify\<br/\>MD\&A numbers & business context"\]  
    Issuer\_GenerateMDATables\["Issuer: Generate MD\&A sensitivity tables & pro forma schedules"\]  
    CompCounsel\_DraftCommodityRisks\["Company Counsel: Draft commodity price\<br/\>& reserve estimation risk factors"\]  
    CompCounsel\_DraftRegEnvRisks\["Company Counsel: Draft regulatory\<br/\>& environmental risk factors"\]  
    CompCounsel\_DraftMLPRisks\["Company Counsel: Draft MLP-specific risks\<br/\>(conflicts, IDR dilution,\<br/\>limited voting rights)"\]  
    CompCounsel\_DraftTaxRisks\["Company Counsel: Draft unitholder tax risks\<br/\>(UBTI, K-1 complexity,\<br/\>state filing obligations)"\]  
    CompCounsel\_CrossCheckSECTrends\["Company Counsel: Cross-check risk factors\<br/\>against SEC comment letter trends\<br/\>for E\&P MLPs"\]  
    CompCounsel\_ExpandRiskFactors\["Company Counsel: Expand Risk Factors\<br/\>with mitigants & detailed\<br/\>disclosure language"\]  
    CompCounsel\_DraftLegalProc\["Company Counsel: Draft Item 3 Legal Proceedings\<br/\>from VDR\>Risks"\]  
    Acct\_PrepareFS\["Accountants: Prepare Item 8 FS & Notes\<br/\>(PCAOB) from VDR\>Financials"\]  
    Issuer\_ComputeUoP\["Issuer: Compute Use of Proceeds\<br/\>from offering terms"\]  
    Issuer\_BuildCapDilTables\["Issuer: Build Capitalization\<br/\>& Dilution tables"\]  
    Issuer\_BankersSetTerms\["Issuer: Bankers/counsel set\<br/\>offering terms & verify tables"\]  
    Acct\_PrepareSelFinData\["Accountants: Prepare Selected Financial Data\<br/\>from VDR\>Financials"\]  
    CompCounsel\_ExtractLPADistTerms\["Company Counsel: Extract MQD & IDR\<br/\>terms from LPA"\]  
    CompCounsel\_DraftSubordMechanics\["Company Counsel: Draft subordination\<br/\>period mechanics narrative"\]  
    CompCounsel\_DraftIDRSplitDisc\["Company Counsel: Draft IDR split\<br/\>schedule & distribution waterfall"\]  
    CompCounsel\_GenerateCashDistNarr\["Company Counsel: Generate Cash Distribution\<br/\>narrative with IDR tier examples"\]  
    CompCounsel\_DistillEquityStory\["Company Counsel: Distill equity story\<br/\>& competitive strengths for Summary"\]  
    CompCounsel\_CompileFinSummary\["Company Counsel: Compile summary\<br/\>financial data & offering terms"\]  
    CompCounsel\_DraftBoxSection\["Company Counsel: Draft Box section\<br/\>(front-of-prospectus summary)"\]  
    CompCounsel\_AssistSummaryBox\["Company Counsel: Assist Summary/Box\<br/\>(tone, trace claims\<br/\>to detailed sections)"\]  
    TaxCounsel\_DraftPassThrough\["Tax Counsel: Draft pass-through\<br/\>taxation & K-1 reporting sections"\]  
    TaxCounsel\_DraftUBTIStateForeign\["Tax Counsel: Draft UBTI, state filing\<br/\>& foreign investor withholding"\]  
    TaxCounsel\_VerifyTaxAccuracy\["Tax Counsel: Tax counsel verify\<br/\>technical accuracy of all tax sections"\]  
    TaxCounsel\_AssistTaxConseq\["Tax Counsel: Assist Tax Consequences\<br/\>(unitholder tax scenarios)"\]  
    CompCounsel\_DraftUnitsDesc\["Company Counsel: Draft Description\<br/\>of Common Units from LPA"\]  
    CompCounsel\_DraftSellingUnitholders\["Company Counsel: Draft Selling\<br/\>Unitholders section"\]  
    CompCounsel\_DraftUnderwriting\["Company Counsel: Draft Underwriting\<br/\>section (w/ UW counsel input\<br/\>on negotiated terms)"\]  
    CompCounsel\_PreparePartII\["Company Counsel: Prepare Part II (indemnification, unregistered sales, expenses)"\]  
    CompCounsel\_CompileMatlContracts\["Company Counsel: Compile material contracts\<br/\>as exhibits from VDR\>Legal"\]  
    CompCounsel\_ObtainExhibitConsents\["Company Counsel: Obtain reserve engineer,\<br/\>auditor & nominee consents"\]  
    CompCounsel\_IndexOrgDocs\["Company Counsel: Index organizational\<br/\>documents & verify exhibit list\<br/\>completeness"\]  
    Decision\_SectionsConsistent{"Sections consistent\<br/\>with each other?"}  
end

%% Phase 2B Connections  
CompCounsel\_PullOpsData \--\> CompCounsel\_DraftCompStrengths  
CompCounsel\_PullOpsData \--\> CompCounsel\_DraftBizStrategy  
CompCounsel\_PullOpsData \--\> CompCounsel\_DraftReserveDisc  
CompCounsel\_DraftCompStrengths \--\> CompCounsel\_VerifyReserveConsist  
CompCounsel\_DraftBizStrategy \--\> CompCounsel\_VerifyReserveConsist  
CompCounsel\_DraftReserveDisc \--\> CompCounsel\_VerifyReserveConsist  
CompCounsel\_VerifyReserveConsist \--\> CompCounsel\_AssistItem1  
CompCounsel\_AssistItem1 \--\> Issuer\_AnalyzeProdPriceCost  
Issuer\_AnalyzeProdPriceCost \--\> Issuer\_DraftMDANarrative  
Issuer\_DraftMDANarrative \--\> Issuer\_MgmtVerifyMDA  
Issuer\_MgmtVerifyMDA \--\> Issuer\_GenerateMDATables  
Issuer\_GenerateMDATables \--\> CompCounsel\_DraftCommodityRisks  
Issuer\_GenerateMDATables \--\> CompCounsel\_DraftRegEnvRisks  
Issuer\_GenerateMDATables \--\> CompCounsel\_DraftMLPRisks  
Issuer\_GenerateMDATables \--\> CompCounsel\_DraftTaxRisks  
CompCounsel\_DraftCommodityRisks \--\> CompCounsel\_CrossCheckSECTrends  
CompCounsel\_DraftRegEnvRisks \--\> CompCounsel\_CrossCheckSECTrends  
CompCounsel\_DraftMLPRisks \--\> CompCounsel\_CrossCheckSECTrends  
CompCounsel\_DraftTaxRisks \--\> CompCounsel\_CrossCheckSECTrends  
CompCounsel\_CrossCheckSECTrends \--\> CompCounsel\_ExpandRiskFactors  
CompCounsel\_ExpandRiskFactors \--\> CompCounsel\_DraftLegalProc  
CompCounsel\_DraftLegalProc \--\> Acct\_PrepareFS  
Acct\_PrepareFS \--\> Issuer\_ComputeUoP  
Acct\_PrepareFS \--\> Issuer\_BuildCapDilTables  
Issuer\_ComputeUoP \--\> Issuer\_BankersSetTerms  
Issuer\_BuildCapDilTables \--\> Issuer\_BankersSetTerms  
Issuer\_BankersSetTerms \--\> Acct\_PrepareSelFinData  
Acct\_PrepareSelFinData \--\> CompCounsel\_ExtractLPADistTerms  
CompCounsel\_ExtractLPADistTerms \--\> CompCounsel\_DraftSubordMechanics  
CompCounsel\_ExtractLPADistTerms \--\> CompCounsel\_DraftIDRSplitDisc  
CompCounsel\_DraftSubordMechanics \--\> CompCounsel\_GenerateCashDistNarr  
CompCounsel\_DraftIDRSplitDisc \--\> CompCounsel\_GenerateCashDistNarr  
CompCounsel\_GenerateCashDistNarr \--\> CompCounsel\_DistillEquityStory  
CompCounsel\_GenerateCashDistNarr \--\> CompCounsel\_CompileFinSummary  
CompCounsel\_DistillEquityStory \--\> CompCounsel\_DraftBoxSection  
CompCounsel\_CompileFinSummary \--\> CompCounsel\_DraftBoxSection  
CompCounsel\_DraftBoxSection \--\> CompCounsel\_AssistSummaryBox  
CompCounsel\_AssistSummaryBox \--\> TaxCounsel\_DraftPassThrough  
CompCounsel\_AssistSummaryBox \--\> TaxCounsel\_DraftUBTIStateForeign  
TaxCounsel\_DraftPassThrough \--\> TaxCounsel\_VerifyTaxAccuracy  
TaxCounsel\_DraftUBTIStateForeign \--\> TaxCounsel\_VerifyTaxAccuracy  
TaxCounsel\_VerifyTaxAccuracy \--\> TaxCounsel\_AssistTaxConseq  
TaxCounsel\_AssistTaxConseq \--\> CompCounsel\_PreparePartII  
Issuer\_GenerateMDATables \--\> CompCounsel\_DraftUnitsDesc  
Issuer\_GenerateMDATables \--\> CompCounsel\_DraftSellingUnitholders  
CompCounsel\_DraftUnitsDesc \--\> CompCounsel\_DraftUnderwriting  
CompCounsel\_DraftSellingUnitholders \--\> CompCounsel\_DraftUnderwriting  
CompCounsel\_DraftUnderwriting \--\> CompCounsel\_PreparePartII  
CompCounsel\_PreparePartII \--\> CompCounsel\_CompileMatlContracts  
CompCounsel\_PreparePartII \--\> CompCounsel\_ObtainExhibitConsents  
CompCounsel\_CompileMatlContracts \--\> CompCounsel\_IndexOrgDocs  
CompCounsel\_ObtainExhibitConsents \--\> CompCounsel\_IndexOrgDocs  
CompCounsel\_IndexOrgDocs \--\> Decision\_SectionsConsistent  
Decision\_SectionsConsistent \--\>|No| CompCounsel\_PullOpsData  
Decision\_SectionsConsistent \--\>|Yes| CompCounsel\_Review1VDR

%% \============================================================  
%% PHASE 2C: Internal Review Cycles  
%% \============================================================  
subgraph P2C\["Phase 2C: Internal Review Cycles"\]  
    CompCounsel\_Review1VDR\["Company Counsel: First review: cross-check\<br/\>against VDR"\]  
    CompCounsel\_Review2CrossRefs\["Company Counsel: Second review: cross-refs,\<br/\>defined terms, financial ties\<br/\>(MD\&A↔FS↔Summary↔Cap)"\]  
    CompCounsel\_CheckDefinedTerms\["Company Counsel: Cross-check defined\<br/\>terms consistency; flag mismatches"\]  
    CompCounsel\_CheckNarrConsist\["Company Counsel: Check narrative\<br/\>consistency across all sections"\]  
    CompCounsel\_ReviewGunJumping\["Company Counsel: Review for\<br/\>gun-jumping compliance\<br/\>(30-day bright-line test)"\]  
    CompCounsel\_VerifyFLSSafeHarbor\["Company Counsel: Verify forward-looking\<br/\>statement safe harbor language"\]  
    CompCounsel\_Section11Review\["Company Counsel: Full Section 11 liability\<br/\>review of registration statement"\]  
    Decision\_ReviewResolved{"All review comments resolved?"}  
    Issuer\_FinalSignOff\["Issuer: Execute final internal sign-off on draft S-1"\]  
end

%% Phase 2C Connections  
CompCounsel\_Review1VDR \--\> CompCounsel\_Review2CrossRefs  
CompCounsel\_Review2CrossRefs \--\> CompCounsel\_CheckDefinedTerms  
CompCounsel\_CheckDefinedTerms \--\> CompCounsel\_CheckNarrConsist  
CompCounsel\_CheckNarrConsist \--\> CompCounsel\_ReviewGunJumping  
CompCounsel\_ReviewGunJumping \--\> CompCounsel\_VerifyFLSSafeHarbor  
CompCounsel\_VerifyFLSSafeHarbor \--\> CompCounsel\_Section11Review  
CompCounsel\_Section11Review \--\> Decision\_ReviewResolved  
Decision\_ReviewResolved \--\>|No| CompCounsel\_Review1VDR  
Decision\_ReviewResolved \--\>|Yes| Issuer\_FinalSignOff  
Issuer\_FinalSignOff \--\> CompCounsel\_ObtainCUSIP

%% \============================================================  
%% PHASE 3: Pre-Filing Mechanics  
%% \============================================================  
subgraph P3\["Phase 3: S-1 Filing Preparation"\]  
    CompCounsel\_PrepareIndemAgt\["Company Counsel: Prepare indemnification\<br/\>agreements (S-1 exhibit)"\]  
    CompCounsel\_ObtainCUSIP\["Company Counsel: Obtain CUSIP number"\]  
    CompCounsel\_CollectSigPages\["Company Counsel: Collect executed signature\<br/\>pages & powers of attorney"\]  
    CompCounsel\_ObtainCIKCCC\["Company Counsel: Obtain CIK/CCC EDGAR codes"\]  
    CompCounsel\_CheckRegSK\["Company Counsel: Check Reg S-K\<br/\>narrative disclosure requirements"\]  
    CompCounsel\_CheckRegSX\["Company Counsel: Check Reg S-X\<br/\>financial statement requirements"\]  
    CompCounsel\_VerifySigExhibits\["Company Counsel: Verify signatures,\<br/\>powers of attorney & exhibit list"\]  
    CompCounsel\_Edgarize\["Company Counsel: Edgarize S-1 & exhibits; test EDGAR filing"\]  
    CompCounsel\_PrepareRule134\["Company Counsel: Prepare Rule 134 press release"\]  
    Decision\_S1Ready{"S-1 ready for submission?"}  
end

%% Phase 3 Connections  
CompCounsel\_PrepareIndemAgt \--\> CompCounsel\_CompileMatlContracts  
Issuer\_FinalSignOff \--\> CompCounsel\_CollectSigPages  
Issuer\_FinalSignOff \--\> CompCounsel\_ObtainCIKCCC  
CompCounsel\_ObtainCUSIP \--\> CompCounsel\_CheckRegSK  
CompCounsel\_CollectSigPages \--\> CompCounsel\_CheckRegSK  
CompCounsel\_ObtainCIKCCC \--\> CompCounsel\_CheckRegSK  
CompCounsel\_CheckRegSK \--\> CompCounsel\_CheckRegSX  
CompCounsel\_CheckRegSX \--\> CompCounsel\_VerifySigExhibits  
CompCounsel\_VerifySigExhibits \--\> CompCounsel\_Edgarize  
CompCounsel\_Edgarize \--\> CompCounsel\_PrepareRule134  
CompCounsel\_PrepareRule134 \--\> Decision\_S1Ready  
Decision\_S1Ready \--\>|No| CompCounsel\_CheckRegSK  
Decision\_S1Ready \--\>|Yes| CompCounsel\_AssembleDRSPackage

%% \============================================================  
%% PHASE 4: Confidential Submission & SEC Review  
%% \============================================================  
subgraph P4\["Phase 4: Confidential Submission & SEC Review"\]

    subgraph P4A\["Filing with SEC, FINRA, and Exchange"\]  
        CompCounsel\_AssembleDRSPackage\["Company Counsel: Assemble final S-1\<br/\>+ all exhibits into DRS package"\]  
        CompCounsel\_VerifyExhibitsAttached\["Company Counsel: Verify all exhibits\<br/\>& consents attached"\]  
        CompCounsel\_CounselConfirmDRS\["Company Counsel: Counsel confirms\<br/\>DRS completeness for submission"\]  
        Acct\_ObtainAuditorConsent\["Accountants: Obtain signed auditor's consent"\]  
        CompCounsel\_SubmitDRS\["Company Counsel: Submit confidential DRS via EDGAR"\]  
        UWCounsel\_FileFINRA\["UW Counsel: File with FINRA within 1 business day (Rule 5110)"\]  
        UWCounsel\_SubmitExchange\["UW Counsel: Submit S-1 to NYSE/Nasdaq for review"\]  
        Acct\_ComfortLetterScope\["Accountants: Discuss comfort letter scope\<br/\>(AS 6101); circle-up begins;\<br/\>auditors deliver initial draft"\]  
    end

    subgraph P4B\["SEC Review & Amendment Cycle"\]  
        SEC\_AssignExaminer\["SEC: SEC assigns examiner team\<br/\>(Div of Corp Finance)"\]  
        SEC\_CommentLetterReceived{"SEC: SEC comment letter\<br/\>received?\<br/\>(27-30 cal days)"}  
        CompCounsel\_CategorizeSECComments\["Company Counsel: Categorize SEC comments\<br/\>by section (reserves, MD\&A,\<br/\>risks, tax, other)"\]  
        CompCounsel\_DraftResponseLetter\["Company Counsel: Draft response letter\<br/\>addressing each comment"\]  
        CompCounsel\_DraftS1AAmendments\["Company Counsel: Draft proposed\<br/\>S-1/A amendments per responses"\]  
        CompCounsel\_CounselMgmtReview\["Company Counsel: Counsel & management\<br/\>review responses & amendments"\]  
        CompCounsel\_FileAmendedDRS\["Company Counsel: File amended DRS (S-1/A) via EDGAR"\]  
        SEC\_FollowUpComments{"SEC: SEC follow-up\<br/\>comments?\<br/\>(2-3 wks)"}  
        SEC\_AllCommentsCleared{"All SEC comments cleared?"}  
        CompCounsel\_PublicFileConf\["Company Counsel: Publicly file all prior\<br/\>confidential submissions\<br/\>(≥15 days before roadshow)"\]  
        UWCounsel\_UpdateFINRA\["UW Counsel: Update FINRA filing;\<br/\>pay additional fees"\]  
        SEC\_FINRANoObjections{"FINRA: No Objections or Unreasonable?"}  
        UWCounsel\_ObtainFINRALetter\["UW Counsel: Obtain FINRA No Objections\<br/\>letter (15-25 bus. days)"\]  
        SEC\_ExchangeApproved{"Exchange listing approved?"}  
    end

end

%% Phase 4 Connections  
CompCounsel\_AssembleDRSPackage \--\> CompCounsel\_VerifyExhibitsAttached  
CompCounsel\_VerifyExhibitsAttached \--\> CompCounsel\_CounselConfirmDRS  
CompCounsel\_CounselConfirmDRS \--\> Acct\_ObtainAuditorConsent  
Acct\_ObtainAuditorConsent \--\> CompCounsel\_SubmitDRS  
CompCounsel\_SubmitDRS \--\> UWCounsel\_FileFINRA  
CompCounsel\_SubmitDRS \--\> UWCounsel\_SubmitExchange  
CompCounsel\_SubmitDRS \--\> Acct\_ComfortLetterScope  
CompCounsel\_SubmitDRS \--\> SEC\_AssignExaminer  
UWCounsel\_FileFINRA \--\> UWCounsel\_UpdateFINRA  
UWCounsel\_SubmitExchange \--\> SEC\_ExchangeApproved  
Acct\_ComfortLetterScope \--\> Decision\_PreEffConditions  
SEC\_AssignExaminer \--\> SEC\_CommentLetterReceived  
SEC\_CommentLetterReceived \--\>|Pending| SEC\_CommentLetterReceived  
SEC\_CommentLetterReceived \--\>|Yes| CompCounsel\_CategorizeSECComments  
CompCounsel\_CategorizeSECComments \--\> CompCounsel\_DraftResponseLetter  
CompCounsel\_DraftResponseLetter \--\> CompCounsel\_DraftS1AAmendments  
CompCounsel\_DraftS1AAmendments \--\> CompCounsel\_CounselMgmtReview  
CompCounsel\_CounselMgmtReview \--\> CompCounsel\_FileAmendedDRS  
CompCounsel\_FileAmendedDRS \--\> SEC\_FollowUpComments  
SEC\_FollowUpComments \--\>|Yes| CompCounsel\_CategorizeSECComments  
SEC\_FollowUpComments \--\>|No| SEC\_AllCommentsCleared  
SEC\_AllCommentsCleared \--\>|No| CompCounsel\_CategorizeSECComments  
SEC\_AllCommentsCleared \--\>|Yes| CompCounsel\_PublicFileConf  
CompCounsel\_PublicFileConf \--\> UWCounsel\_UpdateFINRA  
UWCounsel\_UpdateFINRA \--\> SEC\_FINRANoObjections  
SEC\_FINRANoObjections \--\>|Unreasonable| UWCounsel\_UpdateFINRA  
SEC\_FINRANoObjections \--\>|No Objections| UWCounsel\_ObtainFINRALetter  
UWCounsel\_ObtainFINRALetter \--\> SEC\_ExchangeApproved  
SEC\_ExchangeApproved \--\>|No| UWCounsel\_SubmitExchange  
SEC\_ExchangeApproved \--\>|Yes| CompCounsel\_FileRedHerring  
SEC\_ExchangeApproved \--\>|Yes| UWCounsel\_PrepareBlueSky  
SEC\_ExchangeApproved \--\>|Yes| CompCounsel\_ReviewRoadshow  
SEC\_ExchangeApproved \--\>|Yes| CompCounsel\_PrepareForm3s  
SEC\_ExchangeApproved \--\>|Yes| CompCounsel\_PrepareForm8A

%% \============================================================  
%% PHASE 5: Pre-Effectiveness Mechanics  
%% \============================================================  
subgraph P5\["Phase 5: Pre-Effectiveness Filing Mechanics"\]  
    CompCounsel\_FileRedHerring\["Company Counsel: File & print preliminary prospectus (red herring)"\]  
    UWCounsel\_PrepareBlueSky\["UW Counsel: Prepare preliminary blue sky memo"\]  
    CompCounsel\_ReviewRoadshow\["Company Counsel: Review roadshow for S-1 consistency & gun-jumping"\]  
    CompCounsel\_IssueLaunchPR\["Company Counsel: Issue Rule 134 launch press release"\]  
    CompCounsel\_PrepareForm3s\["Company Counsel: Prepare Form 3s\<br/\>(Sec 16 beneficial ownership)"\]  
    CompCounsel\_PrepareForm8A\["Company Counsel: Prepare Form 8-A (Exchange Act registration)"\]  
    CompCounsel\_FinalizeListingApp\["Company Counsel: Finalize listing application;\<br/\>confirm exchange approval"\]  
    Decision\_FSCurrent{"FS current under 135-day staleness rule?"}  
    Decision\_PreEffConditions{"All pre-effectiveness\<br/\>conditions met?\<br/\>(FINRA, exchange, FS, consents)"}  
end

%% Phase 5 Connections  
%% Group A (road show prep): CompCounsel\_FileRedHerring, UWCounsel\_PrepareBlueSky, CompCounsel\_ReviewRoadshow \--\> converge at CompCounsel\_IssueLaunchPR  
CompCounsel\_FileRedHerring \--\> CompCounsel\_IssueLaunchPR  
UWCounsel\_PrepareBlueSky \--\> CompCounsel\_IssueLaunchPR  
CompCounsel\_ReviewRoadshow \--\> CompCounsel\_IssueLaunchPR  
%% Group B (pre-effectiveness filings): CompCounsel\_PrepareForm3s, CompCounsel\_PrepareForm8A \--\> converge at CompCounsel\_FinalizeListingApp  
CompCounsel\_PrepareForm3s \--\> CompCounsel\_FinalizeListingApp  
CompCounsel\_PrepareForm8A \--\> CompCounsel\_FinalizeListingApp  
%% Both groups converge at Decision\_FSCurrent  
CompCounsel\_IssueLaunchPR \--\> Decision\_FSCurrent  
CompCounsel\_FinalizeListingApp \--\> Decision\_FSCurrent  
Decision\_FSCurrent \--\>|No \- Stale| CompCounsel\_FileAmendedDRS  
Decision\_FSCurrent \--\>|Yes \- Current| Decision\_PreEffConditions  
Decision\_PreEffConditions \--\>|No| CompCounsel\_FinalizeListingApp  
Decision\_PreEffConditions \--\>|Yes| Issuer\_BringDownDD

%% \============================================================  
%% PHASE 6: Effectiveness  
%% \============================================================  
subgraph P6\["Phase 6: Effectiveness"\]  
    Issuer\_BringDownDD\["Issuer: Conduct bring-down DD call"\]  
    CompCounsel\_RequestAccel\["Company Counsel: Deliver to SEC request\<br/\>for acceleration\<br/\>(Rule 461; 2 bus. days prior)"\]  
    UW\_JoinAccelRequest\["Underwriters: Deliver to SEC letter joining acceleration request"\]  
    SEC\_DeclaresEffective{"SEC declares S-1 effective?"}  
    Milestone\_Effective(\["SEC DECLARES REGISTRATION\<br/\>STATEMENT EFFECTIVE\<br/\>— END —"\])  
end

%% Phase 6 Connections  
Issuer\_BringDownDD \--\> CompCounsel\_RequestAccel  
CompCounsel\_RequestAccel \--\> UW\_JoinAccelRequest  
UW\_JoinAccelRequest \--\> SEC\_DeclaresEffective  
SEC\_DeclaresEffective \--\>|No| CompCounsel\_CategorizeSECComments  
SEC\_DeclaresEffective \--\>|Yes| Milestone\_Effective

%% \============================================================  
%% STYLE DEFINITIONS — Okabe-Ito Colorblind-Safe Palette  
%% \============================================================  
%%  
%% Color Legend (8 roles):  
%% Company Counsel          \= Blue           \#0072B2  (white text)  
%% Issuer (Management)      \= Orange         \#E69F00  (black text)  
%% Underwriters             \= Sky Blue       \#56B4E9  (black text)  
%% Underwriters' Counsel    \= Bluish Green   \#009E73  (white text)  
%% Accountants              \= Yellow         \#F0E442  (black text)  
%% Reserve Engineer         \= Vermillion     \#D55E00  (white text)  
%% Tax Counsel              \= Reddish Purple \#CC79A7  (black text)  
%% SEC/FINRA/Exchange       \= Black          \#000000  (white text)  
%%  
%% Decision diamonds (Decision\_VDRReady, Decision\_SectionsConsistent, Decision\_ReviewResolved, Decision\_S1Ready, Decision\_FSCurrent, Decision\_PreEffConditions): default Mermaid styling  
%% Start/End milestones (Milestone\_IPOTrigger, Milestone\_Effective): default Mermaid styling

%% \--- Company Counsel (Blue \#0072B2) \---  
style CompCounsel\_ReviewMatlContracts stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ReviewRelPartyTxn stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ReviewLitigation stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_FlagDDGaps stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ExtractGovTerms stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftUnitholderRights stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftIDRSubord stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftFiduciary stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ReviewLPADraft stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftContribAgt stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftOmnibusAgt stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftServicesAgt stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftRegRightsAgt stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftLTIP stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_PullOpsData stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftCompStrengths stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftBizStrategy stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftReserveDisc stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_VerifyReserveConsist stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_AssistItem1 stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftCommodityRisks stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftRegEnvRisks stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftMLPRisks stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftTaxRisks stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CrossCheckSECTrends stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ExpandRiskFactors stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftLegalProc stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ExtractLPADistTerms stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftSubordMechanics stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftIDRSplitDisc stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_GenerateCashDistNarr stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DistillEquityStory stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CompileFinSummary stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftBoxSection stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_AssistSummaryBox stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftUnitsDesc stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftSellingUnitholders stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftUnderwriting stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_PreparePartII stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CompileMatlContracts stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ObtainExhibitConsents stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_IndexOrgDocs stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_Review1VDR stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_Review2CrossRefs stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CheckDefinedTerms stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CheckNarrConsist stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ReviewGunJumping stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_VerifyFLSSafeHarbor stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_Section11Review stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_PrepareIndemAgt stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ObtainCUSIP stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CollectSigPages stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ObtainCIKCCC stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CheckRegSK stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CheckRegSX stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_VerifySigExhibits stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_Edgarize stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_PrepareRule134 stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_AssembleDRSPackage stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_VerifyExhibitsAttached stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CounselConfirmDRS stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_SubmitDRS stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CategorizeSECComments stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftResponseLetter stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_DraftS1AAmendments stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_CounselMgmtReview stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_FileAmendedDRS stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_PublicFileConf stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_FileRedHerring stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ReviewRoadshow stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_IssueLaunchPR stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_PrepareForm3s stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_PrepareForm8A stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_FinalizeListingApp stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_RequestAccel stroke:\#000,fill:\#0072B2,color:\#FFF

%% \--- Issuer / Management (Orange \#E69F00) \---  
style Issuer\_EstablishVDR stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_RunChecklistComparison stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_FlagVDRGaps stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_ConfirmPhysicalComplete stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_AssignSectionOwners stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_HoldOrgMeeting stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_CompileOpsData stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_AnalyzeProdPriceCost stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_DraftMDANarrative stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_MgmtVerifyMDA stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_GenerateMDATables stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_ComputeUoP stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_BuildCapDilTables stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_BankersSetTerms stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_FinalSignOff stroke:\#000,fill:\#E69F00,color:\#000  
style Issuer\_BringDownDD stroke:\#000,fill:\#E69F00,color:\#000

%% \--- Underwriters (Sky Blue \#56B4E9) \---  
style UW\_JoinAccelRequest stroke:\#000,fill:\#56B4E9,color:\#000

%% \--- Underwriters' Counsel (Bluish Green \#009E73) \---  
style UWCounsel\_FileFINRA stroke:\#000,fill:\#009E73,color:\#FFF  
style UWCounsel\_SubmitExchange stroke:\#000,fill:\#009E73,color:\#FFF  
style UWCounsel\_UpdateFINRA stroke:\#000,fill:\#009E73,color:\#FFF  
style UWCounsel\_ObtainFINRALetter stroke:\#000,fill:\#009E73,color:\#FFF  
style UWCounsel\_PrepareBlueSky stroke:\#000,fill:\#009E73,color:\#FFF

%% \--- Accountants (Yellow \#F0E442) \---  
style Acct\_CommenceAudit stroke:\#000,fill:\#F0E442,color:\#000  
style Acct\_PrepareFS stroke:\#000,fill:\#F0E442,color:\#000  
style Acct\_PrepareSelFinData stroke:\#000,fill:\#F0E442,color:\#000  
style Acct\_ObtainAuditorConsent stroke:\#000,fill:\#F0E442,color:\#000  
style Acct\_ComfortLetterScope stroke:\#000,fill:\#F0E442,color:\#000

%% \--- Reserve Engineer (Vermillion \#D55E00) \---  
style ResEng\_PrepareReserveReport stroke:\#000,fill:\#D55E00,color:\#FFF

%% \--- Tax Counsel (Reddish Purple \#CC79A7) \---  
style TaxCounsel\_ObtainTaxOpinion stroke:\#000,fill:\#CC79A7,color:\#000  
style TaxCounsel\_DraftPassThrough stroke:\#000,fill:\#CC79A7,color:\#000  
style TaxCounsel\_DraftUBTIStateForeign stroke:\#000,fill:\#CC79A7,color:\#000  
style TaxCounsel\_VerifyTaxAccuracy stroke:\#000,fill:\#CC79A7,color:\#000  
style TaxCounsel\_AssistTaxConseq stroke:\#000,fill:\#CC79A7,color:\#000

%% \--- SEC/FINRA/Exchange (Black \#000000) \---  
style SEC\_AssignExaminer stroke:\#000,fill:\#000000,color:\#FFF  
style SEC\_CommentLetterReceived stroke:\#000,fill:\#000000,color:\#FFF  
style SEC\_FollowUpComments stroke:\#000,fill:\#000000,color:\#FFF  
style SEC\_AllCommentsCleared stroke:\#000,fill:\#000000,color:\#FFF  
style SEC\_FINRANoObjections stroke:\#000,fill:\#000000,color:\#FFF  
style SEC\_ExchangeApproved stroke:\#000,fill:\#000000,color:\#FFF  
style SEC\_DeclaresEffective stroke:\#000,fill:\#000000,color:\#FFF

\`\`\`