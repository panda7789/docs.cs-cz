---
title: Cluster květin iris pomocí clusteringu learner - ML.NET
description: Zjistěte, jak použít ve scénáři clusteringu ML.NET
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 5bd73c774f60466daaf52215c34e7e17b5f5cc9c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145622"
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

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "IrisClustering" a pak vyberte **OK** tlačítko.

1. Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

1. Nainstalujte **Microsoft.ML** balíček NuGet:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

## <a name="prepare-the-data"></a>Příprava dat

1. Stáhněte si [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dat nastavit a uložit ho. tím *Data* složky, které jste vytvořili v předchozím kroku. Další informace o datové sady iris najdete v článku [datovou sadu Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) stránky Wikipedia a [datovou sadu Iris](http://archive.ics.uci.edu/ml/datasets/Iris) stránku, což je zdrojové datové sady.

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

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

Odeberte stávající definice třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, možnosti *IrisData.cs* souboru:

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

`IrisData` je třída vstupní data a obsahuje definice pro jednotlivé funkce z datové sady. Použití [sloupec](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atributy indexů zdrojových sloupců v souboru datové sady.

`ClusterPrediction` Třída reprezentuje výstup model clusteringu u `IrisData` instance. Použití [Názevsloupce](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut pro vytvoření vazby `PredictedClusterId` a `Distances` polím **PredictedLabel** a **skóre** sloupce v uvedeném pořadí. V případě clusteru úloh tyto sloupce mají následující význam:

- **PredictedLabel** sloupec obsahuje ID předpokládané clusteru.
- **Skóre** sloupec obsahuje pole s kvadratických Euclidean vzdálenosti se centroids clusteru. Délka pole je rovna počtu clusterů.

> [!NOTE]
> Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.

## <a name="define-data-and-model-paths"></a>Definovat cesty k datům a model

Přejděte zpět *Program.cs* a přidejte dvě pole pro uložení cesty k souboru datové sady a do souboru uložit model:

- `_dataPath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.
- `_modelPath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.

Přidejte následující kód vpravo nahoře `Main` metoda zadat tyto cesty:

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

Aby předchozí kód zkompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a>Vytvoření kanálu učení

Přidejte následující další `using` direktivy k hornímu okraji *Program.cs* souboru:

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

V `Main` metoda, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

`Train` Metoda trénovat modelu. Vytvoření metody hned pod `Main` metodu, pomocí následujícího kódu:

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu. Přidejte následující kód do `Train` metody:

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a>Načítání a transformace dat.

Prvním krokem k provedení je načíst trénovací datové sady. V našem případě trénovací datové sady se ukládají v textovém souboru s cestu definovanou `_dataPath` pole. Sloupce v souboru jsou oddělené čárkou (","). Přidejte následující kód do `Train` metody:

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

Dalším krokem je kombinací všech sloupců funkce do **funkce** pomocí sloupce <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> třídy transformace. Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce. Přidejte následující kód:

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Po přidání dat do kanálu a jejich transformace na správný formát vstupu, vyberte algoritmus učení (**learner**). Learner trénovat modelu. Poskytuje ML.NET <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> student, který implementuje [algoritmus k-means](https://en.wikipedia.org/wiki/K-means_clustering) vylepšené metodou pro výběr centroids počáteční clusteru.

Přidejte následující kód do `Train` metoda po zpracování dat kód přidaný v předchozím kroku:

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

Použití <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> vlastnosti a určit tak počet clusterů. Výše uvedený kód určuje, že datová sada by měla lze rozdělit tři clustery.

## <a name="train-the-model"></a>Trénování modelu

Kroky přidání v předchozích částech připravili kanálu pro školení, ale, že byly provedeny žádné. `pipeline.Train<TInput, TOutput>` Metoda vytváří model, který přijímá instanci `TInput` zadejte a vypíše instance `TOutput` typu. Přidejte následující kód do `Train` metody:

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a>Uložit model

V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET. Uložit model do souboru .zip, přidejte následující kód, který `Main` metodu pod volání `Train` metoda:

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

Pomocí `await` v `Main` znamená, že metoda `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

Budete také muset přidat následující `using` direktiv v horní části *Program.cs* souboru:

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

Vzhledem k tomu, `async Main` metoda je funkce přidané v jazyce C# 7.1 a výchozí jazyková verze projektu je C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější. Chcete-li to mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**. Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko. V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze). Vyberte tlačítko **OK**.

## <a name="use-the-model-for-predictions"></a>Použít model pro předpovědi

Vytvořte `TestIrisData` třídy pro uložení testovací data instancí:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TestIrisData.cs*. Vyberte **přidat** tlačítko.
1. Upravte třídu pro statické stejně jako v následujícím příkladu:

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

Tento kurz představuje jednu instanci data iris v rámci této třídy. Můžete přidat další scénáře můžete experimentovat s modelem. Přidejte následující kód do `TestIrisData` třídy:

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

Chcete-li zjistit, ke kterému zadaná položka patří do clusteru, přejděte zpět na *Program.cs* a přidejte následující kód do `Main` metody:

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

Spusťte program clusteru, které obsahuje instanci zadaného data a kvadratických vzdálenosti směrem dovnitř od této instance na centroids clusteru. Výsledky by měl vypadat přibližně takto. Jak zpracovává kanálu, může se zobrazit upozornění nebo zpracování zpráv. Ty se odstranily z následující výstup pro přehlednost.

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

Blahopřejeme! Teď jste úspěšně sestaven služby machine learning model iris clustering a použít ho k následné predikci. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) úložiště GitHub.

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
