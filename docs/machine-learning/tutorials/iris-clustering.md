---
title: 'Kurz: Kategorizace Iris květin – k – znamená clusteringu'
description: Naučte se používat ML.NET ve scénáři clusteringu.
author: pkulikov
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: e2aaeb8abc6981b420329f194aa7b82c90cae00a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929104"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Kurz: Kategorizace Iris květin pomocí k-znamená Clustering pomocí ML.NET

Tento kurz ukazuje, jak pomocí ML.NET vytvořit [model clusteringu](../resources/tasks.md#clustering) pro [datovou sadu Iris pro květ](https://en.wikipedia.org/wiki/Iris_flower_data_set).

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Pochopení problému
> - Vyberte příslušný úkol strojového učení.
> - Příprava dat
> - Načtení a transformace dat
> - Výběr algoritmu učení
> - Trénování modelu
> - Použití modelu pro předpovědi

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

## <a name="understand-the-problem"></a>Pochopení problému

Tento problém se týká dělení sady Iris květin v různých skupinách na základě funkcí květu. Tyto funkce jsou délkou a šířkou sepal a délkou a šířkou Petal. Pro účely tohoto kurzu Předpokládejme, že typ každé květe není znám. Chcete se seznámit se strukturou sady dat z funkcí a předpovědět, jak instance dat odpovídá této struktuře.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte příslušný úkol strojového učení.

Vzhledem k tomu, do které skupiny patří jednotlivé květy, si zvolíte úlohu [Machine Learning, která není pod dohledem](../resources/glossary.md#unsupervised-machine-learning) . Chcete-li rozdělit datovou sadu ve skupinách takovým způsobem, že prvky ve stejné skupině jsou lépe podobné těm, než je to u jiných skupin, použijte úlohu strojového učení [clusteringu](../resources/tasks.md#clustering) .

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřít Visual Studio. Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** . V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** . Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** . Do textového pole **název** zadejte "IrisFlowerClustering" a pak vyberte tlačítko **OK** .

1. Vytvořte v projektu adresář s názvem *data* pro uložení datové sady a souborů modelu:

    V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **novou složku**. Zadejte "data" a stiskněte ENTER.

1. Nainstalujte balíček NuGet **Microsoft.ml** :

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v **1.0.0** v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

## <a name="prepare-the-data"></a>Příprava dat

1. Stáhněte si sadu dat [Iris. data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) a uložte ji do složky *dat* , kterou jste vytvořili v předchozím kroku. Další informace o sadě dat Iris najdete na stránce Wikipedii [sady dat Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) a na stránce [sady dat Iris](https://archive.ics.uci.edu/ml/datasets/Iris) , která je zdrojem datové sady.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *Iris. data* a vyberte možnost **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

Soubor *Iris. data* obsahuje pět sloupců, které reprezentují:

- Délka sepal v centimetrech
- sepal Šířka v centimetrech
- Délka Petal v centimetrech
- Petal Šířka v centimetrech
- typ Iris květu

V případě příkladu clusteringu tento kurz ignoruje poslední sloupec.

## <a name="create-data-classes"></a>Vytváření datových tříd

Vytvořte třídy pro vstupní data a předpovědi:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *IrisData.cs*. Pak vyberte tlačítko **Přidat** .
1. Do nového souboru `using` přidejte následující direktivu:

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

Odeberte existující definici třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, do souboru *IrisData.cs* :

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData`je vstupní datová třída a má definice pro jednotlivé funkce z datové sady. Pomocí atributu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v souboru sady dat.

Třída představuje výstup modelu clusteringu, který `IrisData` se použije pro instanci. `ClusterPrediction` Použijte atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) k navázání `PredictedClusterId` polí `Distances` a ke sloupcům **PredictedLabel** a **skore** v uvedeném pořadí. V případě úlohy clusteringu mají tyto sloupce následující význam:

- Sloupec **PredictedLabel** obsahuje ID předpokládaného clusteru.
- Sloupec **skóre** obsahuje pole, které má na centroids Euclideané vzdálenosti na čtverci. Délka pole se rovná počtu clusterů.

> [!NOTE]
> `float` Použijte typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupních a prediktivních datových třídách.

## <a name="define-data-and-model-paths"></a>Definování cest k datům a modelům

Vraťte se k souboru *program.cs* a přidejte dvě pole, do kterých se budou uchovávat cesty k souboru sady dat a k souboru pro uložení modelu:

- `_dataPath`obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.
- `_modelPath`obsahuje cestu k souboru, ve kterém je uložený model trained.

Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest:

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

Chcete-li provést předchozí kompilování kódu, přidejte `using` do horní části souboru *program.cs* následující direktivy:

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Vytvořit kontext ML

Do horní části souboru `using` *program.cs* přidejte následující další direktivy:

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

V metodě nahraďte `Console.WriteLine("Hello World!");`řádeknásledujícímkódem: `Main`

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Třída představuje prostředí strojového učení a poskytuje mechanismy pro protokolování a vstupní body pro načítání dat, školení modelů, předpovědi a další úkoly. Tato informace je srovnatelná s používáním `DbContext` v Entity Framework.

## <a name="setup-data-loading"></a>Načítání dat instalace

Přidejte následující kód do `Main` metody pro nastavení způsobu načtení dat:

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

Obecná `IrisData` [ `MLContext.Data.LoadFromTextFile` metoda rozšíření](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) odvodí schéma datové sady ze zadaného typu a vrátí <xref:Microsoft.ML.IDataView> , které lze použít jako vstup pro transformátory.

## <a name="create-a-learning-pipeline"></a>Vytvoření výukového kanálu

Pro účely tohoto kurzu se studijní kanál úlohy clusteringu skládá ze dvou následujících kroků:

- Zřetězí načtené sloupce do jednoho sloupce **funkce** , který používá clustering Trainer;
- Použijte Trainer <xref:Microsoft.ML.Trainers.KMeansTrainer> k vytvoření výukového modelu pomocí algoritmu k – znamená + + clustering.

Do `Main` metody přidejte následující kód:

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

Kód určuje, že sada dat by měla být rozdělena do tří clusterů.

## <a name="train-the-model"></a>Trénování modelu

Postup, který jste přidali v předchozích částech, připravil kanál pro školení, ale žádný nebyl proveden. Přidejte následující řádek do `Main` metody pro provádění načítání dat a školení modelu:

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Uložit model

V tomto okamžiku máte model, který lze integrovat do jakékoli existující nebo nové aplikace .NET. Chcete-li uložit model do souboru. zip, přidejte do `Main` metody následující kód:

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Použití modelu pro předpovědi

K provedení předpovědi použijte <xref:Microsoft.ML.PredictionEngine%602> třídu, která přebírá instance vstupního typu prostřednictvím kanálu transformátoru a vytváří instance výstupního typu. Přidejte následující řádek do `Main` metody pro vytvoření instance této třídy:

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

`TestIrisData` Vytvořte třídu pro domovní testování instancí testovacích dat:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TestIrisData.cs*. Pak vyberte tlačítko **Přidat** .
1. Upravte třídu tak, aby byla statická jako v následujícím příkladu:

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

Tento kurz zavádí jednu instanci dat Iris v rámci této třídy. Můžete přidat další scénáře pro experimentování s modelem. Do `TestIrisData` třídy přidejte následující kód:

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

Chcete-li zjistit cluster, do kterého patří zadaná položka, vraťte se do souboru *program.cs* a přidejte následující kód do `Main` metody:

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

Spusťte program, abyste viděli, který cluster obsahuje zadanou instanci dat a čtvercové vzdálenosti od této instance až po cluster centroids. Výsledky by měly být podobné následujícímu:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení pro clustering Iris a použili ho k vytvoření předpovědi. Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub.

## <a name="next-steps"></a>Další postup

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Pochopení problému
> - Vyberte příslušný úkol strojového učení.
> - Příprava dat
> - Načtení a transformace dat
> - Výběr algoritmu učení
> - Trénování modelu
> - Použití modelu pro předpovědi

Podívejte se na naše úložiště GitHub a pokračujte v učení a Najděte další ukázky.
> [!div class="nextstepaction"]
> [dotnet/machinelearning – úložiště GitHubu](https://github.com/dotnet/machinelearning/)
