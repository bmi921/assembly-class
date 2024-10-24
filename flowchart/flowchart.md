flowchart TD
    S[start]-->A
    A[レジスタを退避] -->B[GR2の値を10倍する]
    B --> C[GR3をGR2に加算する]
    C --> D[加算結果をGR0に入れる]
    D --> E[end]


flowchart TD
    S[start]-->A
    A[レジスタを退避] -->B[2n-1を求めてカウンタにいれる]
    B --> C[GR0をリセット]
    C --> D[GR0にカウンタを加算する]
    D --> E[カウンタを2減らす]
    E --> F{カウンタ>0}
    F --> |yes|D
    F --> |no|G[end]

flowchart TD
    S[start]-->A
    A[レジスタを退避] -->B[GR1の値をGR3に入れる]
    B --> C[GR2の値をGR4にいれる]
    C --> D[GR0を0に初期化する]
    D --> E{GR3,GR4の比較}
    E --> |GR3=GR4|I
    E --> |GR3<GR4|F[GR3からGR4を引く]
    F --> E
    E --> |GR3>GR4|H[GR4からGR3を引く]
    H--> E
    I[GR4の値をGR0に入れる]-->J[end]

flowchart TD
    S[start]-->A
    A[レジスタを退避] -->B[GR1の値をGR3に入れる]
    B --> C[GR2の値をGR4にいれる]
    C --> D[GR0を0に初期化する]
    D --> E[GR1に1をいれて、GR1とおGR3のANDをとる]
    E --> F{結果がo?1?}
    F -->|0|H[GR3を左に1シフトする]
    F-->|1|K[GR0にGR3を加算する]
    K--> 
    H--> G[GR4を右に1シフトする]
    G --> I{GR4は0?}
    I -->|yes|E
    I -->|no|X[end]

flowchart TD
    S[start]-->A
    A[レジスタを退避] -->B[カウンタにyを値を入れる]
    B --> C[GR1に1, GR2にxをいれる]
    C --> D[GR0を0に初期化する]
    D --> E[サブルーチンを呼び出す]
    E --> F[結果MをGR0に格納]
    F -->H[カウンタを1減らす]
    H--> G[GR4を右に1シフトする]
    G --> I{カウンタ>0?}
    I -->|yes|E
    I -->|no|X[end]
