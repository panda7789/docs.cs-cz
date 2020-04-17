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
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="c362d-103">Kurz: Prognóza poptávky po půjčovně kol s analýzou časových řad a ML.NET</span><span class="sxs-lookup"><span data-stu-id="c362d-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="c362d-104">Zjistěte, jak předpovídat poptávku po půjčovně kol pomocí analýzy jednorozměrné časové řady na datech uložených v databázi serveru SQL Server s ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c362d-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="c362d-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="c362d-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="c362d-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="c362d-106">Understand the problem</span></span>
> * <span data-ttu-id="c362d-107">Načtení dat z databáze</span><span class="sxs-lookup"><span data-stu-id="c362d-107">Load data from a database</span></span>
> * <span data-ttu-id="c362d-108">Vytvoření modelu prognózy</span><span class="sxs-lookup"><span data-stu-id="c362d-108">Create a forecasting model</span></span>
> * <span data-ttu-id="c362d-109">Vyhodnotit model prognózy</span><span class="sxs-lookup"><span data-stu-id="c362d-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="c362d-110">Uložení modelu prognózy</span><span class="sxs-lookup"><span data-stu-id="c362d-110">Save a forecasting model</span></span>
> * <span data-ttu-id="c362d-111">Použití modelu prognózy</span><span class="sxs-lookup"><span data-stu-id="c362d-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c362d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c362d-112">Prerequisites</span></span>

- <span data-ttu-id="c362d-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".</span><span class="sxs-lookup"><span data-stu-id="c362d-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="c362d-114">Přehled ukázkových prognóz časových řad</span><span class="sxs-lookup"><span data-stu-id="c362d-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="c362d-115">Tato ukázka je **aplikace konzoly C# .NET Core,** která předpovídá poptávku po zapůjčení jízdních kol pomocí algoritmu analýzy jednorozměrné časové řady známého jako Analýza jednoho spektra.</span><span class="sxs-lookup"><span data-stu-id="c362d-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="c362d-116">Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c362d-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="c362d-117">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="c362d-117">Understand the problem</span></span>

<span data-ttu-id="c362d-118">Pro efektivní provoz hraje řízení zásob klíčovou roli.</span><span class="sxs-lookup"><span data-stu-id="c362d-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="c362d-119">Mít příliš mnoho výrobku na skladě znamená neprodané výrobky sedí na regálech nevytváří žádné příjmy.</span><span class="sxs-lookup"><span data-stu-id="c362d-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="c362d-120">Mít příliš málo produktů vede ke ztrátě prodeje a zákazníkům nakupujícím od konkurentů.</span><span class="sxs-lookup"><span data-stu-id="c362d-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="c362d-121">Proto je neustálou otázkou, jaké je optimální množství zásob, které mají být po ruce?</span><span class="sxs-lookup"><span data-stu-id="c362d-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="c362d-122">Analýza časových řad pomáhá poskytnout odpověď na tyto otázky tím, že se podíváte na historická data, identifikujete vzory a pomocí těchto informací předpovídáte hodnoty někdy v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="c362d-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="c362d-123">Technika pro analýzu dat použitých v tomto kurzu je jednorozměrné analýzy časových řad.</span><span class="sxs-lookup"><span data-stu-id="c362d-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="c362d-124">Analýza jednorozměrných časových řad se podívá na jedno číselné pozorování v určitém časovém období v určitých intervalech, jako je měsíční prodej.</span><span class="sxs-lookup"><span data-stu-id="c362d-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="c362d-125">Algoritmus použitý v tomto kurzu je [single spectrum analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="c362d-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="c362d-126">SSA funguje tak, že rozkládá časové řady do sady hlavních součástí.</span><span class="sxs-lookup"><span data-stu-id="c362d-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="c362d-127">Tyto komponenty lze interpretovat jako části signálu, které odpovídají trendům, šumu, sezónnosti a mnoha dalším faktorům.</span><span class="sxs-lookup"><span data-stu-id="c362d-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="c362d-128">Potom tyto součásti jsou rekonstruovány a slouží k prognóze hodnoty nějaký čas v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="c362d-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="c362d-129">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="c362d-129">Create console application</span></span>

