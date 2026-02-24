```mermaid
---
title: "S-1 Production Flowchart - Oil & Gas MLP IPO"
---
flowchart TD

%% ============================================================
%% PHASE 1: S-1 Input Assembly
%% ============================================================
subgraph P1["Phase 1: S-1 Input Assembly"]

    subgraph P1A["VDR Readiness"]
        Milestone_IPOTrigger(["TRIGGER: Sponsor decides to pursue IPO"])
        Issuer_EstablishVDR["Issuer: Establish & populate VDR folders<br/>(Financials, Reserves, Ops, Legal,<br/>Governance, Risks, Tax)"]
        Issuer_RunChecklistComparison["Issuer: Run VDR index against<br/>S-1 checklist"]
        Issuer_FlagVDRGaps["Issuer: Flag missing or incomplete<br/>VDR items"]
        Issuer_ConfirmPhysicalComplete["Issuer: Confirm physical completeness<br/>of VDR folders"]
        Decision_VDRReady{"VDR ready for S-1 drafting?"}
    end

    subgraph P1B["Section Assignment & Kickoff"]
        Issuer_AssignSectionOwners["Issuer: Assign S-1 section owners<br/>(Counsel→1/1A/3; Acctg→7/8;<br/>Bankers→UoP/Cap/Dil; Ops→reserves)"]
        Issuer_HoldOrgMeeting["Issuer: Hold organizational meeting<br/>(style guide, drafting<br/>timeline, gun-jumping rules, comps)"]
    end

    subgraph P1C["Direct Input Production"]
        ResEng_PrepareReserveReport["Reserve Engineer: Engage reserve engineer<br/>for SEC reserve report<br/>from VDR>Reserves per Reg S-X 4-10(a)"]
        Acct_CommenceAudit["Accountants: Commence audited FS<br/>from VDR>Financials<br/>(3yr non-EGC / 2yr EGC; pro forma)"]
        CompCounsel_ReviewMatlContracts["Company Counsel: Review material contracts<br/>from VDR>Legal"]
        CompCounsel_ReviewRelPartyTxn["Company Counsel: Review related-party<br/>transactions (current + 3 prior yrs)"]
        CompCounsel_ReviewLitigation["Company Counsel: Review litigation,<br/>environmental & regulatory<br/>from VDR>Risks"]
        CompCounsel_FlagDDGaps["Company Counsel: Flag DD gaps;<br/>counsel reviews findings"]
        Issuer_CompileOpsData["Issuer: Compile acreage, drilling locations,<br/>infrastructure from VDR>Ops"]
    end

end

%% Phase 1 Connections
Milestone_IPOTrigger --> Issuer_EstablishVDR
Issuer_EstablishVDR --> Issuer_RunChecklistComparison
Issuer_RunChecklistComparison --> Issuer_FlagVDRGaps
Issuer_FlagVDRGaps --> Issuer_ConfirmPhysicalComplete
Issuer_ConfirmPhysicalComplete --> Decision_VDRReady
Decision_VDRReady -->|No| Issuer_RunChecklistComparison
Decision_VDRReady -->|Yes| Issuer_AssignSectionOwners
Issuer_AssignSectionOwners --> Issuer_HoldOrgMeeting
Issuer_HoldOrgMeeting --> ResEng_PrepareReserveReport
Issuer_HoldOrgMeeting --> Acct_CommenceAudit
Issuer_HoldOrgMeeting --> CompCounsel_ReviewMatlContracts
Issuer_HoldOrgMeeting --> CompCounsel_ReviewRelPartyTxn
Issuer_HoldOrgMeeting --> CompCounsel_ReviewLitigation
Issuer_HoldOrgMeeting --> Issuer_CompileOpsData
Issuer_HoldOrgMeeting --> CompCounsel_PrepareIndemAgt
ResEng_PrepareReserveReport --> CompCounsel_ExtractGovTerms
Acct_CommenceAudit --> CompCounsel_ExtractGovTerms
CompCounsel_ReviewMatlContracts --> CompCounsel_FlagDDGaps
CompCounsel_ReviewRelPartyTxn --> CompCounsel_FlagDDGaps
CompCounsel_ReviewLitigation --> CompCounsel_FlagDDGaps
CompCounsel_FlagDDGaps --> CompCounsel_ExtractGovTerms
Issuer_CompileOpsData --> CompCounsel_ExtractGovTerms

%% ============================================================
%% PHASE 2A: S-1 Exhibit Document Drafting
%% ============================================================
subgraph P2A["Phase 2A: S-1 Exhibit Document Drafting"]
    CompCounsel_ExtractGovTerms["Company Counsel: Extract governance terms<br/>from VDR>Governance"]
    CompCounsel_DraftUnitholderRights["Company Counsel: Draft unitholder rights<br/>& GP powers provisions"]
    CompCounsel_DraftIDRSubord["Company Counsel: Draft IDR tier structure<br/>& subordination period mechanics"]
    CompCounsel_DraftFiduciary["Company Counsel: Draft fiduciary duty<br/>modifications & conflicts provisions"]
    CompCounsel_ReviewLPADraft["Company Counsel: Review & negotiate<br/>complete LPA draft"]
    CompCounsel_DraftContribAgt["Company Counsel: Draft Contribution Agreement<br/>from VDR>Governance<br/>(sponsor assets → MLP)"]
    CompCounsel_DraftOmnibusAgt["Company Counsel: Draft Omnibus Agreement<br/>from VDR>Legal<br/>(indemnification, non-compete, ROFO)"]
    CompCounsel_DraftServicesAgt["Company Counsel: Draft Services Agreement<br/>from VDR>Governance"]
    CompCounsel_DraftRegRightsAgt["Company Counsel: Draft Registration Rights Agreement<br/>from VDR>Governance"]
    CompCounsel_DraftLTIP["Company Counsel: Draft LTIP<br/>from VDR>Governance"]
    TaxCounsel_ObtainTaxOpinion["Tax Counsel: Obtain tax opinion from VDR>Tax<br/>(qualifying income, pass-through,<br/>disguised sale rules)"]
end

%% Phase 2A Connections
CompCounsel_ExtractGovTerms --> CompCounsel_DraftUnitholderRights
CompCounsel_ExtractGovTerms --> CompCounsel_DraftIDRSubord
CompCounsel_ExtractGovTerms --> CompCounsel_DraftFiduciary
CompCounsel_DraftUnitholderRights --> CompCounsel_ReviewLPADraft
CompCounsel_DraftIDRSubord --> CompCounsel_ReviewLPADraft
CompCounsel_DraftFiduciary --> CompCounsel_ReviewLPADraft
CompCounsel_ReviewLPADraft --> CompCounsel_DraftContribAgt
CompCounsel_ReviewLPADraft --> CompCounsel_DraftOmnibusAgt
CompCounsel_ReviewLPADraft --> CompCounsel_DraftServicesAgt
CompCounsel_ReviewLPADraft --> CompCounsel_DraftRegRightsAgt
CompCounsel_ReviewLPADraft --> CompCounsel_DraftLTIP
CompCounsel_DraftContribAgt --> TaxCounsel_ObtainTaxOpinion
CompCounsel_DraftOmnibusAgt --> TaxCounsel_ObtainTaxOpinion
CompCounsel_DraftServicesAgt --> TaxCounsel_ObtainTaxOpinion
CompCounsel_DraftRegRightsAgt --> TaxCounsel_ObtainTaxOpinion
CompCounsel_DraftLTIP --> TaxCounsel_ObtainTaxOpinion
TaxCounsel_ObtainTaxOpinion --> CompCounsel_PullOpsData

%% ============================================================
%% PHASE 2B: S-1 Prospectus Drafting
%% ============================================================
subgraph P2B["Phase 2B: S-1 Prospectus Drafting"]
    CompCounsel_PullOpsData["Company Counsel: Pull acreage, drilling<br/>& reserve data from VDR>Ops"]
    CompCounsel_DraftCompStrengths["Company Counsel: Draft competitive<br/>strengths narrative"]
    CompCounsel_DraftBizStrategy["Company Counsel: Draft business strategy<br/>& midstream advantage sections"]
    CompCounsel_DraftReserveDisc["Company Counsel: Draft reserve disclosure<br/>per Reg S-K Subpart 1200"]
    CompCounsel_VerifyReserveConsist["Company Counsel: Verify Item 1 consistency<br/>with reserve engineer report"]
    CompCounsel_AssistItem1["Company Counsel: Assist Item 1 narrative<br/>(tone, reserve<br/>report consistency)"]
    Issuer_AnalyzeProdPriceCost["Issuer: Analyze production, price<br/>& cost trends from VDR>Financials"]
    Issuer_DraftMDANarrative["Issuer: Draft MD&A narrative<br/>(liquidity, capital resources,<br/>known trends)"]
    Issuer_MgmtVerifyMDA["Issuer: CFO/management verify<br/>MD&A numbers & business context"]
    Issuer_GenerateMDATables["Issuer: Generate MD&A sensitivity tables & pro forma schedules"]
    CompCounsel_DraftCommodityRisks["Company Counsel: Draft commodity price<br/>& reserve estimation risk factors"]
    CompCounsel_DraftRegEnvRisks["Company Counsel: Draft regulatory<br/>& environmental risk factors"]
    CompCounsel_DraftMLPRisks["Company Counsel: Draft MLP-specific risks<br/>(conflicts, IDR dilution,<br/>limited voting rights)"]
    CompCounsel_DraftTaxRisks["Company Counsel: Draft unitholder tax risks<br/>(UBTI, K-1 complexity,<br/>state filing obligations)"]
    CompCounsel_CrossCheckSECTrends["Company Counsel: Cross-check risk factors<br/>against SEC comment letter trends<br/>for E&P MLPs"]
    CompCounsel_ExpandRiskFactors["Company Counsel: Expand Risk Factors<br/>with mitigants & detailed<br/>disclosure language"]
    CompCounsel_DraftLegalProc["Company Counsel: Draft Item 3 Legal Proceedings<br/>from VDR>Risks"]
    Acct_PrepareFS["Accountants: Prepare Item 8 FS & Notes<br/>(PCAOB) from VDR>Financials"]
    Issuer_ComputeUoP["Issuer: Compute Use of Proceeds<br/>from offering terms"]
    Issuer_BuildCapDilTables["Issuer: Build Capitalization<br/>& Dilution tables"]
    Issuer_BankersSetTerms["Issuer: Bankers/counsel set<br/>offering terms & verify tables"]
    Acct_PrepareSelFinData["Accountants: Prepare Selected Financial Data<br/>from VDR>Financials"]
    CompCounsel_ExtractLPADistTerms["Company Counsel: Extract MQD & IDR<br/>terms from LPA"]
    CompCounsel_DraftSubordMechanics["Company Counsel: Draft subordination<br/>period mechanics narrative"]
    CompCounsel_DraftIDRSplitDisc["Company Counsel: Draft IDR split<br/>schedule & distribution waterfall"]
    CompCounsel_GenerateCashDistNarr["Company Counsel: Generate Cash Distribution<br/>narrative with IDR tier examples"]
    CompCounsel_DistillEquityStory["Company Counsel: Distill equity story<br/>& competitive strengths for Summary"]
    CompCounsel_CompileFinSummary["Company Counsel: Compile summary<br/>financial data & offering terms"]
    CompCounsel_DraftBoxSection["Company Counsel: Draft Box section<br/>(front-of-prospectus summary)"]
    CompCounsel_AssistSummaryBox["Company Counsel: Assist Summary/Box<br/>(tone, trace claims<br/>to detailed sections)"]
    TaxCounsel_DraftPassThrough["Tax Counsel: Draft pass-through<br/>taxation & K-1 reporting sections"]
    TaxCounsel_DraftUBTIStateForeign["Tax Counsel: Draft UBTI, state filing<br/>& foreign investor withholding"]
    TaxCounsel_VerifyTaxAccuracy["Tax Counsel: Tax counsel verify<br/>technical accuracy of all tax sections"]
    TaxCounsel_AssistTaxConseq["Tax Counsel: Assist Tax Consequences<br/>(unitholder tax scenarios)"]
    CompCounsel_DraftUnitsDesc["Company Counsel: Draft Description<br/>of Common Units from LPA"]
    CompCounsel_DraftSellingUnitholders["Company Counsel: Draft Selling<br/>Unitholders section"]
    CompCounsel_DraftUnderwriting["Company Counsel: Draft Underwriting<br/>section (w/ UW counsel input<br/>on negotiated terms)"]
    CompCounsel_PreparePartII["Company Counsel: Prepare Part II (indemnification, unregistered sales, expenses)"]
    CompCounsel_CompileMatlContracts["Company Counsel: Compile material contracts<br/>as exhibits from VDR>Legal"]
    CompCounsel_ObtainExhibitConsents["Company Counsel: Obtain reserve engineer,<br/>auditor & nominee consents"]
    CompCounsel_IndexOrgDocs["Company Counsel: Index organizational<br/>documents & verify exhibit list<br/>completeness"]
    Decision_SectionsConsistent{"Sections consistent<br/>with each other?"}
end

%% Phase 2B Connections
CompCounsel_PullOpsData --> CompCounsel_DraftCompStrengths
CompCounsel_PullOpsData --> CompCounsel_DraftBizStrategy
CompCounsel_PullOpsData --> CompCounsel_DraftReserveDisc
CompCounsel_DraftCompStrengths --> CompCounsel_VerifyReserveConsist
CompCounsel_DraftBizStrategy --> CompCounsel_VerifyReserveConsist
CompCounsel_DraftReserveDisc --> CompCounsel_VerifyReserveConsist
CompCounsel_VerifyReserveConsist --> CompCounsel_AssistItem1
CompCounsel_AssistItem1 --> Issuer_AnalyzeProdPriceCost
Issuer_AnalyzeProdPriceCost --> Issuer_DraftMDANarrative
Issuer_DraftMDANarrative --> Issuer_MgmtVerifyMDA
Issuer_MgmtVerifyMDA --> Issuer_GenerateMDATables
Issuer_GenerateMDATables --> CompCounsel_DraftCommodityRisks
Issuer_GenerateMDATables --> CompCounsel_DraftRegEnvRisks
Issuer_GenerateMDATables --> CompCounsel_DraftMLPRisks
Issuer_GenerateMDATables --> CompCounsel_DraftTaxRisks
CompCounsel_DraftCommodityRisks --> CompCounsel_CrossCheckSECTrends
CompCounsel_DraftRegEnvRisks --> CompCounsel_CrossCheckSECTrends
CompCounsel_DraftMLPRisks --> CompCounsel_CrossCheckSECTrends
CompCounsel_DraftTaxRisks --> CompCounsel_CrossCheckSECTrends
CompCounsel_CrossCheckSECTrends --> CompCounsel_ExpandRiskFactors
CompCounsel_ExpandRiskFactors --> CompCounsel_DraftLegalProc
CompCounsel_DraftLegalProc --> Acct_PrepareFS
Acct_PrepareFS --> Issuer_ComputeUoP
Acct_PrepareFS --> Issuer_BuildCapDilTables
Issuer_ComputeUoP --> Issuer_BankersSetTerms
Issuer_BuildCapDilTables --> Issuer_BankersSetTerms
Issuer_BankersSetTerms --> Acct_PrepareSelFinData
Acct_PrepareSelFinData --> CompCounsel_ExtractLPADistTerms
CompCounsel_ExtractLPADistTerms --> CompCounsel_DraftSubordMechanics
CompCounsel_ExtractLPADistTerms --> CompCounsel_DraftIDRSplitDisc
CompCounsel_DraftSubordMechanics --> CompCounsel_GenerateCashDistNarr
CompCounsel_DraftIDRSplitDisc --> CompCounsel_GenerateCashDistNarr
CompCounsel_GenerateCashDistNarr --> CompCounsel_DistillEquityStory
CompCounsel_GenerateCashDistNarr --> CompCounsel_CompileFinSummary
CompCounsel_DistillEquityStory --> CompCounsel_DraftBoxSection
CompCounsel_CompileFinSummary --> CompCounsel_DraftBoxSection
CompCounsel_DraftBoxSection --> CompCounsel_AssistSummaryBox
CompCounsel_AssistSummaryBox --> TaxCounsel_DraftPassThrough
CompCounsel_AssistSummaryBox --> TaxCounsel_DraftUBTIStateForeign
TaxCounsel_DraftPassThrough --> TaxCounsel_VerifyTaxAccuracy
TaxCounsel_DraftUBTIStateForeign --> TaxCounsel_VerifyTaxAccuracy
TaxCounsel_VerifyTaxAccuracy --> TaxCounsel_AssistTaxConseq
TaxCounsel_AssistTaxConseq --> CompCounsel_PreparePartII
Issuer_GenerateMDATables --> CompCounsel_DraftUnitsDesc
Issuer_GenerateMDATables --> CompCounsel_DraftSellingUnitholders
CompCounsel_DraftUnitsDesc --> CompCounsel_DraftUnderwriting
CompCounsel_DraftSellingUnitholders --> CompCounsel_DraftUnderwriting
CompCounsel_DraftUnderwriting --> CompCounsel_PreparePartII
CompCounsel_PreparePartII --> CompCounsel_CompileMatlContracts
CompCounsel_PreparePartII --> CompCounsel_ObtainExhibitConsents
CompCounsel_CompileMatlContracts --> CompCounsel_IndexOrgDocs
CompCounsel_ObtainExhibitConsents --> CompCounsel_IndexOrgDocs
CompCounsel_IndexOrgDocs --> Decision_SectionsConsistent
Decision_SectionsConsistent -->|No| CompCounsel_PullOpsData
Decision_SectionsConsistent -->|Yes| CompCounsel_Review1VDR

%% ============================================================
%% PHASE 2C: Internal Review Cycles
%% ============================================================
subgraph P2C["Phase 2C: Internal Review Cycles"]
    CompCounsel_Review1VDR["Company Counsel: First review: cross-check<br/>against VDR"]
    CompCounsel_Review2CrossRefs["Company Counsel: Second review: cross-refs,<br/>defined terms, financial ties<br/>(MD&A↔FS↔Summary↔Cap)"]
    CompCounsel_CheckDefinedTerms["Company Counsel: Cross-check defined<br/>terms consistency; flag mismatches"]
    CompCounsel_CheckNarrConsist["Company Counsel: Check narrative<br/>consistency across all sections"]
    CompCounsel_ReviewGunJumping["Company Counsel: Review for<br/>gun-jumping compliance<br/>(30-day bright-line test)"]
    CompCounsel_VerifyFLSSafeHarbor["Company Counsel: Verify forward-looking<br/>statement safe harbor language"]
    CompCounsel_Section11Review["Company Counsel: Full Section 11 liability<br/>review of registration statement"]
    Decision_ReviewResolved{"All review comments resolved?"}
    Issuer_FinalSignOff["Issuer: Execute final internal sign-off on draft S-1"]
end

%% Phase 2C Connections
CompCounsel_Review1VDR --> CompCounsel_Review2CrossRefs
CompCounsel_Review2CrossRefs --> CompCounsel_CheckDefinedTerms
CompCounsel_CheckDefinedTerms --> CompCounsel_CheckNarrConsist
CompCounsel_CheckNarrConsist --> CompCounsel_ReviewGunJumping
CompCounsel_ReviewGunJumping --> CompCounsel_VerifyFLSSafeHarbor
CompCounsel_VerifyFLSSafeHarbor --> CompCounsel_Section11Review
CompCounsel_Section11Review --> Decision_ReviewResolved
Decision_ReviewResolved -->|No| CompCounsel_Review1VDR
Decision_ReviewResolved -->|Yes| Issuer_FinalSignOff
Issuer_FinalSignOff --> CompCounsel_ObtainCUSIP

%% ============================================================
%% PHASE 3: Pre-Filing Mechanics
%% ============================================================
subgraph P3["Phase 3: S-1 Filing Preparation"]
    CompCounsel_PrepareIndemAgt["Company Counsel: Prepare indemnification<br/>agreements (S-1 exhibit)"]
    CompCounsel_ObtainCUSIP["Company Counsel: Obtain CUSIP number"]
    CompCounsel_CollectSigPages["Company Counsel: Collect executed signature<br/>pages & powers of attorney"]
    CompCounsel_ObtainCIKCCC["Company Counsel: Obtain CIK/CCC EDGAR codes"]
    CompCounsel_CheckRegSK["Company Counsel: Check Reg S-K<br/>narrative disclosure requirements"]
    CompCounsel_CheckRegSX["Company Counsel: Check Reg S-X<br/>financial statement requirements"]
    CompCounsel_VerifySigExhibits["Company Counsel: Verify signatures,<br/>powers of attorney & exhibit list"]
    CompCounsel_Edgarize["Company Counsel: Edgarize S-1 & exhibits; test EDGAR filing"]
    CompCounsel_PrepareRule134["Company Counsel: Prepare Rule 134 press release"]
    Decision_S1Ready{"S-1 ready for submission?"}
end

%% Phase 3 Connections
CompCounsel_PrepareIndemAgt --> CompCounsel_CompileMatlContracts
Issuer_FinalSignOff --> CompCounsel_CollectSigPages
Issuer_FinalSignOff --> CompCounsel_ObtainCIKCCC
CompCounsel_ObtainCUSIP --> CompCounsel_CheckRegSK
CompCounsel_CollectSigPages --> CompCounsel_CheckRegSK
CompCounsel_ObtainCIKCCC --> CompCounsel_CheckRegSK
CompCounsel_CheckRegSK --> CompCounsel_CheckRegSX
CompCounsel_CheckRegSX --> CompCounsel_VerifySigExhibits
CompCounsel_VerifySigExhibits --> CompCounsel_Edgarize
CompCounsel_Edgarize --> CompCounsel_PrepareRule134
CompCounsel_PrepareRule134 --> Decision_S1Ready
Decision_S1Ready -->|No| CompCounsel_CheckRegSK
Decision_S1Ready -->|Yes| CompCounsel_AssembleDRSPackage

%% ============================================================
%% PHASE 4: Confidential Submission & SEC Review
%% ============================================================
subgraph P4["Phase 4: Confidential Submission & SEC Review"]

    subgraph P4A["Filing with SEC, FINRA, and Exchange"]
        CompCounsel_AssembleDRSPackage["Company Counsel: Assemble final S-1<br/>+ all exhibits into DRS package"]
        CompCounsel_VerifyExhibitsAttached["Company Counsel: Verify all exhibits<br/>& consents attached"]
        CompCounsel_CounselConfirmDRS["Company Counsel: Counsel confirms<br/>DRS completeness for submission"]
        Acct_ObtainAuditorConsent["Accountants: Obtain signed auditor's consent"]
        CompCounsel_SubmitDRS["Company Counsel: Submit confidential DRS via EDGAR"]
        UWCounsel_FileFINRA["UW Counsel: File with FINRA within 1 business day (Rule 5110)"]
        UWCounsel_SubmitExchange["UW Counsel: Submit S-1 to NYSE/Nasdaq for review"]
        Acct_ComfortLetterScope["Accountants: Discuss comfort letter scope<br/>(AS 6101); circle-up begins;<br/>auditors deliver initial draft"]
    end

    subgraph P4B["SEC Review & Amendment Cycle"]
        SEC_AssignExaminer["SEC: SEC assigns examiner team<br/>(Div of Corp Finance)"]
        SEC_CommentLetterReceived{"SEC: SEC comment letter<br/>received?<br/>(27-30 cal days)"}
        CompCounsel_CategorizeSECComments["Company Counsel: Categorize SEC comments<br/>by section (reserves, MD&A,<br/>risks, tax, other)"]
        CompCounsel_DraftResponseLetter["Company Counsel: Draft response letter<br/>addressing each comment"]
        CompCounsel_DraftS1AAmendments["Company Counsel: Draft proposed<br/>S-1/A amendments per responses"]
        CompCounsel_CounselMgmtReview["Company Counsel: Counsel & management<br/>review responses & amendments"]
        CompCounsel_FileAmendedDRS["Company Counsel: File amended DRS (S-1/A) via EDGAR"]
        SEC_FollowUpComments{"SEC: SEC follow-up<br/>comments?<br/>(2-3 wks)"}
        SEC_AllCommentsCleared{"All SEC comments cleared?"}
        CompCounsel_PublicFileConf["Company Counsel: Publicly file all prior<br/>confidential submissions<br/>(≥15 days before roadshow)"]
        UWCounsel_UpdateFINRA["UW Counsel: Update FINRA filing;<br/>pay additional fees"]
        SEC_FINRANoObjections{"FINRA: No Objections or Unreasonable?"}
        UWCounsel_ObtainFINRALetter["UW Counsel: Obtain FINRA No Objections<br/>letter (15-25 bus. days)"]
        SEC_ExchangeApproved{"Exchange listing approved?"}
    end

end

%% Phase 4 Connections
CompCounsel_AssembleDRSPackage --> CompCounsel_VerifyExhibitsAttached
CompCounsel_VerifyExhibitsAttached --> CompCounsel_CounselConfirmDRS
CompCounsel_CounselConfirmDRS --> Acct_ObtainAuditorConsent
Acct_ObtainAuditorConsent --> CompCounsel_SubmitDRS
CompCounsel_SubmitDRS --> UWCounsel_FileFINRA
CompCounsel_SubmitDRS --> UWCounsel_SubmitExchange
CompCounsel_SubmitDRS --> Acct_ComfortLetterScope
CompCounsel_SubmitDRS --> SEC_AssignExaminer
UWCounsel_FileFINRA --> UWCounsel_UpdateFINRA
UWCounsel_SubmitExchange --> SEC_ExchangeApproved
Acct_ComfortLetterScope --> Decision_PreEffConditions
SEC_AssignExaminer --> SEC_CommentLetterReceived
SEC_CommentLetterReceived -->|Pending| SEC_CommentLetterReceived
SEC_CommentLetterReceived -->|Yes| CompCounsel_CategorizeSECComments
CompCounsel_CategorizeSECComments --> CompCounsel_DraftResponseLetter
CompCounsel_DraftResponseLetter --> CompCounsel_DraftS1AAmendments
CompCounsel_DraftS1AAmendments --> CompCounsel_CounselMgmtReview
CompCounsel_CounselMgmtReview --> CompCounsel_FileAmendedDRS
CompCounsel_FileAmendedDRS --> SEC_FollowUpComments
SEC_FollowUpComments -->|Yes| CompCounsel_CategorizeSECComments
SEC_FollowUpComments -->|No| SEC_AllCommentsCleared
SEC_AllCommentsCleared -->|No| CompCounsel_CategorizeSECComments
SEC_AllCommentsCleared -->|Yes| CompCounsel_PublicFileConf
CompCounsel_PublicFileConf --> UWCounsel_UpdateFINRA
UWCounsel_UpdateFINRA --> SEC_FINRANoObjections
SEC_FINRANoObjections -->|Unreasonable| UWCounsel_UpdateFINRA
SEC_FINRANoObjections -->|No Objections| UWCounsel_ObtainFINRALetter
UWCounsel_ObtainFINRALetter --> SEC_ExchangeApproved
SEC_ExchangeApproved -->|No| UWCounsel_SubmitExchange
SEC_ExchangeApproved -->|Yes| CompCounsel_FileRedHerring
SEC_ExchangeApproved -->|Yes| UWCounsel_PrepareBlueSky
SEC_ExchangeApproved -->|Yes| CompCounsel_ReviewRoadshow
SEC_ExchangeApproved -->|Yes| CompCounsel_PrepareForm3s
SEC_ExchangeApproved -->|Yes| CompCounsel_PrepareForm8A

%% ============================================================
%% PHASE 5: Pre-Effectiveness Mechanics
%% ============================================================
subgraph P5["Phase 5: Pre-Effectiveness Filing Mechanics"]
    CompCounsel_FileRedHerring["Company Counsel: File & print preliminary prospectus (red herring)"]
    UWCounsel_PrepareBlueSky["UW Counsel: Prepare preliminary blue sky memo"]
    CompCounsel_ReviewRoadshow["Company Counsel: Review roadshow for S-1 consistency & gun-jumping"]
    CompCounsel_IssueLaunchPR["Company Counsel: Issue Rule 134 launch press release"]
    CompCounsel_PrepareForm3s["Company Counsel: Prepare Form 3s<br/>(Sec 16 beneficial ownership)"]
    CompCounsel_PrepareForm8A["Company Counsel: Prepare Form 8-A (Exchange Act registration)"]
    CompCounsel_FinalizeListingApp["Company Counsel: Finalize listing application;<br/>confirm exchange approval"]
    Decision_FSCurrent{"FS current under 135-day staleness rule?"}
    Decision_PreEffConditions{"All pre-effectiveness<br/>conditions met?<br/>(FINRA, exchange, FS, consents)"}
end

%% Phase 5 Connections
%% Group A (road show prep): CompCounsel_FileRedHerring, UWCounsel_PrepareBlueSky, CompCounsel_ReviewRoadshow --> converge at CompCounsel_IssueLaunchPR
CompCounsel_FileRedHerring --> CompCounsel_IssueLaunchPR
UWCounsel_PrepareBlueSky --> CompCounsel_IssueLaunchPR
CompCounsel_ReviewRoadshow --> CompCounsel_IssueLaunchPR
%% Group B (pre-effectiveness filings): CompCounsel_PrepareForm3s, CompCounsel_PrepareForm8A --> converge at CompCounsel_FinalizeListingApp
CompCounsel_PrepareForm3s --> CompCounsel_FinalizeListingApp
CompCounsel_PrepareForm8A --> CompCounsel_FinalizeListingApp
%% Both groups converge at Decision_FSCurrent
CompCounsel_IssueLaunchPR --> Decision_FSCurrent
CompCounsel_FinalizeListingApp --> Decision_FSCurrent
Decision_FSCurrent -->|No - Stale| CompCounsel_FileAmendedDRS
Decision_FSCurrent -->|Yes - Current| Decision_PreEffConditions
Decision_PreEffConditions -->|No| CompCounsel_FinalizeListingApp
Decision_PreEffConditions -->|Yes| Issuer_BringDownDD

%% ============================================================
%% PHASE 6: Effectiveness
%% ============================================================
subgraph P6["Phase 6: Effectiveness"]
    Issuer_BringDownDD["Issuer: Conduct bring-down DD call"]
    CompCounsel_RequestAccel["Company Counsel: Deliver to SEC request<br/>for acceleration<br/>(Rule 461; 2 bus. days prior)"]
    UW_JoinAccelRequest["Underwriters: Deliver to SEC letter joining acceleration request"]
    SEC_DeclaresEffective{"SEC declares S-1 effective?"}
    Milestone_Effective(["SEC DECLARES REGISTRATION<br/>STATEMENT EFFECTIVE<br/>— END —"])
end

%% Phase 6 Connections
Issuer_BringDownDD --> CompCounsel_RequestAccel
CompCounsel_RequestAccel --> UW_JoinAccelRequest
UW_JoinAccelRequest --> SEC_DeclaresEffective
SEC_DeclaresEffective -->|No| CompCounsel_CategorizeSECComments
SEC_DeclaresEffective -->|Yes| Milestone_Effective

%% ============================================================
%% STYLE DEFINITIONS — Okabe-Ito Colorblind-Safe Palette
%% ============================================================
%%
%% Color Legend (8 roles):
%% Company Counsel          = Blue           #0072B2  (white text)
%% Issuer (Management)      = Orange         #E69F00  (black text)
%% Underwriters             = Sky Blue       #56B4E9  (black text)
%% Underwriters' Counsel    = Bluish Green   #009E73  (white text)
%% Accountants              = Yellow         #F0E442  (black text)
%% Reserve Engineer         = Vermillion     #D55E00  (white text)
%% Tax Counsel              = Reddish Purple #CC79A7  (black text)
%% SEC/FINRA/Exchange       = Black          #000000  (white text)
%%
%% Decision diamonds (Decision_VDRReady, Decision_SectionsConsistent, Decision_ReviewResolved, Decision_S1Ready, Decision_FSCurrent, Decision_PreEffConditions): default Mermaid styling
%% Start/End milestones (Milestone_IPOTrigger, Milestone_Effective): default Mermaid styling

%% --- Company Counsel (Blue #0072B2) ---
style CompCounsel_ReviewMatlContracts stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ReviewRelPartyTxn stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ReviewLitigation stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_FlagDDGaps stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ExtractGovTerms stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftUnitholderRights stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftIDRSubord stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftFiduciary stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ReviewLPADraft stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftContribAgt stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftOmnibusAgt stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftServicesAgt stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftRegRightsAgt stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftLTIP stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_PullOpsData stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftCompStrengths stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftBizStrategy stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftReserveDisc stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_VerifyReserveConsist stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_AssistItem1 stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftCommodityRisks stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftRegEnvRisks stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftMLPRisks stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftTaxRisks stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CrossCheckSECTrends stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ExpandRiskFactors stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftLegalProc stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ExtractLPADistTerms stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftSubordMechanics stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftIDRSplitDisc stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_GenerateCashDistNarr stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DistillEquityStory stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CompileFinSummary stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftBoxSection stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_AssistSummaryBox stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftUnitsDesc stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftSellingUnitholders stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftUnderwriting stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_PreparePartII stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CompileMatlContracts stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ObtainExhibitConsents stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_IndexOrgDocs stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_Review1VDR stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_Review2CrossRefs stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CheckDefinedTerms stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CheckNarrConsist stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ReviewGunJumping stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_VerifyFLSSafeHarbor stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_Section11Review stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_PrepareIndemAgt stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ObtainCUSIP stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CollectSigPages stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ObtainCIKCCC stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CheckRegSK stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CheckRegSX stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_VerifySigExhibits stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_Edgarize stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_PrepareRule134 stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_AssembleDRSPackage stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_VerifyExhibitsAttached stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CounselConfirmDRS stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_SubmitDRS stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CategorizeSECComments stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftResponseLetter stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_DraftS1AAmendments stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_CounselMgmtReview stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_FileAmendedDRS stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_PublicFileConf stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_FileRedHerring stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_ReviewRoadshow stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_IssueLaunchPR stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_PrepareForm3s stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_PrepareForm8A stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_FinalizeListingApp stroke:#000,fill:#0072B2,color:#FFF
style CompCounsel_RequestAccel stroke:#000,fill:#0072B2,color:#FFF

%% --- Issuer / Management (Orange #E69F00) ---
style Issuer_EstablishVDR stroke:#000,fill:#E69F00,color:#000
style Issuer_RunChecklistComparison stroke:#000,fill:#E69F00,color:#000
style Issuer_FlagVDRGaps stroke:#000,fill:#E69F00,color:#000
style Issuer_ConfirmPhysicalComplete stroke:#000,fill:#E69F00,color:#000
style Issuer_AssignSectionOwners stroke:#000,fill:#E69F00,color:#000
style Issuer_HoldOrgMeeting stroke:#000,fill:#E69F00,color:#000
style Issuer_CompileOpsData stroke:#000,fill:#E69F00,color:#000
style Issuer_AnalyzeProdPriceCost stroke:#000,fill:#E69F00,color:#000
style Issuer_DraftMDANarrative stroke:#000,fill:#E69F00,color:#000
style Issuer_MgmtVerifyMDA stroke:#000,fill:#E69F00,color:#000
style Issuer_GenerateMDATables stroke:#000,fill:#E69F00,color:#000
style Issuer_ComputeUoP stroke:#000,fill:#E69F00,color:#000
style Issuer_BuildCapDilTables stroke:#000,fill:#E69F00,color:#000
style Issuer_BankersSetTerms stroke:#000,fill:#E69F00,color:#000
style Issuer_FinalSignOff stroke:#000,fill:#E69F00,color:#000
style Issuer_BringDownDD stroke:#000,fill:#E69F00,color:#000

%% --- Underwriters (Sky Blue #56B4E9) ---
style UW_JoinAccelRequest stroke:#000,fill:#56B4E9,color:#000

%% --- Underwriters' Counsel (Bluish Green #009E73) ---
style UWCounsel_FileFINRA stroke:#000,fill:#009E73,color:#FFF
style UWCounsel_SubmitExchange stroke:#000,fill:#009E73,color:#FFF
style UWCounsel_UpdateFINRA stroke:#000,fill:#009E73,color:#FFF
style UWCounsel_ObtainFINRALetter stroke:#000,fill:#009E73,color:#FFF
style UWCounsel_PrepareBlueSky stroke:#000,fill:#009E73,color:#FFF

%% --- Accountants (Yellow #F0E442) ---
style Acct_CommenceAudit stroke:#000,fill:#F0E442,color:#000
style Acct_PrepareFS stroke:#000,fill:#F0E442,color:#000
style Acct_PrepareSelFinData stroke:#000,fill:#F0E442,color:#000
style Acct_ObtainAuditorConsent stroke:#000,fill:#F0E442,color:#000
style Acct_ComfortLetterScope stroke:#000,fill:#F0E442,color:#000

%% --- Reserve Engineer (Vermillion #D55E00) ---
style ResEng_PrepareReserveReport stroke:#000,fill:#D55E00,color:#FFF

%% --- Tax Counsel (Reddish Purple #CC79A7) ---
style TaxCounsel_ObtainTaxOpinion stroke:#000,fill:#CC79A7,color:#000
style TaxCounsel_DraftPassThrough stroke:#000,fill:#CC79A7,color:#000
style TaxCounsel_DraftUBTIStateForeign stroke:#000,fill:#CC79A7,color:#000
style TaxCounsel_VerifyTaxAccuracy stroke:#000,fill:#CC79A7,color:#000
style TaxCounsel_AssistTaxConseq stroke:#000,fill:#CC79A7,color:#000

%% --- SEC/FINRA/Exchange (Black #000000) ---
style SEC_AssignExaminer stroke:#000,fill:#000000,color:#FFF
style SEC_CommentLetterReceived stroke:#000,fill:#000000,color:#FFF
style SEC_FollowUpComments stroke:#000,fill:#000000,color:#FFF
style SEC_AllCommentsCleared stroke:#000,fill:#000000,color:#FFF
style SEC_FINRANoObjections stroke:#000,fill:#000000,color:#FFF
style SEC_ExchangeApproved stroke:#000,fill:#000000,color:#FFF
style SEC_DeclaresEffective stroke:#000,fill:#000000,color:#FFF
```
