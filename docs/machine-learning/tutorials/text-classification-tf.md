---
title: 'Kurz: analýza míněních kontrol pomocí modelu TensorFlow'
description: V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu. Binární klasifikátor mínění je Konzolová aplikace v jazyce C# vyvinutá pomocí sady Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9a2e7f72d59e31cfd7db5b89bfad55bccb063cea
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281404"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Kurz: analýza míněních recenzí filmů pomocí předem připraveného modelu TensorFlow v ML.NET

V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu. Binární klasifikátor mínění je Konzolová aplikace v jazyce C# vyvinutá pomocí sady Visual Studio.

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

## <a name="setup"></a>Nastavení

### <a name="create-the-application"></a>Vytvoření aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TextClassificationTF".

2. Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.

3. Nainstalujte **balíček NuGet Microsoft.ml**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** . Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček. Opakujte tyto kroky pro **Microsoft. ml. TensorFlow**, **Microsoft. ml. SampleUtils** a **SciSharp. TensorFlow. Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Přidání modelu TensorFlow do projektu

> [!NOTE]
> Model pro tento kurz je z úložiště GitHub [/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) . Model je ve formátu TensorFlow SavedModel.

1. Stáhněte [soubor zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)a rozbalte ho.

    Soubor zip obsahuje:

    * `saved_model.pb`: TensorFlow samotný model. Model přebírá pevnou délku (Size 600) celočíselné pole funkcí reprezentující text v řetězci IMDB revize a má dvě pravděpodobnosti, které se sčítají 1: pravděpodobnost, že vstupní revize má pozitivní mínění, a pravděpodobnost, že vstupní revize má negativní mínění.
    * `imdb_word_index.csv`: mapování jednotlivých slov na celočíselnou hodnotu. Mapování slouží k vygenerování vstupních funkcí modelu TensorFlow.

2. Zkopírujte obsah nejvnitřnějšího `sentiment_model` adresáře do adresáře projektu *TextClassificationTF* `sentiment_model` . Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:

   ![obsah sentiment_model adresáře](./media/text-classification-tf/sentiment-model-files.png)

3. V Průzkumník řešení klikněte pravým tlačítkem myši na každý ze souborů v `sentiment_model` adresáři a v podadresáři a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="add-using-statements-and-global-variables"></a>Přidat příkazy using a globální proměnné

1. `using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:

   [!code-csharp[AddUsings](./snippets/text-classification-tf/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Vytvořte dvě globální proměnné přímo nad `Main` metodu pro uchování cesty k souboru uloženého modelu a délku vektoru funkce.

   [!code-csharp[DeclareGlobalVariables](./snippets/text-classification-tf/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`je cesta k souboru trained modelu.
    * `FeatureLength`je délka pole funkce celého čísla, které model očekává.

### <a name="model-the-data"></a>Modelování dat

Recenze filmů je text bezplatné Form. Vaše aplikace převede text na vstupní formát očekávaný modelem v řadě diskrétních fází.

První je rozdělit text na samostatná slova a použít poskytnutý soubor mapování pro mapování jednotlivých slov na celočíselné kódování. Výsledkem této transformace je pole celé číslo proměnné s délkou odpovídající počtu slov ve větě.

|Vlastnost| Hodnota|Typ|
|-------------|-----------------------|------|
|ReviewText|Tato film je skutečně dobrá|řetězec|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|

Velikost pole s proměnnou délkou se pak změní na pevně stanovenou délku 600. Jedná se o délku, kterou model TensorFlow očekává.

|Vlastnost| Hodnota|Typ|
|-------------|-----------------------|------|
|ReviewText|Tato film je skutečně dobrá|řetězec|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|
|Funkce|14, 22, 9, 66, 78,... |int [600]|