1. <span data-ttu-id="c362d-130">Vytvořte novou **aplikaci konzoly C# .NET Core** s názvem "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="c362d-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="c362d-131">Instalace **Microsoft.ML** verze **1.4.0** NuGet balíček</span><span class="sxs-lookup"><span data-stu-id="c362d-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="c362d-132">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c362d-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="c362d-133">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** a vyhledejte **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="c362d-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="c362d-134">Zaškrtněte políčko **Zahrnout předběžnou verzi.**</span><span class="sxs-lookup"><span data-stu-id="c362d-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="c362d-135">Vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="c362d-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="c362d-136">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně Přijetí licence vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="c362d-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="c362d-137">Opakujte tyto kroky pro **System.Data.SqlClient** verze **4.7.0** a **Microsoft.ML.TimeSeries** verze **1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="c362d-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="c362d-138">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="c362d-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="c362d-139">Vytvořte adresář s názvem *Data*.</span><span class="sxs-lookup"><span data-stu-id="c362d-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="c362d-140">Stáhněte [databázový soubor *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) a uložte jej do *datového* adresáře.</span><span class="sxs-lookup"><span data-stu-id="c362d-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="c362d-141">Data použitá v tomto kurzu pochází z [datové sady Sdílení kol UCI](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="c362d-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="c362d-142">Fanaee-T, Hadi a Gama, Joao, "Event labeling kombinující detektory souborů a znalosti pozadí", Pokrok v umělé inteligenci (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="c362d-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="c362d-143">Původní datová sada obsahuje několik sloupců odpovídajících sezónnosti a počasí.</span><span class="sxs-lookup"><span data-stu-id="c362d-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="c362d-144">Pro stručnost a protože algoritmus použitý v tomto kurzu vyžaduje pouze hodnoty z jednoho číselného sloupce, původní datová sada byla zhuštěna tak, aby zahrnovala pouze následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="c362d-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="c362d-145">**dteday**: Datum pozorování.</span><span class="sxs-lookup"><span data-stu-id="c362d-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="c362d-146">**rok**: Zakódovaný rok pozorování (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="c362d-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="c362d-147">**cnt**: Celkový počet půjčoven kol pro tento den.</span><span class="sxs-lookup"><span data-stu-id="c362d-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="c362d-148">Původní datová sada je mapována na databázovou tabulku s následujícím schématem v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c362d-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="c362d-149">Následuje ukázka dat:</span><span class="sxs-lookup"><span data-stu-id="c362d-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="c362d-150">Datum pronájmu</span><span class="sxs-lookup"><span data-stu-id="c362d-150">RentalDate</span></span> | <span data-ttu-id="c362d-151">Year</span><span class="sxs-lookup"><span data-stu-id="c362d-151">Year</span></span> | <span data-ttu-id="c362d-152">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="c362d-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="c362d-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="c362d-153">1/1/2011</span></span>|<span data-ttu-id="c362d-154">0</span><span class="sxs-lookup"><span data-stu-id="c362d-154">0</span></span>|<span data-ttu-id="c362d-155">985</span><span class="sxs-lookup"><span data-stu-id="c362d-155">985</span></span>|
|<span data-ttu-id="c362d-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="c362d-156">1/2/2011</span></span>|<span data-ttu-id="c362d-157">0</span><span class="sxs-lookup"><span data-stu-id="c362d-157">0</span></span>|<span data-ttu-id="c362d-158">801</span><span class="sxs-lookup"><span data-stu-id="c362d-158">801</span></span>|
|<span data-ttu-id="c362d-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="c362d-159">1/3/2011</span></span>|<span data-ttu-id="c362d-160">0</span><span class="sxs-lookup"><span data-stu-id="c362d-160">0</span></span>|<span data-ttu-id="c362d-161">1349</span><span class="sxs-lookup"><span data-stu-id="c362d-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="c362d-162">Vytvoření vstupních a výstupních tříd</span><span class="sxs-lookup"><span data-stu-id="c362d-162">Create input and output classes</span></span>

