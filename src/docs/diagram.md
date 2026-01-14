# Diagram przepływu rozgrywki – Tower Defense 3D

```mermaid
flowchart TD
    A[START] --> B[MENU GŁÓWNE<br/>Start, Opcje, Wyjście]
    B --> C[Wybór mapy]
    C --> D[PĘTLA ROZGRYWKI]

    D --> E[FAZA PRZYGOTOWANIA<br/>- Buduj wieże<br/>- Ulepsz / sprzedaj<br/>- Planuj ustawienie]
    D --> F[FAZA FALI<br/>- Start fali<br/>- Spawn wrogów<br/>- Walka]

    E --> G
    F --> G

    G[RUCH WROGÓW<br/>- Przejście po punktach<br/>- Dotarł do bazy?]

    G -->|NIE| H[ATAK WIEŻ<br/>- Wybór celu<br/>- Obrót do celu<br/>- Strzał<br/>- Obrażenia]
    G -->|TAK| I[OBRAŻENIA BAZY<br/>- HP bazy -= DMG<br/>- Usuń wroga]

    H --> J[ŚMIERĆ WROGA<br/>- Wróg HP <= 0<br/>- Nagroda gold<br/>- Usuń wroga]

    I --> K{HP BAZY <= 0?}
    K -->|TAK| L[PRZEGRANA]
    K -->|NIE| U[KONTYNUUJ FALE]

    U --> M[KONIEC FALI<br/>- Dodaj nagrody<br/>- Zwiększ nr fali]

    M --> V[FAZA PRZYGOTOWANIA]

    J --> N{KONIEC FALI?<br/>- Brak wrogów<br/>- Spawn zakończony}

    N --> P{OSTATNIA FALA?}
    P -->|TAK| Q[WYGRANA<br/>- ekran wyniku]
    P -->|NIE| X[PĘTLA TRWA]

    X --> V
