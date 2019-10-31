---
title: 'Kurz: předpověď cen pomocí regrese pomocí Tvůrce modelů'
description: V tomto kurzu se naučíte, jak vytvořit regresní model pomocí Tvůrce modelů ML.NET pro předpověď cen, konkrétně v New Yorku City taxislužby tarifs.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/08/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 314b637b4a43725f6daeefa6097544567dcaabc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124288"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Kurz: předpověď cen pomocí regrese pomocí Tvůrce modelů

Naučte se používat Tvůrce modelů ML.NET k vytvoření regresního modelu pro předpověď cen.  Aplikace konzoly .NET, kterou vyvíjíte v tomto kurzu, předpovídá taxislužby tarify na základě historických dat o taxislužby tarifech z historických Praha.

Šablona předpovědi ceny tvůrce modelů se dá použít pro libovolný scénář, který vyžaduje hodnotu číselné předpovědi. Mezi příklady scénářů patří: předpověď ceny na pracovišti, Předpověď poptávky a prognózování prodeje.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Příprava a pochopení dat
> - Zvolit scénář
> - Načtení dat
> - Výuka modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

> [!NOTE]
> Tvůrce modelů je aktuálně ve verzi Preview.

## <a name="pre-requisites"></a>Předpoklady

Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Vytvořte v projektu adresář s názvem *data* pro uložení souborů datové sady.

