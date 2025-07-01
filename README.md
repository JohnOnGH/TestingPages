# Testing
This is a testbed/scratchbed/Sandpit nothing serious here at all repository to explore features and ways of using GitHub

## And another thing
Just playing with markdown. There is no need at all for the list I'm about to introduce:
1. Item 1
2. Item 2
3. Item 3

No need at *all*.

'''mermaid
graph TD
    %% Define swimlanes for each actor
    subgraph Requester
        direction LR
        A1(Start) --> A2[Register as User];
        A2 --> A3[Draft and Submit DMR<br>(New/Modify)];
        A3 --> B1;
        C4 --> A4[Receive Notification<br>on Status Change];
        D4 --> A4;
        E6 --> A4;
        A4 --> A5(End);
    end

    subgraph DMR System
        direction LR
        B1[Receive DMR] --> B2{Automated Triage:<br>NFP for country exists?};
        B2 -- Yes --> C1;
        B2 -- No --> E1;
    end

    subgraph National Focal Point (NFP)
        direction LR
        C1[Receive DMR for Validation] --> C2{Validate Request};
        C2 -- "More Info Needed" --> A3;
        C2 -- Invalid --> C3[Reject DMR];
        C3 --> C4[Notify Requester of Rejection];
        C2 -- Valid --> D1[Forward Validated DMR];
    end

    subgraph "UNECE Secretariat / Maintenance Team"
        direction LR
        %% Path for DMRs without an NFP
        E1[Receive DMR from System] --> E2[Validate Request];
        E2 --> E3;

        %% Path for DMRs validated by an NFP
        D1 --> E3[Final Review & Approval];

        %% Common path for all approved changes
        E3 --> E4[Batch Approved Changes];
        E4 --> E5[Publish New UN/LOCODE Release<br>(Biannually)];
        E5 --> E6[Notify Requester of Publication];
        D4(End);
        C4 --> D4;
    end

    %% Styling
    style A1 fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style A5 fill:#ffcdd2,stroke:#c62828,stroke-width:2px
    style D4 fill:#ffcdd2,stroke:#c62828,stroke-width:2px
    '''
