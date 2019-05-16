---
title: Použijte v případě detekce anomálií prodejní ML.NET
description: Zjistěte, jak pochopit, jak analyzovat data špiček anomálií a body přijmout vhodná opatření změny pomocí ML.NET v případě detekce anomálií prodejní produktu.
ms.date: 05/06/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 39e812facccfa75d1643704f8960a387a70c94bc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641154"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a>Kurz: Použití ML.NET pro detekci anomálií prodejní produktu 

Tento ukázkový kurz ukazuje použití ML.NET zjišťovat anomálie v produktu daty z prodeje přijmout vhodná opatření prostřednictvím aplikace konzoly .NET Core using C# v aplikaci Visual Studio 2019. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Načtení dat
> * Trénování modelu pro detekci anomálií ve špičce
> * Detekovat anomálie ve špičce pomocí trénovaného modelu
> * Trénování modelu pro změnu bodu pro detekci anomálií
> * Detekovat anomálie bodu změnu s trénovaného modelu

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) úložiště.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

* [Datová sada sales.csv produktu](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Formátování dat v `product-sales.csv` je založena na této datové sadě "Šampón prodej přes tří let" původně zdrojem je DataMarket a k dispozici podle času řady dat knihovny (TSDL), Autor Rob Hyndman. Datová sada "Šampón prodeje za období tří let" licencovaného v rámci programu Open License DataMarket výchozí.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvoření **konzolovou aplikaci .NET Core** nazývá "ProductSalesAnomalyDetection".

2. Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady.

3. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte **v1.0.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené. Opakujte tyto kroky pro **Microsoft.ML.TimeSeries v0.12.0**.

4. Přidejte následující `using` příkazů v horní části vašeho *Program.cs* souboru:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Stáhněte si vaše data

1. Stáhnout datovou sadu a uložit ho. tím *Data* dříve vytvořená složka:

   * Klikněte pravým tlačítkem na [ *produktu sales.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) a vyberte možnost "Uložit jako odkaz (neboli na cílový)..."

     Ujistěte se, že buď uložit \*soubor .csv *Data* složky, nebo poté, co jste jej uložili jinde, přesunout \*soubor .csv *Data* složky.

2. V Průzkumníku řešení klikněte pravým tlačítkem myši \*soubor .csv a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

V následující tabulce je náhled dat z vašich \*souboru CSV:

|Měsíc  |ProductSales |
|-------|-------------|
|1. leden  |    271      |
|2 – leden  |    150.9    |
|.....  |    .....    |
|1 – únor  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Dále definujte vstupní třídy datovou strukturu.

Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **Přidat > Nová položka**.

2. V **dialogové okno Přidat novou položku**vyberte **třídy** a změnit **název** pole *ProductSalesData.cs*. Vyberte **přidat** tlačítko.

*ProductSalesData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *ProductSalesData.cs*:

```csharp
using Microsoft.ML.Data;
```

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `ProductSalesData` a `ProductSalesPrediction`, možnosti *ProductSalesData.cs* souboru:

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData` Určuje třídu vstupní data. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atribut určuje, jaké sloupce (podle index sloupce) v datové sadě se mají načíst. 

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

Je potřeba vytvořit dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:

* `_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.
* `_docsize` soubor datové sady obsahuje několik záznamů. Budete využit k výpočtu `pvalueHistoryLength`.

Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Nahradit `Console.WriteLine("Hello World!")` řádku v `Main` metoda následujícím kódem, jak deklarovat a inicializovat `mlContext` proměnné:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>Načtení dat

Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView). `IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové). Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu. Přidejte následující kód jako další řádek `Main()` metody:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru. Přijímá proměnné cesty dat a vrátí `IDataView`.

## <a name="ml-task---time-series-anomaly-detection"></a>Úloha ML – čas detekce anomálií řady 

Detekce anomálií příznaky neočekávaná nebo neobvyklá událostí nebo chování. Poskytuje možné místo pro vyhledání problémů a pomáhá odpovědět na otázku "Je tato divně?".

![Je to divné](./media/sales-anomaly-detection/anomalydetection.png)

Detekce anomálií je proces zjišťování dat časových řad odlehlé hodnoty; odkazuje na daný vstupní časovou řadu, kde chování není očekávaným, nebo "divné".

To může být užitečné v mnoha způsoby. Příklad:

Pokud máte automobilu, můžete chtít vědět: Je tento olej měřidla čtení normální nebo mít nevracení?
Pokud monitorujete spotřebu energie, byste měli vědět: Je k dispozici kvůli výpadku?

Existují dva typy anomálií řady čas, které lze zjistit: 

* **Špičky** označují dočasné nárůstům neobvyklé chování v systému. 

* **Body změny** označuje začátek trvalé změny časem v systému. 

V ML.NET, identifikátor IID zásobníku zjišťování nebo detekce změn bodu IID algoritmy jsou vhodné pro [nezávislé a stejně jako distribuovaných datových sad](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables). 

Budete analyzuje stejný produkt prodejní data, zjistit provozní špičky a změnit body. Model procesu sestavovat a vzdělávání je stejný pro zjišťování zásobníku a detekce změn bod; Hlavní rozdíl je použitý algoritmus konkrétní zjišťování.

## <a name="spike-detection"></a>Detekce zásobníku 

Cílem zásobníku detekce je k identifikaci i s náhlými ještě dočasné nárůsty zatížení, které výrazně se liší od většinou časových řad dat hodnoty. Je důležité pro detekci těchto výjimečných podezřelé položky, události nebo pozorování minimalizaci včas. Následující postup slouží ke zjištění různých anomálie, jako: výpadky, kybernetických útoků nebo virální webového obsahu. Na následujícím obrázku je příklad špičky v datové sadě řady čas:

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>Vytvoření DetectSpike() – metoda

Přidejte následující volání `DetectSpike()`metody jako další řádek kódu v `Main()` metody:

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

`DetectSpike()` Metoda spustí následující úlohy:

* Trénovat modelu.
* Detekuje na základě na historická data o prodeji provozní špičky.
* Zobrazí výsledky.

Vytvořte `DetectSpike()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Použití [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) pro trénování modelu pro zjišťování (špičky). Přidejte ji tak `DetectChangepoint()` metodu s následujícím kódem:

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