1. <span data-ttu-id="c362d-163">Otevřete *Program.cs* soubor `using` a nahraďte existující příkazy následujícími příkazy:</span><span class="sxs-lookup"><span data-stu-id="c362d-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="c362d-164">Vytvořte třídu `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="c362d-164">Create `ModelInput` class.</span></span> <span data-ttu-id="c362d-165">Pod `Program` třídu přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c362d-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="c362d-166">Třída `ModelInput` obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="c362d-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="c362d-167">**RentalDate**: Datum pozorování.</span><span class="sxs-lookup"><span data-stu-id="c362d-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="c362d-168">**Rok**: Zakódovaný rok pozorování (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="c362d-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="c362d-169">**TotalRentals**: Celkový počet půjčoven kol pro tento den.</span><span class="sxs-lookup"><span data-stu-id="c362d-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="c362d-170">Vytvořte `ModelOutput` třídu `ModelInput` pod nově vytvořenou třídou.</span><span class="sxs-lookup"><span data-stu-id="c362d-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="c362d-171">Třída `ModelOutput` obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="c362d-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="c362d-172">**ForecastedRentals**: Předpokládané hodnoty pro předpokládané období.</span><span class="sxs-lookup"><span data-stu-id="c362d-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="c362d-173">**LowerBoundRentals**: Předpokládané minimální hodnoty pro předpokládané období.</span><span class="sxs-lookup"><span data-stu-id="c362d-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="c362d-174">**UpperBoundRentals**: Předpokládané maximální hodnoty pro předpokládané období.</span><span class="sxs-lookup"><span data-stu-id="c362d-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="c362d-175">Definování cest a inicializaci proměnných</span><span class="sxs-lookup"><span data-stu-id="c362d-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="c362d-176">Uvnitř `Main` metody definujte proměnné pro uložení umístění dat, připojovacířetězec a kde uložit trénovaný model.</span><span class="sxs-lookup"><span data-stu-id="c362d-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="c362d-177">Inicializovat `mlContext` proměnnou s [`MLContext`](xref:Microsoft.ML.MLContext) novou instanci přidáním následující řádek k metodě. `Main`</span><span class="sxs-lookup"><span data-stu-id="c362d-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="c362d-178">Třída [`MLContext`](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET a inicializace mlContext vytvoří nové ML.NET prostředí, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="c362d-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="c362d-179">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="c362d-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="c362d-180">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="c362d-180">Load the data</span></span>

