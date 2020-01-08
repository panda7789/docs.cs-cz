---
title: 'Kurz: klasifikace porušení stavu pomocí Tvůrce modelů'
description: Tento kurz ukazuje, jak vytvořit model klasifikace s více třídami pomocí Tvůrce modelů ML.NET ke klasifikaci závažnosti porušení stavu Restaurace v San Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 90abbc9ffe5765880d18d0d29c8e13bc1330ddc3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341558"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Kurz: klasifikace závažnosti porušení stavu restaurací pomocí Tvůrce modelů

Naučte se vytvářet model klasifikace s více třídami pomocí Tvůrce modelů ke kategorizaci úrovně rizika porušení v restauracích, která byla zjištěna během kontrol stavu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Příprava a pochopení dat
> - Zvolte scénář
> - Načtení dat z databáze
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

> [!NOTE]
> Tvůrce modelů je aktuálně ve verzi Preview.

## <a name="prerequisites"></a>Požadavky

Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Přehled klasifikace více tříd tvůrce modelů

Tato ukázka vytvoří konzolovou aplikaci C# .NET Core, která kategorizuje riziko porušení stavu pomocí modelu strojového učení sestaveného pomocí Tvůrce modelů. Zdrojový kód pro tento kurz najdete v úložišti GitHub [/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte  **C# konzolovou aplikaci .NET Core** nazvanou "RestaurantViolations". Ujistěte se, že **umístění řešení a projekt ve stejném adresáři** není **zaškrtnuté** (vs 2019), nebo je **zaškrtnuté** políčko **vytvořit adresář pro řešení** (vs 2017).

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

