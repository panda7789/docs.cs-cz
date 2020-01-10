---
title: 'Kurz: analýza míněních recenzí filmů pomocí předem připraveného modelu TensorFlow'
description: V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu. Mínění třídění binárního prostředí C# je Konzolová aplikace vyvinutá pomocí sady Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0e80cdc6bb7dcc62a57466e909451da972c92db8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75738694"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Kurz: analýza míněních recenzí filmů pomocí předem připraveného modelu TensorFlow v ML.NET

V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu. Mínění třídění binárního prostředí C# je Konzolová aplikace vyvinutá pomocí sady Visual Studio.

Model TensorFlow použitý v tomto kurzu byl vyškolen pomocí recenzí filmů z databáze IMDB. Jakmile dokončíte vývoj aplikace, budete moci zadat text recenze filmu a aplikace vám oznámí, zda má recenze pozitivní nebo negativní mínění.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Načtení předem připraveného modelu TensorFlow
> * Transformovat text komentáře webu k funkcím vhodným pro model
> * Použití modelu k vytvoření předpovědi

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

## <a name="setup"></a>Instalace

### <a name="create-the-application"></a>Vytvoření aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TextClassificationTF".

2. Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.

3. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** . Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček. Opakujte tyto kroky pro **Microsoft. ml. TensorFlow** a **SciSharp. TensorFlow. Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Přidání modelu TensorFlow do projektu

> [!NOTE]
> Model pro tento kurz je z úložiště GitHub [/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) . Model je ve formátu TensorFlow SavedModel.

1. Stáhněte [soubor zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)a rozbalte ho.

    Soubor zip obsahuje:

    * `saved_model.pb`: samotného modelu TensorFlow. Model přebírá pevnou délku (Size 600) celočíselné pole funkcí reprezentující text v řetězci IMDB revize a vytvoří výstup dvou pravděpodobností, které se sčítají 1: pravděpodobnost, že vstupní revize má pozitivní mínění a pravděpodobnost, že kontrola vstupu má negativní mínění
    * `imdb_word_index.csv`: mapování jednotlivých slov na celočíselnou hodnotu. Mapování slouží k vygenerování vstupních funkcí modelu TensorFlow.

2. Zkopírujte obsah nejvnitřnějšího adresáře `sentiment_model` do projektu aplikace *TextClassificationTF* `sentiment_model` Directory. Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:

   ![obsah sentiment_model adresáře](./media/text-classification-tf/sentiment-model-files.png)

3. V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři `sentiment_model` a v podadresáři a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="add-using-statements-and-global-variables"></a>Přidat příkazy using a globální proměnné

