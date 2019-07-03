---
title: Předvídání cen prostřednictvím regrese s Tvůrce modelu
description: Tento kurz ukazuje, jak sestavit pomocí Tvůrce modelu ML.NET k předvídání cen, konkrétně tarify taxislužby města New York regresní model.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9a6f193d877fc1a679b7a3cafd7491e021cb2ad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539625"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Předvídání cen prostřednictvím regrese s Tvůrce modelu

Další informace o použití Tvůrce modelu ML.NET k sestavení [regresní model](../resources/glossary.md#regression) předpovídat ceny.  Konzolové aplikace .NET, který v tomto kurzu vyvinete předpovídá podle historických dat. tarif taxislužby města New York tarify taxislužby.

Šablonu predikce ceny Tvůrce modelu lze použít pro jakýkoli scénář vyžaduje hodnotu číselné předpovědi. Ukázkové scénáře zahrnují: organizace predikce ceny, předpověď poptávky a prognózy prodeje.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Příprava a pochopení dat
> * Zvolte scénář
> * Načtení dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Použít model pro předpovědi

> [!NOTE]
> Tvůrce modelu je aktuálně ve verzi Preview.

## <a name="pre-requisites"></a>Požadavky

Seznam požadavků a pokyny k instalaci, přejděte [Tvůrce modelu Průvodce instalací](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvoření **konzolovou aplikaci .NET Core** nazývá "TaxiFarePrediction".

1. Nainstalujte **Microsoft.ML** balíček NuGet:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *TaxiFarePrediction* projektu a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte balíček, v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Vytvořte adresář *Data* ve vašem projektu a ukládat soubory datové sady.

1. Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) dat nastavit a uložit ho. tím *Data* složky, které jste vytvořili v předchozím kroku. Tato datová sada se používá k natrénování a vyhodnocení modelu strojového učení. Tato datová sada je původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *taxislužby. tarif train.csv* a vyberte možnost **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

Každý řádek `taxi-fare-train.csv` datová sada obsahuje podrobné informace o cesty taxislužby.

1. Otevřít **taxislužby. tarif train.csv** datové sady

    Zadaná datová sada obsahuje následující sloupce:

    * **vendor_id:** ID dodavatele taxislužby je funkce.
    * **rate_code:** Typ kursu cesty taxíkem je funkce.
    * **passenger_count:** Počet cestujících na cestě je funkce.
    * **trip_time_in_secs:** Dobu trvání cesty. Chcete předpovědět tarif cesty před dokončením cesty. V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách. Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.
    * **trip_distance:** Vzdálenost cesty je funkce.
    * **payment_type:** Způsob platby (hotovosti nebo kreditní karta) je funkce.
    * **fare_amount:** Celkový počet taxislužby tarif placené je popisek.

`label` Je sloupec, který chcete předpovědět. Když provádíte úlohu regrese, cílem je předpovědět číselnou hodnotu. V tomto scénáři predikce ceny se očekává náklady jízdní taxislužby. Proto **fare_amount** popisek. Identifikovanou `features` jsou vstupy, poskytují model k predikci `label`. V takovém případě zbývající sloupce, které se používají jako vstupy nebo funkce odhadnout množství tarif.

## <a name="choose-a-scenario"></a>Zvolte scénář

K natrénování modelu, musíte vybrat ze seznamu dostupných strojového učení scénáře, které poskytuje tvůrce modelu. V takovém případě je scénář `Price Prediction`. Rozsáhlejší seznam najdete [Tvůrce modelu přehledovém článku](../automate-training-with-model-builder.md#scenarios).

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *TaxiFarePrediction* projektu a vyberte **přidat** > **Machine Learning**.
1. V kroku scénář nástroj Tvůrce modelu, vyberte *predikce ceny* scénář.

## <a name="load-the-data"></a>Načtení dat

Tvůrce modelu přijme data ze dvou zdrojů, databáze SQL serveru nebo souboru csv nebo tsv místního souboru. Další informace o požadavky na formát dat, navštivte následující [odkaz](../how-to-guides/install-model-builder.md#limitations).

1. V kroku data nástroj Tvůrce modelu, vyberte *souboru* z rozevíracího seznamu datového zdroje.
1. Vyberte tlačítko vedle *vyberte soubor* textové pole a použití Průzkumníka souborů a procházet a vybrat *taxislužby. tarif test.csv* v *Data* adresáře
1. Zvolte *fare_amount* v *popisek nebo sloupec, který se Predict* rozevírací seznam a přejděte ke kroku trénování nástroje Tvůrce modelu.

## <a name="train-the-model"></a>Trénování modelu

Strojové učení úlohy využívají k tréninku modelu predikce ceny v tomto kurzu je regrese. Během procesu trénování modelu trénovat Tvůrce modelu samostatných modelů pomocí různých regrese algoritmů a nastavení najít nejvýkonnějšího modelu pro datové sady.

Objem dat úměrné čas potřebný k natrénování modelu. Vyberte odpovídající hodnotu pomocí tohoto grafu jako vodítko `Time to train (seconds)` pole:

\* Velikost datové sady  | Typ datové sady       | Střední Čas k trénování *
------------- | ------------------ | --------------
0 - 10 Mb     | Číselné a Text   | 10 sekund
10 - 100 Mb   | Číselné a Text   | 10 minut
100 – 500 mb  | Číselné a Text   | 30 min
500 - 1 Gb    | Číselné a Text   | 60 min
1 Gb+         | Číselné a Text   | 3 hodiny +

1. Protože školení datový soubor je větší než 10MB, použijte jako hodnotu pro 600 sekund (10 minut) *čas pro učení (v sekundách)* .
2. Vyberte *spustit Trénovací*.

V průběhu procesu trénování průběh data se zobrazí v `Progress` část krok trénování.

- Stav se zobrazí stav dokončení procesu trénování.
- Největší přesností zobrazí přesnost nejvýkonnějšího modelu zatím objevila Tvůrce modelu. Vyšší přesnost znamená, že model více správně předpovědět na testovací data.
- Nejlepší algoritmus zobrazí název algoritmu nejlépe provádí provést zatím objevila Tvůrce modelu.
- Poslední algoritmus zobrazí název algoritmu Tvůrce modelu naposledy použité pro trénování modelu.

Po dokončení školení přejděte ke kroku vyhodnotit.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Výsledek kroku školení bude jeden model, který měl nejlepší výkon. V kroku vyhodnotit nástroj Tvůrce modelu, bude obsahovat výstupní sekce algoritmus používaný serverem nejvýkonnějšího modelu v *nejlepší Model* položka společně s metrikami v *nejlepší kvalita modelu (RSquared)* . Kromě toho souhrnnou tabulku obsahující pěti hlavních modelů a jejich metriky. Navštivte následující odkaz na další informace o [vyhodnocení modelu metriky](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).

Pokud si nejste spokojeni s metriky přesnosti, zvýšit množství času pro trénování modelu nebo používat další data jsou některé snadných způsobů, jak vyzkoušet a zlepšit přesnost modelu.

## <a name="use-the-model-for-predictions"></a>Použít model pro předpovědi

Dva projekty budou vytvořeny v důsledku procesu trénování.

- TaxiFarePredictionML.ConsoleApp: Aplikace konzoly .NET, která obsahuje kód modelu školení a spotřebu.
- TaxiFarePredictionML.Model: .NET Standard knihovny tříd obsahující datové modely, které definujete schéma vstupní a výstupní modelování dat, jakož i trvalou verzí nejvýkonnějšího modelu během cvičení.

1. V části kódu nástroj Tvůrce modelu vyberte **přidány projekty** přidat projekty do řešení.
2. V Průzkumníku řešení klikněte pravým tlačítkem myši *TaxiFarePrediction* projektu. Vyberte **Přidat > existující položku**. Soubor typu z rozevíracího seznamu vyberte `All Files`, přejděte *TaxiFarePredictionML.Model* projekt adresář a zaškrtnout možnost `MLModel.zip` souboru. Klikněte pravým tlačítkem na naposledy přidané `MLModel.zip` a vyberte možnost *vlastnosti*. Kopírovat do výstupního adresáře možnosti, vyberte *kopírovat, pokud je novější* z rozevíracího seznamu.
3. Klikněte pravým tlačítkem na *TaxiFarePrediction* projektu. Potom **Přidat > odkaz**. Zvolte **projektů > řešení** uzlu a ze seznamu, zkontrolujte *TaxiFarePredictionML.Model* projektu a vyberte OK.

4. Otevřít *Program.cs* soubor *TaxiFarePrediction* projektu.
5. Přidejte následující příkazy using:

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. Přidat `ConsumeModel` metodu `Program` třídy. `ConsumeModel` Vytvoří `PredictionEngine` na základě modelu generovaných Tvůrce Model k predikci na nová data a je vytisknout na konzole.

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

7. Přidejte následující kód, který `Main` metoda a spusťte aplikaci.

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

    Výstup vygenerovaný program by měl vypadat podobně jako v následujícím fragmentu kódu:

    ```bash
    Predicted Fare: 16.82245
    ```

Pokud potřebujete odkazovat na vygenerované projekty později uvnitř jiné řešení, najdete je uvnitř `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` adresáře.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Příprava a pochopení dat
> * Zvolte scénář
> * Načtení dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Použít model pro předpovědi

Přejděte k některé z některého z těchto článků se naučíte, jak model nasadit.

> [!div class="nextstepaction"]
> [Nasazení modelu do služby Azure Functions](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [Nasazení modelu pro webové rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md)
