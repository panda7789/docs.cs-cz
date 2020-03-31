---
title: 'Kurz: Předvídejte ceny pomocí regrese pomocí tvůrce modelů'
description: Tento kurz ukazuje, jak vytvořit regresní model pomocí ML.NET Model Builder předpovědět ceny, konkrétně new york city taxi tarify.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: 750738f8e3c65363e9996667feeccd1b84391f9f
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438235"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Kurz: Předvídejte ceny pomocí regrese pomocí tvůrce modelů

Naučte se používat ML.NET Tvůrce modelů k vytvoření regresního modelu k předvídání cen.  Konzolová aplikace .NET, kterou vyvíjíte v tomto kurzu, předpovídá tarify taxi na základě historických dat o jízdném taxi v New Yorku.

Šablonu předpovědi ceny tvůrce modelu lze použít pro libovolný scénář, který vyžaduje číselnou hodnotu předpovědi. Příklady scénářů zahrnují: předpověď cen domů, předpověď poptávky a prognózu prodeje.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Příprava a pochopení dat
> - Výběr scénáře
> - Načtení dat
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

> [!NOTE]
> Tvůrce modelů je momentálně ve verzi Preview.

## <a name="pre-requisites"></a>Požadavky

Seznam předpokladů a pokynů k instalaci naleznete v [instalační příručce výrobce modelů](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **aplikaci základní konzoly C# .NET** s názvem "TaxiFarePrediction". Ujistěte se, že **umístit řešení a projekt ve stejném adresáři** je **nezaškrtnuté** (VS 2019) nebo **vytvořit adresář pro řešení** je **zaškrtnuto** (VS 2017).

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.

1. Datová sada použitá k trénování a vyhodnocování modelu strojového učení je původně z datové sady NYC TLC Taxi Trip.

    1. Chcete-li stáhnout sadu dat, přejděte na [odkaz ke stažení taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    1. Po načtení stránky klikněte pravým tlačítkem myši na libovolné místo na stránce a vyberte **Uložit jako**.

    1. Pomocí **dialogového okna Uložit jako** uložte soubor do složky *Data,* kterou jste vytvořili v předchozím kroku.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *taxi-fare-train.csv* a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

Každý řádek `taxi-fare-train.csv` v datové sadě obsahuje podrobnosti o cestách taxi.

1. Otevřete datovou sadu **taxi-fare-train.csv**

    Zadaný soubor dat obsahuje následující sloupce:

    - **vendor_id:** ID dodavatele taxi služby je funkce.
    - **rate_code:** Typ sazby taxi cesty je funkce.
    - **passenger_count:** Počet cestujících na cestě je funkce.
    - **trip_time_in_secs:** Doba, po kterou cesta trvala. Chcete předpovědět jízdné cesty před dokončením cesty. V tu chvíli nevíte, jak dlouho cesta bude trvat. Doba jízdy tedy není funkcí a tento sloupec z modelu vyloučíte.
    - **trip_distance:** Vzdálenost cesty je funkce.
    - **payment_type:** Platební metoda (v hotovosti nebo kreditní kartou) je funkce.
    - **fare_amount:** Celková zaplacená taxi služba je štítek.

Je `label` sloupec, který chcete předpovědět. Při provádění regresní úlohy je cílem předpovědět číselnou hodnotu. V tomto scénáři predikce ceny se předpovězí náklady na jízdu taxíkem. Proto **fare_amount** je popisek. Identifikované `features` jsou vstupy, které poskytnete `label`modelu předpovědět . V tomto případě se zbývající sloupce s výjimkou **trip_time_in_secs** používají jako funkce nebo vstupy k předvídání částky jízdného.

## <a name="choose-a-scenario"></a>Výběr scénáře

Chcete-li trénovat model, musíte vybrat ze seznamu dostupných scénářů strojového učení poskytovaných tvůrcem modelů. V tomto případě je `Price Prediction`scénář .

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt *TaxiFarePrediction* a vyberte **přidat** > **strojové učení**.
1. V kroku scénáře nástroje Tvůrce modelů vyberte scénář *Předpověď cen.*

## <a name="load-the-data"></a>Načtení dat

Tvůrce modelů přijímá data ze dvou zdrojů, databáze serveru SQL Server nebo místního souboru ve formátu CSV nebo tsv.

1. V datovém kroku nástroje Tvůrce modelů vyberte *Soubor* z rozevíracího souboru zdroje dat.
1. Vyberte tlačítko vedle textového pole *Vybrat soubor* a pomocí Průzkumníka souborů procházet a vyberte *soubor taxi-fare-test.csv* v adresáři *Data.*
1. V rozevíracím seznamu Sloupec zvolte *fare_amount,* *který chcete předpovědět (Popisek).*
1. Rozbalte rozbalovací seznam *Vstupní sloupce (Funkce)* a odškrtnout sloupec *trip_time_in_secs,* abyste ho během tréninku vyloučili jako funkci.  Přejděte ke kroku vlaku nástroje Tvůrce modelů.

## <a name="train-the-model"></a>Trénování modelu

Úloha strojového učení slouží k trénování modelu předpověď cen v tomto kurzu je regrese. Během procesu školení modelu Model Builder trénuje samostatné modely pomocí různých regresní algoritmy a nastavení najít nejvýkonnější model pro datovou sadu.

Doba potřebná pro vyškolení modelu je úměrná množství dat. Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas pro trénování (sekundy)** na základě velikosti zdroje dat.

1. Ponechte výchozí hodnotu jako *čas pro trénování (sekundy),* pokud nechcete trénovat delší dobu.
2. Vyberte *možnost Zahájit trénink*.

V průběhu tréninkového procesu se `Progress` údaje o průběhu zobrazují v části kroku vlaku.

- Stav zobrazuje stav dokončení procesu školení.
- Nejlepší přesnost zobrazuje přesnost nejvýkonnějšího modelu, který dosud našel Model Builder. Vyšší přesnost znamená, že model byl na testovacích datech předpovězen správněji.
- Nejlepší algoritmus zobrazí název nejvýkonnějšíalgoritmus u kterého našel Model Builder tak daleko.
- Poslední algoritmus zobrazí název algoritmu, který byl naposledy použit tvůrcem modelů k trénování modelu.

Po dokončení školení přejděte ke kroku vyhodnocení.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Výsledkem tréninkového kroku bude jeden model, který měl nejlepší výkon. V kroku vyhodnocení nástroje Tvůrce modelů bude výstupní část obsahovat algoritmus používaný nejvýkonnějším modelem v položce *Nejlepší model* spolu s metrikami v *best model quality (RSquared).* Kromě toho souhrnná tabulka obsahující prvních pět modelů a jejich metriky.

Pokud nejste spokojeni s metrikami přesnosti, některé jednoduché způsoby, jak se pokusit zlepšit přesnost modelu, jsou prodloužení doby pro trénování modelu nebo použití více dat. V opačném případě přejděte na krok kódu.

## <a name="add-the-code-to-make-predictions"></a>Přidání kódu pro předpověď

V důsledku procesu školení budou vytvořeny dva projekty.

- TaxiFarePredictionML.ConsoleApp: Aplikace .NET Core Console, která obsahuje trénování modelu a kód spotřeby vzorku.
- TaxiFarePredictionML.Model: Knihovna třídy .NET Standard obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, uloženou `ConsumeModel` verzi nejvýkonnějšího modelu během trénování a pomocnou třídu volánou k předpovědi.

1. V kroku kódu nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.
1. Otevřete soubor *Program.cs* v projektu *TaxiFarePrediction.*
1. Přidejte následující příkaz using, abyste odkazovali na projekt *TaxiFarePredictionML.Model:*

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Chcete-li předpovědět nová data pomocí modelu, vytvořte `ModelInput` novou `Main` instanci třídy uvnitř metody vaší aplikace. Všimněte si, že částka jízdného není součástí vstupu. Důvodem je, že model bude generovat předpověď pro něj.

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

1. Použijte `Predict` metodu `ConsumeModel` z třídy. Metoda `Predict` načte trénovaný [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model, vytvořit pro model a používá jej k vytváření předpovědí na nová data.

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Spusťte aplikaci.

    Výstup generovaný programem by měl vypadat podobně jako výstřižek níže:

    ```bash
    Predicted Fare: 14.96086
    ```

Pokud potřebujete odkazovat na generované projekty později uvnitř jiného řešení, `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` můžete je najít uvnitř adresáře.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Příprava a pochopení dat
> - Výběr scénáře
> - Načtení dat
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

### <a name="additional-resources"></a>Další zdroje

Další informace o tématech uvedených v tomto kurzu naleznete v následujících zdrojích:

- [Scénáře tvůrce modelů](../automate-training-with-model-builder.md#scenario)
- [Regrese](../resources/glossary.md#regression)
- [Metriky regresního modelu](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [NYC TLC Taxi Výlet datový soubor](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
