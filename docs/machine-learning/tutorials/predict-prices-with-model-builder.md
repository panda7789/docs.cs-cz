---
title: Předpověď cen pomocí regrese pomocí Tvůrce modelů
description: V tomto kurzu se naučíte, jak vytvořit regresní model pomocí Tvůrce modelů ML.NET pro předpověď cen, konkrétně v New Yorku City taxislužby tarifs.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1bdbe31e16408da2d7dfe17941c90a022f3d8c32
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107146"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Předpověď cen pomocí regrese pomocí Tvůrce modelů

Naučte se používat Tvůrce modelů ML.NET k vytvoření regresního modelu () pro předpověď cen.  Aplikace konzoly .NET, kterou vyvíjíte v tomto kurzu, předpovídá taxislužby tarify na základě historických dat o taxislužby tarifech z historických Praha.

Šablona předpovědi ceny tvůrce modelů se dá použít pro libovolný scénář, který vyžaduje hodnotu číselné předpovědi. Mezi příklady scénářů patří: předpověď ceny na pracovišti, Předpověď poptávky a prognózování prodeje.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Příprava a pochopení dat
> - Zvolit scénář
> - Načtení dat
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

> [!NOTE]
> Tvůrce modelů je aktuálně ve verzi Preview.

## <a name="pre-requisites"></a>Požadavky

Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Vytvořte v projektu adresář s názvem *data* pro uložení souborů datové sady.

1. Sada dat, která se používá ke studiu a vyhodnocení modelu Machine Learning, je původně ze sady dat NYC TLC taxislužby Trip.

    Datovou sadu stáhnete tak, že přejdete na [odkaz ke stažení taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    Po načtení stránky klikněte pravým tlačítkem myši kamkoli na stránku a vyberte **Uložit jako**.

    Pomocí **dialogového okna Uložit jako** uložte soubor do složky *data* , kterou jste vytvořili v předchozím kroku.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *taxi-Fare-Train. csv* a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

Každý řádek v `taxi-fare-train.csv` datové sadě obsahuje podrobnosti o cestách provedených taxislužby.

1. Otevřete sadu dat **taxi-Fare-Train. csv.**

    Poskytnutá datová sada obsahuje následující sloupce:

    - **vendor_id:** ID dodavatele taxislužby je funkce.
    - **rate_code:** Typ rychlosti taxislužby Trip je funkce.
    - **passenger_count:** Počet cestujících na cestách je funkce.
    - **trip_time_in_secs:** Doba, po kterou cesta trvala.
    - **trip_distance:** Vzdálenost na cestách je funkce.
    - **payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.
    - **fare_amount:** Celková částka taxislužby jízdné je štítek.

`label` Je sloupec, který chcete předpovědět. Při provádění regresní úlohy je cílem předpovědět číselnou hodnotu. V tomto scénáři odhadu cen se předpokládá, že náklady na taxislužby jízdní část budou předpovězeny. Proto je **fare_amount** jmenovka. Identifikované `features` jsou vstupy, které modelu poskytnete pro `label`předpověď. V tomto případě se zbytek sloupců používá jako funkce nebo vstupy pro předpověď množství tarifů.

## <a name="choose-a-scenario"></a>Zvolit scénář

Abyste mohli model vyškolit, musíte si vybrat ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů. V tomto případě je `Price Prediction`to scénář.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt *TaxiFarePrediction* a vyberte **Přidat** > **Machine Learning**.
1. V kroku scénář nástroje Tvůrce modelů vyberte možnost scénář *předpovědi cen* .

## <a name="load-the-data"></a>Načtení dat

Tvůrce modelů přijímá data ze dvou zdrojů, SQL Server databáze nebo místního souboru ve formátu CSV nebo TSV.

1. V kroku dat nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat *soubor* .
1. Vyberte tlačítko vedle textového pole *Vybrat soubor* a pomocí Průzkumníka souborů Procházejte a vyberte soubor *taxi-Fare-test. csv* v *datovém* adresáři.
1. V rozevíracím seznamu *popisek nebo sloupec* vyberte *fare_amount* a přejděte do kroku výuka nástroje Tvůrce modelů.

## <a name="train-the-model"></a>Trénování modelu

Úkol strojového učení, který se používá k výuce modelu předpovědi cen v tomto kurzu, je regrese. V průběhu procesu školení modelů vlacích sestaví model modelování samostatné modely pomocí různých regresních algoritmů a nastavení, které pro datovou sadu vyhledají nejlepší model provádění.

Čas potřebný ke školení modelu je úměrný množství dat. Tento graf použijte jako vodítko pro výběr vhodné hodnoty pro `Time to train (seconds)` pole:

\* Velikost datové sady  | Typ datové sady       | Střední Čas do výuky *
------------- | ------------------ | --------------
0-10 MB     | Číslice a text   | 10 sekund
10-100 MB   | Číslice a text   | 10 min
100 – 500 MB  | Číslice a text   | 30 min
500 - 1 Gb    | Číslice a text   | 60 min.
1 Gb+         | Číslice a text   | 3 hodiny +

1. Vzhledem k tomu, že soubor školicích dat je větší než 10 MB, jako hodnota *Time to vlak (sekundy)* použijte 600 sekund (10 minut).
2. Vyberte *Spustit školení*.

V průběhu procesu školení se data o průběhu zobrazují v `Progress` části kroku výuka.

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

- TaxiFarePredictionML.ConsoleApp: Konzolová aplikace .NET Core, která obsahuje kód pro školení a spotřebu modelu.
- TaxiFarePredictionML.Model: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu a také trvalou verzi modelu nejlepšího provádění během školení.

1. V kroku kód nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.
1. Klikněte pravým tlačítkem na projekt *TaxiFarePrediction* . Pak **přidejte odkaz >** . Zvolte **projekty > uzel řešení** a ze seznamu zaškrtněte projekt *TaxiFarePredictionML. model* a vyberte OK.
1. Otevřete soubor *program.cs* v projektu *TaxiFarePrediction* .
1. Přidejte následující příkazy using pro odkazování na balíček NuGet *Microsoft.ml* a projekt *TaxiFarePredictionML. model* :

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. `ConsumeModel` Přidejte metodu`Program` do třídy.

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

    Načte školený model, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) vytvoří pro model a použije ho k tomu, aby se předpovědi na nová data. `ConsumeModel`

1. Chcete-li vytvořit předpovědi pro nová data pomocí modelu, vytvořte novou instanci `ModelInput` třídy a `ConsumeModel` použijte metodu. Všimněte si, že částka tarifů není součástí vstupu. Důvodem je to, že model vygeneruje předpověď pro něj. Do `Main` metody přidejte následující kód a spusťte aplikaci.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    Výstup generovaný programem by měl vypadat podobně jako následující fragment kódu:

    ```bash
    Predicted Fare: 16.82245
    ```

Pokud potřebujete odkazovat na vygenerované projekty později v jiném řešení, můžete je vyhledat v `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` adresáři.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> - Příprava a pochopení dat
> - Zvolit scénář
> - Načtení dat
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

### <a name="additional-resources"></a>Další prostředky

Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:

- [Scénáře tvůrce modelů](../automate-training-with-model-builder.md#scenarios)
- [Nevýhody](../resources/glossary.md#regression)
- [Metriky regresního modelu](../resources/metrics.md#metrics-for-regression)
- [Sada dat pro cestu NYC TLC taxislužby](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