> Datová sada, která se používá ke studiu a vyhodnocení modelu Machine Learning, je původně od [Francisco oddělení San veřejného zdravotního hodnocení z oblasti bezpečnosti restaurace](https://www.sfdph.org/dph/EH/Food/score/default.asp). Pro usnadnění pohodlí byla datová sada zhuštěná tak, aby obsahovala pouze sloupce, které jsou relevantní pro výuku modelu a předpovědi. Další informace o této [datové sadě](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)najdete na následujícím webu.

[Stáhněte si datovou sadu výsledků pro bezpečnost restaurace](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) a rozbalte ji.

Každý řádek v datové sadě obsahuje informace o porušeních zjištěných během kontroly ze zdravotního oddělení a posouzení rizika ohrožení bezpečnosti veřejného zdraví a bezpečnosti.

| InspectionType | ViolationDescription | RiskCategory |
| --- | --- | --- |
| Rutina – neplánovaná | Nedostatečné vyčištěné nebo upravené kontaktní plochy v potravinách | Střední riziko |
| Nové vlastnictví | Vysoce rizikové napadení škůdci | Vysoké riziko |
| Rutina – neplánovaná | Vymazání tkanin není čisté nebo správně uložené nebo nedostatečného upraveného. | Nízké riziko |

- **InspectionType**: typ kontroly. Může to být buď první kontrola pro nové zařízení, rutinní kontrola, kontrola stížnosti a mnoho dalších typů.
- **ViolationDescription**: byl zjištěn popis porušení během kontroly.
- **RiskCategory**: závažnost rizika, které je porušením, představuje veřejný stav a bezpečnost.

`label` je sloupec, který chcete předpovědět. Při provádění úlohy klasifikace je cílem přiřadit kategorii (text nebo číselnou). V tomto scénáři klasifikace je závažnost porušení přiřazena hodnotě nízké, střední nebo vysoké rizikovosti. Proto je **RiskCategory** jmenovka. `features` jsou vstupy, které modelu udělíte pro předpověď `label`. V tomto případě se **InspectionType** a **ViolationDescription** používají jako funkce nebo vstupy pro předpověď **RiskCategory**.

## <a name="choose-a-scenario"></a>Zvolte scénář

![Průvodce tvůrcem modelů v aplikaci Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Pokud chcete svůj model naučit, vyberte si ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů. V takovém případě se jedná o scénář *klasifikace*.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt *RestaurantViolations* a vyberte **Přidat** > **Machine Learning**.
1. Pro tuto ukázku je scénářem klasifikace s více třídami. V kroku *scénář* v Tvůrci modelů vyberte scénář **klasifikace problému** .

## <a name="load-the-data"></a>Načtení dat

Tvůrce modelů přijímá data z databáze SQL Server nebo místního souboru ve formátu `csv` nebo `tsv`.

1. V kroku data nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat možnost **SQL Server** .
1. Vyberte tlačítko vedle textového pole **připojit k SQL Server databázi** .
    1. V dialogovém okně **Vybrat data** vyberte **Microsoft SQL Server databázový soubor**.
    1. Zrušte zaškrtnutí políčka **vždy použít tento výběr** a vyberte **pokračovat**.
    1. V dialogovém okně **Vlastnosti připojení** vyberte **Procházet** a vyberte stažený soubor *RestaurantScores. mdf* .
    1. Vyberte **OK**.
1. V rozevíracím seznamu **název tabulky** vyberte možnost **porušení** .
1. V rozevíracím seznamu **sloupec pro předpověď (popisek)** vyberte **RiskCategory** .
1. Ponechte výchozí výběry sloupců, **InspectionType** a **ViolationDescription**, zaškrtněte rozevírací seznam **vstupní sloupce (funkce)** .
1. Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v Tvůrci modelů.

## <a name="train-the-model"></a>Trénování modelu

Úkolem strojového učení, který se používá ke studiu modelu klasifikace problému v tomto kurzu, je klasifikace s více třídami. V průběhu procesu školení modelů vlacích sestaví model modelování samostatné modely pomocí různých algoritmů a nastavení třídy s více třídami, aby bylo možné najít nejlepší model pro datovou sadu.

Čas potřebný ke školení modelu je úměrný množství dat. Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas do výuky (sekundy)** na základě velikosti zdroje dat.

1. I když tvůrce modelů nastaví hodnotu **času na vlak (sekundy)** až 10 sekund, narůstá na 30 sekund. Školení po delší dobu umožňuje tvůrci modelů prozkoumat větší počet algoritmů a kombinaci parametrů při hledání nejlepšího modelu.
1. Vyberte **Spustit školení**.

    V průběhu procesu školení se data o průběhu zobrazují v části `Progress` v kroku výuka.

    - **Stav** zobrazuje stav dokončení procesu školení.
    - **Nejlepší přesnost** zobrazuje přesnost nejlepšího modelu, kterou najde tvůrce modelů, zatím. Vyšší přesnost znamená, že model se v testovacích datech podrobnějším způsobem vypovídat.
    - **Nejlepší algoritmus** zobrazuje název nejlepšího algoritmu nalezeného tvůrcem modelu, zatím.
    - **Poslední algoritmus** zobrazuje název algoritmu naposledy, který tvůrce modelů použil k vytvoření výukového modelu.

1. Po dokončení školení vyberte odkaz **vyhodnotit** , který se přesune k dalšímu kroku.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Výsledkem kroku školení je jeden model, který má nejlepší výkon. V kroku vyhodnocení v Tvůrci modelů obsahuje oddíl Output algoritmus používaný modelem nejlepšího provádění v **nejlepším záznamu modelu** spolu se metrikami v **nejvyšší přesnosti modelu**. Kromě toho se zobrazí Souhrnná tabulka obsahující až pět modelů, které se prozkoumaly a jejich metriky.

Pokud nejste spokojeni s metrikami přesnosti, můžou se některé snadné způsoby, jak se pokusit zvýšit přesnost modelu, zvýšit množství času pro výuku modelu nebo použít více dat. V opačném případě vyberte odkaz **kód** , který se přesune k poslednímu kroku v Tvůrci modelů.

## <a name="add-the-code-to-make-predictions"></a>Přidejte kód, který provede předpovědi

Dva projekty jsou vytvořeny v důsledku školicího procesu.

- RestaurantViolationsML. ConsoleApp: Konzolová aplikace C# .NET Core, která obsahuje kód pro školení modelů a ukázku kódu.
- RestaurantViolationsML. model: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, uloženou verzi modelu nejlepšího provádění během školení a pomocnou třídu nazvanou `ConsumeModel` k vytvoření předpovědi.

1. V kroku Code v Tvůrci modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.
1. Otevřete soubor *program.cs* v projektu *RestaurantViolations* .
1. Přidejte následující příkaz using pro odkaz na projekt *RestaurantViolationsML. model* :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Chcete-li vytvořit předpovědi pro nová data pomocí modelu, vytvořte novou instanci třídy `ModelInput` v rámci metody `Main` vaší aplikace. Všimněte si, že kategorie rizik není součástí vstupu. Důvodem je to, že model vygeneruje předpověď pro něj.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Použijte metodu `Predict` z `ConsumeModel` třídy. Metoda `Predict` načte vyškolený model, vytvoří [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro model a použije ho k předpovědií nových dat.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Spusťte aplikaci.

    Výstup generovaný programem by měl vypadat podobně jako následující fragment kódu:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Pokud potřebujete odkazovat na vygenerované projekty později v jiném řešení, můžete je najít v adresáři `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

Blahopřejeme! Úspěšně jste vytvořili model strojového učení pro kategorizaci rizika narušení stavu pomocí Tvůrce modelů. Zdrojový kód pro tento kurz najdete v úložišti GitHub [/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="additional-resources"></a>Další materiály a zdroje informací

Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:

- [Scénáře tvůrce modelů](../automate-training-with-model-builder.md#scenarios)
- [Klasifikace s více třídami](../resources/glossary.md#multiclass-classification)
- [Metrika modelu klasifikace s více třídami](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
