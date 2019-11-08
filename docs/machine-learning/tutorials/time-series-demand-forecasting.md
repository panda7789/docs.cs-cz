---
title: 'Kurz: odhad poptávky po absolvování kol – časové řady'
description: V tomto kurzu se dozvíte, jak předpovědět poptávku za službu pronájmu kol pomocí analýzy univariate časových řad a ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: e913c27c3501c4c553d7d62f948de31abb3d6f49
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740535"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Kurz: odhadování poptávky po nájemce kol s využitím analýzy časových řad a ML.NET

Naučte se, jak odhadnout poptávku za službu pronájmu kol pomocí analýzy univariate časových řad s daty uloženými v databázi SQL Server s ML.NET.

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

- [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

## <a name="time-series-forecasting-sample-overview"></a>Ukázka prognózy časových řad – přehled

Tato ukázka je  **C# Konzolová aplikace .NET Core** , která vypovídá poptávku za nájemné za kolo pomocí algoritmu analýzy univariate Time Series, který se označuje jako analýza s jedním spektrem. Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) na GitHubu.

## <a name="understand-the-problem"></a>Pochopení problému

Aby bylo možné spustit efektivní operaci, Správa inventáře hraje klíčovou roli. Pokud máte příliš mnoho produktů na skladě, znamená to, že neprodávané produkty jsou v police negenerují žádné výnosy. S příliš malým množstvím produktů vede ke ztrátě prodeje a zákazníkům, kteří si kupují z konkurence. Proto se jedná o konstantní otázku, co je optimální množství inventáře, abyste mohli zůstat na ruce? Analýza časových řad pomáhá poskytnout odpověď na tyto otázky zobrazením historických dat, identifikace vzorů a využitím těchto informací k předpovědi hodnot v budoucnu. 

Technika analýzy dat používaných v tomto kurzu je univariate analýza časových řad. Analýza Univariate Time-Series se při určitých intervalech, jako je měsíční prodej, podívá na jedno číselné pozorování v určitém časovém intervalu. 

Algoritmus použitý v tomto kurzu je [Analýza s jedním spektrem (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA funguje tak, že rozdělí časovou řadu do sady základních komponent. Tyto komponenty lze interpretovat jako části signálu, který odpovídá trendům, hluku, sezónnost a mnoha dalším faktorům. Poté jsou tyto komponenty znovu sestaveny a použity k předpovědi hodnot v budoucnu.

## <a name="create-console-application"></a>Vytvořit konzolovou aplikaci

1. Vytvořte novou  **C# konzolovou aplikaci .NET Core** nazvanou "BikeDemandForecasting".
1. Balíček NuGet pro instalaci **Microsoft.ml** verze **1.4.0**
    1. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.
    1. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** a vyhledejte **Microsoft.ml**.
    1. Zaškrtněte políčko **zahrnout předběžné verze** .
    1. Vyberte tlačítko **instalovat** .
    1. Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .
    1. Opakujte tyto kroky pro **System. data. SqlClient** verze **4.7.0** a **Microsoft. ml. časové řady** verze **1.4.0**.

### <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Vytvořte adresář s názvem *data*.
1. Stáhněte [soubor databáze *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) a uložte ho do *datového* adresáře.

> [!NOTE]
> Data použitá v tomto kurzu pocházejí z [datové sady pro sdílení kol UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, hadi a gama, Joao, "označování událostí kombinující detektory kompletu a znalosti na pozadí", pokrok v umělých Intelligencech (2013): PP. 1-15, Springer Berlín Heidelberg, [webový odkaz](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Původní datová sada obsahuje několik sloupců, které odpovídají sezónnost a počasí. Pro zkrácení, protože algoritmus používaný v tomto kurzu vyžaduje jenom hodnoty z jednoho číselného sloupce, původní datová sada byla zúžená, aby zahrnovala jenom tyto sloupce:  

- **dteday**: datum pozorování.
- **year**: kódovaný rok sledování (0 = 2011, 1 = 2012).
- **CNT**: celkový počet pronajatých kol za tento den.

Původní datová sada je namapována na databázovou tabulku s následujícím schématem ve SQL Server databázi.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Následuje ukázka dat:

| RentalDate | Rok | TotalRentals |
| --- | --- | --- |
|1/1/2011|0,8|985|
|1/2/2011|0,8|801|
|1/3/2011|0,8|1349|

### <a name="create-input-and-output-classes"></a>Vytvoření vstupní a výstupní třídy

1. Otevřete soubor *program.cs* a nahraďte existující příkazy `using` následujícím způsobem:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Vytvořte třídu `ModelInput`. Pod `Program` třídy přidejte následující kód.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]    

    Třída `ModelInput` obsahuje následující sloupce:

    - **RentalDate**: datum pozorování.
    - **Year**: kódovaný rok sledování (0 = 2011, 1 = 2012).
    - **TotalRentals**: celkový počet pronajatých kol za tento den.

1. Vytvořte třídu `ModelOutput` pod nově vytvořenou `ModelInput` třídou.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    Třída `ModelOutput` obsahuje následující sloupce:

    - **ForecastedRentals**: předpokládané hodnoty pro období prognózy.
    - **LowerBoundRentals**: předpokládané minimální hodnoty pro období prognózy.
    - **UpperBoundRentals**: předpokládané maximální hodnoty pro období prognózy.

### <a name="define-paths-and-initialize-variables"></a>Definování cest a inicializovat proměnné

1. V rámci metody `Main` Definujte proměnné pro ukládání umístění vašich dat, připojovací řetězec a místo, kam se má vyškolený model Uložit.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Inicializujte `mlContext` proměnnou novou instancí [`MLContext`](xref:Microsoft.ML.MLContext) přidáním následujícího řádku do metody `Main`.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    Třída [`MLContext`](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace mlContext vytvoří nové prostředí ml.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů. Je podobné, koncepčně, `DBContext` v Entity Framework.

## <a name="load-the-data"></a>Načtení dat

1. Vytvoří `DatabaseLoader`, který načte záznamy typu `ModelInput`.

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Definujte dotaz pro načtení dat z databáze.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algoritmy očekávají, že data jsou typu [`Single`](xref:System.Single). Z toho vyplývá, že číselné hodnoty pocházející z databáze, které nejsou typu [`Real`](xref:System.Data.SqlDbType), mají hodnotu s plovoucí desetinnou čárkou s jednoduchou přesností, která musí být převedena na [`Real`](xref:System.Data.SqlDbType). 

    Sloupce `Year` a `TotalRental` jsou v databázi typu Integer. Pomocí `CAST` vestavěné funkce jsou obě přetypování do `Real`.

1. Vytvořte `DatabaseSource` pro připojení k databázi a spuštění dotazu.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Načtěte data do `IDataView`.

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Datová sada obsahuje dva roky s daty. Pro školení se použijí jenom data z prvního roku, druhý rok se porovná s porovnáním skutečných hodnot s prognózou vytvořenou modelem. Filtrujte data pomocí [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transformace. 

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    Pro první rok jsou vybrány pouze hodnoty ve sloupci `Year` méně než 1 nastavením parametru `upperBound` na hodnotu 1. Naopak pro druhý rok jsou hodnoty větší než nebo rovny 1 vybrány nastavením parametru `lowerBound` na hodnotu 1.

## <a name="define-time-series-analysis-pipeline"></a>Definování kanálu analýzy časové řady

1. Definujte kanál, který používá [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) k předpovědi hodnot v datové sadě časových řad.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    `forecastingPipeline` přebírá 365 datových bodů za první rok a ukázky nebo rozdělí datovou sadu do 30 dnů (měsíčně) intervalů určených parametrem `seriesLength`. Každá z těchto ukázek je analyzována v týdenním nebo 7 denním intervalu. Při určování toho, jaká hodnota předpovědi je pro další období, se pro vytvoření předpovědi použijí hodnoty z předchozích sedmi dnů. Model je nastaven na předpověď sedmi teček do budoucna, jak je definováno parametrem `horizon`. Vzhledem k tomu, že prognóza je včas odhad, není vždy 100% přesná. Proto je dobré znát rozsah hodnot ve scénářích nejlepšího a nejhoršího případu, jak jsou definovány horní a dolní mezí. V takovém případě je úroveň spolehlivosti pro dolní a horní mez nastavena na 95%. Úroveň spolehlivosti se proto dá zvýšit nebo snížit. Čím vyšší je hodnota, tím širší je rozsah mezi horní a dolní mezí, abyste dosáhli požadované úrovně důvěry. 

1. Použijte metodu [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) pro výuku modelu a přizpůsobení dat dříve definovaným `forecastingPipeline`.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Vyhodnoťte, jak dobře se model provádí prognózou dat z následujícího roku a porovnáním s aktuálními hodnotami.

1. Pod metodu `Main` vytvořte novou metodu Utility nazvanou `Evaluate`.

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {
        
    }
    ```

1. V rámci metody `Evaluate` vypovídat data druhého roku pomocí metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) s školeným modelem.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Získat skutečné hodnoty z dat pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Získejte hodnoty předpovědi pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Vypočítá rozdíl mezi skutečnými a předpověď hodnotami, které se běžně označují jako chyba.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Změřte výkon tím, že vypočítají střední absolutní chybu a hlavní střední hodnoty chyb.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    K vyhodnocení výkonu se použijí následující metriky:

    - **Střední absolutní chyba**: měří, jak blízkoa předpovědi je skutečná hodnota. Rozsah hodnot je od 0 do nekonečno. Nejblíže k 0, což je lepší kvalita modelu.
    - **Hlavní střední hodnota: Chyba na čtverci**: shrnuje chybu thhe v modelu. Rozsah hodnot je od 0 do nekonečno. Nejblíže k 0, což je lepší kvalita modelu.

1. Výstup metrik do konzoly.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Použijte metodu `Evaluate` v rámci metody `Main`.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Uložit model

Pokud jste s modelem spokojeni, uložte ho pro pozdější použití v jiných aplikacích.

1. V metodě `Main` vytvořte [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602). [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) je pohodlnější způsob, jak vytvořit jeden předpovědi.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Uložte model do souboru s názvem `MLModel.zip`, jak je určeno dříve definovanou `modelPath` proměnnou. K uložení modelu použijte metodu [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) .

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Použití modelu k prognózování poptávky

1. Pod metodu `Evaluate` vytvořte novou metodu Utility nazvanou `Forecast`.

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. V rámci metody `Forecast` použijte k předpovědi nájemné za dalších sedm dní metodu [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) .

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Zarovnejte hodnoty skutečných hodnot a prognózy pro sedm teček.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Iterujte ve výstupu předpovědi a zobrazte ji v konzole.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Spuštění aplikace

1. Uvnitř metody `Main` volejte metodu `Forecast`.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Spusťte aplikaci. Výstup podobný tomuto: by měl být zobrazený v konzole nástroje. V případě zkrácení byl výstup zúžený.

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

Kontrola skutečných a předpokládaných hodnot zobrazuje následující vztahy:

![Aktuální porovnání předpovědi vs.](./media/time-series-demand-forecasting/forecast.png)

I když hodnoty prognózy nepředpověď nad přesný počet nájemného, poskytují přesnější rozsah hodnot, který umožňuje operaci optimalizace používání prostředků. 

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení s časovou řadou k prognózování poptávky po pronájmu kol.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .

## <a name="next-steps"></a>Další kroky

- [Úlohy strojového učení v ML.NET](../resources/tasks.md)
- [Zvýšit přesnost modelu](../resources/improve-machine-learning-model-ml-net.md)