Přizpůsobit modelu, který má `productSales` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `DetectSpike()` metody:

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) metoda trénovat modelu transformace datové sady a aplikováním školení.

Přidejte následující řádek kódu, který umožňuje transformovat `productSales` data jako další řádek v `DetectSpike()` metody:

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda k následné predikci pro více poskytuje vstupní řádky z datové sady testů.

Převést vaše `transformedData` do silného typu `IEnumerable` pro snadnější zobrazení pomocí [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metodu s následujícím kódem:

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

Vytvořit řádek záhlaví zobrazení pomocí následující <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

Ve výsledcích zjišťování zásobníku budete zobrazovat následující informace:

* `Alert` označuje zásobníku upozornění pro daný datový bod.

* `Score` je `ProductSales` hodnotu pro daný datový bod v datové sadě.

* `P-Value` "P" jsou zahrnovaného pravděpodobnosti. To znamená, jaká je pravděpodobnost tento datový bod je anomálie. 

Použijte následující kód k iteraci v rámci `predictions` `IEnumerable` a zobrazit výsledky:

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>Výsledky vyhledávání (špičky)

Výsledky by měl vypadat přibližně takto. Během zpracování zprávy se zobrazují. Může se zobrazit upozornění nebo zpracování zpráv. Ty se odebraly z následujících výsledků pro přehlednost.

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

## <a name="change-point-detection"></a>Změna bodu zjišťování

`Change points` jsou trvalé změny v řady čas události datového proudu distribuci hodnot, jako jsou změny na úrovni a trendy. Trvalé změny naposledy mnohem delší než `spikes` a může znamenat katastrofické události. `Change points` se obvykle nezobrazí pouhým okem, ale můžete zjistit ve vašich datech pomocí přístupů například následující metodu.  Na následujícím obrázku je příklad bodu detekce změn:

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>Vytvoření DetectChangepoint() – metoda

Přidejte následující volání `DetectChangepoint()`metody jako další řádek kódu v `Main()` metody:

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

`DetectChangepoint()` Metoda spustí následující úlohy:

* Trénovat modelu.
* Zjistí změnu body na základě historických dat prodeje.
* Zobrazí výsledky.

Vytvořte `DetectChangepoint()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) se používá pro trénování modelu pro změnu bodu zjišťování. Přidejte ji tak `DetectChangepoint()` metodu s následujícím kódem:

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

Stejně jako dříve, podle modelu, který má `productSales` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `DetectChangePoint()` metody:

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

Použití `Transform()` metody k transformaci `Training` data přidáním následujícího kódu do `DetectChangePoint()`:

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

Stejně jako dříve, převést vaše `transformedData` do silného typu `IEnumerable` pro snadnější zobrazení pomocí `CreateEnumerable()`metodu s následujícím kódem:

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

Vytvořit záhlaví zobrazení jako na další řádek v následujícím kódem `DetectChangePoint()` metody:

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

Ve výsledcích zjišťování změn bodu budete zobrazovat následující informace:

* `Alert` označuje změnit bod oznámení pro daný datový bod.
* `Score` je `ProductSales` hodnotu pro daný datový bod v datové sadě.
* `P-Value` "P" jsou zahrnovaného pravděpodobnosti. To znamená, jaká je pravděpodobnost tento datový bod je anomálie. 
* `Martingale value` se používá k identifikaci, jak je "divně" datový bod, v závislosti na sekvenci hodnot P.  

Iterovat přes `predictions` `IEnumerable` a zobrazit výsledky s následujícím kódem:

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>Změna bodu zjišťování výsledky

Výsledky by měl vypadat přibližně takto. Během zpracování zprávy se zobrazují. Může se zobrazit upozornění nebo zpracování zpráv. Ty se odebraly z následujících výsledků pro přehlednost.

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

Blahopřejeme! Jste teď úspěšně sestaven modelů strojového učení pro zjišťování provozní špičky a změnit bod anomálie v prodejní data.

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) úložiště.

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Načtení dat
> * Trénování modelu pro detekci anomálií ve špičce
> * Detekovat anomálie ve špičce pomocí trénovaného modelu
> * Trénování modelu pro změnu bodu pro detekci anomálií
> * Detekovat anomálie bodu změnu s režimem trénovaného

## <a name="next-steps"></a>Další kroky

Projděte si úložišti GitHub s ukázkami Machine Learning a prozkoumejte ukázkový spotřebu energie pro detekci anomálií.
> [!div class="nextstepaction"]
> [úložiště GitHub DotNet/machinelearning – ukázky](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/TimeSeries_PowerAnomalyDetection)
