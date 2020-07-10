---
title: 'Kurz: odhad poptávky po absolvování kol – časové řady'
description: V tomto kurzu se dozvíte, jak předpovědět poptávku za službu pronájmu kol pomocí analýzy univariate časových řad a ML.NET.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: d93bdee8d5a057be0f405fe4334d7edbdc0649ec
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174403"
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

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.

## <a name="time-series-forecasting-sample-overview"></a>Ukázka prognózy časových řad – přehled

Tato ukázka je **Konzolová aplikace C# .NET Core** , která vypovídá poptávku za nájemné za kolo pomocí algoritmu analýzy univariate Time Series, který se označuje jako analýza v jednotném spektru. Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) na GitHubu.

## <a name="understand-the-problem"></a>Pochopení problému

Aby bylo možné spustit efektivní operaci, Správa inventáře hraje klíčovou roli. Pokud máte příliš mnoho produktů na skladě, znamená to, že neprodávané produkty jsou v police negenerují žádné výnosy. S příliš malým množstvím produktů vede ke ztrátě prodeje a zákazníkům, kteří si kupují z konkurence. Proto se jedná o konstantní otázku, co je optimální množství inventáře, abyste mohli zůstat na ruce? Analýza časových řad pomáhá poskytnout odpověď na tyto otázky zobrazením historických dat, identifikace vzorů a využitím těchto informací k předpovědi hodnot v budoucnu.

Technika analýzy dat používaných v tomto kurzu je univariate analýza časových řad. Analýza Univariate Time-Series se při určitých intervalech, jako je měsíční prodej, podívá na jedno číselné pozorování v určitém časovém intervalu.