1. Vytvořte třídu pro vstupní data za `Main` metodou:

    [!code-csharp[MovieReviewClass](./snippets/text-classification-tf/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    Vstupní datová třída `MovieReview` obsahuje `string` komentář pro uživatele ( `ReviewText` ).

1. Vytvořte třídu pro funkce s proměnlivou délkou za `Main` metodou:

    [!code-csharp[VariableLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    `VariableLengthFeatures`Vlastnost má atribut [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) , který ho určí jako vektor.  Všechny prvky Vector musí být stejného typu. U datových sad s velkým počtem sloupců načítá více sloupců jako jeden vektor při použití transformace dat.

    Tato třída se používá v `ResizeFeatures` akci. Názvy vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v zobrazení DataView lze použít jako _vstup_ pro akci vlastního mapování.

1. Vytvořte třídu pro funkce s pevnou délkou za `Main` metodou:

    [!code-csharp[FixedLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#FixedLengthFeatures)]

    Tato třída se používá v `ResizeFeatures` akci. Názvy vlastností (v tomto případě pouze jeden) se používají k označení toho, které sloupce v zobrazení DataView lze použít jako _výstup_ akce vlastního mapování.

    Všimněte si, že název vlastnosti `Features` je určen modelem TensorFlow. Tento název vlastnosti nelze změnit.

1. Vytvořte třídu pro předpověď za `Main` metodou:

    [!code-csharp[Prediction](./snippets/text-classification-tf/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction`je třídou předpovědi použitou po školení modelu. `MovieReviewSentimentPrediction`má jedno `float` pole ( `Prediction` ) a `VectorType` atribut.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Vytvoření MLContext, vyhledávacího slovníku a akce pro změnu velikosti funkcí

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET. Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

1. Nahraďte `Console.WriteLine("Hello World!")` řádek v `Main` metodě následujícím kódem pro deklaraci a inicializaci proměnné mlContext:

   [!code-csharp[CreateMLContext](./snippets/text-classification-tf/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Vytvořte slovník pro kódování slov jako celé číslo pomocí [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody pro načtení mapování dat ze souboru, jak je vidět v následující tabulce:

    |Word     |Index    |
    |---------|---------|
    |dětí     |  362    |
    |požadovaného     |  181    |
    |něco    |  355    |
    |effects  |  302    |
    |úplně  |  547    |

    Přidejte následující kód pro vytvoření mapy vyhledávání:

    [!code-csharp[CreateLookupMap](./snippets/text-classification-tf/csharp/Program.cs#CreateLookupMap)]

1. Přidejte, `Action` Chcete-li změnit velikost pole celé číslo proměnné na celé číslo s pevnou velikostí s dalšími řádky kódu:

   [!code-csharp[ResizeFeatures](./snippets/text-classification-tf/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Načtení předem připraveného modelu TensorFlow

1. Přidejte kód pro načtení modelu TensorFlow:

    [!code-csharp[LoadTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#LoadTensorFlowModel)]

    Po načtení modelu můžete extrahovat jeho vstupní a výstupní schéma. Schémata se zobrazují jenom pro vás a jenom učení. Tento kód nepotřebujete, aby konečná aplikace fungovala:

    [!code-csharp[GetModelSchema](./snippets/text-classification-tf/csharp/Program.cs#GetModelSchema)]

    Vstupní schéma je pole s pevnou délkou kódovaných slov typu Integer. Výstupní schéma je plovoucí pole pravděpodobnosti, které označuje, zda je mínění revize záporná nebo kladná. Tyto hodnoty se sčítají na 1, protože pravděpodobnost, že je kladné, je doplňkem pravděpodobnosti mínění negativní.

## <a name="create-the-mlnet-pipeline"></a>Vytvoření kanálu ML.NET

1. Vytvořte kanál a rozdělte vstupní text na slova pomocí transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) pro rozdělení textu na slova jako další řádek kódu:

   [!code-csharp[TokenizeIntoWords](./snippets/text-classification-tf/csharp/Program.cs#TokenizeIntoWords)]

   Transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) používá mezery k analýze textu nebo řetězce na slova. Vytvoří nový sloupec a rozdělí jednotlivé vstupní řetězce na vektor podřetězců na základě oddělovače definovaného uživatelem.

1. Namapujte slova na celočíselné kódování pomocí vyhledávací tabulky, kterou jste deklarovali výše:

    [!code-csharp[MapValue](./snippets/text-classification-tf/csharp/Program.cs#MapValue)]

1. Změňte velikost celočíselných kódování proměnné na pevnou délku, kterou vyžaduje model:

    [!code-csharp[CustomMapping](./snippets/text-classification-tf/csharp/Program.cs#CustomMapping)]

1. Klasifikace vstupu pomocí načteného modelu TensorFlow:

    [!code-csharp[ScoreTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#ScoreTensorFlowModel)]

    Výstup modelu TensorFlow se zavolá `Prediction/Softmax` . Všimněte si, že název `Prediction/Softmax` je určený podle modelu TensorFlow. Tento název nemůžete změnit.

1. Vytvoří nový sloupec pro předpověď výstupu:

    [!code-csharp[SnippetCopyColumns](./snippets/text-classification-tf/csharp/Program.cs#SnippetCopyColumns)]

    Je nutné zkopírovat `Prediction/Softmax` sloupec do jednoho s názvem, který lze použít jako vlastnost ve třídě C#: `Prediction` . `/`Znak není povolen v názvu vlastnosti C#.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Vytvoření modelu ML.NET z kanálu

1. Přidejte kód pro vytvoření modelu z kanálu:

    [!code-csharp[SnippetCreateModel](./snippets/text-classification-tf/csharp/Program.cs#SnippetCreateModel)]

    Model ML.NET se vytvoří z řetězce odhady v kanálu voláním `Fit` metody. V takovém případě nebudeme pro vytvoření modelu vytvářet žádná data, protože model TensorFlow již byl dříve vyškolen. Dodáváme prázdný objekt zobrazení dat, který splňuje požadavky `Fit` metody.

## <a name="use-the-model-to-make-a-prediction"></a>Použití modelu k vytvoření předpovědi

1. Přidejte `PredictSentiment` metodu pod `Main` metodu:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Přidejte následující kód k vytvoření `PredictionEngine` jako první řádek v `PredictSentiment()` metodě:

    [!code-csharp[CreatePredictionEngine](./snippets/text-classification-tf/csharp/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > `PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.

1. Přidejte komentář k otestování předpovědi vyškolených modelů v `Predict()` metodě vytvořením instance `MovieReview` :

    [!code-csharp[CreateTestData](./snippets/text-classification-tf/csharp/Program.cs#CreateTestData)]

1. Předání dat testovacích komentářů do do `Prediction Engine` přidejte další řádky kódu v `PredictSentiment()` metodě:

    [!code-csharp[Predict](./snippets/text-classification-tf/csharp/Program.cs#Predict)]

1. Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat:

    |Vlastnost| Hodnota|Typ|
    |-------------|-----------------------|------|
    |Předpověď|[0,5459937, 0,454006255]|float []|

1. Zobrazit předpovědi mínění pomocí následujícího kódu:

    [!code-csharp[DisplayPredictions](./snippets/text-classification-tf/csharp/Program.cs#DisplayPredictions)]

1. Na `PredictSentiment` konec metody přidejte volání `Main` :

    [!code-csharp[CallPredictSentiment](./snippets/text-classification-tf/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Výsledky

Sestavte a spusťte aplikaci.

Výsledky by měly vypadat podobně jako následující. Během zpracování se zobrazí zprávy. Můžou se zobrazovat upozornění nebo zpracovávat zprávy. Tyto zprávy byly pro přehlednost odebrány z následujících výsledků.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění opětovným použitím předem připraveného `TensorFlow` modelu v ml.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Načtení předem připraveného modelu TensorFlow
> * Transformovat text komentáře webu k funkcím vhodným pro model
> * Použití modelu k vytvoření předpovědi
