---
title: Cluster květin iris pomocí clusteringu learner - ML.NET
description: Zjistěte, jak použít ve scénáři clusteringu ML.NET
author: pkulikov
ms.author: johalex
ms.date: 01/11/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 03a584095badf4b1c3318833f6e67367f27b32ba
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583716"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a>Kurz: Cluster květin iris pomocí clusteringu learner ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento kurz ukazuje, jak použít ML.NET k sestavení [clusteringový model](../resources/tasks.md#clustering) pro [datovou sadu iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Pochopení problému
> - Vyberte úlohu odpovídající machine learning
> - Příprava dat
> - Načíst a transformovat data
> - Vyberte algoritmus učení
> - Trénování modelu
> - Použít model pro předpovědi

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

## <a name="understand-the-problem"></a>Pochopení problému

Tento problém je o rozdělení sadu iris květin v různých skupinách na základě funkcí květinu. Tyto funkce jsou délku a šířku sepal a délku a šířku petal. Pro účely tohoto kurzu předpokládá, že typ jednotlivých květinu neznámý. Chcete seznámit se se strukturou datové sady z funkcí a předpovědět, jak zapadá data instance této struktury.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

Jak si nejste jisti, do které skupiny patří každý květinu, zvolte [nastavenou možnost bez dohledu strojového učení](../resources/glossary.md#unsupervised-machine-learning) úloh. Pokud chcete rozdělit datové sady ve skupinách tak, že prvky ve stejné skupině jsou u jiného než více podobné těm v jiných skupinách, použijte [clustering](../resources/tasks.md#clustering) machine learning úloh.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "IrisFlowerClustering" a pak vyberte **OK** tlačítko.

1. Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

1. Nainstalujte **Microsoft.ML** balíček NuGet:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

## <a name="prepare-the-data"></a>Příprava dat

1. Stáhněte si [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dat nastavit a uložit ho. tím *Data* složky, které jste vytvořili v předchozím kroku. Další informace o datové sady iris najdete v článku [datovou sadu Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) stránky Wikipedia a [datovou sadu Iris](https://archive.ics.uci.edu/ml/datasets/Iris) stránku, což je zdrojové datové sady.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *iris.data* a vyberte možnost **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

*Iris.data* soubor obsahuje pět sloupců, které představují:

- sepal length v cm
- sepal width v cm
- petal length v cm
- petal width v cm
- Typ květinu iris

Pro účely clusteringu příkladu v tomto kurzu ignoruje posledního sloupce.

## <a name="create-data-classes"></a>Vytvoření datových tříd

Vytvoření třídy pro vstupní data a předpovědí:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *IrisData.cs*. Vyberte **přidat** tlačítko.
1. Přidejte následující `using` směrnice do nového souboru:

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

Odeberte stávající definice třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, možnosti *IrisData.cs* souboru:

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData` je třída vstupní data a obsahuje definice pro jednotlivé funkce z datové sady. Použití [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) atributy indexů zdrojových sloupců v souboru datové sady.

`ClusterPrediction` Třída reprezentuje výstup model clusteringu u `IrisData` instance. Použití [Názevsloupce](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut pro vytvoření vazby `PredictedClusterId` a `Distances` polím **PredictedLabel** a **skóre** sloupce v uvedeném pořadí. V případě clusteru úloh tyto sloupce mají následující význam:

- **PredictedLabel** sloupec obsahuje ID předpokládané clusteru.
- **Skóre** sloupec obsahuje pole s kvadratických Euclidean vzdálenosti se centroids clusteru. Délka pole je rovna počtu clusterů.

> [!NOTE]
> Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.

## <a name="define-data-and-model-paths"></a>Definovat cesty k datům a model

Přejděte zpět *Program.cs* a přidejte dvě pole pro uložení cesty k souboru datové sady a do souboru uložit model:

- `_dataPath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.
- `_modelPath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.

Přidejte následující kód vpravo nahoře `Main` metoda zadat tyto cesty:

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

Aby předchozí kód zkompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Vytvoří kontext ML

Přidejte následující další `using` direktivy k hornímu okraji *Program.cs* souboru:

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

V `Main` metoda, nahraďte `Console.WriteLine("Hello World!");` řádek s následujícím kódem:

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Třída představuje prostředí machine learning a poskytuje mechanismus pro protokolování a vstupních bodů pro načítání dat, trénování modelu, predikcí a další úlohy. Toto je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework.

## <a name="setup-data-loading"></a>Nastavení načítání dat

Přidejte následující kód, který `Main` metoda nastavit způsob, jak načíst data:

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

Použití [obecný `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%60%601(Microsoft.ML.DataOperationsCatalog,System.Boolean,System.Char,System.Boolean,System.Boolean,System.Boolean)) metodu pro odvození schématu datové sady z `IrisData` definici třídy.

Použití vytvořena instance <xref:Microsoft.ML.Data.TextLoader> instance má vytvořit <xref:Microsoft.Data.DataView.IDataView> instanci, která představuje zdroj dat pro trénovací datové sady:

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a>Vytvoření kanálu učení

Pro účely tohoto kurzu kanál učení clusteringu úkolu se skládá z následujících dvou kroků:

- zřetězit načíst sloupce do jednoho **funkce** sloupec, který používá clustering trainer;
- použít <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> trainer k natrénování modelu s použitím s kB – znamená, že ++ clustering algoritmus.

Přidejte následující kód, který `Main` metody:

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

Kód určuje, že datová sada by měla lze rozdělit tři clustery.

## <a name="train-the-model"></a>Trénování modelu

Kroky přidání v předchozích částech připravili kanálu pro školení, ale, že byly provedeny žádné. Přidejte následující řádek, který `Main` metodu za účelem načtení dat a trénování modelu:

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Uložit model

V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET. Uložit model do souboru .zip, přidejte následující kód, který `Main` metody:

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Použít model pro předpovědi

K následné predikci, použijte <xref:Microsoft.ML.PredictionEngine%602> třídu, která přebírá instance typu vstupním kanálem transformer a vytváří instance typu výstupu. Přidejte následující řádek, který `Main` metodu pro vytvoření instance této třídy:

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

Vytvořte `TestIrisData` třídy pro uložení testovací data instancí:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TestIrisData.cs*. Vyberte **přidat** tlačítko.
1. Upravte třídu pro statické stejně jako v následujícím příkladu:

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

Tento kurz představuje jednu instanci data iris v rámci této třídy. Můžete přidat další scénáře můžete experimentovat s modelem. Přidejte následující kód do `TestIrisData` třídy:

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

Chcete-li zjistit, ke kterému zadaná položka patří do clusteru, přejděte zpět na *Program.cs* a přidejte následující kód do `Main` metody:

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

Spusťte program clusteru, které obsahuje instanci zadaného data a kvadratických vzdálenosti směrem dovnitř od této instance na centroids clusteru. Výsledky by měl vypadat přibližně takto:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Blahopřejeme! Teď jste úspěšně sestaven služby machine learning model iris clustering a použít ho k následné predikci. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) úložiště GitHub.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> - Pochopení problému
> - Vyberte úlohu odpovídající machine learning
> - Příprava dat
> - Načíst a transformovat data
> - Vyberte algoritmus učení
> - Trénování modelu
> - Použít model pro předpovědi

Přečtěte si našeho úložiště GitHub, pokračujte ve čtení a najít další ukázky.
> [!div class="nextstepaction"]
> [DotNet/machinelearning úložiště GitHub](https://github.com/dotnet/machinelearning/)