Algoritmus použitý v tomto kurzu je [Analýza jednotného spektra (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA funguje tak, že rozdělí časovou řadu do sady základních komponent. Tyto komponenty lze interpretovat jako části signálu, který odpovídá trendům, hluku, sezónnost a mnoha dalším faktorům. Poté jsou tyto komponenty znovu sestaveny a použity k předpovědi hodnot v budoucnu.

## <a name="create-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte novou **konzolovou aplikaci .NET Core** s názvem "BikeDemandForecasting".
1. Nainstalovat balíček NuGet verze **Microsoft.ml**

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.
    1. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** a vyhledejte **Microsoft.ml**.
    1. Zaškrtněte políčko **zahrnout předběžné verze** .
    1. Vyberte tlačítko **instalovat** .
    1. Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .
    1. Opakujte tyto kroky pro **System. data. SqlClient** a **Microsoft. ml. časové řady**.

### <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Vytvořte adresář s názvem *data*.
1. Stáhněte [soubor databáze *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) a uložte ho do *datového* adresáře.

> [!NOTE]
> Data použitá v tomto kurzu pocházejí z [datové sady pro sdílení kol UCI](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, hadi a gama, Joao, "označování událostí kombinující detektory kompletu a znalosti na pozadí", pokrok v umělých Intelligencech (2013): PP. 1-15, Springer Berlín Heidelberg, [webový odkaz](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

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

| RentalDate | Year (Rok) | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Vytvoření vstupní a výstupní třídy

1. Otevřete soubor *program.cs* a nahraďte existující `using` příkazy následujícím způsobem:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Vytvořte třídu `ModelInput`. Pod `Program` třídou přidejte následující kód.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    `ModelInput`Třída obsahuje následující sloupce:

    - **RentalDate**: datum pozorování.
    - **Year**: kódovaný rok sledování (0 = 2011, 1 = 2012).
    - **TotalRentals**: celkový počet pronajatých kol za tento den.

1. Vytvořte `ModelOutput` třídu pod nově vytvořenou `ModelInput` třídou.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    `ModelOutput`Třída obsahuje následující sloupce:

    - **ForecastedRentals**: předpokládané hodnoty pro období prognózy.
    - **LowerBoundRentals**: předpokládané minimální hodnoty pro období prognózy.
    - **UpperBoundRentals**: předpokládané maximální hodnoty pro období prognózy.

### <a name="define-paths-and-initialize-variables"></a>Definování cest a inicializovat proměnné

1. V rámci `Main` metody Definujte proměnné pro ukládání umístění vašich dat, připojovací řetězec a místo, kam chcete vyškolený model Uložit.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Inicializujte `mlContext` proměnnou s novou instancí přidáním [`MLContext`](xref:Microsoft.ML.MLContext) následujícího řádku do `Main` metody.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    [`MLContext`](xref:Microsoft.ML.MLContext)Třída je výchozím bodem pro všechny operace ml.NET a inicializuje mlContext vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

## <a name="load-the-data"></a>Načtení dat

1. Vytvořte `DatabaseLoader` , který načte záznamy typu `ModelInput` .

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Definujte dotaz pro načtení dat z databáze.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algoritmy očekávají, že data jsou typu [`Single`](xref:System.Single) . Proto číselné hodnoty pocházející z databáze, které nejsou typu, je [`Real`](xref:System.Data.SqlDbType) třeba převést na hodnotu s plovoucí desetinnou čárkou s jednoduchou přesností [`Real`](xref:System.Data.SqlDbType) .

    `Year`Sloupce a `TotalRental` jsou oba typy celého čísla v databázi. Pomocí `CAST` integrované funkce jsou obě přetypování na `Real` .

1. Vytvořte a `DatabaseSource` Připojte se k databázi a spusťte dotaz.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Načtěte data do `IDataView` .

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Datová sada obsahuje dva roky s daty. Pro školení se použijí jenom data z prvního roku, druhý rok se porovná s porovnáním skutečných hodnot s prognózou vytvořenou modelem. Filtrujte data pomocí [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transformace.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    Pro první rok jsou vybrány pouze hodnoty ve `Year` sloupci menším než 1, a to nastavením `upperBound` parametru na hodnotu 1. Naopak pro druhý rok jsou hodnoty větší než nebo rovny 1 vybrány nastavením `lowerBound` parametru na hodnotu 1.

## <a name="define-time-series-analysis-pipeline"></a>Definování kanálu analýzy časové řady

1. Definujte kanál, který používá [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) k předpovědi hodnot v datové sadě časových řad.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    `forecastingPipeline`Převezme 365 datových bodů za první rok a ukázky nebo rozdělí datovou sadu do 30 dnů (měsíčně) intervalů, které jsou určeny `seriesLength` parametrem. Každá z těchto ukázek je analyzována v týdenním nebo 7 denním intervalu. Při určování toho, jaká hodnota předpovědi je pro další období, se pro vytvoření předpovědi použijí hodnoty z předchozích sedmi dnů. Model je nastaven na předpověď sedmi teček do budoucna, jak je definováno `horizon` parametrem. Vzhledem k tomu, že prognóza je včas odhad, není vždy 100% přesná. Proto je dobré znát rozsah hodnot ve scénářích nejlepšího a nejhoršího případu, jak jsou definovány horní a dolní mezí. V takovém případě je úroveň spolehlivosti pro dolní a horní mez nastavena na 95%. Úroveň spolehlivosti se proto dá zvýšit nebo snížit. Čím vyšší je hodnota, tím širší je rozsah mezi horní a dolní mezí, abyste dosáhli požadované úrovně důvěry.

1. Použijte [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metodu pro výuku modelu a přizpůsobení dat dříve definovaným způsobem `forecastingPipeline` .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Vyhodnoťte, jak dobře se model provádí prognózou dat z následujícího roku a porovnáním s aktuálními hodnotami.

1. Pod `Main` metodou vytvořte novou metodu Utility s názvem `Evaluate` .

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. V rámci `Evaluate` metody předpovědět data druhého roku pomocí [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody s školeným modelem.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Získat skutečné hodnoty z dat pomocí [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Získejte hodnoty prognózy pomocí [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Vypočítá rozdíl mezi skutečnými a předpověď hodnotami, které se běžně označují jako chyba.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Změřte výkon tím, že vypočítají střední absolutní chybu a hlavní střední hodnoty chyb.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    K vyhodnocení výkonu se použijí následující metriky:

    - **Střední absolutní chyba**: měří, jak blízkoa předpovědi je skutečná hodnota. Rozsah hodnot je od 0 do nekonečno. Nejblíže k 0, což je lepší kvalita modelu.
    - **Hlavní střední hodnota: Chyba na čtverci**: shrnuje chybu v modelu. Rozsah hodnot je od 0 do nekonečno. Nejblíže k 0, což je lepší kvalita modelu.

1. Výstup metrik do konzoly.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Použijte `Evaluate` metodu uvnitř `Main` metody.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Uložení modelu

Pokud jste s modelem spokojeni, uložte ho pro pozdější použití v jiných aplikacích.

1. V `Main` metodě vytvořte [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) . [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)je pohodlnější způsob, jak vytvořit jeden předpovědi.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Uložte model do souboru s názvem, který je `MLModel.zip` určen dříve definovanou `modelPath` proměnnou. [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*)K uložení modelu použijte metodu.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Použití modelu k prognózování poptávky

1. Pod `Evaluate` metodou vytvořte novou metodu Utility s názvem `Forecast` .

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. V rámci `Forecast` metody použijte [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metodu k předpovědi nájemného za dalších sedm dní.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Zarovnejte hodnoty skutečných hodnot a prognózy pro sedm teček.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Iterujte ve výstupu předpovědi a zobrazte ji v konzole.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Spuštění aplikace

1. Uvnitř `Main` metody zavolejte `Forecast` metodu.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Aplikaci spusťte. Výstup podobný tomuto: by měl být zobrazený v konzole nástroje. V případě zkrácení byl výstup zúžený.

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

Blahopřejeme. Teď jste úspěšně vytvořili model strojového učení s časovou řadou k prognózování poptávky po pronájmu kol.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .

## <a name="next-steps"></a>Další kroky

- [Úlohy strojového učení v ML.NET](../resources/tasks.md)
- [Vylepšení přesnosti modelu](../resources/improve-machine-learning-model-ml-net.md)
