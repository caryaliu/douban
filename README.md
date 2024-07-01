flowchart TD
    A[Start] --> B{Directory "pages" exists?}
    B -- Yes --> C[Proceed]
    B -- No --> D[Create "pages" directory]
    D --> C
    
    C --> E[Main Function]
    
    E --> F[Fetch Douban Top 250 Books]
    F --> G[Base URL: 'https://book.douban.com/top250?start=']
    G --> H{For each page in range(10)}
    
    H --> I[Generate URL for page]
    I --> J[Fetch Page and Save Locally]
    
    J --> K[Wait Random 2-4 Seconds]
    K --> H
    
    H -- Complete --> L[Parse Douban Top 250 Books]
    L --> M{For each page in range(10)}
    
    M --> N[Parse Local Page]
    N --> O[Extract Book Info and Append to List]
    O --> M
    
    M -- Complete --> P[Save All Books to CSV]
    P --> Q[Print: Data Saved]
    
    Q --> R{Print Each Book Info}
    R --> S[Print Book Info]
    S --> R
    
    R -- All Books Printed --> T[End]
