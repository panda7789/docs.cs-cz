---
title: 'Kurz: odhad poptávky po absolvování kol – časové řady'
description: V tomto kurzu se dozvíte, jak předpovědět poptávku za službu pronájmu kol pomocí analýzy univariate časových řad a ML.NET.
ms.date: 10/31/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: f30aac5f8467c2410e9008bafea3cf35af3f4e2a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425637"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="93ad1-103">Kurz: odhadování poptávky po nájemce kol s využitím analýzy časových řad a ML.NET</span><span class="sxs-lookup"><span data-stu-id="93ad1-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="93ad1-104">Naučte se, jak odhadnout poptávku za službu pronájmu kol pomocí analýzy univariate časových řad s daty uloženými v databázi SQL Server s ML.NET.</span><span class="sxs-lookup"><span data-stu-id="93ad1-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="93ad1-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="93ad1-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="93ad1-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="93ad1-106">Understand the problem</span></span>
> * <span data-ttu-id="93ad1-107">Načtení dat z databáze</span><span class="sxs-lookup"><span data-stu-id="93ad1-107">Load data from a database</span></span>
> * <span data-ttu-id="93ad1-108">Vytvoření modelu prognózy</span><span class="sxs-lookup"><span data-stu-id="93ad1-108">Create a forecasting model</span></span>
> * <span data-ttu-id="93ad1-109">Vyhodnotit model prognózy</span><span class="sxs-lookup"><span data-stu-id="93ad1-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="93ad1-110">Uložení modelu prognózy</span><span class="sxs-lookup"><span data-stu-id="93ad1-110">Save a forecasting model</span></span>
> * <span data-ttu-id="93ad1-111">Použití modelu prognózy</span><span class="sxs-lookup"><span data-stu-id="93ad1-111">Use a forecasting model</span></span>

> [!NOTE]
> <span data-ttu-id="93ad1-112">V tomto kurzu se používá verze Preview sady DatabaseLoader.</span><span class="sxs-lookup"><span data-stu-id="93ad1-112">This tutorial uses a preview version of DatabaseLoader.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="93ad1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93ad1-113">Prerequisites</span></span>

- <span data-ttu-id="93ad1-114">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="93ad1-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="93ad1-115">Ukázka prognózy časových řad – přehled</span><span class="sxs-lookup"><span data-stu-id="93ad1-115">Time series forecasting sample overview</span></span>

<span data-ttu-id="93ad1-116">Tato ukázka je  **C# Konzolová aplikace .NET Core** , která vypovídá poptávku za nájemné za kolo pomocí algoritmu analýzy univariate Time Series, který se označuje jako analýza s jedním spektrem.</span><span class="sxs-lookup"><span data-stu-id="93ad1-116">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="93ad1-117">Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-117">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="93ad1-118">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="93ad1-118">Understand the problem</span></span>

<span data-ttu-id="93ad1-119">Aby bylo možné spustit efektivní operaci, Správa inventáře hraje klíčovou roli.</span><span class="sxs-lookup"><span data-stu-id="93ad1-119">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="93ad1-120">Pokud máte příliš mnoho produktů na skladě, znamená to, že neprodávané produkty jsou v police negenerují žádné výnosy.</span><span class="sxs-lookup"><span data-stu-id="93ad1-120">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="93ad1-121">S příliš malým množstvím produktů vede ke ztrátě prodeje a zákazníkům, kteří si kupují z konkurence.</span><span class="sxs-lookup"><span data-stu-id="93ad1-121">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="93ad1-122">Proto se jedná o konstantní otázku, co je optimální množství inventáře, abyste mohli zůstat na ruce?</span><span class="sxs-lookup"><span data-stu-id="93ad1-122">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="93ad1-123">Analýza časových řad pomáhá poskytnout odpověď na tyto otázky zobrazením historických dat, identifikace vzorů a využitím těchto informací k předpovědi hodnot v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-123">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span> 

<span data-ttu-id="93ad1-124">Technika analýzy dat používaných v tomto kurzu je univariate analýza časových řad.</span><span class="sxs-lookup"><span data-stu-id="93ad1-124">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="93ad1-125">Analýza Univariate Time-Series se při určitých intervalech, jako je měsíční prodej, podívá na jedno číselné pozorování v určitém časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-125">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span> 