1. <span data-ttu-id="c362d-181">Vytvořte, `DatabaseLoader` že `ModelInput`načte záznamy typu .</span><span class="sxs-lookup"><span data-stu-id="c362d-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="c362d-182">Definujte dotaz pro načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="c362d-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="c362d-183">ML.NET algoritmy očekávají, že [`Single`](xref:System.Single)data budou typu .</span><span class="sxs-lookup"><span data-stu-id="c362d-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="c362d-184">Proto číselné hodnoty pocházející z databáze, [`Real`](xref:System.Data.SqlDbType)které nejsou typu , s jednou přesností s [`Real`](xref:System.Data.SqlDbType)plovoucí desetinnou hodnotou, musí být převedeny na .</span><span class="sxs-lookup"><span data-stu-id="c362d-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="c362d-185">Sloupce `Year` `TotalRental` a jsou oba celé typy v databázi.</span><span class="sxs-lookup"><span data-stu-id="c362d-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="c362d-186">Pomocí `CAST` vestavěné funkce jsou oba `Real`přetypovány do .</span><span class="sxs-lookup"><span data-stu-id="c362d-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="c362d-187">Vytvořte `DatabaseSource` a pro připojení k databázi a spusťte dotaz.</span><span class="sxs-lookup"><span data-stu-id="c362d-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="c362d-188">Načtěte data `IDataView`do .</span><span class="sxs-lookup"><span data-stu-id="c362d-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="c362d-189">Datová sada obsahuje data za dva roky.</span><span class="sxs-lookup"><span data-stu-id="c362d-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="c362d-190">Pro školení se používají pouze údaje z prvního roku, druhý rok se koná pro porovnání skutečných hodnot s prognózou vytvořenou modelem.</span><span class="sxs-lookup"><span data-stu-id="c362d-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="c362d-191">Filtrujte data [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) pomocí transformace.</span><span class="sxs-lookup"><span data-stu-id="c362d-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="c362d-192">Pro první rok jsou pouze `Year` hodnoty ve sloupci menší `upperBound` než 1 vybrány nastavením parametru na 1.</span><span class="sxs-lookup"><span data-stu-id="c362d-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="c362d-193">Naopak pro druhý rok jsou hodnoty větší než nebo rovny `lowerBound` 1 vybrány nastavením parametru na 1.</span><span class="sxs-lookup"><span data-stu-id="c362d-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="c362d-194">Definování kanálu analýzy časových řad</span><span class="sxs-lookup"><span data-stu-id="c362d-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="c362d-195">Definujte kanál, který používá [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) k prognóze hodnot v datové sadě časových řad.</span><span class="sxs-lookup"><span data-stu-id="c362d-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="c362d-196">Trvá `forecastingPipeline` 365 datových bodů za první rok a vzorkuje nebo rozdělí datovou sadu časových řad na `seriesLength` 30denní (měsíční) intervaly určené parametrem.</span><span class="sxs-lookup"><span data-stu-id="c362d-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="c362d-197">Každý z těchto vzorků je analyzován prostřednictvím týdenního nebo 7denního okna.</span><span class="sxs-lookup"><span data-stu-id="c362d-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="c362d-198">Při určování, co je prognózovaná hodnota pro další období, hodnoty z předchozích sedmi dnů se používají k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c362d-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="c362d-199">Model je nastaven tak, aby předpovídal sedm období `horizon` do budoucnosti, jak je definováno parametrem.</span><span class="sxs-lookup"><span data-stu-id="c362d-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="c362d-200">Vzhledem k tomu, že prognóza je informovaný odhad, není vždy 100% přesná.</span><span class="sxs-lookup"><span data-stu-id="c362d-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="c362d-201">Proto je vhodné znát rozsah hodnot v nejlepších a nejhorších scénářích, jak je definováno horní a dolní hranice.</span><span class="sxs-lookup"><span data-stu-id="c362d-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="c362d-202">V tomto případě je úroveň spolehlivosti dolní a horní hranice nastavena na 95%.</span><span class="sxs-lookup"><span data-stu-id="c362d-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="c362d-203">Úroveň spolehlivosti může být odpovídajícím způsobem zvýšena nebo snížena.</span><span class="sxs-lookup"><span data-stu-id="c362d-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="c362d-204">Čím vyšší je hodnota, tím širší je rozsah mezi horním a dolním mezí, aby bylo dosaženo požadované úrovně spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="c362d-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="c362d-205">Pomocí [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metody můžete model trénovat a `forecastingPipeline`přizpůsobit data dříve definovanému .</span><span class="sxs-lookup"><span data-stu-id="c362d-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="c362d-206">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="c362d-206">Evaluate the model</span></span>

