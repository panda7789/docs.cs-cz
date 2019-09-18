---
title: 'Kurz: Přeučení klasifikátoru imagí TensorFlow – učení pro přenos'
description: Naučte se, jak předávat model TensorFlow pro klasifikaci imagí pomocí učení pro přenos a ML.NET. Původní model byl vyškolený pro klasifikaci jednotlivých imagí. Po přeškolení nový model uspořádá obrázky do rozsáhlých kategorií.
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e069abe44b77b1dc31b78ecec1971ccc73f2e012
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054083"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>Kurz: Přeškolování klasifikátoru imagí TensorFlow pomocí učení přenosu a ML.NET

Naučte se, jak předávat model TensorFlow pro klasifikaci imagí pomocí učení pro přenos a ML.NET. Původní model byl vyškolený pro klasifikaci jednotlivých imagí. Po přeškolení nový model uspořádá obrázky do rozsáhlých kategorií. 

Školení modelu [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od začátku vyžaduje nastavení milionů parametrů, tunu školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU). I když není tak efektivní jako školení vlastního modelu od začátku, pomůže vám tento proces zástupcem pracovat s tisíci imagí. miliony imagí s popisky a sestavování vlastního modelu je poměrně rychlé (během hodiny na počítači bez GPU).

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Pochopení problému
> * Opakované využití a vyladění předučeného modelu
> * Klasifikace imagí

## <a name="what-is-transfer-learning"></a>Co je učení přenosu?

Co když byste mohli znovu použít model, který už je předem vyškolený, aby vyřešil podobný problém a znovu provedl jednu nebo několik vrstev tohoto modelu, aby problém vyřešil? Tato metoda opětovného použití části již vyškolených modelů pro sestavení nového modelu se označuje jako [učení přenosu](https://en.wikipedia.org/wiki/Transfer_learning).

## <a name="image-classification-sample-overview"></a>Ukázka klasifikace obrázků – přehled

Ukázka je Konzolová aplikace, která používá ML.NET k vytvoření klasifikátoru imagí tím, že znovu používá předem připravený model pro klasifikaci imagí s malým množstvím školicích dat.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) . Všimněte si, že ve výchozím nastavení je konfigurace projektu .NET pro tento kurz určena pro .NET Core 2,2.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy. 

* Balíček NuGet pro Microsoft.ML 1.0.0
* Balíček NuGet Microsoft. ML. ImageAnalytics 1.0.0
* Balíček NuGet Microsoft. ML. TensorFlow 0.12.0

