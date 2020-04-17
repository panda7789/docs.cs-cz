---
title: 'Kurz: Předpověď půjčovny kol poptávka - časové řady'
description: Tento kurz ukazuje, jak předpovědět poptávku po půjčovně kol pomocí jednorozměrné analýzy časových řad a ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: bceb32f4ea22ade6d3b49b3a99d7ec48a7ba168d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607399"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Kurz: Prognóza poptávky po půjčovně kol s analýzou časových řad a ML.NET

Zjistěte, jak předpovídat poptávku po půjčovně kol pomocí analýzy jednorozměrné časové řady na datech uložených v databázi serveru SQL Server s ML.NET.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Pochopení problému
> * Načtení dat z databáze
> * Vytvoření modelu prognózy
> * Vyhodnotit model prognózy
> * Uložení modelu prognózy
> * Použití modelu prognózy

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".

## <a name="time-series-forecasting-sample-overview"></a>Přehled ukázkových prognóz časových řad

Tato ukázka je **aplikace konzoly C# .NET Core,** která předpovídá poptávku po zapůjčení jízdních kol pomocí algoritmu analýzy jednorozměrné časové řady známého jako Analýza jednoho spektra. Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) na GitHubu.

## <a name="understand-the-problem"></a>Pochopení problému

Pro efektivní provoz hraje řízení zásob klíčovou roli. Mít příliš mnoho výrobku na skladě znamená neprodané výrobky sedí na regálech nevytváří žádné příjmy. Mít příliš málo produktů vede ke ztrátě prodeje a zákazníkům nakupujícím od konkurentů. Proto je neustálou otázkou, jaké je optimální množství zásob, které mají být po ruce? Analýza časových řad pomáhá poskytnout odpověď na tyto otázky tím, že se podíváte na historická data, identifikujete vzory a pomocí těchto informací předpovídáte hodnoty někdy v budoucnu.

Technika pro analýzu dat použitých v tomto kurzu je jednorozměrné analýzy časových řad. Analýza jednorozměrných časových řad se podívá na jedno číselné pozorování v určitém časovém období v určitých intervalech, jako je měsíční prodej.