<span data-ttu-id="c362d-207">Vyhodnoťte, jak si model vede, a to prognózou dat příštího roku a porovnáním se skutečnými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="c362d-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="c362d-208">Pod `Main` metodou vytvořte novou metodu nástroje nazvanou `Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="c362d-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="c362d-209">Uvnitř `Evaluate` metody prognóza data druhého roku pomocí [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody s trénovaným modelem.</span><span class="sxs-lookup"><span data-stu-id="c362d-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="c362d-210">Získejte skutečné hodnoty z dat [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="c362d-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="c362d-211">Získejte hodnoty prognózy [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="c362d-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="c362d-212">Vypočítejte rozdíl mezi skutečnou hodnotou a hodnotou prognózy, běžně označovanou jako chyba.</span><span class="sxs-lookup"><span data-stu-id="c362d-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="c362d-213">Změřte výkon výpočtem hodnot Střední absolutní chyba a Střední kvadratická chyba kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="c362d-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="c362d-214">K vyhodnocení výkonu se používají následující metriky:</span><span class="sxs-lookup"><span data-stu-id="c362d-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="c362d-215">**Střední absolutní chyba**: Měří, jak blízko předpovědi jsou na skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c362d-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="c362d-216">Tato hodnota se pohybuje mezi 0 a nekonečno.</span><span class="sxs-lookup"><span data-stu-id="c362d-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="c362d-217">Čím blíže k 0, tím lepší je kvalita modelu.</span><span class="sxs-lookup"><span data-stu-id="c362d-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="c362d-218">**Kořenová střední kvadratmárská chyba**: Shrnuje chybu v modelu.</span><span class="sxs-lookup"><span data-stu-id="c362d-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="c362d-219">Tato hodnota se pohybuje mezi 0 a nekonečno.</span><span class="sxs-lookup"><span data-stu-id="c362d-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="c362d-220">Čím blíže k 0, tím lepší je kvalita modelu.</span><span class="sxs-lookup"><span data-stu-id="c362d-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="c362d-221">Výstup metriky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c362d-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="c362d-222">Použijte `Evaluate` metodu `Main` uvnitř metody.</span><span class="sxs-lookup"><span data-stu-id="c362d-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="c362d-223">Uložení modelu</span><span class="sxs-lookup"><span data-stu-id="c362d-223">Save the model</span></span>

<span data-ttu-id="c362d-224">Pokud jste s modelem spokojeni, uložte jej pro pozdější použití v jiných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="c362d-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="c362d-225">V `Main` metodě vytvořte [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="c362d-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="c362d-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)je komfortní metoda, aby se jednotlivé předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c362d-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="c362d-227">Uložte model do `MLModel.zip` souboru volaném `modelPath` dříve definovanou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="c362d-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="c362d-228">Pomocí [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) metody uložte model.</span><span class="sxs-lookup"><span data-stu-id="c362d-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="c362d-229">Použití modelu k prognóze poptávky</span><span class="sxs-lookup"><span data-stu-id="c362d-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="c362d-230">Pod `Evaluate` metodou vytvořte novou metodu nástroje nazvanou `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="c362d-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="c362d-231">Uvnitř `Forecast` metody použijte [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metodu k prognóze pronájmů pro příštích sedm dní.</span><span class="sxs-lookup"><span data-stu-id="c362d-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="c362d-232">Zarovnejte skutečné hodnoty a hodnoty prognózy pro sedm období.</span><span class="sxs-lookup"><span data-stu-id="c362d-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="c362d-233">Iterate prostřednictvím výstupu prognózy a zobrazí jej na konzoli.</span><span class="sxs-lookup"><span data-stu-id="c362d-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="c362d-234">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="c362d-234">Run the application</span></span>

1. <span data-ttu-id="c362d-235">Uvnitř `Main` metody volejte `Forecast` metodu.</span><span class="sxs-lookup"><span data-stu-id="c362d-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="c362d-236">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c362d-236">Run the application.</span></span> <span data-ttu-id="c362d-237">Výstup podobný tomu níže by se měl objevit na konzoli.</span><span class="sxs-lookup"><span data-stu-id="c362d-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="c362d-238">Pro stručnost byl výstup zhuštěn.</span><span class="sxs-lookup"><span data-stu-id="c362d-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="c362d-239">Kontrola skutečných a předpokládaných hodnot ukazuje následující vztahy:</span><span class="sxs-lookup"><span data-stu-id="c362d-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Skutečné vs porovnání prognóz](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="c362d-241">Zatímco předpokládané hodnoty nepředpovídají přesný počet pronájmů, poskytují užší rozsah hodnot, který umožňuje operaci optimalizovat jejich využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="c362d-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="c362d-242">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="c362d-242">Congratulations!</span></span> <span data-ttu-id="c362d-243">Nyní jste úspěšně vytvořili model strojového učení řady časových řad, abyste předpovídali poptávku po pronájmu jízdních kol.</span><span class="sxs-lookup"><span data-stu-id="c362d-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="c362d-244">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)</span><span class="sxs-lookup"><span data-stu-id="c362d-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c362d-245">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c362d-245">Next steps</span></span>

- [<span data-ttu-id="c362d-246">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="c362d-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="c362d-247">Vylepšení přesnosti modelu</span><span class="sxs-lookup"><span data-stu-id="c362d-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
