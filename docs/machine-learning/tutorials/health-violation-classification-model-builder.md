---
title: 'Kurz: Klasifikovat porušení stavu s Model Builder'
description: Tento kurz ukazuje, jak vytvořit vícetřídní klasifikační model pomocí ML.NET Model Builder klasifikovat závažnost porušení stavu restaurace v San Francisku.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: e94313277a025d482105a6d78b6608d4df442c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185844"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Kurz: Klasifikujte závažnost porušení stavu restaurace s Model Builder

Naučte se, jak vytvořit vícetřídní klasifikační model pomocí Tvůrce modelů ke kategorizaci úrovně rizika porušení restaurací zjištěných při kontrolách stavu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Příprava a pochopení dat
> - Výběr scénáře
> - Načtení dat z databáze
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

> [!NOTE]
> Tvůrce modelů je momentálně ve verzi Preview.

## <a name="prerequisites"></a>Požadavky

Seznam předpokladů a pokynů k instalaci naleznete v [instalační příručce výrobce modelů](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Přehled klasifikace vícetřídového tvůrce modelů

Tato ukázka vytvoří aplikaci konzoly C# .NET Core, která kategorizuje riziko porušení stavu pomocí modelu strojového učení vytvořeného pomocí tvůrce modelů. Zdrojový kód pro tento kurz najdete v úložišti GitHub [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **aplikaci konzoly C# .NET Core** s názvem "RestaurantViolations". Ujistěte se, že **umístit řešení a projekt ve stejném adresáři** je **nezaškrtnuté** (VS 2019) nebo **vytvořit adresář pro řešení** je **zaškrtnuto** (VS 2017).

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

> Soubor dat používaný k trénování a vyhodnocování modelu strojového učení pochází původně z [oddělení sanfranciského ministerstva bezpečnosti restaurací pro veřejné zdraví](https://www.sfdph.org/dph/EH/Food/score/default.asp). Pro větší pohodlí byla datová sada zhuštěna tak, aby obsahovala pouze sloupce důležité pro trénování modelu a předpovědi. Další informace o [datové sadě](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)naleznete na následujícím webu .

[Stáhněte si datovou sadu Restaurant Safety Scores](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) a rozbalte ji.

Každý řádek v datovém souboru obsahuje informace o porušeních zjištěných při kontrole ze strany ministerstva zdravotnictví a posouzení rizik a rizika, které tato porušení představují pro veřejné zdraví a bezpečnost.

| Typ kontroly | PorušeníPopis | Kategorie rizika |
| --- | --- | --- |
| Rutina - neplánovaná | Nedostatečně vyčištěné nebo dezinfikované povrchy styku s potravinami | Mírné riziko |
| Nové vlastnictví | Vysoce rizikové zamoření škůdci | Vysoké riziko |
| Rutina - neplánovaná | Utěrací utěrky nejsou čisté nebo řádně uložené nebo nedostatečné dezinfekční | Nízké riziko |

- **InspectionType**: typ kontroly. Může se jednalo buď o první inspekci nového zařízení, rutinní inspekci, inspekci stížností a mnoho dalších typů.
- **PorušeníPopis**: popis porušení zjištěného během kontroly.
- **RizikaKategorie**: závažnost rizika porušení představuje pro veřejné zdraví a bezpečnost.

Je `label` sloupec, který chcete předpovědět. Při provádění úkolu klasifikace je cílem přiřadit kategorii (text nebo číselné). V tomto scénáři klasifikace závažnost porušení je přiřazena hodnota nízké, střední nebo vysoké riziko. Proto **RiskCategory** je popisek. Jsou `features` vstupy, které dáte modelu `label`předpovědět . V tomto případě **InspectionType** a **ViolationDescription** se používají jako funkce nebo vstupy předpovědět **RiskCategory**.

## <a name="choose-a-scenario"></a>Výběr scénáře

![Průvodce tvůrcem modelů v sadě Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Chcete-li trénovat model, vyberte ze seznamu dostupných scénářů strojového učení, které poskytuje Tvůrce modelů. V tomto případě je scénář *klasifikace vydání*.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt *RestaurantViolations* a vyberte **přidat** > **strojové učení**.
1. Pro tuto ukázku scénář je klasifikace více tříd. V kroku *scénář* tvůrce modelů vyberte scénář **klasifikace problémů.**

## <a name="load-the-data"></a>Načtení dat

Tvůrce modelů přijímá data z databáze serveru SQL `csv` `tsv` Server nebo místního souboru ve formátu nebo formátu.

1. V datovém kroku nástroje Model Builder vyberte **SQL Server** z rozevíracího souboru zdroje dat.
1. Vyberte tlačítko vedle textového pole **Připojit k databázi serveru SQL Server.**
    1. V dialogovém okně **Zvolit data** vyberte **položku Microsoft SQL Server Database File**.
    1. Zrušte zaškrtnutí políčka **Vždy použít tento výběr** a vyberte **pokračovat**.
    1. V dialogovém okně **Vlastnosti připojení** vyberte **Procházet** a vyberte stažený soubor *RestaurantScores.mdf.*
    1. Vyberte **OK**.
1. V rozevíracím souboru **Název tabulky** zvolte **Porušení.**
1. V rozevíracím seznamu **Sloupec k předvídání (Popisek)** zvolte **Kategorie rizika.**
1. Ponechte výchozí výběr **sloupců, InspectionType** a **ViolationDescription**, se změnami v rozevírací seznam **Vstupní sloupce (Funkce).**
1. Vyberte **vlak** odkaz přejít na další krok v Builder.

## <a name="train-the-model"></a>Trénování modelu

Úloha strojového učení slouží k trénování modelu klasifikace problémů v tomto kurzu je klasifikace více tříd. Během procesu školení modelu Model Builder trénuje samostatné modely pomocí různých algoritmů klasifikace více tříd a nastavení, aby našel nejvýkonnější model pro vaši datovou sadu.

Doba potřebná pro model pro trénování je úměrná množství dat. Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas pro trénování (sekundy)** na základě velikosti zdroje dat.

1. Přestože Model Builder nastaví hodnotu **Čas trénovat (sekundy)** na 10 sekund, zvyšte ji na 30 sekund. Školení pro delší časové zpracování umožňuje Model Builder prozkoumat větší počet algoritmů a kombinace parametrů při hledání nejlepší model.
1. Vyberte **možnost Zahájit trénink**.

    V průběhu tréninkového procesu se `Progress` údaje o průběhu zobrazují v části kroku vlaku.

    - **Stav** zobrazuje stav dokončení procesu školení.
    - **Nejlepší přesnost** zobrazuje přesnost nejvýkonnějšího modelu, který dosud našel Model Builder. Vyšší přesnost znamená, že model byl na testovacích datech předpovězen správněji.
    - **Nejlepší algoritmus** zobrazí název algoritmu s nejlepším výkonem, který dosud našel Model Builder.
    - **Poslední algoritmus** zobrazí název algoritmu, který byl naposledy použit tvůrcem modelů k trénování modelu.

1. Po dokončení tréninku vyberte odkaz **Vyhodnotit a** přejděte k dalšímu kroku.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Výsledkem kroku školení je jeden model, který měl nejlepší výkon. V kroku vyhodnocení Tvůrce modelů obsahuje výstupní část algoritmus používaný nejvýkonnějším modelem v položce **Nejlepší model** spolu s metrikami v **kategorii Nejlepší přesnost modelu**. Kromě toho se zobrazí souhrnná tabulka obsahující až pět modelů, které byly prozkoumány a jejich metriky.

Pokud nejste spokojeni s metrikami přesnosti, některé jednoduché způsoby, jak se pokusit zlepšit přesnost modelu, je prodloužit dobu pro trénování modelu nebo použití více dat. V opačném případě vyberte odkaz **kódu** pro přechod na poslední krok v Builder.

## <a name="add-the-code-to-make-predictions"></a>Přidání kódu pro předpověď

Dva projekty jsou vytvořeny v důsledku procesu školení.

- RestaurantViolationsML.ConsoleApp: Aplikace C# .NET Core Console, která obsahuje trénování modelu a kód spotřeby vzorku.
- RestaurantViolationsML.Model: Knihovna třídy .NET Standard obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, uloženou `ConsumeModel` verzi nejvýkonnějšího modelu během trénovaní a pomocnou třídu volanou k předpovědi.

1. V kroku kódu Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.
1. Otevřete soubor *Program.cs* v projektu *RestaurantViolations.*
1. Přidejte následující příkaz using, abyste odkazovali na projekt *RestaurantViolationsML.Model:*

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Chcete-li předpovědět nová data pomocí modelu, vytvořte `ModelInput` novou `Main` instanci třídy uvnitř metody vaší aplikace. Všimněte si, že kategorie rizika není součástí vstupu. Důvodem je, že model generuje předpověď pro něj.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Použijte `Predict` metodu `ConsumeModel` z třídy. Metoda `Predict` načte trénovaný [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model, vytvoří pro model a používá jej k vytváření předpovědí na nová data.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Spusťte aplikaci.

    Výstup generovaný programem by měl vypadat podobně jako výstřižek níže:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Pokud potřebujete odkazovat na generované projekty později uvnitř jiného řešení, `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` můžete je najít uvnitř adresáře.

Blahopřejeme! Úspěšně jste vytvořili model strojového učení, abyste kategorizovali riziko porušení stavu pomocí Tvůrce modelů. Zdrojový kód pro tento kurz najdete v úložišti GitHub [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="additional-resources"></a>Další zdroje

Další informace o tématech uvedených v tomto kurzu naleznete v následujících zdrojích:

- [Scénáře tvůrce modelů](../automate-training-with-model-builder.md#scenarios)
- [Klasifikace více tříd](../resources/glossary.md#multiclass-classification)
- [Metriky modelu klasifikace více tříd](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