Algoritmus použitý v tomto kurzu je [single spectrum analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA funguje tak, že rozkládá časové řady do sady hlavních součástí. Tyto komponenty lze interpretovat jako části signálu, které odpovídají trendům, šumu, sezónnosti a mnoha dalším faktorům. Potom tyto součásti jsou rekonstruovány a slouží k prognóze hodnoty nějaký čas v budoucnu.

## <a name="create-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte novou **aplikaci konzoly C# .NET Core** s názvem "BikeDemandForecasting".
1. Instalace **Microsoft.ML** verze **1.4.0** NuGet balíček
    1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.
    1. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** a vyhledejte **Microsoft.ML**.
    1. Zaškrtněte políčko **Zahrnout předběžnou verzi.**
    1. Vyberte tlačítko **Instalovat.**
    1. V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně Přijetí licence vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.
    1. Opakujte tyto kroky pro **System.Data.SqlClient** verze **4.7.0** a **Microsoft.ML.TimeSeries** verze **1.4.0**.

### <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Vytvořte adresář s názvem *Data*.
1. Stáhněte [databázový soubor *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) a uložte jej do *datového* adresáře.

> [!NOTE]
> Data použitá v tomto kurzu pochází z [datové sady Sdílení kol UCI](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, Hadi a Gama, Joao, "Event labeling kombinující detektory souborů a znalosti pozadí", Pokrok v umělé inteligenci (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Původní datová sada obsahuje několik sloupců odpovídajících sezónnosti a počasí. Pro stručnost a protože algoritmus použitý v tomto kurzu vyžaduje pouze hodnoty z jednoho číselného sloupce, původní datová sada byla zhuštěna tak, aby zahrnovala pouze následující sloupce:

- **dteday**: Datum pozorování.
- **rok**: Zakódovaný rok pozorování (0=2011, 1=2012).
- **cnt**: Celkový počet půjčoven kol pro tento den.

Původní datová sada je mapována na databázovou tabulku s následujícím schématem v databázi serveru SQL Server.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Následuje ukázka dat:

| Datum pronájmu | Year | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Vytvoření vstupních a výstupních tříd

1. Otevřete *Program.cs* soubor `using` a nahraďte existující příkazy následujícími příkazy:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Vytvořte třídu `ModelInput`. Pod `Program` třídu přidejte následující kód.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    Třída `ModelInput` obsahuje následující sloupce:

    - **RentalDate**: Datum pozorování.
    - **Rok**: Zakódovaný rok pozorování (0=2011, 1=2012).
    - **TotalRentals**: Celkový počet půjčoven kol pro tento den.

1. Vytvořte `ModelOutput` třídu `ModelInput` pod nově vytvořenou třídou.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    Třída `ModelOutput` obsahuje následující sloupce:

    - **ForecastedRentals**: Předpokládané hodnoty pro předpokládané období.
    - **LowerBoundRentals**: Předpokládané minimální hodnoty pro předpokládané období.
    - **UpperBoundRentals**: Předpokládané maximální hodnoty pro předpokládané období.

### <a name="define-paths-and-initialize-variables"></a>Definování cest a inicializaci proměnných

1. Uvnitř `Main` metody definujte proměnné pro uložení umístění dat, připojovacířetězec a kde uložit trénovaný model.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Inicializovat `mlContext` proměnnou s [`MLContext`](xref:Microsoft.ML.MLContext) novou instanci přidáním následující řádek k metodě. `Main`

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    Třída [`MLContext`](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET a inicializace mlContext vytvoří nové ML.NET prostředí, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

## <a name="load-the-data"></a>Načtení dat

1. Vytvořte, `DatabaseLoader` že `ModelInput`načte záznamy typu .

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Definujte dotaz pro načtení dat z databáze.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algoritmy očekávají, že [`Single`](xref:System.Single)data budou typu . Proto číselné hodnoty pocházející z databáze, [`Real`](xref:System.Data.SqlDbType)které nejsou typu , s jednou přesností s [`Real`](xref:System.Data.SqlDbType)plovoucí desetinnou hodnotou, musí být převedeny na .

    Sloupce `Year` `TotalRental` a jsou oba celé typy v databázi. Pomocí `CAST` vestavěné funkce jsou oba `Real`přetypovány do .

1. Vytvořte `DatabaseSource` a pro připojení k databázi a spusťte dotaz.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Načtěte data `IDataView`do .

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Datová sada obsahuje data za dva roky. Pro školení se používají pouze údaje z prvního roku, druhý rok se koná pro porovnání skutečných hodnot s prognózou vytvořenou modelem. Filtrujte data [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) pomocí transformace.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    Pro první rok jsou pouze `Year` hodnoty ve sloupci menší `upperBound` než 1 vybrány nastavením parametru na 1. Naopak pro druhý rok jsou hodnoty větší než nebo rovny `lowerBound` 1 vybrány nastavením parametru na 1.

## <a name="define-time-series-analysis-pipeline"></a>Definování kanálu analýzy časových řad

1. Definujte kanál, který používá [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) k prognóze hodnot v datové sadě časových řad.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    Trvá `forecastingPipeline` 365 datových bodů za první rok a vzorkuje nebo rozdělí datovou sadu časových řad na `seriesLength` 30denní (měsíční) intervaly určené parametrem. Každý z těchto vzorků je analyzován prostřednictvím týdenního nebo 7denního okna. Při určování, co je prognózovaná hodnota pro další období, hodnoty z předchozích sedmi dnů se používají k předpovědi. Model je nastaven tak, aby předpovídal sedm období `horizon` do budoucnosti, jak je definováno parametrem. Vzhledem k tomu, že prognóza je informovaný odhad, není vždy 100% přesná. Proto je vhodné znát rozsah hodnot v nejlepších a nejhorších scénářích, jak je definováno horní a dolní hranice. V tomto případě je úroveň spolehlivosti dolní a horní hranice nastavena na 95%. Úroveň spolehlivosti může být odpovídajícím způsobem zvýšena nebo snížena. Čím vyšší je hodnota, tím širší je rozsah mezi horním a dolním mezí, aby bylo dosaženo požadované úrovně spolehlivosti.

1. Pomocí [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metody můžete model trénovat a `forecastingPipeline`přizpůsobit data dříve definovanému .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Vyhodnoťte, jak si model vede, a to prognózou dat příštího roku a porovnáním se skutečnými hodnotami.

1. Pod `Main` metodou vytvořte novou metodu nástroje nazvanou `Evaluate`.

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. Uvnitř `Evaluate` metody prognóza data druhého roku pomocí [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody s trénovaným modelem.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Získejte skutečné hodnoty z dat [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pomocí metody.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Získejte hodnoty prognózy [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pomocí metody.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Vypočítejte rozdíl mezi skutečnou hodnotou a hodnotou prognózy, běžně označovanou jako chyba.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Změřte výkon výpočtem hodnot Střední absolutní chyba a Střední kvadratická chyba kořenového adresáře.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    K vyhodnocení výkonu se používají následující metriky:

    - **Střední absolutní chyba**: Měří, jak blízko předpovědi jsou na skutečnou hodnotu. Tato hodnota se pohybuje mezi 0 a nekonečno. Čím blíže k 0, tím lepší je kvalita modelu.
    - **Kořenová střední kvadratmárská chyba**: Shrnuje chybu v modelu. Tato hodnota se pohybuje mezi 0 a nekonečno. Čím blíže k 0, tím lepší je kvalita modelu.

1. Výstup metriky do konzoly.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Použijte `Evaluate` metodu `Main` uvnitř metody.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Uložení modelu

Pokud jste s modelem spokojeni, uložte jej pro pozdější použití v jiných aplikacích.

1. V `Main` metodě vytvořte [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602). [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)je komfortní metoda, aby se jednotlivé předpovědi.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Uložte model do `MLModel.zip` souboru volaném `modelPath` dříve definovanou proměnnou. Pomocí [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) metody uložte model.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Použití modelu k prognóze poptávky

1. Pod `Evaluate` metodou vytvořte novou metodu nástroje nazvanou `Forecast`.

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. Uvnitř `Forecast` metody použijte [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metodu k prognóze pronájmů pro příštích sedm dní.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Zarovnejte skutečné hodnoty a hodnoty prognózy pro sedm období.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Iterate prostřednictvím výstupu prognózy a zobrazí jej na konzoli.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Spuštění aplikace

1. Uvnitř `Main` metody volejte `Forecast` metodu.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Spusťte aplikaci. Výstup podobný tomu níže by se měl objevit na konzoli. Pro stručnost byl výstup zhuštěn.

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

Kontrola skutečných a předpokládaných hodnot ukazuje následující vztahy:

![Skutečné vs porovnání prognóz](./media/time-series-demand-forecasting/forecast.png)

Zatímco předpokládané hodnoty nepředpovídají přesný počet pronájmů, poskytují užší rozsah hodnot, který umožňuje operaci optimalizovat jejich využití prostředků.

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení řady časových řad, abyste předpovídali poptávku po pronájmu jízdních kol.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)

## <a name="next-steps"></a>Další kroky

- [Úlohy strojového učení v ML.NET](../resources/tasks.md)
- [Vylepšení přesnosti modelu](../resources/improve-machine-learning-model-ml-net.md)
