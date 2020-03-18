---
title: 'Výuka: Kategorizovat iris květiny - k-znamená shlukování'
description: Naučte se používat ML.NET ve scénáři clusteringu
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 174907adac5741d5cc7d02cb134921debc586061
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241088"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Kurz: Kategorizovat iris květiny pomocí k-prostředky shlukování s ML.NET

Tento kurz ukazuje, jak použít ML.NET k vytvoření [modelu clusteringu](../resources/tasks.md#clustering) pro [sadu dat květin iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Pochopení problému
> - Výběr příslušného úkolu strojového učení
> - Příprava dat
> - Načtení a transformace dat
> - Výběr algoritmu učení
> - Trénování modelu
> - Použití modelu pro předpovědi

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".

## <a name="understand-the-problem"></a>Pochopení problému

Tento problém je o rozdělení souboru iris květů v různých skupinách na základě květinových prvků. Tyto rysy jsou délka a šířka sepal a délka a šířka okvětního lístku. V tomto kurzu předpokládejme, že typ každé květiny není znám. Chcete se naučit strukturu sady dat z funkcí a předpovědět, jak instance dat odpovídá této struktuře.

## <a name="select-the-appropriate-machine-learning-task"></a>Výběr příslušného úkolu strojového učení

Vzhledem k tomu, že nevíte, do které skupiny každá květina patří, zvolíte úkol [strojového učení bez dozoru.](../resources/glossary.md#unsupervised-machine-learning) Chcete-li rozdělit sadu dat do skupin tak, aby prvky ve stejné skupině byly navzájem více podobné než prvky v jiných skupinách, použijte úlohu strojového učení [clusteringu.](../resources/tasks.md#clustering)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete sadu Visual Studio. Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.** V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core.** Pak vyberte šablonu projektu **Konzola Aplikace (.NET Core).** Do textového pole **Název** zadejte "IrisFlowerClustering" a pak vyberte tlačítko **OK.**

1. Vytvořte adresář s názvem *Data* v projektu pro uložení datové sady a souborů modelů:

    V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte enter.

1. Nainstalujte **balíček Microsoft.ML** NuGet:

    V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet,** vyhledejte **Microsoft.ML** a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

## <a name="prepare-the-data"></a>Příprava dat

1. Stáhněte si datovou sadu [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) a uložte ji do složky *Data,* kterou jste vytvořili v předchozím kroku. Další informace o datové sadě duhovky naleznete na stránce [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia a na stránce Iris Data [Set,](https://archive.ics.uci.edu/ml/datasets/Iris) která je zdrojem datové sady.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *iris.data* a vyberte **příkaz Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

Datový soubor *iris.data* obsahuje pět sloupců, které představují:

- sepal délka v centimetrech
- šířka sepalu v centimetrech
- délka okvětních plodů v centimetrech
- šířka okvětních plodů v centimetrech
- typ iris květu

V zájmu clustering příkladu tohoto kurzu ignoruje poslední sloupec.

## <a name="create-data-classes"></a>Vytvoření tříd dat

Vytvořte třídy pro vstupní data a předpovědi:

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *IrisData.cs*. Potom vyberte tlačítko **Přidat.**
1. Do nového souboru přidejte následující `using` direktivu:

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

Odeberte existující definici třídy a přidejte `IrisData` `ClusterPrediction`následující kód, který definuje třídy a , do *souboru IrisData.cs:*

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

`IrisData`je třída vstupních dat a má definice pro každou funkci ze sady dat. Pomocí atributu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v souboru sady dat.

Třída `ClusterPrediction` představuje výstup clusteringmodelu aplikovaného na instanci. `IrisData` Pomocí atributu [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) `PredictedClusterId` můžete `Distances` svázat pole a se sloupci **PredictedLabel** a **Score.** V případě clustering úlohy tyto sloupce mají následující význam:

- **Sloupec PredictedLabel** obsahuje ID předpokládaného clusteru.
- **Sloupec Notscore** obsahuje pole se kvadratými euklidovskými vzdálenostmi od centroidů kupy. Délka pole se rovná počtu clusterů.

> [!NOTE]
> Použijte `float` typ k reprezentaci hodnot s plovoucí desetinnou desetinnou třídou vstupních dat a predikcí.

## <a name="define-data-and-model-paths"></a>Definování dat a cest modelu

Vraťte se do *Program.cs* souboru a přidejte dvě pole pro uložení cest k souboru sady dat a k souboru pro uložení modelu:

- `_dataPath`obsahuje cestu k souboru se sadou dat použitou k trénování modelu.
- `_modelPath`obsahuje cestu k souboru, kde je uložen trénovaný model.

Chcete-li zadat tyto `Main` cesty, přidejte přímo nad metodu následující kód:

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

Chcete-li zkompilovat předchozí `using` kód, přidejte následující direktivy v horní části *souboru Program.cs:*

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Vytvořit kontext ML

Do horní `using` části *Program.cs* souboru přidejte následující další direktivy:

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

V `Main` metodě nahraďte `Console.WriteLine("Hello World!");` řádek následujícím kódem:

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

Třída <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> představuje prostředí strojového učení a poskytuje mechanismy pro protokolování a vstupní body pro načítání dat, školení modelu, předpověď a další úkoly. To je srovnatelné koncepčně s použitím `DbContext` v entity frameworku.

## <a name="set-up-data-loading"></a>Nastavení načítání dat

Přidejte do `Main` metody následující kód pro nastavení způsobu načítání dat:

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

Metoda [ `MLContext.Data.LoadFromTextFile` obecného rozšíření](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) odvodí schéma datové sady `IrisData` z zadaného typu a vrátí, <xref:Microsoft.ML.IDataView> které lze použít jako vstup pro transformátory.

## <a name="create-a-learning-pipeline"></a>Vytvoření výukového kanálu

V tomto kurzu učení kanálu clustering úlohy se skládá ze dvou následujících kroků:

- zřetězit načtené sloupce do jednoho sloupce **Funkce,** který používá shlukovací trenér;
- pomocí <xref:Microsoft.ML.Trainers.KMeansTrainer> trenéra trénování modelu pomocí k-prostředky++ clustering algoritmus.

Do metody `Main` přidejte následující kód:

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

Kód určuje, že sada dat by měla být rozdělena do tří clusterů.

## <a name="train-the-model"></a>Trénování modelu

Kroky přidané v předchozích částech připravily kanál pro školení, ale žádný nebyl proveden. Přidejte k metodě `Main` následující řádek pro načtení dat a trénování modelu:

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Uložení modelu

V tomto okamžiku máte model, který lze integrovat do některé z existujících nebo nových aplikací .NET. Chcete-li model uložit do souboru ZIP, `Main` přidejte k metodě následující kód:

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Použití modelu pro předpovědi

Chcete-li předpovědi, <xref:Microsoft.ML.PredictionEngine%602> použijte třídu, která přebírá instance vstupního typu prostřednictvím kanálu transformátoru a vytváří instance typu výstupu. Přidejte k metodě `Main` následující řádek pro vytvoření instance této třídy:

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Je přijatelné používat v jednovláknových nebo prototypových prostředích. Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci. V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.

Vytvořte `TestIrisData` třídu pro testování testovacích dat instance:

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *TestIrisData.cs*. Potom vyberte tlačítko **Přidat.**
1. Upravte třídu tak, aby byla statická jako v následujícím příkladu:

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

Tento kurz představuje jednu instanci dat duhovky v rámci této třídy. Můžete přidat další scénáře experimentovat s modelem. Do `TestIrisData` třídy přidejte následující kód:

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

Chcete-li zjistit cluster, do kterého zadaná *Program.cs* položka patří, vraťte se `Main` do souboru Program.cs a do metody přidejte následující kód:

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

Spusťte program a zjistěte, který cluster obsahuje zadanou instanci dat a kvadračské vzdálenosti od této instance k centroidům clusteru. Vaše výsledky by měly být podobné následujícímu:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro clustering duhovky a použili jste ho k předpovědi. Zdrojový kód pro tento kurz najdete v úložišti [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Pochopení problému
> - Výběr příslušného úkolu strojového učení
> - Příprava dat
> - Načtení a transformace dat
> - Výběr algoritmu učení
> - Trénování modelu
> - Použití modelu pro předpovědi

Podívejte se na naše úložiště GitHub, abyste se dál učili a našli další ukázky.
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub repozitář](https://github.com/dotnet/machinelearning/)