1. Do horní části souboru *program.cs* přidejte následující další příkazy `using`:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. Vytvořte dvě globální proměnné přímo nad `Main` metodou pro uchování cesty k souboru uloženého modelu a délka vektoru funkce.

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath` je cesta k souboru trained model.
    * `FeatureLength` je délka pole funkcí celého čísla, které model očekává.

### <a name="model-the-data"></a>Modelování dat

Recenze filmů je text bezplatné Form. Vaše aplikace převede text na vstupní formát očekávaný modelem v řadě diskrétních fází.

První je rozdělit text na samostatná slova a použít poskytnutý soubor mapování pro mapování jednotlivých slov na celočíselné kódování. Výsledkem této transformace je pole celé číslo proměnné s délkou odpovídající počtu slov ve větě.

|Vlastnost| Hodnota|Type|
|-------------|-----------------------|------|
|ReviewText|Tato film je skutečně dobrá|odkazy řetězců|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|

Velikost pole s proměnnou délkou se pak změní na pevně stanovenou délku 600. Jedná se o délku, kterou model TensorFlow očekává.

|Vlastnost| Hodnota|Type|
|-------------|-----------------------|------|
|ReviewText|Tato film je skutečně dobrá|odkazy řetězců|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|
|Funkce|14, 22, 9, 66, 78,... |int [600]|

1. Vytvořte třídu pro vstupní data za `Main` metodou:

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    Vstupní datová třída `MovieReview`obsahuje `string` pro komentáře uživatele (`ReviewText`).

1. Vytvořte třídu pro funkce s proměnlivou délkou za `Main` metodou:

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    Vlastnost `VariableLengthFeatures` má atribut [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) , který ho určí jako vektor.  Všechny prvky Vector musí být stejného typu. U datových sad s velkým počtem sloupců načítá více sloupců jako jeden vektor při použití transformace dat.

    Tato třída se používá v akci `ResizeFeatures`. Názvy vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v zobrazení DataView lze použít jako _vstup_ pro akci vlastního mapování.

1. Vytvořte třídu pro funkce s pevnou délkou za `Main` metodou:

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    Tato třída se používá v akci `ResizeFeatures`. Názvy vlastností (v tomto případě pouze jeden) se používají k označení toho, které sloupce v zobrazení DataView lze použít jako _výstup_ akce vlastního mapování.

    Všimněte si, že název vlastnosti `Features` určuje model TensorFlow. Tento název vlastnosti nelze změnit.

1. Vytvořte třídu pro předpověď za `Main` metodou:

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` je předpověď Třída použitá po školení modelu. `MovieReviewSentimentPrediction` má jedno pole `float` (`Prediction`) a atribut `VectorType`.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Vytvoření MLContext, vyhledávacího slovníku a akce pro změnu velikosti funkcí

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET. Inicializuje se `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů. Je podobný a koncepčně `DBContext` v Entity Framework.

1. Nahraďte `Console.WriteLine("Hello World!")` řádek v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné mlContext:

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. Vytvořte slovník pro kódování slov jako celé číslo pomocí metody [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) pro načtení mapování dat ze souboru, jak je vidět v následující tabulce:

    |Word     |Index    |
    |---------|---------|
    |dětí     |  362    |
    |požadovaného     |  181    |
    |něco    |  355    |
    |efekty  |  302    |
    |úplně  |  547    |

    Přidejte následující kód pro vytvoření mapy vyhledávání:

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. Přidejte `Action` pro změnu velikosti pole celé číslo (Integer) proměnné délky na celé číslo pole s pevnou velikostí s dalšími řádky kódu:

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Načtení předem připraveného modelu TensorFlow

1. Přidejte kód pro načtení modelu TensorFlow:

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    Po načtení modelu můžete extrahovat jeho vstupní a výstupní schéma. Schémata se zobrazují jenom pro vás a jenom učení. Tento kód nepotřebujete, aby konečná aplikace fungovala:

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    Vstupní schéma je pole s pevnou délkou kódovaných slov typu Integer. Výstupní schéma je plovoucí pole pravděpodobnosti, které označuje, zda je mínění revize záporná nebo kladná. Tyto hodnoty se sčítají na 1, protože pravděpodobnost, že je kladné, je doplňkem pravděpodobnosti mínění negativní.

## <a name="create-the-mlnet-pipeline"></a>Vytvoření kanálu ML.NET

1. Vytvořte kanál a rozdělte vstupní text na slova pomocí transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) pro rozdělení textu na slova jako další řádek kódu:

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   Transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) používá mezery k analýze textu nebo řetězce na slova. Vytvoří nový sloupec a rozdělí jednotlivé vstupní řetězce na vektor podřetězců na základě oddělovače definovaného uživatelem.

1. Namapujte slova na celočíselné kódování pomocí vyhledávací tabulky, kterou jste deklarovali výše:

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. Změňte velikost celočíselných kódování proměnné na pevnou délku, kterou vyžaduje model:

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. Klasifikace vstupu pomocí načteného modelu TensorFlow:

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    Výstup modelu TensorFlow se nazývá `Prediction/Softmax`. Všimněte si, že název `Prediction/Softmax` určuje model TensorFlow. Tento název nemůžete změnit.

1. Vytvoří nový sloupec pro předpověď výstupu:

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    Je nutné zkopírovat sloupec `Prediction/Softmax` do jednoho s názvem, který lze použít jako vlastnost ve C# třídě: `Prediction`. V názvu C# vlastnosti není povolený `/` znak.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Vytvoření modelu ML.NET z kanálu

1. Přidejte kód pro vytvoření modelu z kanálu:

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    Model ML.NET je vytvořen z řetězce odhady v kanálu voláním metody `Fit`. V takovém případě nebudeme pro vytvoření modelu vytvářet žádná data, protože model TensorFlow již byl dříve vyškolen. Dodáváme prázdný objekt zobrazení dat, který splňuje požadavky metody `Fit`.

## <a name="use-the-model-to-make-a-prediction"></a>Použití modelu k vytvoření předpovědi

1. Do `Main` metody přidejte metodu `PredictSentiment`:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Přidejte následující kód k vytvoření `PredictionEngine` jako první řádek v metodě `PredictSentiment()`:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > rozšíření služby `PredictionEnginePool` je aktuálně ve verzi Preview.

1. Přidejte komentář k otestování předpovědi vyškolených modelů v metodě `Predict()` vytvořením instance `MovieReview`:

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. Předání dat testovacích komentářů do `Prediction Engine` přidáním dalších řádků kódu do metody `PredictSentiment()`:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat:

    |Vlastnost| Hodnota|Type|
    |-------------|-----------------------|------|
    |Předpověď|[0,5459937, 0,454006255]|float []|

1. Zobrazit předpovědi mínění pomocí následujícího kódu:

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. Na konec `Main` metody přidejte volání `PredictSentiment`:

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a>výsledků

Sestavte a spusťte aplikaci.

Výsledky by měly vypadat podobně jako následující. Během zpracování se zobrazí zprávy. Můžou se zobrazovat upozornění nebo zpracovávat zprávy. Tyto zprávy byly pro přehlednost odebrány z následujících výsledků.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění pomocí předem připraveného modelu `TensorFlow` v ML.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Načtení předem připraveného modelu TensorFlow
> * Transformovat text komentáře webu k funkcím vhodným pro model
> * Použití modelu k vytvoření předpovědi
