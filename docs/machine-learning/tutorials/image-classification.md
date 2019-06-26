---
title: 'Kurz: Třídění image obsloužených TensorFlow - learningu'
description: Zjistěte, jak přeučování TensorFlow model klasifikace obrázků s využitím learningu a ML.NET. Původní model se trénuje klasifikovat jednotlivých obrázků. Po přetrénování, nový model slouží k uspořádání obrázků do kategorií.
ms.date: 06/12/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 62a926795ce34a8c1639f1d42ebbb34b53dc67ad
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401741"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>Kurz: Přeučování klasifikátor TensorFlow image s learningu a ML.NET

Zjistěte, jak přeučování TensorFlow model klasifikace obrázků s využitím learningu a ML.NET. Původní model se trénuje klasifikovat jednotlivých obrázků. Po přetrénování, nový model slouží k uspořádání obrázků do kategorií. 

Školení [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model úplně od začátku vyžaduje nastavení miliony parametry, spoustu s popiskem trénovacích dat a velké množství výpočetních prostředků (vzdálené stovky hodin GPU). Přestože není tak účinné jako trénujete model pro vlastní úplně od začátku, learningu vám umožní místní tento proces při práci s tisíci imagí a miliony označené obrázky a poměrně rychle vytvářet vlastní model (za hodinu na počítači bez GPU).

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Opakovaně používat a vyladit předem natrénovaných modelů
> * Klasifikace obrázků

## <a name="what-is-transfer-learning"></a>Co je přenos učení?

Co když můžete znovu použít model, který již byl před vyškolit tak, aby podobný problém vyřešit a přeučování všechny nebo některé z vrstev tento model, aby byl váš problém vyřešit? Opětovné použití součást již trénovaného modelu vytvoříte nový model Tato technika se nazývá [přenos learning](https://en.wikipedia.org/wiki/Transfer_learning).

## <a name="image-classification-sample-overview"></a>Přehled ukázky klasifikace obrázků

Ukázka je konzolová aplikace, která používá ML.NET k sestavení třídění image opětovným použitím předem vytrénovaných model pro klasifikaci obrázků s menším objemem trénovací data.

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) úložiště.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

* Balíček Nuget Microsoft.ML 1.0.0
* Balíček Nuget Microsoft.ML.ImageAnalytics 1.0.0
* Balíček Nuget Microsoft.ML.TensorFlow 0.12.0

* [Adresář, který kurzů aktiv. Soubor ZIP](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [Model InceptionV3 strojového učení](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

[Obsáhlý learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, která je revolutionizing oblastem, jako pro počítačové zpracování obrazu a řeči.

Obsáhlý learning jsou trénované modely s využitím velkých sad [označené data](https://en.wikipedia.org/wiki/Labeled_data) a [neuronových sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více vrstev učení. Obsáhlý learning:

* Na některé úkoly, jako je pro počítačové zpracování obrazu vrací lepší výsledky.

* Provádí také data obrovské objemy.

Klasifikace obrázků je běžný úkol Machine Learning, která umožňuje automaticky klasifikovat bitové kopie do více kategorií, jako například:

* Detekuje lidské tváře v obrázku nebo ne.
* Zjišťování koček a psů.

 Nebo jako v následujících imagí zjištění, zda je bitová kopie položku food, hračka nebo zařízení:

![Obrázek pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![míša opatřeny image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Předchozí obrázky Commons o Wikimedia patří a mají atributy následujícím způsobem:
>
> * "220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" podle [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) -svým fotografovali kopie BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster.jpg" podle [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) – vlastní práci, CC BY SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403

Přenos learning obsahuje několik strategií, jako například *přeučování všechny vrstvy* a *předposlední vrstvy*. V tomto kurzu se vysvětlují, ukazují, jak používat *předposlední vrstvy strategie*. *Předposlední vrstvy strategie* opětovně používá model, který je již předběžně školení k vyřešení konkrétního problému. Strategie pak retrains poslední vrstva tohoto modelu k němu nový problém vyřešit. Opětovné použití předem natrénovaných modelů jako součást nového modelu vám ušetří spoustu času a prostředků.

Opětovně používá model klasifikace obrázků [vzniku modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), model rozpoznávání image Oblíbené trénovaných na `ImageNet` datovou sadu, ve kterém modelu TensorFlow pokusí o klasifikaci celého Image na tisíc třídy, jako je třeba " Zastřešující","Jersey"a"Nádobí".

`Inception v3 model` Dají považovat za [hluboké konvoluční neuronové sítě](https://en.wikipedia.org/wiki/Convolutional_neural_network) a dosáhnout adekvátní výkon na pevné visual rozpoznávání úloh, odpovídající nebo překročení lidské výkonu v některé domény. / Algoritmem modelu byla vypracovanou organizací cccppf více výzkumní pracovníci a podle původního dokumentu: ["Jiný pohled na architekturu zahájení pro počítačové zpracování obrazu" podle Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)

Protože `Inception model` již byl před trénovaných na tisíce jinou Image, obsahuje [obrázku funkce](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné k identifikaci image. Nižších vrstvách funkce image rozpoznat jednoduché funkce (například okraje) a vyšší vrstvy rozpoznávání podobě komplexních funkcí (jako je například tvary). Poslední vrstva se trénuje proti mnohem menší sady dat, vzhledem k tomu, že začínáte s pre trénovaného modelu, která již analyzuje jak klasifikovat bitové kopie. Jako model umožňuje klasifikovat více než dvě kategorie, toto je příklad [roc třídění](../resources/tasks.md#multiclass-classification). 

`TensorFlow` je oblíbená obsáhlého learningu a nástrojů strojového učení pro školení hluboké neuronové sítě (a obecné numerické výpočty) a je implementovaný jako `transformer` v ML.NET. V tomto kurzu se používá pro opětovné použití `Inception model`.

Jak je znázorněno v následujícím diagramu, přidejte odkaz na balíčky ML.NET NuGet v aplikacích .NET Core nebo .NET Framework. Pod pokličkou, ML.NET zahrnuje a odkazuje na nativní `TensorFlow` knihovnu, která umožňuje napsat kód, který načte existující školení `TensorFlow` souboru modelu pro vyhodnocení.  

![Transformace TensorFlow ML.NET Arch diagramu](./media/image-classification/tensorflow-mlnet.png)

`Inception model` Trénovaných ke klasifikaci obrázků do tisíce kategorií, ale je potřeba klasifikace obrázků v menší sadu kategorií a pouze tyto kategorie. Zadejte `transfer` součástí `transfer learning`. Můžete převést `Inception model`vaší schopnost rozpoznat a klasifikace obrázků na nové omezené kategorie klasifikátoru vlastní image.  

 Chystáte se přeučování poslední vrstva tohoto modelu používáte sadu tří kategorií:

* Potravinářství
* Hračka
* Zařízení

Používá vaše vrstvy [algoritmu logistické regrese multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) co nejrychleji najít správnou kategorii. Tento algoritmus klasifikuje pomocí pravděpodobnosti určit odpověď, poskytuje jednu hodnotu na správnou kategorii a nulová hodnota ostatním.  

### <a name="dataset"></a>DataSet

Existují dva zdroje dat: `.tsv` souborů a souborů obrázků.  `tags.tsv` Soubor obsahuje dva sloupce: první z nich je definován jako `ImagePath` a druhý je `Label` odpovídající do bitové kopie. Následující příklad souboru nemá řádek záhlaví a vypadá takto:

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

Trénovací a testovací bitové kopie jsou umístěny ve složkách prostředky, které budete stáhnout jako soubor zip. Tyto Image patří do Commons o Wikimedia.
> *[Commons o Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), úložiště volných médií.* Načtená 10:48, 17. října 2018 od:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Vytvoření **konzolovou aplikaci .NET Core** nazývá "TransferLearningTF".

2. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**. Klikněte na **verze** rozevíracího seznamu, vyberte **1.0.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené. Opakujte tyto kroky pro **Microsoft.ML.ImageAnalytics v1.0.0** a **Microsoft.ML.TensorFlow v0.12.0**.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte si [souboru zip projektu prostředků adresáře](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)a rozbalte ho.

2. Kopírovat `assets` adresáře do vašeho *TransferLearningTF* adresáře projektu. Tento adresář a jeho podadresářích obsahovat soubory dat a podporu (s výjimkou vzniku modelu, který budete stáhnout a přidat v dalším kroku) pro tento kurz potřeba.

3. Stáhněte si [vzniku modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)a rozbalte ho.

4. Zkopírujte obsah `inception5h` rozzipoval. stačí do adresáře vašeho *TransferLearningTF* projektu `assets\inputs-train\inception` adresáře. Tento adresář obsahuje model a další podpůrné soubory pro tento kurz potřeba, jak je znázorněno na následujícím obrázku:

   ![Obsah adresáře zahájení](./media/image-classification/inception-files.png)

5. V Průzkumníku řešení klikněte pravým tlačítkem myši na každém ze souborů v majetku adresáře a podadresářů a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Vytvořte globální pole pro uložení cest k různým prostředkům a globálních proměnných pro `LabelTokey`,`ImageReal`, a `PredictedLabelValue`:

* `_assetsPath` obsahuje cestu k prostředky.
* `_trainTagsTsv` má cestu k souboru tsv školení image data značek.
* `_predictTagsTsv` má cestu k souboru tsv předpovědi image data značek.
* `_trainImagesFolder` obsahuje v cestě k obrázkům využívají k tréninku modelu.
* `_predictImagesFolder` obsahuje v cestě k obrázkům zařazují trénovaného modelu.
* `_inceptionPb` obsahuje cestu k předem vytrénovaných vzniku model znovu použije k přeučování modelu.
* `_inputImageClassifierZip` má cesta kde trénovaný model je načtený z.
* `_outputImageClassifierZip` obsahuje cestu k uložení naučeného modelu.
* `LabelTokey` je `Label` hodnotu namapovány na klíče.
* `ImageReal`  je sloupec obsahující hodnotu předpokládané obrázku.
* `PredictedLabelValue` je sloupec obsahující hodnoty předpovězené popisku.

Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Vytvořte některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *ImageData.cs*. Vyberte **přidat** tlačítko.

    *ImageData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *ImageData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Odeberte stávající definice třídy a přidejte následující kód `ImageData` třídu *ImageData.cs* souboru:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData` je třída dat vstupního obrázku a má následující <xref:System.String> pole:

* `ImagePath` obsahuje název souboru obrázku.
* `Label` obsahuje hodnotu pro popisek image.

Přidejte novou třídu do projektu pro `ImagePrediction`:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *ImagePrediction.cs*. Vyberte **přidat** tlačítko.

    *ImagePrediction.cs* soubor se otevře v editoru kódu. Odebrat i `System.Collections.Generic` a `System.Text` `using` příkazů v horní části *ImagePrediction.cs*:

Odeberte stávající definice třídy a přidejte následující kód, který má `ImagePrediction` do třídy *ImagePrediction.cs* souboru:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction` je třída prediktivní vkládání obrázků a obsahuje následující pole:

* `Score` obsahuje procento spolehlivosti pro danou image klasifikaci.
* `PredictedLabelValue` obsahuje hodnotu pro popisek klasifikace předpokládané image.

`ImagePrediction` Třída slouží k předpovědi po model se trénuje. Má `string` (`ImagePath`) pro cestu k obrázku. `Label` Se používá pro opětovné použití přeučování modelu. `PredictedLabelValue` Se používá při předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.

[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Inicializovat `mlContext` proměnné s novou instanci třídy `MLContext`.  Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Vytvořte strukturu pro výchozí parametry

Zahájení model má několik výchozích parametrů, které je potřeba předat. Vytvořte strukturu pro mapování výchozí hodnoty parametrů pro popisných názvů následujícím kódem, bezprostředně po `Main()` metody:

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Vytvořit metodu nástroj zobrazení

Vzhledem k tomu, že budete více než jednou zobrazovat obrazová data a související predikcí, vytvořte metodu zobrazení nástroj pro zpracování zobrazení výsledků image a předpovědi.

`DisplayResults()` Metoda spustí následující úlohy:

* Zobrazí predikované výsledky.

Vytvořte `DisplayResults()` metoda, hned za `InceptionSettings` struktury, pomocí následujícího kódu:

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

`Transform()` Metoda vyplní `ImagePath` v `ImagePrediction` spolu s předpokládanou pole. V průběhu procesu ML.NET jednotlivých komponent přidá sloupce, a to usnadňuje zobrazení výsledků:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

Budete volat `DisplayResults()` metoda v metodách klasifikace dvě image.

### <a name="create-a-tsv-file-utility-method"></a>Vytvořit metodu nástroj soubor TSV

`ReadFromTsv()` Metoda spustí následující úlohy:

* Přečte data bitové kopie `tags.tsv` souboru.
* Cesta k souboru se přidá k názvu souboru bitové kopie.
* Načte datový soubor do použití rozhraní IEnumerable`ImageData` objektu.

Vytvořte `ReadFromTsv()` metoda, hned za `PairAndDisplayResults()` metodu, pomocí následujícího kódu:

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

Následující kód analyzuje prostřednictvím `tags.tsv` soubor a přidejte cestu k souboru na název souboru obrázku `ImagePath` vlastnost a načtěte ho a `Label` do `ImageData` objektu. Přidejte jako první řádek `ReadFromTsv()` metody.  Budete potřebovat plně kvalifikovanou cestu k zobrazení výsledků předpovědí.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
Existují tři hlavní koncepty v ML.NET: [Data](../resources/glossary.md#data), [transformátory](../resources/glossary.md#transformer), a [odhady](../resources/glossary.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Opakovaně používat a vyladit předem natrénovaných modelů

Přidejte následující volání `ReuseAndTuneInceptionModel()`metody jako další řádek kódu v `Main()` metody:

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` Metoda spustí následující úlohy:

* Načte data
* Extrahuje a transformuje data.
* Stanoví skóre TensorFlow model.
* Vyladí (retrains) modelu.
* Zobrazí výsledky modelu.
* Vyhodnotí modelu.
* Vrátí hodnotu modelu.

Vytvořit `ReuseAndTuneInceptionModel()` metoda, hned za `InceptionSettings` struktury a těsně před `DisplayResults()` metodu, pomocí následujícího kódu:

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Načtení dat

Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView). `IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové). Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.

Načtení dat pomocí `MLContext.Data.LoadFromTextFile` obálky. Přidejte následující kód jako další řádek `ReuseAndTuneInceptionModel()` metody:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Extrakce funkce a transformaci dat

Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.  Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.

Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) dat, a při práci s hluboké neuronové sítě musí přizpůsobit imagí do formátu očekávaném v síti. Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).

Po trénování a hodnocení předpovědět **popisek** hodnot sloupců. Jak při použití předem natrénovaných modelů, mapování polí na nový model [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody. Tato metoda transformuje `Label` na číselný typ klíče (`LabelTokey`) sloupce a přidejte ho jako nový sloupec datové sady:  Pojmenujte toto `estimator` jako také přidáte školitele k němu. Přidáte další řádek kódu:

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

Váš odhad používá předem pro zpracování obrázků [hluboké Neuronové Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers pro extrakci funkce. Při zpracování komplexnějších hluboké neuronové sítě, můžete přizpůsobit bitové kopie do formátu očekávanému sítě. To je důvod, že použití několika transformací bitové kopie k načtení dat obrázků do očekávanému vzoru:

1. `LoadImages`Transformace obrázky jsou načtena do paměti jako typ rastrového obrázku.
2. `ResizeImages` Transformace změní velikost obrázků předem natrénovaných modelů má definovaný vstupní image šířku a výšku.
3. `ExtractPixels` Transformace extrahuje pixely ze vstupní Image a převede je na číselné vektoru.

Přidejte tyto image transformace jako další řádky kódu:

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

`LoadTensorFlowModel` Je pohodlné metodu, která umožňuje `TensorFlow` model, který se má načíst jednou a potom vytvoří `TensorFlowEstimator` pomocí `ScoreTensorFlowModel`. `ScoreTensorFlowModel` Výpisy zadaný výstupy ( `Inception model`vaší image funkce `softmax2_pre_activation`) a stanoví skóre datové sady pomocí předem vytrénovaných `TensorFlow` modelu.

`softmax2_pre_activation` sestavit model k zjištění, které třída obrázků patří. `softmax2_pre_activation` vrací pravděpodobnost pro každou kategorii pro bitovou kopii a ve všech těchto pravděpodobností musíte přidat až 1. Předpokládá, že obraz bude patřit pouze jednu kategorii, jak je znázorněno v následujícím příkladu:

| Třída         | Pravděpodobnost   |
| ------------- | ------------- |
| `Food`        |  0.001        |
| `Toy`         |  0.95         |
| `Appliance`   |  0,06         |

Připojte `TensorFlowTransform` k `estimator` s následující řádek kódu:

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Zvolte cvičení algoritmu

Chcete-li přidat cvičení algoritmu, zavolejte `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` obalující metodu.  [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) se připojí `estimator` a přijímá funkce vzniku bitové kopie (`softmax2_pre_activation`) a `Label` vstupní parametry učit se z historických dat.  Přidáte trainer následujícím kódem:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Je také nutné `predictedlabel` k `predictedlabelvalue`:

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` Metoda trénovat modelu transformace datové sady a aplikováním školení. Přizpůsobení modelu, který má trénovací datové sady a vrátí trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `ReuseAndTuneInceptionModel()` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda vytváří předpovědi pro více poskytuje vstupní řádky z datové sady testů.  Transformace `Training` data přidáním následujícího kódu do `ReuseAndTuneInceptionModel()`:

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Převod dat obrázků a předpovědi `DataViews` do silného typu `IEnumerables` spárovat pro snadnější zobrazení. Použití `MLContext.CreateEnumerable()` metodu, pomocí následujícího kódu:

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Volání `DisplayResults()` metodu pro zobrazení vašich dat a předpovědí na dalším řádku `ReuseAndTuneInceptionModel()` metody:

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

Jakmile budete mít předpovědi nastavit, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metody:

* Posuzuje modelu (porovná předpovězené hodnoty v datové sadě skutečná `Labels`).

* Vrátí metriky výkonu modelu.

Přidejte následující kód, který `ReuseAndTuneInceptionModel()` metody jako další řádek:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

Klasifikace obrázků, se vyhodnotí následující metriky:

* `Log-loss` -naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss). Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.

* `Per class Log-loss`. Budete chtít na třídu protokolu ztrátu byly co nejblíže nuly nejvíce.

Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 Přidejte následující kód, který vrátí trénovaného modelu jako další řádek:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>Klasifikace obrázků s načíst model

Přidejte následující volání `ClassifyImages()` metody jako další řádek kódu v `Main` metody:

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` Metoda spustí následující úlohy:

* Operace čtení. Soubor TSV do `IEnumerable`.
* Předpovídá klasifikace obrázků na základě dat testu.

Vytvořit `ClassifyImages()` metoda, hned za `ReuseAndTuneInceptionModel()` metoda a těsně před `PairAndDisplayResults()` metodu, pomocí následujícího kódu:

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

Nejprve volat `ReadFromTsv()` metodu pro vytvoření `IEnumerable<ImageData>` třídu, která obsahuje plně kvalifikovanou cestu pro každý `ImagePath`. Je nutné tuto cesta k souboru spárovat se vaše data a předpovědi výsledky. Je také potřeba převést `IEnumerable<ImageData>` třídu `IDataView` , kterou použijete k předpovědi. Přidejte následující kód jako následující dva řádky v `ClassifyImages()` metody:

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

Kategorie testu image data s využitím předpovědět, jako jste to udělali dříve s trénovací data bitové kopie, [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) předaný metodě modelu. Přidejte následující kód, který `ClassifyImages()` metodu pro předpovědi a k převodu `predictions` `IDataView` do `IEnumerable` pro párování a zobrazení:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Spárujte a zobrazit testovací data bitové kopie a predikcí, přidejte následující kód k volání `DisplayResults()` metoda dříve vytvořeny jako další řádek v `ClassifyImages()` metody:

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Klasifikovat jedné image s načíst model

Přidejte následující volání `ClassifySingleImage()` metody jako další řádek kódu v `Main` metody:

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifySingleImage()` Metoda spustí následující úlohy:

* Načtení `ImageData` instance.
* Předpovídá klasifikace obrázků na základě dat testu.

Vytvořit `ClassifySingleImage()` metoda, hned za `ClassifyImages()` metoda a těsně před `PairAndDisplayResults()` metodu, pomocí následujícího kódu:

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

Nejprve vytvořte `ImageData` třídu, která obsahuje plně kvalifikovaný název souboru cestu a image pro jednoho `ImagePath`. Přidejte následující kód jako následující řádky `ClassifySingleImage()` metody:

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[PredictionEngine třídy](xref:Microsoft.ML.PredictionEngine%602) je pohodlné rozhraní API, které provádí predikcí na jednu instanci data. [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce vytváří predikcí na jeden sloupec data. Předejte `imageData` k `PredictionEngine` předpovědět kategorie obrázku tak, že přidáte následující kód, který `ClassifySingleImage()`:

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

Jako další řádek kódu v zobrazení výsledků předpovědí `ClassifySingleImage()` metody:

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Výsledky

Po provedení předchozích kroků spuštění aplikace konzoly (Ctrl + F5). Vaše výsledky by měly být podobně jako následující výstup.  Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy se odebraly z následujících výsledků pro přehlednost.

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

Blahopřejeme! Teď úspěšně sestavíte model strojového učení pro klasifikace obrázků opětovným použitím předem vytrénovaných `TensorFlow` model ML.NET.

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) úložiště.

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Pochopení problému
> * Opakovaně používat a vyladit předem natrénovaných modelů
> * Klasifikace obrázků s načíst model

Projděte si úložišti GitHub s ukázkami Machine Learning a prozkoumejte ukázkový klasifikace rozšířené image.
> [!div class="nextstepaction"]
> [úložiště GitHub DotNet/machinelearning – ukázky](https://github.com/dotnet/machinelearning-samples/)