* [Adresář assetů tutorial Soubor ZIP](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [Model strojového učení InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte příslušný úkol strojového učení.

[Obsáhlý Learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, což jsou revolutionizing oblasti, jako je počítačové zpracování obrazu a rozpoznávání řeči.

Modely hloubkového učení jsou vyškoleny pomocí rozsáhlých sad [dat s popisky](https://en.wikipedia.org/wiki/Labeled_data) a [neuronové sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více výukových vrstev. Obsáhlý Learning:

* Je lepší pro některé úkoly, jako je Počítačové zpracování obrazu.

* Provede i velké množství dat.

Klasifikace obrázku je běžný Machine Learning úkol, který nám umožňuje automaticky klasifikovat obrázky do více kategorií, například:

* Zjištění lidského obličeje v obrázku nebo ne.
* Detekce koček a psi.

 Nebo jako v následujících imagích, které určují, jestli je image a (n) jídla, hračka nebo zařízení:

![obrázek![informační](./media/image-classification/220px-Pepperoni_pizza.jpg)
zprávy image Pizza](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
image![Teddy](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Předchozí image patří do Wikimedia a jsou jim tyto atributy:
>
> * "220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505 ,
> * "119px-Nalle_-_a_small_brown_teddy_bear. jpg" pomocí [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) – s použitím uživatelsky optimalizovaného grafu, kopie od-SA https://commons.wikimedia.org/w/index.php?curid=48166 2,0,.
> * "193px-Broodrooster. jpg" podle [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) vlastní práce, CC by-sa 3,0, https://commons.wikimedia.org/w/index.php?curid=27403

Učení přenosu zahrnuje několik strategií, jako je například *převlakování všech vrstev* a *předposlední vrstvy*. V tomto kurzu se dozvíte, jak používat *předposlední strategii vrstev*. *Předposlední strategie vrstev* znovu používá model, který již byl předem vyškolen pro vyřešení konkrétního problému. Strategie potom přeškolí konečnou vrstvu tohoto modelu, aby vyřešila nový problém. Po opětovném použití předem připraveného modelu v rámci nového modelu ušetříte významný čas a prostředky.

Model klasifikace imagí znovu používá [model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)zahájení, oblíbený model rozpoznávání imagí, který je vyškolený pro `ImageNet` datovou sadu, kde se TensorFlow model snaží klasifikovat celé obrázky do tisíc tříd, jako jsou "deštník", "Jersey" a " Myčka nádobí.

Může být klasifikován jako [rozsáhlá síť neuronové konvoluční](https://en.wikipedia.org/wiki/Convolutional_neural_network) a může dosáhnout přiměřeného výkonu pro úlohy s vysokým vizuálním rozpoznáváním, v porovnání s nebo překročení lidského výkonu v některých doménách. `Inception v1 model` Model/algoritmus byl vyvinutý několika výzkumníky a na základě původního papíru: ["Přemýšlení architektury zahájení pro Počítačové zpracování obrazu" podle Szegedy, et. VŠ.](https://arxiv.org/abs/1512.00567)

Vzhledem k tomu, že již byl předem vyškolen na tisících různých imagí, obsahuje [funkce obrázků](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné pro identifikaci obrázku. `Inception model` Nižší vrstvy funkcí obrázku rozpoznávají jednoduché funkce (například hrany) a vyšší vrstvy rozpoznávají složitější funkce (například tvary). Konečná vrstva je vyučena s mnohem menším množstvím dat, protože začínáte předučeným modelem, který již rozumí způsobu klasifikace obrázků. Jak model umožňuje klasifikovat více než dvě kategorie, jedná se například o [klasifikátor více tříd](../resources/tasks.md#multiclass-classification). 

`TensorFlow`je oblíbená sada nástrojů pro hloubkové učení a strojové učení, která umožňuje školicí neuronové sítě (a obecné číselné výpočty) a implementuje se jako `transformer` v ml.NET. Pro tento kurz se používá k opakovanému použití `Inception model`.

Jak je znázorněno v následujícím diagramu, přidáte odkaz na balíčky NuGet ML.NET v aplikacích .NET Core nebo .NET Framework. V rámci zahrnutí ml.NET zahrnuje a odkazuje na nativní `TensorFlow` knihovnu, která umožňuje napsat kód, který načte existující soubor trained `TensorFlow` model pro bodování.  

![Diagram TensorFlow Transform ML.NET archu](./media/image-classification/tensorflow-mlnet.png)

`Inception model` Je vyškolena pro klasifikaci imagí do tisíc kategorií, ale je třeba klasifikovat obrázky v menší sadě kategorií a pouze na tyto kategorie. `transfer` Zadejte`transfer learning`část. Můžete přenést `Inception model`schopnost rozpoznávat a klasifikovat obrázky pro nové kategorie omezené na vlastní třídění imagí.  

 Chystáte se přesměrovat finální vrstvu tohoto modelu pomocí sady tří kategorií:

* Potravinářství
* Hračk
* Náplně

Vaše vrstva používá [algoritmus MULTINOMIAL logistické regrese](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) k co nejrychlejšímu nalezení správné kategorie. Tento algoritmus klasifikuje použití pravděpodobností k určení odpovědi, zadání jedné hodnoty do správné kategorie a nulová hodnoty ostatním.  

### <a name="dataset"></a>DataSet

Existují dva zdroje dat: `.tsv` soubor a soubory obrázků.  Soubor obsahuje dva sloupce: první je definována jako `ImagePath` a druhá druhá `Label` odpovídá obrázku. `tags.tsv` Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:

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

Obrázky školení a testování se nacházejí ve složkách assetů, které stáhnete do souboru ZIP. Tyto image patří do Wikimedia.
> *[Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), bezplatné úložiště médií.* Načteno 10:48, 17. října 2018 z:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TransferLearningTF".

2. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ml**. Klikněte na rozevírací seznam **verze** , v seznamu vyberte balíček **1.0.0** a vyberte tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** . Opakujte tyto kroky pro **Microsoft. ml. ImageAnalytics v 1.0.0** a **Microsoft. ml. TensorFlow v 0.12.0**.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte si [soubor zip adresáře Project assets](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)a rozbalte ho.

2. Zkopírujte adresář do adresáře projektu *TransferLearningTF.* `assets` Tento adresář a jeho podadresáře obsahují data a podpůrné soubory (s výjimkou modelu zahájení, který si stáhnete a přidáte v dalším kroku) potřebném pro tento kurz.

3. Stáhněte si [model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)zahájení a rozbalte ho.

4. Zkopírujte obsah `inception5h` adresáře pouze do složky projektu `assets\inputs-train\inception` *TransferLearningTF* . Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:

   ![Obsah adresáře v adresáři](./media/image-classification/inception-files.png)

5. V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři assetů a podadresářích a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

Do horní části souboru `using` *program.cs* přidejte následující dodatečné příkazy:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Vytvořte globální pole pro uchování cest k různým prostředkům a globální proměnné pro `LabelTokey`,`ImageReal` `PredictedLabelValue`a:

* `_assetsPath`má cestu k assetům.
* `_trainTagsTsv`má cestu k souboru. TSV datových značek pro školicí image.
* `_predictTagsTsv`má cestu k souboru TSV značek dat předpovědi.
* `_trainImagesFolder`má cestu k obrázkům používaným ke výukě modelu.
* `_predictImagesFolder`má cestu k obrázkům, které mají být klasifikovány podle vyškolených modelů.
* `_inceptionPb`má cestu k předučenému modelu zahájení, který se má znovu použít k přeškolování modelu.
* `_inputImageClassifierZip`má cestu, ze které je načten model trained.
* `_outputImageClassifierZip`má cestu, kde je uložený model trained.
* `LabelTokey``Label` je hodnota namapovaná na klíč.
* `ImageReal`je sloupec obsahující předpovězenou hodnotu obrázku.
* `PredictedLabelValue`je sloupec obsahující předpokládanou hodnotu popisku.

Přidejte následující kód na řádek přímo nad `Main` metodu pro určení těchto cest a dalších proměnných:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Vytvořte některé třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *imageData.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *imageData.cs* . Do horní části `using` *imageData.cs*přidejte následující příkaz:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Odeberte existující definici třídy a přidejte následující kód pro `ImageData` třídu do souboru *imageData.cs* :

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData`je třída vstupních dat obrázku a obsahuje následující <xref:System.String> pole:

* `ImagePath`obsahuje název souboru obrázku.
* `Label`obsahuje hodnotu pro popisek obrázku.

Přidejte do projektu novou třídu pro `ImagePrediction`:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *ImagePrediction.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *ImagePrediction.cs* . `System.Collections.Generic` Odeberte příkazy`using` a v horní části *ImagePrediction.cs:* `System.Text`

Odeberte existující definici třídy a přidejte následující kód, který má `ImagePrediction` třídu, do souboru *ImagePrediction.cs* :

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction`je třída prediktivních imagí a má následující pole:

* `Score`obsahuje procento spolehlivosti pro danou klasifikaci obrázku.
* `PredictedLabelValue`obsahuje hodnotu pro předpokládaný popisek klasifikace obrázku.

`ImagePrediction`je třída použitá pro předpověď po vyškolení modelu. Má `string` (`ImagePath`) pro cestu k obrázku. `Label` Slouží k opakovanému použití a přeučení modelu. `PredictedLabelValue` Je používán během předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

Inicializujte `MLContext`proměnnou novou instancí. `mlContext`  `Main` Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Vytvoření struktury pro výchozí parametry

Model zahájení má několik výchozích parametrů, které je třeba předat. Vytvořte strukturu pro mapování výchozích hodnot parametrů na popisné názvy pomocí následujícího kódu, a to hned za `Main()` metodou:

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Vytvoření metody zobrazovacího nástroje

Vzhledem k tomu, že zobrazíte data obrázku a související předpovědi více než jednou, vytvořte metodu zobrazení nástrojů pro zpracování zobrazení obrázků a výsledků předpovědi.

`DisplayResults()` Metoda provádí následující úlohy:

* Zobrazí předpovězené výsledky.

Vytvořte metodu hned `InceptionSettings` za strukturou pomocí následujícího kódu: `DisplayResults()`

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

Metoda naplněná `ImagePath`společněspředpovězenými poli.`ImagePrediction` `Transform()` V průběhu procesu ML.NET jednotlivé komponenty přidávají sloupce a usnadňují zobrazení výsledků:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

`DisplayResults()` Metodu zavoláte do dvou metod klasifikace imagí.

### <a name="create-a-tsv-file-utility-method"></a>Vytvoření metody Utility souboru. TSV

`ReadFromTsv()` Metoda provádí následující úlohy:

* Přečte soubor dat `tags.tsv` obrázku.
* Přidá cestu k souboru s názvem souboru obrázku.
* Načte data souboru do objektu IEnumerable`ImageData` .

Vytvořte metodu hned `PairAndDisplayResults()` za metodou pomocí následujícího kódu: `ReadFromTsv()`

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

Následující kód analyzuje `tags.tsv` soubor, aby přidal cestu k souboru bitové kopie pro danou `ImagePath` vlastnost `Label` a načetl `ImageData` ji a do objektu. Přidejte ho jako první řádek `ReadFromTsv()` metody.  K zobrazení výsledků předpovědi potřebujete plně kvalifikovanou cestu k souboru.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
ML.NET jsou tři hlavní koncepty: [Data](../resources/glossary.md#data), [transformátory](../resources/glossary.md#transformer)a [odhady](../resources/glossary.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Opakované použití a vyladění předem připraveného modelu

Do metody přidejte následující volání `ReuseAndTuneInceptionModel()`metody jako další řádek kódu `Main()` v metodě:

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` Metoda provádí následující úlohy:

* Načte data.
* Extrahuje a transformuje data.
* Skóre modelu TensorFlow.
* Vyladí (převlaky) modelu.
* Zobrazí výsledky modelu.
* Vyhodnotí model.
* Vrátí model.

Vytvořte metodu hned `InceptionSettings` za`DisplayResults()` strukturou a těsně před metodou pomocí následujícího kódu: `ReuseAndTuneInceptionModel()`

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Načtení dat

Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.

Načtěte data pomocí `MLContext.Data.LoadFromTextFile` obálky. Přidejte následující kód jako další řádek v `ReuseAndTuneInceptionModel()` metodě:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Extrakce funkcí a transformace dat

Data před zpracováním a čištěním jsou důležité úlohy, ke kterým dochází předtím, než se pro strojové učení efektivně použije datová sada.  Použití dat bez těchto úloh modelování může způsobit zavádějící výsledky.

Algoritmy strojového učení rozumějí data [natrénuje](../resources/glossary.md#feature) a při práci s hlubokými neuronové sítěmi musíte image přizpůsobit podle formátu očekávaného sítí. Tento formát je [číselného vektoru](../resources/glossary.md#numerical-feature-vector).

Po školení a vyhodnocení vyhodnoťte hodnoty sloupce **popisek** . Při použití předem připraveného modelu mapujte pole do nového modelu pomocí metody [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) . Tato metoda transformuje `Label` sloupec do číselného typu klíče (`LabelTokey`) a přidá ho jako sloupec nové datové sady:  Pojmenujte ho `estimator` , protože do něj taky přidáte Trainer. Přidat další řádek kódu:

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

Pro extrakci funkcí používá Estimator zpracování imagí předem vyškolenou [neuronové síť (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers. Při práci s hluboce neuronové sítěmi přiřadíte image k očekávanému formátu sítě. To je důvod, proč pomocí několika transformací obrázku získá obrazová data do očekávaného formátu modelu:

1. `LoadImages`Transformační obrázky jsou načteny do paměti jako typ rastrového obrázku.
2. `ResizeImages` Transformace změní velikost obrázků jako předučený model s definovanou šířkou a výškou vstupní bitové kopie.
3. Tato `ExtractPixels` transformace extrahuje pixely ze vstupních imagí a převede je na číselný vektor.

Přidejte tyto transformace obrázků jako další řádky kódu:

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

Je pohodlnější způsob, který `TensorFlow` umožňuje načíst model `TensorFlowEstimator` jednou a pak vytvoří pomocí `ScoreTensorFlowModel`. `LoadTensorFlowModel` Extrahuje zadané výstupy `Inception model`(funkce `softmax2_pre_activation`obrázku) a vyhodnotí datovou sadu pomocí předem připraveného `TensorFlow` modelu. `ScoreTensorFlowModel`

`softmax2_pre_activation`pomáhá modelu při určování, do které třídy patří obrázky. `softmax2_pre_activation`vrací pravděpodobnost pro každou kategorii pro obrázek a všechny tyto pravděpodobnosti musí přidat až 1. Předpokládá, že bitová kopie bude patřit pouze do jedné kategorie, jak je znázorněno v následujícím příkladu:

| Třída         | Jakou   |
| ------------- | ------------- |
| `Food`        |  0,001        |
| `Toy`         |  0,95         |
| `Appliance`   |  0,06         |

`TensorFlowTransform` Přidejte`estimator` k a následující řádek kódu:

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Zvolit algoritmus školení

Chcete-li přidat školicí algoritmus, zavolejte `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` metodu obálky.  [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) je připojen k `estimator` a přijímá funkce informování imagí `Label` (`softmax2_pre_activation`) a vstupní parametry, abyste se dozvěděli z historických dat.  Přidejte Trainer s následujícím kódem:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Je také nutné namapovat `predictedlabel` `predictedlabelvalue`na:

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` Metoda navlakuje váš model transformací datové sady a použitím školení. Přizpůsobte model do datové sady školení a vraťte vyškolený model přidáním následujícího jako další řádek kódu v `ReuseAndTuneInceptionModel()` metodě:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro více zadaných vstupních řádků testovací sady dat.  Transformujte `ReuseAndTuneInceptionModel()`data přidáním následujícího kódu do: `Training`

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Převeďte obrazová data a `DataViews` předpovědi na dvojici `IEnumerables` se silným typem a pro snazší zobrazení. Použijte k tomu metodu pomocí následujícího kódu: `MLContext.CreateEnumerable()`

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Přidejte následující kód pro zobrazení dat a předpovědi jako další řádky v `ReuseAndTuneInceptionModel()` metodě:

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

Jakmile máte předsadu předpovědi, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

* Vyhodnotí model (porovná předpovězené hodnoty se skutečnou datovou `Labels`sadou).

* Vrátí metriku výkonu modelu.

Do `ReuseAndTuneInceptionModel()` metody přidejte následující kód jako další řádek:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

Pro klasifikaci imagí jsou vyhodnocovány následující metriky:

* `Log-loss`– viz [ztráta protokolu](../resources/glossary.md#log-loss). Chcete, aby byla ztráta protokolu co nejblíže k nule.

* `Per class Log-loss`. Požadujete, aby byla ztráta protokolu podle třídy co nejblíže k nule.

Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 Přidejte následující kód, který vrátí vycvičený model jako další řádek:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>Klasifikace imagí pomocí načteného modelu

Do metody přidejte následující volání `ClassifyImages()` metody jako další řádek kódu `Main` v metodě:

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` Metoda provádí následující úlohy:

* Operace. Soubor TSV do `IEnumerable`.
* Předpovídá klasifikace obrázků na základě testovacích dat.

Vytvořte metodu hned `ReuseAndTuneInceptionModel()` za`PairAndDisplayResults()` metodou a těsně před metodou pomocí následujícího kódu: `ClassifyImages()`

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

Nejprve zavolejte `ReadFromTsv()` metodu pro `IEnumerable<ImageData>` vytvoření třídy, která obsahuje úplnou cestu pro každý z nich `ImagePath`. K spárování vašich dat a výsledků předpovědi potřebujete tuto cestu k souboru. Také je nutné převést `IEnumerable<ImageData>` třídu na objekt `IDataView` , který budete používat k předpovědi. Přidejte následující kód jako následující dva řádky v `ClassifyImages()` metodě:

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

Jak jste prošli s daty školicích imagí, předpověď kategorie testovacích dat pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) předaného modelu. Přidejte `ClassifyImages()` následující kód do metody pro předpovědi a pro `predictions` `IDataView` převod `IEnumerable` na pro párování a zobrazení:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Pro spárování a zobrazení dat testovací image a předpovědi přidejte následující kód pro volání `DisplayResults()` metody dříve vytvořené jako další řádek `ClassifyImages()` v metodě:

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Klasifikace jednoho obrázku s načteným modelem

Do metody přidejte následující volání `ClassifySingleImage()` metody jako další řádek kódu `Main` v metodě:

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifySingleImage()` Metoda provádí následující úlohy:

* `ImageData` Načte instanci.
* Odhadne klasifikaci obrázku na základě testovacích dat.

Vytvořte metodu hned `ClassifyImages()` za`PairAndDisplayResults()` metodou a těsně před metodou pomocí následujícího kódu: `ClassifySingleImage()`

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

Nejprve vytvořte `ImageData` třídu, která obsahuje plně kvalifikovanou cestu a název souboru obrázku pro jednu `ImagePath`z nich. Přidejte následující kód jako další řádky v `ClassifySingleImage()` metodě:

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[Třída PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které provádí předpovědi pro jednu instanci dat. Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden sloupec dat. Předat `imageData` do `ClassifySingleImage()`a předpovědět kategorii obrázku přidáním následujícího kódu do: `PredictionEngine`

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

Zobrazit výsledek předpovědi jako další řádek kódu v `ClassifySingleImage()` metodě:

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Výsledky

Po provedení předchozích kroků spusťte konzolovou aplikaci (CTRL + F5). Výsledky by měly být podobné následujícímu výstupu.  Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.

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

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení pro klasifikaci imagí tím, že znovu použijete předem připravený `TensorFlow` model v ml.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Pochopení problému
> * Opakované využití a vyladění předučeného modelu
> * Klasifikace imagí pomocí načteného modelu

Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku klasifikace rozbalené image.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-Samples – úložiště GitHub](https://github.com/dotnet/machinelearning-samples/)
