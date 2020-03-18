---
title: 'Kurz: Analýza mínění recenze pomocí modelu TensorFlow'
description: Tento kurz ukazuje, jak používat předem vyškolený model TensorFlow ke klasifikaci mínění v komentářích k webu. Binární třídění mínění je konzolová aplikace jazyka C# vyvinutá pomocí sady Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241114"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Kurz: Analyzujte mínění filmových recenzí pomocí předem trénovaného modelu TensorFlow v ML.NET

Tento kurz ukazuje, jak používat předem vyškolený model TensorFlow ke klasifikaci mínění v komentářích k webu. Binární třídění mínění je konzolová aplikace jazyka C# vyvinutá pomocí sady Visual Studio.

Model TensorFlow použitý v tomto kurzu byl trénován pomocí filmových recenzí z databáze IMDB. Jakmile dokončíte vývoj aplikace, budete moci zadat text pro kontrolu filmu a aplikace vám řekne, zda má recenze pozitivní nebo negativní sentiment.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Načtení předem vyškoleného modelu TensorFlow
> * Transformace textu komentáře na webových stránkách na funkce vhodné pro model
> * Pomocí modelu proveďte předpověď

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".

## <a name="setup"></a>Nastavení

### <a name="create-the-application"></a>Vytvoření aplikace

1. Vytvořte **aplikaci .NET Core Console** s názvem "TextClassificationTF".

2. Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.

3. Nainstalujte **balíček nuget Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet.** **Vyhledejte Microsoft.ML**, vyberte požadovaný balíček a pak vyberte tlačítko **Instalovat.** Pokračujte v instalaci souhlasem s licenčními podmínkami pro vámi zvolené balíček. Opakujte tyto kroky pro **Microsoft.ML.TensorFlow** a **SciSharp.TensorFlow.Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Přidání modelu TensorFlow do projektu