1. Sada dat, která se používá ke studiu a vyhodnocení modelu Machine Learning, je původně ze sady dat NYC TLC taxislužby Trip.

    1. Datovou sadu stáhnete tak, že přejdete na [odkaz ke stažení taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    1. Po načtení stránky klikněte pravým tlačítkem myši kamkoli na stránku a vyberte **Uložit jako**.

    1. Pomocí **dialogového okna Uložit jako** uložte soubor do složky *data* , kterou jste vytvořili v předchozím kroku.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *taxi-Fare-Train. csv* a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

Každý řádek v datové sadě `taxi-fare-train.csv` obsahuje podrobnosti o cestách provedených taxislužby.

1. Otevřete sadu dat **taxi-Fare-Train. csv.**

    Poskytnutá datová sada obsahuje následující sloupce:

    - **vendor_id:** ID dodavatele taxislužby je funkce.
    - **rate_code:** Typ rychlosti taxislužby Trip je funkce.
    - **passenger_count:** Počet cestujících na cestách je funkce.
    - **trip_time_in_secs:** Doba, po kterou cesta trvala. Chcete předpovědět jízdné za cestu před dokončením cesty. V tuto chvíli nevíte, jak dlouho trvá služební cyklus. Doba odezvy tedy není funkcí a tento sloupec z modelu vyloučíte.
    - **trip_distance:** Vzdálenost na cestách je funkce.
    - **payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.
    - **fare_amount:** Celková částka taxislužby jízdné je štítek.

`label` je sloupec, který chcete předpovědět. Při provádění regresní úlohy je cílem předpovědět číselnou hodnotu. V tomto scénáři odhadu cen se předpokládá, že náklady na taxislužby jízdní část budou předpovězeny. Proto je **fare_amount** jmenovka. Identifikované `features` jsou vstupy, které modelu udělíte pro předpověď `label`. V tomto případě se zbývající sloupce s výjimkou **trip_time_in_secs** používají jako funkce nebo vstupy pro předpověď množství tarifů.

## <a name="choose-a-scenario"></a>Zvolit scénář

Abyste mohli model vyškolit, musíte si vybrat ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů. V takovém případě je scénář `Price Prediction`.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt *TaxiFarePrediction* a vyberte **Přidat** > **Machine Learning**.
1. V kroku scénář nástroje Tvůrce modelů vyberte možnost scénář *předpovědi cen* .

## <a name="load-the-data"></a>Načtení dat

Tvůrce modelů přijímá data ze dvou zdrojů, SQL Server databáze nebo místního souboru ve formátu CSV nebo TSV.

1. V kroku dat nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat *soubor* .
1. Vyberte tlačítko vedle textového pole *Vybrat soubor* a pomocí Průzkumníka souborů Procházejte a vyberte soubor *taxi-Fare-test. csv* v *datovém* adresáři.
1. V rozevíracím seznamu *sloupec pro předpověď (popisek)* vyberte *fare_amount* .
1. Rozbalte rozevírací seznam *vstupní sloupce (funkce)* a zrušte kontrolu sloupce *trip_time_in_secs* , aby se vyloučil jako funkce během školení.  Přejděte do kroku výuka nástroje Tvůrce modelů.

## <a name="train-the-model"></a>Výuka modelu

Úkol strojového učení, který se používá k výuce modelu předpovědi cen v tomto kurzu, je regrese. V průběhu procesu školení modelů vlacích sestaví model modelování samostatné modely pomocí různých regresních algoritmů a nastavení, které pro datovou sadu vyhledají nejlepší model provádění.

Čas potřebný ke školení modelu je úměrný množství dat. Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas do výuky (sekundy)** na základě velikosti zdroje dat.

1. Ponechte výchozí hodnotu tak, aby byla pro *čas do výuky (sekundy)* , pokud nechcete, aby se vlak vydával po delší dobu.
2. Vyberte *Spustit školení*.

V průběhu procesu školení se data o průběhu zobrazují v části `Progress` kroku výukového programu.

- Stav zobrazuje stav dokončení procesu školení.
- Nejlepší přesnost zobrazuje přesnost nejlepšího modelu, kterou najde tvůrce modelů, zatím. Vyšší přesnost znamená, že model se v testovacích datech podrobnějším způsobem vypovídat.
- Nejlepší algoritmus zobrazuje název nejlepšího výkonu, který našel tvůrce modelů, zatím.
- Poslední algoritmus zobrazuje název algoritmu naposledy, který tvůrce modelů použil k vytvoření výukového modelu.

Po dokončení školení přejděte k kroku vyhodnocení.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Výsledkem kroku školení bude jeden model, který má nejlepší výkon. V kroku vyhodnocení nástroje pro sestavování modelů bude v sekci výstup obsahovat algoritmus používaný modelem nejlepšího provádění v *nejlepším záznamu modelu* spolu se metrikami v *nejlepší kvalitě modelu (RSquared)* . Navíc Souhrnná tabulka obsahující pět modelů a jejich metriky.

Pokud nejste spokojeni s metrikami přesnosti, můžou vám některé jednoduché způsoby, jak zkusit a zlepšit přesnost modelu, zvýšit množství času pro výuku modelu nebo použít víc dat. V opačném případě přejděte do kroku Code (kód).

## <a name="add-the-code-to-make-predictions"></a>Přidejte kód, který provede předpovědi

V důsledku školicího procesu se vytvoří dva projekty.

- TaxiFarePredictionML. ConsoleApp: Konzolová aplikace .NET Core, která obsahuje kód pro školení modelů a ukázku kódu.
- TaxiFarePredictionML. model: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, uloženou verzi modelu nejlepšího provádění během školení a pomocnou třídu s názvem `ConsumeModel` pro vytvoření předpovědi.

1. V kroku kód nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.
1. Otevřete soubor *program.cs* v projektu *TaxiFarePrediction* .
1. Přidejte následující příkaz using pro odkaz na projekt *TaxiFarePredictionML. model* :

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Chcete-li vytvořit předpovědi pro nová data pomocí modelu, vytvořte novou instanci třídy `ModelInput` uvnitř metody `Main` vaší aplikace. Všimněte si, že částka tarifů není součástí vstupu. Důvodem je to, že model vygeneruje předpověď pro něj. 

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. Použijte metodu `Predict` ze třídy `ConsumeModel`. Metoda `Predict` načte školený model, vytvoří pro model [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) a použije ho k předpovědií nových dat. 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Spusťte aplikaci.

    Výstup generovaný programem by měl vypadat podobně jako následující fragment kódu:

    ```bash
    Predicted Fare: 14.96086
    ```

Pokud potřebujete odkazovat na vygenerované projekty později v jiném řešení, můžete je najít v adresáři `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak:
> [!div class="checklist"]
>
> - Příprava a pochopení dat
> - Zvolit scénář
> - Načtení dat
> - Výuka modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

### <a name="additional-resources"></a>Další prostředky

Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:

- [Scénáře tvůrce modelů](../automate-training-with-model-builder.md#scenarios)
- [Nevýhody](../resources/glossary.md#regression)
- [Metriky regresního modelu](../resources/metrics.md#metrics-for-regression)
- [Sada dat pro cestu NYC TLC taxislužby](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
