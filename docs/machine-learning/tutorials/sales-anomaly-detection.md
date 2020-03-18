---
title: 'Kurz: Detekce anomálií v prodeji produktů'
description: Zjistěte, jak vytvořit aplikaci pro detekci anomálií pro data o prodeji produktů. Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí jazyka C# v sadě Visual Studio 2019.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: c3fd4aa715a64a20f1eff9b789f6a87eaa749163
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239986"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Kurz: Detekce anomálií v prodeji produktů s ML.NET

Zjistěte, jak vytvořit aplikaci pro detekci anomálií pro data o prodeji produktů. Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí jazyka C# v sadě Visual Studio.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Načtení dat
> * Vytvoření transformace pro detekci anomálií špičky
> * Detekce spikač anomálie s transformací
> * Vytvoření transformace pro detekci anomálií bodů změny
> * Detekce anomálií bodů změny pomocí transformace

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".

* [Datová sada product-sales.csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Formát dat `product-sales.csv` v je založen na datové sadě "Shampoo Sales Over a Three Year Period" původně pořízené z DataMarketu a poskytované Datovou knihovnou Time Series (TSDL), kterou vytvořil Rob Hyndman.
> Dataset "Shampoo Sales Over a Three Year Period" s licencí pod výchozí otevřenou licencí DataMarket.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **aplikaci .NET Core Console** s názvem ProductSalesAnomalyDetection.

2. Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.

3. Nainstalujte **balíček nuget Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML** a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky. Opakujte tento postup pro **Microsoft.ML.TimeSeries**.

4. V horní `using` části *Program.cs* souboru přidejte následující příkazy:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Stažení dat

1. Stáhněte si datovou sadu a uložte ji do dříve vytvořené *datové* složky:

   * Klikněte pravým tlačítkem myši na [*produkt-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) a vyberte "Uložit odkaz (nebo cíl) Jako ..."

     Ujistěte se, \*že soubor .csv uložíte do složky *Data,* nebo jej po uložení jinde přesuňte \*do složky *Data.*

2. V Průzkumníku řešení klepněte pravým tlačítkem \*myši na soubor .csv a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

Následující tabulka obsahuje náhled dat \*ze souboru .csv:

|Month  |Prodej produktů |
|-------|-------------|
|1-Jan  |    271      |
|2-Jan  |    150.9    |
|.....  |    .....    |
|1-Únor  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

Dále definujte struktury dat vstupní a předpověď třídy.

Přidání nové třídy do projektu:

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a potom vyberte **přidat > novou položku**.

2. V **dialogovém okně Přidat novou položku**vyberte **Třídu** a změňte pole **Název** na *ProductSalesData.cs*. Potom vyberte tlačítko **Přidat.**

   V editoru kódu se otevře *soubor ProductSalesData.cs.*

3. Na začátek `using` *ProductSalesData.cs*přidejte následující příkaz :

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `ProductSalesData` a `ProductSalesPrediction`, do souboru *ProductSalesData.cs:*

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    `ProductSalesData`určuje třídu vstupních dat. Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny.

    `ProductSalesPrediction`určuje třídu dat předpověď. Pro detekci anomálií předpověď se skládá z výstrahy k označení, zda je anomálie, nezpracované skóre a p-hodnota. Čím blíže je hodnota p 0, tím je pravděpodobnější, že došlo k anomálii.

5. Vytvořte dvě globální pole pro uložení cesty k nedávno stažené datové sadě a cesty k uloženému souboru modelu:

    * `_dataPath`má cestu k datové sadě použité k trénování modelu.
    * `_docsize`má počet záznamů v souboru datové sady. Budete používat `_docSize` k `pvalueHistoryLength`výpočtu .

6. Přidejte následující kód na řádek `Main` přímo nad metodou a určete tyto cesty:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v hlavní

1. Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro `mlContext` deklarování a inicializaci proměnné:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

### <a name="load-the-data"></a>Načtení dat

Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových). Data lze načíst z textového souboru nebo z jiných zdrojů (například databáze SQL nebo souborů protokolu) do objektu. `IDataView`

1. Jako další řádek `Main()` metody přidejte následující kód:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru. Přebírá proměnné cesty dat a vrátí `IDataView`.

