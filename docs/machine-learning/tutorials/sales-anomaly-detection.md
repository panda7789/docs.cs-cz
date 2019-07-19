---
title: 'Kurz: Detekovat anomálie v prodeji produktů'
description: Naučte se, jak vytvořit aplikaci pro detekci anomálií pro prodejní data produktu. Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí C# sady Visual Studio 2019.
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e87034733b048153202bc11ab94ed7605749f60c
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331685"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Kurz: Detekce anomálií v prodeji produktů pomocí ML.NET

Naučte se, jak vytvořit aplikaci pro detekci anomálií pro prodejní data produktu. Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí C# sady Visual Studio.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Načtení dat
> * Vyškolit model pro detekci anomálií špičky
> * Zjištění anomálií špičky pomocí trained model
> * Výuka modelu pro detekci anomálií bodů změn
> * Zjištění anomálií bodů změn pomocí trained model

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

* [Datová sada Product-Sales. csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Formát dat v `product-sales.csv` nástroji je založen na datové sadě "šampon Sales" za tříleté období "původně nacházejícím z datového trhu a poskytovaných pomocí TSDL (Time Series data Library), které vytvořila Rob Hyndman. "Nemožnost prodeje za tři roky v rámci" datové sady ", která je licencovaná na základě výchozího Open License pro datamarketo.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "ProductSalesAnomalyDetection".

2. Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.

3. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte balíček v **1.0.0** v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** . Opakujte tyto kroky pro **Microsoft. ml. časové řady v 0.12.0**.

4. Do horní části `using` souboru *program.cs* přidejte následující příkazy:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Stažení dat

1. Stáhněte si datovou sadu a uložte ji do složky *dat* , kterou jste vytvořili dříve:

   * Klikněte pravým tlačítkem na [*Product-Sales. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) a vyberte Uložit odkaz (nebo cíl) jako...

     Ujistěte se, \*že soubor. csv buď uložíte do složky *dat* , nebo když ho uložíte \*jinam, přesuňte soubor. CSV do složky *data* .

2. V Průzkumník řešení klikněte pravým tlačítkem na \*soubor. csv a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

Následující tabulka je náhled dat ze \*souboru. CSV:

|Měsíčně  |ProductSales |
|-------|-------------|
|1 – leden  |    271      |
|2 – leden  |    150,9    |
|.....  |    .....    |
|1 – únor  |    199,3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

Dále definujte svou datovou strukturu vstupní třídy.

Přidejte do projektu novou třídu:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > Nová položka**.

2. V **dialogovém okně Přidat novou položku**vyberte **třída** a změňte pole **název** na *ProductSalesData.cs*. Pak vyberte tlačítko **Přidat** .

V editoru kódu se otevře soubor *ProductSalesData.cs* . Do horní části `using` *ProductSalesData.cs*přidejte následující příkaz:

```csharp
using Microsoft.ML.Data;
```

Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `ProductSalesData` a `ProductSalesPrediction`, do souboru *ProductSalesData.cs* :

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData`Určuje vstupní datovou třídu. Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny. 

Do horní části souboru `using` *program.cs* přidejte následující dodatečné příkazy:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

Je potřeba vytvořit dvě globální pole, která budou uchovávat nedávno staženou cestu k souboru datové sady a uloženou cestu k souboru modelu:

* `_dataPath`má cestu k datové sadě, která se používá ke výukě modelu.
* `_docsize`obsahuje počet záznamů v souboru datové sady. Použijete ho k výpočtu `pvalueHistoryLength`.

Přidejte následující kód na řádek přímo nad `Main` metodu pro určení těchto cest:

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

Nahraďte `Main` `mlContext` řádek v metodě následujícím kódem pro deklaraci a inicializaci proměnné: `Console.WriteLine("Hello World!")`

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>Načtení dat

Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu. Jako další řádek `Main()` metody přidejte následující kód:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru. Převezme proměnné cesty k datům a vrátí `IDataView`.

## <a name="ml-task---time-series-anomaly-detection"></a>Detekce anomálií v ML úlohy – časová řada 

Detekce anomálií příznaky neočekávaná nebo neobvyklá událostí nebo chování. Dává v tom, kde hledat problémy a pomáhá zodpovědět otázku "je to divné?".

![Je toto divné](./media/sales-anomaly-detection/anomalydetection.png)

Detekce anomálií je proces zjišťování nezaložených dat časových řad. body v dané vstupní časové řadě, kde chování není očekávané, nebo "divné".

To může být užitečné v mnoha různých ohledech. Příklad:

Pokud máte auto, možná budete chtít znát: Je tento měřič olivového oleje běžný nebo mám netěsné?
Pokud sledujete spotřebu energie, měli byste si být vědomi: Dochází k výpadku?

Existují dva typy anomálií časových řad, které je možné zjistit: 

* **Špičky** označují dočasné shluky chování neobvyklé v systému. 

* **Body změny** označují začátek trvalých změn v průběhu času v systému. 

V ML.NET jsou algoritmy detekce špičky IID nebo identifikátory identifikátoru IID pro nezávislou [a identickou distribuovanou](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)datovou sadu vhodné. 

Budete analyzovat stejná prodejní data produktu za účelem detekce Špičk a změn bodů. Proces vytváření a školicích modelů je stejný pro detekci špičky a detekci bodu změny; Hlavním rozdílem je konkrétní použitý algoritmus detekce.

## <a name="spike-detection"></a>Detekce špičky 

Cílem detekce špičky je identifikovat náhlé ještě dočasné shluky, které se významně liší od většiny hodnot dat časových řad. Je důležité detekovat tyto podezřelé výjimečné položky, události nebo pozorování včas, aby byly minimalizovány. K detekci nejrůznějších anomálií, jako jsou výpadky, internetoví útoky nebo virové webovému obsahu, se dá použít následující přístup. Následující obrázek je příkladem špičky v datové sadě časových řad:

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>Vytvoření metody DetectSpike ()

Do metody přidejte následující volání `DetectSpike()`metody jako další řádek kódu `Main()` v metodě:

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

`DetectSpike()` Metoda provádí následující úlohy:

* Navlakuje model.
* Detekuje špičky na základě historických dat o prodeji.
* Zobrazí výsledky.

Vytvořte metodu hned `Main()` za metodou pomocí následujícího kódu: `DetectSpike()`

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Pomocí [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) můžete vyškolit model pro detekci špičky. Přidejte ho do `DetectSpike()` metody s následujícím kódem:

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

Přizpůsobit model `productSales` datům přidáním následujícího jako další řádek kódu `DetectSpike()` v metodě:

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) váš model pomocí transformace datové sady a použití školení.

Přidejte následující řádek kódu pro transformaci `productSales` dat jako další řádek `DetectSpike()` v metodě:

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.

Pro snazší zobrazení pomocí metody [CreateEnumerable ()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) s následujícím kódem převeďte dosilnéhotypu.`transformedData` `IEnumerable`

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

Pomocí následujícího <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu vytvořte řádek záhlaví zobrazení:

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

Ve výsledcích detekce špičky zobrazíte následující informace:

* `Alert`Označuje upozornění špičky pro daný datový bod.

* `Score``ProductSales` je hodnota pro daný datový bod v datové sadě.

* `P-Value`"P" představuje pravděpodobnost. To označuje, jak pravděpodobná je tento datový bod anomálií. 

Použijte následující kód k iterování `predictions` `IEnumerable` a zobrazení výsledků:

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>Výsledky detekce špičky

Výsledky by měly vypadat podobně jako následující. Během zpracování se zobrazí zprávy. Můžou se zobrazovat upozornění nebo zpracovávat zprávy. Tyto výsledky byly z důvodu srozumitelnosti odebrány z následujících výsledků.

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a>Detekce bodu změny

`Change points`jsou trvalé změny v průběhu distribuce hodnot datového proudu událostí, jako jsou například změny úrovně a trendy. Tyto trvalé změny jsou poslední mnohem delší `spikes` než a mohly označovat závažné události. `Change points`nejsou obvykle viditelné pro holé oči, ale lze je zjistit ve vašich datech pomocí přístupů, jako je například v následující metodě.  Následující obrázek je příkladem detekce bodu změny:

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>Vytvoření metody DetectChangepoint ()

Do metody přidejte následující volání `DetectChangepoint()`metody jako další řádek kódu `Main()` v metodě:

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

`DetectChangepoint()` Metoda provádí následující úlohy:

* Navlakuje model.
* Detekuje body změn na základě historických dat o prodeji.
* Zobrazí výsledky.

Vytvořte metodu hned `Main()` za metodou pomocí následujícího kódu: `DetectChangepoint()`

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) se používá ke školení modelu pro detekci bodu změny. Přidejte ho do `DetectChangepoint()` metody s následujícím kódem:

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

Jak jste předtím pracovali, přizpůsobte `productSales` jim data přidáním následujícího jako další řádek kódu `DetectChangePoint()` v metodě:

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

Použijte metodu pro `Training` transformaci dat přidáním následujícího kódu do `DetectChangePoint()`: `Transform()`

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

Jak jste předtím pracovali, převeďte `transformedData` na silně typované `IEnumerable` `CreateEnumerable()`pro snazší zobrazení pomocí metody s následujícím kódem:

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

Vytvořte záhlaví zobrazení s následujícím kódem jako další řádek v `DetectChangePoint()` metodě:

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

Ve výsledcích detekce bodů změny se zobrazí následující informace:

* `Alert`Označuje upozornění na změnu bodu pro daný datový bod.
* `Score``ProductSales` je hodnota pro daný datový bod v datové sadě.
* `P-Value`"P" představuje pravděpodobnost. To označuje, jak pravděpodobná je tento datový bod anomálií. 
* `Martingale value`slouží k identifikaci způsobu, jakým je "divné" a datovým bodem "na základě sekvence hodnot P.  

Iterujte pomocí `predictions` `IEnumerable` a zobrazte výsledky s následujícím kódem:

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>Výsledky detekce bodu změny

Výsledky by měly vypadat podobně jako následující. Během zpracování se zobrazí zprávy. Můžou se zobrazovat upozornění nebo zpracovávat zprávy. Tyto výsledky byly z důvodu srozumitelnosti odebrány z následujících výsledků.

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

Blahopřejeme! Teď jste úspěšně vytvořili modely strojového učení pro zjišťování špiček a anomálií bodů změn v prodejních datech.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Načtení dat
> * Vyškolit model pro detekci anomálií špičky
> * Zjištění anomálií špičky pomocí trained model
> * Výuka modelu pro detekci anomálií bodů změn
> * Detekovat anomálie bodů změny v proškolených režimech

## <a name="next-steps"></a>Další postup

Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku detekce anomálií spotřeby energie.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-Samples – úložiště GitHub](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