> [!NOTE]
> Model pro tento kurz je z [úložiště Dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub. Model je ve formátu TensorFlow SavedModel.

1. Stáhněte si [soubor sentiment_model zip](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)a rozbalte.

    Soubor zip obsahuje:

    * `saved_model.pb`: samotný model TensorFlow. Model má pevnou délku (velikost 600) celé pole funkcí představujících text v řetězci revize IMDB a vynaloží dvě pravděpodobnosti, které součet 1: pravděpodobnost, že vstupní revize má kladný sentiment a pravděpodobnost, že vstupní revize má negativní sentiment.
    * `imdb_word_index.csv`: mapování z jednotlivých slov na celá hodnota. Mapování se používá ke generování vstupních funkcí pro model TensorFlow.

2. Zkopírujte obsah nejvnitřnějšího `sentiment_model` adresáře do adresáře projektu `sentiment_model` *TextClassificationTF.* Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:

   ![sentiment_model obsah adresáře](./media/text-classification-tf/sentiment-model-files.png)

3. V Průzkumníku řešení klepněte pravým tlačítkem myši na jednotlivé soubory v `sentiment_model` adresáři a podadresáři a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="add-using-statements-and-global-variables"></a>Přidání pomocí příkazů a globálních proměnných

1. Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Vytvořte dvě globální proměnné `Main` přímo nad metodou, která pojme uloženou cestu k souboru modelu a délku vektoru prvku.

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`je cesta k souboru trénovaného modelu.
    * `FeatureLength`je délka pole celého prvku, které model očekává.

### <a name="model-the-data"></a>Modelování dat

Filmové recenze jsou textz volné formy. Aplikace převede text do vstupního formátu očekávaného modelem v několika samostatných fázích.

Prvním z nich je rozdělit text na samostatná slova a použít poskytnutý soubor mapování mapovat každé slovo na kódování celé číslo. Výsledkem této transformace je pole s proměnnou délkou celéčíslo s délkou odpovídající počtu slov ve větě.

|Vlastnost| Hodnota|Typ|
|-------------|-----------------------|------|
|ReviewText|tento film je opravdu dobrý|řetězec|
|Proměnné Funkce délky|14,22,9,66,78,... |int[]|

Pole prvku proměnné délky se pak mění na pevnou délku 600. Toto je délka, kterou model TensorFlow očekává.

|Vlastnost| Hodnota|Typ|
|-------------|-----------------------|------|
|ReviewText|tento film je opravdu dobrý|řetězec|
|Proměnné Funkce délky|14,22,9,66,78,... |int[]|
|Funkce|14,22,9,66,78,... |int[600]|

1. Vytvořte třídu pro vstupní `Main` data po metodě:

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    Třída vstupních `MovieReview`dat , `string` má pro`ReviewText`komentáře uživatele ( ).

1. Vytvořte třídu pro prvky `Main` proměnné délky po metodě:

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    Vlastnost `VariableLengthFeatures` má atribut [VectorType,](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) který ji označuje jako vektor.  Všechny vektorové prvky musí být stejného typu. V datových sadách s velkým počtem sloupců se načtení více sloupců jako jednoho vektoru sníží počet dat, když aplikujete transformace dat.

    Tato třída se `ResizeFeatures` používá v akci. Názvy jeho vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v DataView lze použít jako _vstup_ do akce vlastní mapování.

1. Vytvořte třídu pro prvky `Main` pevné délky po metodě:

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    Tato třída se `ResizeFeatures` používá v akci. Názvy jeho vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v DataView lze použít jako _výstup_ vlastní akce mapování.

    Všimněte si, že `Features` název vlastnosti je určen modelem TensorFlow. Tento název vlastnosti nelze změnit.

1. Vytvořte třídu pro `Main` předpověď po metodě:

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction`je třída předpověď použitá po trénování modelu. `MovieReviewSentimentPrediction`má jedno `float` pole`Prediction`( `VectorType` ) a atribut.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Vytvoření funkce MLContext, vyhledávacího slovníku a akce pro změna velikosti funkcí

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET. Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

1. Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro deklarování a inicializaci proměnné mlContext:

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Vytvořte slovník pro kódování slov jako celá čísla [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) pomocí metody pro načtení mapových dat ze souboru, jak je vidět v následující tabulce:

    |Word     |Index    |
    |---------|---------|
    |Děti     |  362    |
    |chcete     |  181    |
    |Špatně    |  355    |
    |effects  |  302    |
    |Pocit  |  547    |

    Chcete-li vytvořit vyhledávací mapu, přidejte níže uvedený kód:

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. Přidáním `Action` a změňte velikost celého pole slova s proměnnou délkou do celého pole s pevnou velikostí s dalšími řádky kódu:

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Načtěte předem vyškolený model TensorFlow

1. Přidání kódu pro načtení modelu TensorFlow:

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    Po načtení modelu můžete extrahovat jeho vstupní a výstupní schéma. Schémata jsou zobrazeny pouze pro zájem a učení. Tento kód nepotřebujete, aby konečná aplikace fungovala:

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    Vstupní schéma je pole s pevnou délkou celočíselných kódovaných slov. Schéma výstupu je plovoucí pole pravděpodobností označující, zda mínění recenze je negativní nebo pozitivní . Tyto hodnoty se součet 1, jako pravděpodobnost, že je pozitivní je doplněk pravděpodobnosti sentimentu je záporná.

## <a name="create-the-mlnet-pipeline"></a>Vytvoření kanálu ML.NET

1. Vytvořte kanál a rozdělte vstupní text na slova pomocí [tokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformace rozdělit text na slova jako další řádek kódu:

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformace používá mezery analyzovat text/řetězec do slov. Vytvoří nový sloupec a rozdělí každý vstupní řetězec na vektor podřetězců na základě uživatelem definovaného oddělovače.

1. Namapujte slova na jejich celé kódování pomocí vyhledávací tabulky, kterou jste deklarovali výše:

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. Změňte velikost celočíselné kódování proměnné délky na kódování s pevnou délkou, kterou model požaduje:

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. Klasifikujte vstup s načteným modelem TensorFlow:

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    Výstup modelu TensorFlow `Prediction/Softmax`se nazývá . Všimněte si, že název `Prediction/Softmax` je určen modelem TensorFlow. Tento název nelze změnit.

1. Vytvořte nový sloupec pro předpověď výstupu:

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    Je třeba zkopírovat `Prediction/Softmax` sloupec do jednoho s názvem, který lze použít `Prediction`jako vlastnost ve třídě C#: . Znak `/` není povolen v názvu vlastnosti Jazyka C#.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Vytvoření modelu ML.NET z kanálu

1. Přidejte kód pro vytvoření modelu z kanálu:

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    Model ML.NET je vytvořen z řetězce odhadců v kanálu `Fit` voláním metody. V tomto případě nejsme montáž žádná data k vytvoření modelu, jako tensorflow model již byl dříve trénovaný. Dodáváme prázdný objekt zobrazení dat, aby `Fit` splňoval požadavky metody.

## <a name="use-the-model-to-make-a-prediction"></a>Pomocí modelu proveďte předpověď

1. Přidejte `PredictSentiment` metodu `Main` pod metodu:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Přidejte následující kód `PredictionEngine` k vytvoření jako `PredictSentiment()` první řádek v metodě:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Je přijatelné používat v jednovláknových nebo prototypových prostředích. Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci. V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .

    > [!NOTE]
    > `PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.

1. Přidejte komentář k testování predikce `Predict()` trénovaného modelu `MovieReview`v metodě vytvořením instance :

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. Předejte data testovacích `Prediction Engine` komentářů přidáním dalších `PredictSentiment()` řádků kódu v metodě:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jeden řádek dat:

    |Vlastnost| Hodnota|Typ|
    |-------------|-----------------------|------|
    |Prediction (Předpověď)|[0.5459937, 0.454006255]|plovák[]|

1. Zobrazení předpovědi mínění pomocí následujícího kódu:

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. Přidejte volání `PredictSentiment` na konci `Main` metody:

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Výsledky

Sestavení a spuštění aplikace.

Vaše výsledky by měly být podobné následujícímu. Během zpracování se zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Tyto zprávy byly odebrány z následujících výsledků pro přehlednost.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předvídání mínění zpráv opětovným použitím předem trénovaného `TensorFlow` modelu v ML.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Načtení předem vyškoleného modelu TensorFlow
> * Transformace textu komentáře na webových stránkách na funkce vhodné pro model
> * Pomocí modelu proveďte předpověď