## <a name="time-series-anomaly-detection"></a>Detekce anomálií časových řad

Detekce anomálií příznaky neočekávané nebo neobvyklé události nebo chování. To dává vodítka, kde hledat problémy a pomůže vám odpovědět na otázku "Je to divné?".

![Příklad detekce anomálií "Je to divné".](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

Detekce anomálií je proces detekce odlehlých časových řad; body na dané vstupní časové řady, kde chování není to, co bylo očekáváno, nebo "divný".

Detekce anomálií může být užitečná mnoha způsoby. Například:

Pokud máte auto, možná budete chtít vědět: Je to olejoměr čtení normální, nebo mám únik?
Pokud sledujete spotřebu energie, chtěli byste vědět: Existuje výpadek?

Existují dva typy anomálií časových řad, které lze zjistit:

* **Hroty** označují dočasné výbuchy anomálníchování v systému.

* **Body změny** označují začátek trvalých změn v průběhu času v systému.

V ML.NET jsou algoritmy detekce špičky IID nebo iid change point vhodné pro [nezávislé a identicky distribuované datové sady](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).

Na rozdíl od modelů v jiných kurzech transformace detektoru anomálií časové řady pracují přímo na vstupních datech. Metoda `IEstimator.Fit()` nepotřebuje trénovací data k vytvoření transformace. Je třeba schéma dat i když, který je poskytován zobrazení dat generované z `ProductSalesData`prázdného seznamu .

Budete analyzovat stejná data o prodeji produktů, abyste zjistili špičky a body změny. Proces modelu budovy a školení je stejný pro detekci špičky a detekci bodů změny; hlavním rozdílem je specifický detekční algoritmus.

## <a name="spike-detection"></a>Detekce špičky

Cílem detekce špičky je identifikovat náhlé, ale dočasné shluky, které se výrazně liší od většiny hodnot dat časových řad. Je důležité zjistit tyto podezřelé vzácné položky, události nebo pozorování včas minimalizovat. Následující přístup lze použít k detekci různých anomálií, jako jsou: výpadky, kybernetické útoky nebo virální webový obsah. Následující obrázek je příkladem špičky v datové sadě časové řady:

![Snímek obrazovky, který zobrazuje dvě detekce špičky.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a>Přidejte metodu CreateEmptyDataView().

Do této metody `Program.cs`přidejte následující metodu :

[!code-csharp[CreateEmptyDataView](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEmptyDataView)]

Vytvoří `CreateEmptyDataView()` prázdný objekt zobrazení dat se správným schématem, které má `IEstimator.Fit()` být použito jako vstup do metody.

### <a name="create-the-detectspike-method"></a>Vytvořit metodu DetectSpike()

Metoda: `DetectSpike()`

* Vytvoří transformaci z odhadu.
* Detekuje špičky na základě historických dat prodeje.
* Zobrazí výsledky.

1. Vytvořte `DetectSpike()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Použijte [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) trénovat model pro detekci špičky. Přidejte ji `DetectSpike()` do metody s následujícím kódem:

    [!code-csharp[AddSpikeTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddSpikeTrainer)]

1. Vytvořte transformaci detekce špičky přidáním následujícího `DetectSpike()` jako následující řádek kódu v metodě:

    [!code-csharp[TrainModel1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel1)]

1. Přidejte následující řádek kódu `productSales` pro transformaci dat jako `DetectSpike()` další řádek v metodě:

    [!code-csharp[TransformData1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData1)]

    Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda, aby předpovědi pro více vstupních řádků datové sady.

1. Převeďte svůj `transformedData` na silně `IEnumerable` zadaný pro snadnější zobrazení pomocí [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metoda s následujícím kódem:

    [!code-csharp[CreateEnumerable1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable1)]

1. Vytvořte řádek záhlaví zobrazení <xref:System.Console.WriteLine?displayProperty=nameWithType> pomocí následujícího kódu:

    [!code-csharp[DisplayHeader1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader1)]

    Ve výsledcích detekce špičky se zobrazí následující informace:

    * `Alert`označuje upozornění na špičku pro daný datový bod.
    * `Score`je `ProductSales` hodnota pro daný datový bod v datové sadě.
    * `P-Value`"P" znamená pravděpodobnost. Čím blíže je hodnota p na hodnotu 0, tím je pravděpodobnější, že datový bod je anomálie.

1. Použijte následující kód k iterátu `predictions` `IEnumerable` prostřednictvím a zobrazit výsledky:

    [!code-csharp[DisplayResults1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults1)]

1. Přidejte volání `DetectSpike()`metody v `Main()` metodě:

    [!code-csharp[CallDetectSpike](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a>Výsledky detekce špičky

Vaše výsledky by měly být podobné následujícímu. Během zpracování se zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Některé zprávy byly odebrány z následujících výsledků pro přehlednost.

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

`Change points`jsou trvalé změny v rozdělení datových proudů událostí časové řady hodnot, jako jsou změny úrovně a trendy. Tyto trvalé změny trvají `spikes` mnohem déle než katastrofické události. `Change points`nejsou obvykle viditelné pouhým okem, ale mohou být detekovány ve vašich datech pomocí přístupů, například v následující metodě.  Následující obrázek je příkladem detekce bodu změny:

![Snímek obrazovky, který zobrazuje detekci bodu změny.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a>Vytvoření metody DetectChangepoint()

Metoda `DetectChangepoint()` provádí následující úkoly:

* Vytvoří transformaci z odhadu.
* Detekuje body změn na základě historických dat o prodeji.
* Zobrazí výsledky.

1. Vytvořte `DetectChangepoint()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Vytvořte [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) `DetectChangepoint()` v metodě s následujícím kódem:

    [!code-csharp[AddChangepointTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddChangepointTrainer)]

1. Stejně jako dříve vytvořte transformaci z odhadu přidáním následujícího řádku kódu do `DetectChangePoint()` metody:

    [!code-csharp[TrainModel2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel2)]

1. Pomocí `Transform()` metody transformujte data přidáním následujícího kódu do `DetectChangePoint()`aplikace :

    [!code-csharp[TransformData2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData2)]

1. Stejně jako dříve `transformedData` převeďte svůj na `IEnumerable` silně zadaný `CreateEnumerable()`pro snadnější zobrazení pomocí metody s následujícím kódem:

    [!code-csharp[CreateEnumerable2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable2)]

1. Vytvořte záhlaví zobrazení s následujícím kódem `DetectChangePoint()` jako další řádek v metodě:

    [!code-csharp[DisplayHeader2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader2)]

    Ve výsledcích zjišťování bodů změny se zobrazí následující informace:

    * `Alert`označuje výstrahu bodu změny pro daný datový bod.
    * `Score`je `ProductSales` hodnota pro daný datový bod v datové sadě.
    * `P-Value`"P" znamená pravděpodobnost. Čím blíže je hodnota P na hodnotu 0, tím je pravděpodobnější, že datový bod je anomálie.
    * `Martingale value`se používá k identifikaci, jak "divný" datový bod je, na základě sekvence P-hodnoty.

1. Iterate prostřednictvím `predictions` `IEnumerable` a zobrazit výsledky s následujícím kódem:

    [!code-csharp[DisplayResults2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults2)]

1. Přidejte do `DetectChangepoint()`metody v `Main()` metodě následující volání:

    [!code-csharp[CallDetectChangepoint](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a>Výsledky zjišťování bodu změny

Vaše výsledky by měly být podobné následujícímu. Během zpracování se zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Některé zprávy byly odebrány z následujících výsledků pro přehlednost.

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

Blahopřejeme! Nyní jste úspěšně vytvořili modely strojového učení pro detekci špiček a anomálií bodů změny v prodejních datech.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Načtení dat
> * Trénování modelu pro detekci anomálií špičky
> * Detekce spikač anomálie s trénovaný model
> * Trénování modelu pro detekci anomálií bodu změny
> * Detekce anomálií bodů změny pomocí trénovaného režimu

## <a name="next-steps"></a>Další kroky

Podívejte se na ukázky machine learningu úložiště GitHub a prozkoumejte ukázku detekce anomálií spotřeby spotřeby.
> [!div class="nextstepaction"]
> [úložiště GitHub u dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
