---
title: Nasazení modelu ML.NET na službu Azure Functions
description: Poskytování ML.NET mínění analýzy modelu strojového učení pro predikci přes internet pomocí služby Azure Functions
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4681b37da64097dd8e537b4c956917277ecff96b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330633"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a><span data-ttu-id="65ff2-103">Postupy: Použití ML.NET modelu ve službě Azure Functions</span><span class="sxs-lookup"><span data-stu-id="65ff2-103">How-To: Use ML.NET Model in Azure Functions</span></span>

<span data-ttu-id="65ff2-104">Tento návod ukazuje, jak jednotlivé předpovědi je možné provádět pomocí předem sestavených ML.NET model strojového učení prostřednictvím Internetu v prostředí bez serveru, třeba Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="65ff2-104">This how-to shows how individual predictions can be made using a pre-built ML.NET machine learning model through the internet in a serverless environment such as Azure Functions.</span></span>

> [!NOTE]
> <span data-ttu-id="65ff2-105">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="65ff2-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="65ff2-106">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="65ff2-106">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="65ff2-107">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-107">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="65ff2-108">Další informace najdete v tématu poznámky k verzi v [úložišti dotnet/machinelearning githubu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="65ff2-108">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65ff2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65ff2-109">Prerequisites</span></span>

- <span data-ttu-id="65ff2-110">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) úlohy "Vývoj pro různé platformy .NET Core" a "Vývoj pro Azure" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="65ff2-110">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span> 
- [<span data-ttu-id="65ff2-111">Nástroje Azure Functions</span><span class="sxs-lookup"><span data-stu-id="65ff2-111">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="65ff2-112">Powershell</span><span class="sxs-lookup"><span data-stu-id="65ff2-112">Powershell</span></span>
- <span data-ttu-id="65ff2-113">Předem natrénovaných modelů.</span><span class="sxs-lookup"><span data-stu-id="65ff2-113">Pre-trained model.</span></span> 
    - <span data-ttu-id="65ff2-114">Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestaví vlastní model.</span><span class="sxs-lookup"><span data-stu-id="65ff2-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="65ff2-115">Stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="65ff2-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="65ff2-116">Vytvoření projektu Azure Functions</span><span class="sxs-lookup"><span data-stu-id="65ff2-116">Create Azure Functions Project</span></span>

1. <span data-ttu-id="65ff2-117">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="65ff2-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="65ff2-118">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="65ff2-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="65ff2-119">V **nový projekt** dialogového okna, vyberte **Visual C#**  uzel, za nímž následuje **cloudu** uzlu.</span><span class="sxs-lookup"><span data-stu-id="65ff2-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="65ff2-120">Vyberte **Azure Functions** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="65ff2-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="65ff2-121">V **název** textového pole zadejte "SentimentAnalysisFunctionsApp" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65ff2-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="65ff2-122">V **nový projekt** dialogového okna, otevřete rozevírací seznam nahoře možnosti projektu a vyberte **Azure Functions v2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="65ff2-123">Vyberte **triggeru Http** projektu a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65ff2-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="65ff2-124">Vytvořte adresář *MLModels* ve vašem projektu a uložit model:</span><span class="sxs-lookup"><span data-stu-id="65ff2-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="65ff2-125">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="65ff2-126">Zadejte "MLModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="65ff2-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="65ff2-127">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="65ff2-127">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="65ff2-128">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="65ff2-129">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65ff2-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="65ff2-130">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="65ff2-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-built-model-to-project"></a><span data-ttu-id="65ff2-131">Přidat do projektu předem sestavených modelů</span><span class="sxs-lookup"><span data-stu-id="65ff2-131">Add Pre-built Model To Project</span></span>

1. <span data-ttu-id="65ff2-132">Zkopírujte předem sestavených model *MLModels* složky.</span><span class="sxs-lookup"><span data-stu-id="65ff2-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="65ff2-133">V Průzkumníku řešení klikněte pravým tlačítkem na soubor předem sestavených modelů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="65ff2-134">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-function-to-analyze-sentiment"></a><span data-ttu-id="65ff2-135">Vytvoření funkce pro analýzu mínění</span><span class="sxs-lookup"><span data-stu-id="65ff2-135">Create Function to Analyze Sentiment</span></span>

<span data-ttu-id="65ff2-136">Vytvoření třídy k předpovědi mínění.</span><span class="sxs-lookup"><span data-stu-id="65ff2-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="65ff2-137">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="65ff2-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="65ff2-138">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="65ff2-139">V **přidat novou položku** dialogu **funkce Azure Functions** a změnit **název** pole *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="65ff2-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="65ff2-140">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65ff2-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="65ff2-141">V **novou funkci Azure Functions** dialogu **triggeru Http**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="65ff2-142">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65ff2-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="65ff2-143">*AnalyzeSentiment.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="65ff2-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="65ff2-144">Přidejte následující `using` příkaz do horní části *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="65ff2-144">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using Newtonsoft.Json;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a><span data-ttu-id="65ff2-145">Vytvoření datových modelů</span><span class="sxs-lookup"><span data-stu-id="65ff2-145">Create Data Models</span></span>

<span data-ttu-id="65ff2-146">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="65ff2-146">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="65ff2-147">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="65ff2-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="65ff2-148">Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů: V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-148">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="65ff2-149">Zadejte "DataModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="65ff2-149">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="65ff2-150">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-150">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="65ff2-151">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="65ff2-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="65ff2-152">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65ff2-152">Then, select the **Add** button.</span></span> <span data-ttu-id="65ff2-153">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="65ff2-153">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="65ff2-154">Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="65ff2-154">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="65ff2-155">Odeberte stávající definice třídy a přidejte následující kód do souboru SentimentData.cs:</span><span class="sxs-lookup"><span data-stu-id="65ff2-155">Remove the existing class definition and add the following code to the SentimentData.cs file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. <span data-ttu-id="65ff2-156">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="65ff2-156">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="65ff2-157">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="65ff2-157">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="65ff2-158">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65ff2-158">Then, select the **Add** button.</span></span> <span data-ttu-id="65ff2-159">*SentimentPrediction.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="65ff2-159">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="65ff2-160">Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="65ff2-160">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="65ff2-161">Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="65ff2-161">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a><span data-ttu-id="65ff2-162">Přidání logiky Predikcí</span><span class="sxs-lookup"><span data-stu-id="65ff2-162">Add Prediction Logic</span></span>

<span data-ttu-id="65ff2-163">Nahraďte stávající implementaci *spustit* metoda *AnalyzeSentiment* třídy následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="65ff2-163">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a><span data-ttu-id="65ff2-164">Místní test</span><span class="sxs-lookup"><span data-stu-id="65ff2-164">Test Locally</span></span>

<span data-ttu-id="65ff2-165">Teď, když je všechno nastavené, je čas k otestování aplikace:</span><span class="sxs-lookup"><span data-stu-id="65ff2-165">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="65ff2-166">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="65ff2-166">Run the application</span></span>
1. <span data-ttu-id="65ff2-167">Otevřete PowerShell a zobrazený kód zadejte do řádku, kde je port vaše aplikace běží na.</span><span class="sxs-lookup"><span data-stu-id="65ff2-167">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="65ff2-168">Port, který je obvykle 7071.</span><span class="sxs-lookup"><span data-stu-id="65ff2-168">Typically the port is 7071.</span></span> 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="65ff2-169">V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="65ff2-169">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="65ff2-170">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="65ff2-170">Congratulations!</span></span> <span data-ttu-id="65ff2-171">Jste úspěšně obsluhovat model k predikci přes internet pomocí funkce Azure functions.</span><span class="sxs-lookup"><span data-stu-id="65ff2-171">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="65ff2-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="65ff2-172">Next Steps</span></span>

- [<span data-ttu-id="65ff2-173">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="65ff2-173">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)