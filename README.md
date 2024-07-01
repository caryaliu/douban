flowchart TD
    A[Start] --> B{Directory "pages" exists?}
    B -- Yes --> C[Proceed]
    B -- No --> D[Create "pages" directory]
    D --> C

    C --> E[Main Function]

    E --> F[Fetch Douban Top 250 Books]
    F --> G[Base URL: 'https://book.douban.com/top250?start=']
    G --> H{For page in range(10)}

    H --> I[URL: f"{base_url}{page * 25}"]
    I --> J[Fetch Page]
    J --> K[Fetch Single Page and Save]

    K --> L{Save to "pages/page_{page_number}.html"?}
    L -- Yes --> M[Print: Page Saved]
    L -- No --> E

    M --> N[Sleep for Random 2-4 Seconds]
    N --> H

    H -- Complete --> O[Parse Douban Top 250 Books]
    O --> P{For page in range(10)}

    P --> Q[Parse Single Page]
    Q --> R[Parse "pages/page_{page_number}.html"]

    R --> S[Extract Book Info]
    S --> T[Append Book Info to List]
    T --> P

    P -- Complete --> U[Save All Books to CSV]
    U --> V[Save to "douban_top250_books.csv"]
    V --> W[Print: Data Saved]

    W --> X{Print Each Book Info}
    X --> Y[For i, book in enumerate(books, 1)]
    Y --> Z[Print Book Info]
    Z --> AA{All Books Printed?}

    AA -- Yes --> AB[End]
    AA -- No --> Y