<span data-ttu-id="93ad1-126">Algoritmus použitý v tomto kurzu je [Analýza s jedním spektrem (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="93ad1-126">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="93ad1-127">SSA funguje tak, že rozdělí časovou řadu do sady základních komponent.</span><span class="sxs-lookup"><span data-stu-id="93ad1-127">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="93ad1-128">Tyto komponenty lze interpretovat jako části signálu, který odpovídá trendům, hluku, sezónnost a mnoha dalším faktorům.</span><span class="sxs-lookup"><span data-stu-id="93ad1-128">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="93ad1-129">Poté jsou tyto komponenty znovu sestaveny a použity k předpovědi hodnot v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-129">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="93ad1-130">Vytvořit konzolovou aplikaci</span><span class="sxs-lookup"><span data-stu-id="93ad1-130">Create console application</span></span>

1. <span data-ttu-id="93ad1-131">Vytvořte novou  **C# konzolovou aplikaci .NET Core** nazvanou "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="93ad1-131">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="93ad1-132">Balíček NuGet pro instalaci verze **Microsoft.ml** **1.4.0-preview2**</span><span class="sxs-lookup"><span data-stu-id="93ad1-132">Install **Microsoft.ML** version **1.4.0-preview2** NuGet package</span></span>
    1. <span data-ttu-id="93ad1-133">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="93ad1-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="93ad1-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** a vyhledejte **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="93ad1-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="93ad1-135">Zaškrtněte políčko **zahrnout předběžné verze** .</span><span class="sxs-lookup"><span data-stu-id="93ad1-135">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="93ad1-136">Vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="93ad1-136">Select the **Install** button.</span></span>
    1. <span data-ttu-id="93ad1-137">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="93ad1-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="93ad1-138">Opakujte tento postup pro **System. data. SqlClient** verze **4.7.0**, **Microsoft. ml. experimentální** verze **0.16.0-preview2**a **Microsoft. ml. časové řady** Version **1.4.0-preview2**.</span><span class="sxs-lookup"><span data-stu-id="93ad1-138">Repeat these steps for **System.Data.SqlClient** version **4.7.0**, **Microsoft.ML.Experimental** version **0.16.0-preview2**, and **Microsoft.ML.TimeSeries** version **1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="93ad1-139">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="93ad1-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="93ad1-140">Vytvořte adresář s názvem *data*.</span><span class="sxs-lookup"><span data-stu-id="93ad1-140">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="93ad1-141">Stáhněte [soubor databáze *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) a uložte ho do *datového* adresáře.</span><span class="sxs-lookup"><span data-stu-id="93ad1-141">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="93ad1-142">Data použitá v tomto kurzu pocházejí z [datové sady pro sdílení kol UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="93ad1-142">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="93ad1-143">Fanaee-T, hadi a gama, Joao, "označování událostí kombinující detektory kompletu a znalosti na pozadí", pokrok v umělých Intelligencech (2013): PP. 1-15, Springer Berlín Heidelberg, [webový odkaz](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="93ad1-143">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="93ad1-144">Původní datová sada obsahuje několik sloupců, které odpovídají sezónnost a počasí.</span><span class="sxs-lookup"><span data-stu-id="93ad1-144">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="93ad1-145">Pro zkrácení, protože algoritmus používaný v tomto kurzu vyžaduje jenom hodnoty z jednoho číselného sloupce, původní datová sada byla zúžená, aby zahrnovala jenom tyto sloupce:</span><span class="sxs-lookup"><span data-stu-id="93ad1-145">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>  

- <span data-ttu-id="93ad1-146">**dteday**: datum pozorování.</span><span class="sxs-lookup"><span data-stu-id="93ad1-146">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="93ad1-147">**year**: kódovaný rok sledování (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="93ad1-147">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="93ad1-148">**CNT**: celkový počet pronajatých kol za tento den.</span><span class="sxs-lookup"><span data-stu-id="93ad1-148">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="93ad1-149">Původní datová sada je namapována na databázovou tabulku s následujícím schématem ve SQL Server databázi.</span><span class="sxs-lookup"><span data-stu-id="93ad1-149">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="93ad1-150">Následuje ukázka dat:</span><span class="sxs-lookup"><span data-stu-id="93ad1-150">The following is a sample of the data:</span></span>

| <span data-ttu-id="93ad1-151">RentalDate</span><span class="sxs-lookup"><span data-stu-id="93ad1-151">RentalDate</span></span> | <span data-ttu-id="93ad1-152">Rok</span><span class="sxs-lookup"><span data-stu-id="93ad1-152">Year</span></span> | <span data-ttu-id="93ad1-153">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="93ad1-153">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="93ad1-154">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="93ad1-154">1/1/2011</span></span>|<span data-ttu-id="93ad1-155">0,8</span><span class="sxs-lookup"><span data-stu-id="93ad1-155">0</span></span>|<span data-ttu-id="93ad1-156">985</span><span class="sxs-lookup"><span data-stu-id="93ad1-156">985</span></span>|
|<span data-ttu-id="93ad1-157">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="93ad1-157">1/2/2011</span></span>|<span data-ttu-id="93ad1-158">0,8</span><span class="sxs-lookup"><span data-stu-id="93ad1-158">0</span></span>|<span data-ttu-id="93ad1-159">801</span><span class="sxs-lookup"><span data-stu-id="93ad1-159">801</span></span>|
|<span data-ttu-id="93ad1-160">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="93ad1-160">1/3/2011</span></span>|<span data-ttu-id="93ad1-161">0,8</span><span class="sxs-lookup"><span data-stu-id="93ad1-161">0</span></span>|<span data-ttu-id="93ad1-162">1349</span><span class="sxs-lookup"><span data-stu-id="93ad1-162">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="93ad1-163">Vytvoření vstupní a výstupní třídy</span><span class="sxs-lookup"><span data-stu-id="93ad1-163">Create input and output classes</span></span>

1. <span data-ttu-id="93ad1-164">Otevřete soubor *program.cs* a nahraďte existující příkazy `using` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="93ad1-164">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="93ad1-165">Vytvořte třídu `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-165">Create `ModelInput` class.</span></span> <span data-ttu-id="93ad1-166">Pod `Program` třídy přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="93ad1-166">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]    

    <span data-ttu-id="93ad1-167">Třída `ModelInput` obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="93ad1-167">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="93ad1-168">**RentalDate**: datum pozorování.</span><span class="sxs-lookup"><span data-stu-id="93ad1-168">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="93ad1-169">**Year**: kódovaný rok sledování (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="93ad1-169">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="93ad1-170">**TotalRentals**: celkový počet pronajatých kol za tento den.</span><span class="sxs-lookup"><span data-stu-id="93ad1-170">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="93ad1-171">Vytvořte třídu `ModelOutput` pod nově vytvořenou `ModelInput` třídou.</span><span class="sxs-lookup"><span data-stu-id="93ad1-171">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="93ad1-172">Třída `ModelOutput` obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="93ad1-172">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="93ad1-173">**ForecastedRentals**: předpokládané hodnoty pro období prognózy.</span><span class="sxs-lookup"><span data-stu-id="93ad1-173">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="93ad1-174">**LowerBoundRentals**: předpokládané minimální hodnoty pro období prognózy.</span><span class="sxs-lookup"><span data-stu-id="93ad1-174">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="93ad1-175">**UpperBoundRentals**: předpokládané maximální hodnoty pro období prognózy.</span><span class="sxs-lookup"><span data-stu-id="93ad1-175">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="93ad1-176">Definování cest a inicializovat proměnné</span><span class="sxs-lookup"><span data-stu-id="93ad1-176">Define paths and initialize variables</span></span>

1. <span data-ttu-id="93ad1-177">V rámci metody `Main` Definujte proměnné pro ukládání umístění vašich dat, připojovací řetězec a místo, kam se má vyškolený model Uložit.</span><span class="sxs-lookup"><span data-stu-id="93ad1-177">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="93ad1-178">Inicializujte `mlContext` proměnnou novou instancí [`MLContext`](xref:Microsoft.ML.MLContext) přidáním následujícího řádku do metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-178">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="93ad1-179">Třída [`MLContext`](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace mlContext vytvoří nové prostředí ml.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="93ad1-179">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="93ad1-180">Je podobné, koncepčně, `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="93ad1-180">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="93ad1-181">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="93ad1-181">Load the data</span></span>

1. <span data-ttu-id="93ad1-182">Vytvoří `DatabaseLoader`, který načte záznamy typu `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-182">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="93ad1-183">Definujte dotaz pro načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="93ad1-183">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="93ad1-184">ML.NET algoritmy očekávají, že data jsou typu [`Single`](xref:System.Single).</span><span class="sxs-lookup"><span data-stu-id="93ad1-184">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="93ad1-185">Z toho vyplývá, že číselné hodnoty pocházející z databáze, které nejsou typu [`Real`](xref:System.Data.SqlDbType), mají hodnotu s plovoucí desetinnou čárkou s jednoduchou přesností, která musí být převedena na [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="93ad1-185">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> 

    <span data-ttu-id="93ad1-186">Sloupce `Year` a `TotalRental` jsou v databázi typu Integer.</span><span class="sxs-lookup"><span data-stu-id="93ad1-186">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="93ad1-187">Pomocí `CAST` vestavěné funkce jsou obě přetypování do `Real`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-187">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="93ad1-188">Vytvořte `DatabaseSource` pro připojení k databázi a spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-188">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="93ad1-189">Načtěte data do `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-189">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="93ad1-190">Datová sada obsahuje dva roky s daty.</span><span class="sxs-lookup"><span data-stu-id="93ad1-190">The dataset contains two years worth of data.</span></span> <span data-ttu-id="93ad1-191">Pro školení se použijí jenom data z prvního roku, druhý rok se porovná s porovnáním skutečných hodnot s prognózou vytvořenou modelem.</span><span class="sxs-lookup"><span data-stu-id="93ad1-191">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="93ad1-192">Filtrujte data pomocí [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transformace.</span><span class="sxs-lookup"><span data-stu-id="93ad1-192">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span> 

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="93ad1-193">Pro první rok jsou vybrány pouze hodnoty ve sloupci `Year` méně než 1 nastavením parametru `upperBound` na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="93ad1-193">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="93ad1-194">Naopak pro druhý rok jsou hodnoty větší než nebo rovny 1 vybrány nastavením parametru `lowerBound` na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="93ad1-194">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="93ad1-195">Definování kanálu analýzy časové řady</span><span class="sxs-lookup"><span data-stu-id="93ad1-195">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="93ad1-196">Definujte kanál, který používá [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) k předpovědi hodnot v datové sadě časových řad.</span><span class="sxs-lookup"><span data-stu-id="93ad1-196">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="93ad1-197">`forecastingPipeline` přebírá 365 datových bodů za první rok a ukázky nebo rozdělí datovou sadu do 30 dnů (měsíčně) intervalů určených parametrem `seriesLength`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-197">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="93ad1-198">Každá z těchto ukázek je analyzována v týdenním nebo 7 denním intervalu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-198">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="93ad1-199">Při určování toho, jaká hodnota předpovědi je pro další období, se pro vytvoření předpovědi použijí hodnoty z předchozích sedmi dnů.</span><span class="sxs-lookup"><span data-stu-id="93ad1-199">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="93ad1-200">Model je nastaven na předpověď sedmi teček do budoucna, jak je definováno parametrem `horizon`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-200">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="93ad1-201">Vzhledem k tomu, že prognóza je včas odhad, není vždy 100% přesná.</span><span class="sxs-lookup"><span data-stu-id="93ad1-201">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="93ad1-202">Proto je dobré znát rozsah hodnot ve scénářích nejlepšího a nejhoršího případu, jak jsou definovány horní a dolní mezí.</span><span class="sxs-lookup"><span data-stu-id="93ad1-202">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="93ad1-203">V takovém případě je úroveň spolehlivosti pro dolní a horní mez nastavena na 95%.</span><span class="sxs-lookup"><span data-stu-id="93ad1-203">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="93ad1-204">Úroveň spolehlivosti se proto dá zvýšit nebo snížit.</span><span class="sxs-lookup"><span data-stu-id="93ad1-204">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="93ad1-205">Čím vyšší je hodnota, tím širší je rozsah mezi horní a dolní mezí, abyste dosáhli požadované úrovně důvěry.</span><span class="sxs-lookup"><span data-stu-id="93ad1-205">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span> 

1. <span data-ttu-id="93ad1-206">Použijte metodu [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) pro výuku modelu a přizpůsobení dat dříve definovaným `forecastingPipeline`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-206">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="93ad1-207">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="93ad1-207">Evaluate the model</span></span>

<span data-ttu-id="93ad1-208">Vyhodnoťte, jak dobře se model provádí prognózou dat z následujícího roku a porovnáním s aktuálními hodnotami.</span><span class="sxs-lookup"><span data-stu-id="93ad1-208">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="93ad1-209">Pod metodu `Main` vytvořte novou metodu Utility nazvanou `Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-209">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {
        
    }
    ```

1. <span data-ttu-id="93ad1-210">V rámci metody `Evaluate` vypovídat data druhého roku pomocí metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) s školeným modelem.</span><span class="sxs-lookup"><span data-stu-id="93ad1-210">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="93ad1-211">Získat skutečné hodnoty z dat pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="93ad1-211">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="93ad1-212">Získejte hodnoty předpovědi pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="93ad1-212">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="93ad1-213">Vypočítá rozdíl mezi skutečnými a předpověď hodnotami, které se běžně označují jako chyba.</span><span class="sxs-lookup"><span data-stu-id="93ad1-213">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="93ad1-214">Změřte výkon tím, že vypočítají střední absolutní chybu a hlavní střední hodnoty chyb.</span><span class="sxs-lookup"><span data-stu-id="93ad1-214">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="93ad1-215">K vyhodnocení výkonu se použijí následující metriky:</span><span class="sxs-lookup"><span data-stu-id="93ad1-215">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="93ad1-216">**Střední absolutní chyba**: měří, jak blízkoa předpovědi je skutečná hodnota.</span><span class="sxs-lookup"><span data-stu-id="93ad1-216">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="93ad1-217">Rozsah hodnot je od 0 do nekonečno.</span><span class="sxs-lookup"><span data-stu-id="93ad1-217">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="93ad1-218">Nejblíže k 0, což je lepší kvalita modelu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-218">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="93ad1-219">**Hlavní střední hodnota: Chyba na čtverci**: shrnuje chybu thhe v modelu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-219">**Root Mean Squared Error**: Summarizes thhe error in the model.</span></span> <span data-ttu-id="93ad1-220">Rozsah hodnot je od 0 do nekonečno.</span><span class="sxs-lookup"><span data-stu-id="93ad1-220">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="93ad1-221">Nejblíže k 0, což je lepší kvalita modelu.</span><span class="sxs-lookup"><span data-stu-id="93ad1-221">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="93ad1-222">Výstup metrik do konzoly.</span><span class="sxs-lookup"><span data-stu-id="93ad1-222">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="93ad1-223">Použijte metodu `Evaluate` v rámci metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-223">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="93ad1-224">Uložit model</span><span class="sxs-lookup"><span data-stu-id="93ad1-224">Save the model</span></span>

<span data-ttu-id="93ad1-225">Pokud jste s modelem spokojeni, uložte ho pro pozdější použití v jiných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="93ad1-225">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="93ad1-226">V metodě `Main` vytvořte [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="93ad1-226">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="93ad1-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) je pohodlnější způsob, jak vytvořit jeden předpovědi.</span><span class="sxs-lookup"><span data-stu-id="93ad1-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="93ad1-228">Uložte model do souboru s názvem `MLModel.zip`, jak je určeno dříve definovanou `modelPath` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="93ad1-228">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="93ad1-229">K uložení modelu použijte metodu [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) .</span><span class="sxs-lookup"><span data-stu-id="93ad1-229">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="93ad1-230">Použití modelu k prognózování poptávky</span><span class="sxs-lookup"><span data-stu-id="93ad1-230">Use the model to forecast demand</span></span>

1. <span data-ttu-id="93ad1-231">Pod metodu `Evaluate` vytvořte novou metodu Utility nazvanou `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-231">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="93ad1-232">V rámci metody `Forecast` použijte k předpovědi nájemné za dalších sedm dní metodu [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) .</span><span class="sxs-lookup"><span data-stu-id="93ad1-232">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="93ad1-233">Zarovnejte hodnoty skutečných hodnot a prognózy pro sedm teček.</span><span class="sxs-lookup"><span data-stu-id="93ad1-233">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="93ad1-234">Iterujte ve výstupu předpovědi a zobrazte ji v konzole.</span><span class="sxs-lookup"><span data-stu-id="93ad1-234">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="93ad1-235">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="93ad1-235">Run the application</span></span>

1. <span data-ttu-id="93ad1-236">Uvnitř metody `Main` volejte metodu `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="93ad1-236">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="93ad1-237">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="93ad1-237">Run the application.</span></span> <span data-ttu-id="93ad1-238">Výstup podobný tomuto: by měl být zobrazený v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="93ad1-238">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="93ad1-239">V případě zkrácení byl výstup zúžený.</span><span class="sxs-lookup"><span data-stu-id="93ad1-239">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="93ad1-240">Kontrola skutečných a předpokládaných hodnot zobrazuje následující vztahy:</span><span class="sxs-lookup"><span data-stu-id="93ad1-240">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Aktuální porovnání předpovědi vs.](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="93ad1-242">I když hodnoty prognózy nepředpověď nad přesný počet nájemného, poskytují přesnější rozsah hodnot, který umožňuje operaci optimalizace používání prostředků.</span><span class="sxs-lookup"><span data-stu-id="93ad1-242">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span> 

<span data-ttu-id="93ad1-243">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="93ad1-243">Congratulations!</span></span> <span data-ttu-id="93ad1-244">Teď jste úspěšně vytvořili model strojového učení s časovou řadou k prognózování poptávky po pronájmu kol.</span><span class="sxs-lookup"><span data-stu-id="93ad1-244">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="93ad1-245">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .</span><span class="sxs-lookup"><span data-stu-id="93ad1-245">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="93ad1-246">Další kroky</span><span class="sxs-lookup"><span data-stu-id="93ad1-246">Next steps</span></span>

- [<span data-ttu-id="93ad1-247">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="93ad1-247">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="93ad1-248">Zvýšit přesnost modelu</span><span class="sxs-lookup"><span data-stu-id="93ad1-248">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
