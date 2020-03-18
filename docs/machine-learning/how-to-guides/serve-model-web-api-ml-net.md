---
title: Nasazení modelu v ASP.NET základního webového rozhraní API
description: Obsluhovat ML.NET model strojového učení analýzy mínění přes internet pomocí ASP.NET Core Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398928"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="b40a5-103">Nasazení modelu v ASP.NET základního webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b40a5-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="b40a5-104">Naučte se, jak sloužit předem vyškolený ML.NET model strojového učení na webu pomocí ASP.NET základní webové rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b40a5-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="b40a5-105">Obsluha modelu přes webové rozhraní API umožňuje předpovědi prostřednictvím standardních metod HTTP.</span><span class="sxs-lookup"><span data-stu-id="b40a5-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b40a5-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b40a5-106">Prerequisites</span></span>

- <span data-ttu-id="b40a5-107">[Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".</span><span class="sxs-lookup"><span data-stu-id="b40a5-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="b40a5-108">Powershell.</span><span class="sxs-lookup"><span data-stu-id="b40a5-108">Powershell.</span></span>
- <span data-ttu-id="b40a5-109">Předem vycvičený model.</span><span class="sxs-lookup"><span data-stu-id="b40a5-109">Pre-trained model.</span></span> <span data-ttu-id="b40a5-110">Použijte [kurz ML.NET analýzy mínění](../tutorials/sentiment-analysis.md) k vytvoření vlastního modelu nebo ke stažení tohoto [předem vytrénovaného modelu strojového učení analýzy mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="b40a5-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="b40a5-111">Vytvořit ASP.NET projekt základního webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b40a5-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="b40a5-112">Otevřete sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b40a5-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="b40a5-113">Na řádku nabídek vyberte **Soubor > Nový > project.**</span><span class="sxs-lookup"><span data-stu-id="b40a5-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="b40a5-114">V dialogovém okně Nový projekt vyberte uzel **Visual C#** následovaný **webovým** uzlem.</span><span class="sxs-lookup"><span data-stu-id="b40a5-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="b40a5-115">Pak vyberte šablonu projektu **ASP.NET core webová aplikace.**</span><span class="sxs-lookup"><span data-stu-id="b40a5-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="b40a5-116">Do textového pole **Název** zadejte "SentimentAnalysisWebAPI" a vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="b40a5-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="b40a5-117">V okně, které zobrazuje různé typy ASP.NET základní projekty, vyberte **rozhraní API** a vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="b40a5-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="b40a5-118">Vytvořte adresář s názvem *MLModels* v projektu pro uložení předem sestavených souborů modelů strojového učení:</span><span class="sxs-lookup"><span data-stu-id="b40a5-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="b40a5-119">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > novou složku.</span><span class="sxs-lookup"><span data-stu-id="b40a5-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="b40a5-120">Zadejte "MLModels" a stiskněte enter.</span><span class="sxs-lookup"><span data-stu-id="b40a5-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="b40a5-121">Nainstalujte **balíček nuget Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b40a5-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="b40a5-122">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b40a5-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b40a5-123">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte tlačítko Instalovat.</span><span class="sxs-lookup"><span data-stu-id="b40a5-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="b40a5-124">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně Přijetí licence vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="b40a5-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="b40a5-125">Nainstalujte **balíček Microsoft.Extensions.ML Nuget**:</span><span class="sxs-lookup"><span data-stu-id="b40a5-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="b40a5-126">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b40a5-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b40a5-127">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a vyberte tlačítko Instalovat.</span><span class="sxs-lookup"><span data-stu-id="b40a5-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="b40a5-128">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně Přijetí licence vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="b40a5-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="b40a5-129">Přidání modelu do projektu ASP.NET základního webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b40a5-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="b40a5-130">Zkopírování předem sestaveného modelu do adresáře *MLModels*</span><span class="sxs-lookup"><span data-stu-id="b40a5-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="b40a5-131">V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor zip modelu a vyberte Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b40a5-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="b40a5-132">V části Upřesnit změňte hodnotu Kopírovat do výstupního adresáře, pokud je novější.</span><span class="sxs-lookup"><span data-stu-id="b40a5-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="b40a5-133">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="b40a5-133">Create data models</span></span>

<span data-ttu-id="b40a5-134">Je třeba vytvořit některé třídy pro vaše vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b40a5-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="b40a5-135">Přidání nové třídy do projektu:</span><span class="sxs-lookup"><span data-stu-id="b40a5-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="b40a5-136">Vytvořte adresář s názvem *DataModels* v projektu pro uložení datových modelů:</span><span class="sxs-lookup"><span data-stu-id="b40a5-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="b40a5-137">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > novou složku.</span><span class="sxs-lookup"><span data-stu-id="b40a5-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="b40a5-138">Zadejte "DataModels" a stiskněte **klávesu Enter**.</span><span class="sxs-lookup"><span data-stu-id="b40a5-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="b40a5-139">V Průzkumníku řešení klikněte pravým tlačítkem myši na adresář *DataModels* a potom vyberte Přidat > novou položku.</span><span class="sxs-lookup"><span data-stu-id="b40a5-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="b40a5-140">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b40a5-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="b40a5-141">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="b40a5-141">Then, select the **Add** button.</span></span> <span data-ttu-id="b40a5-142">Soubor *SentimentData.cs* se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="b40a5-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="b40a5-143">Přidejte následující příkaz using na začátek *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b40a5-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="b40a5-144">Odeberte existující definici třídy a do **souboru SentimentData.cs** přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b40a5-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="b40a5-145">V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *DataModels* a pak vyberte **příkaz Přidat > novou položku**.</span><span class="sxs-lookup"><span data-stu-id="b40a5-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="b40a5-146">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="b40a5-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="b40a5-147">Potom vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="b40a5-147">Then, select the Add button.</span></span> <span data-ttu-id="b40a5-148">Soubor *SentimentPrediction.cs* se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="b40a5-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="b40a5-149">Přidejte následující příkaz using na začátek *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="b40a5-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="b40a5-150">Odeberte existující definici třídy a přidejte do *SentimentPrediction.cs* souboru následující kód:</span><span class="sxs-lookup"><span data-stu-id="b40a5-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="b40a5-151">`SentimentPrediction`dědí `SentimentData`od .</span><span class="sxs-lookup"><span data-stu-id="b40a5-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="b40a5-152">To usnadňuje zobrazení původních dat `SentimentText` ve vlastnosti spolu s výstupem generovaným modelem.</span><span class="sxs-lookup"><span data-stu-id="b40a5-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="b40a5-153">Registrovat PredictionEnginePool pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="b40a5-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="b40a5-154">Chcete-li provést jednu předpověď, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musíte vytvořit .</span><span class="sxs-lookup"><span data-stu-id="b40a5-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="b40a5-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="b40a5-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="b40a5-156">Navíc je nutné vytvořit instanci všude, kde je potřeba v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="b40a5-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="b40a5-157">Jak vaše aplikace roste, tento proces může být nezvladatelný.</span><span class="sxs-lookup"><span data-stu-id="b40a5-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="b40a5-158">Pro zvýšení výkonu a bezpečnosti podprocesů použijte `PredictionEnginePool` kombinaci vkládání [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) závislostí a služby, která vytvoří objekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b40a5-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="b40a5-159">Následující odkaz obsahuje další informace, pokud se chcete dozvědět více o [vkládání závislostí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="b40a5-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="b40a5-160">Otevřete *Startup.cs* třídu a přidejte do horní části souboru následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="b40a5-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="b40a5-161">Přidejte následující kód do metody *ConfigureServices:*</span><span class="sxs-lookup"><span data-stu-id="b40a5-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="b40a5-162">Na vysoké úrovni tento kód inicializuje objekty a služby automaticky pro pozdější použití na požádání aplikace namísto nutnosti ručně provést.</span><span class="sxs-lookup"><span data-stu-id="b40a5-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="b40a5-163">Modely strojového učení nejsou statické.</span><span class="sxs-lookup"><span data-stu-id="b40a5-163">Machine learning models are not static.</span></span> <span data-ttu-id="b40a5-164">Jako nová trénovací data k dispozici, model je retrained a znovu nasadit.</span><span class="sxs-lookup"><span data-stu-id="b40a5-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="b40a5-165">Jedním ze způsobů, jak získat nejnovější verzi modelu do aplikace, je znovu nasadit celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b40a5-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="b40a5-166">To však zavádí prostoje aplikace.</span><span class="sxs-lookup"><span data-stu-id="b40a5-166">However, this introduces application downtime.</span></span> <span data-ttu-id="b40a5-167">Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti snížit počet aplikací.</span><span class="sxs-lookup"><span data-stu-id="b40a5-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="b40a5-168">Nastavte `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) spustí, který naslouchá systému souborů změnit oznámení a vyvolá události, když dojde ke změně souboru.</span><span class="sxs-lookup"><span data-stu-id="b40a5-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="b40a5-169">To vyzve `PredictionEnginePool` k automatickému opětovnému načtení modelu.</span><span class="sxs-lookup"><span data-stu-id="b40a5-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="b40a5-170">Model je identifikován `modelName` parametrem tak, aby více než jeden model na aplikaci lze znovu načíst při změně.</span><span class="sxs-lookup"><span data-stu-id="b40a5-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="b40a5-171">Alternativně můžete použít `FromUri` metodu při práci s modely uloženými vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="b40a5-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="b40a5-172">Místo sledování změn souborů `FromUri` se vyhodnoťuje změny ve vzdáleném umístění.</span><span class="sxs-lookup"><span data-stu-id="b40a5-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="b40a5-173">Interval dotazování je výchozí na 5 minut.</span><span class="sxs-lookup"><span data-stu-id="b40a5-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="b40a5-174">Můžete zvýšit nebo snížit interval dotazování na základě požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b40a5-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="b40a5-175">V ukázce `PredictionEnginePool` kódu níže uskutečuje model uložený na zadaném identifikátoru URI každou minutu.</span><span class="sxs-lookup"><span data-stu-id="b40a5-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="b40a5-176">Vytvořit řadič predict</span><span class="sxs-lookup"><span data-stu-id="b40a5-176">Create Predict controller</span></span>

<span data-ttu-id="b40a5-177">Chcete-li zpracovat příchozí požadavky HTTP, vytvořte řadič.</span><span class="sxs-lookup"><span data-stu-id="b40a5-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="b40a5-178">V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *Řadiče* a potom vyberte **příkaz Přidat > řadič .**</span><span class="sxs-lookup"><span data-stu-id="b40a5-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="b40a5-179">V dialogovém okně **Přidat novou položku** vyberte **Řadič rozhraní API Prázdný** a vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="b40a5-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="b40a5-180">V řádku změňte pole **Název řadiče** na *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="b40a5-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="b40a5-181">Potom vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="b40a5-181">Then, select the Add button.</span></span> <span data-ttu-id="b40a5-182">V editoru kódu se otevře *soubor PredictController.cs.*</span><span class="sxs-lookup"><span data-stu-id="b40a5-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="b40a5-183">Přidejte následující příkaz using na začátek *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="b40a5-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="b40a5-184">Odeberte existující definici třídy a do *PredictController.cs* souboru přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b40a5-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="b40a5-185">Tento kód přiřadí `PredictionEnginePool` předáním konstruktoru řadiče, který získáte prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="b40a5-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="b40a5-186">`Predict` Potom `Post` metoda řadiče používá `PredictionEnginePool` k předpovědi pomocí `SentimentAnalysisModel` registrované `Startup` ve třídě a vrátí výsledky zpět uživateli v případě úspěchu.</span><span class="sxs-lookup"><span data-stu-id="b40a5-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="b40a5-187">Testování webového rozhraní API místně</span><span class="sxs-lookup"><span data-stu-id="b40a5-187">Test web API locally</span></span>

<span data-ttu-id="b40a5-188">Jakmile je vše nastaveno, je čas otestovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b40a5-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="b40a5-189">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b40a5-189">Run the application.</span></span>
1. <span data-ttu-id="b40a5-190">Otevřete powershell a zadejte následující kód, kde PORT je port, na kterém vaše aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="b40a5-190">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="b40a5-191">V případě úspěchu by výstup měl vypadat podobně jako v níže uvedeném textu:</span><span class="sxs-lookup"><span data-stu-id="b40a5-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="b40a5-192">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="b40a5-192">Congratulations!</span></span> <span data-ttu-id="b40a5-193">Úspěšně jste obsluhovali model, abyste mohli provádět předpovědi přes Internet pomocí ASP.NET základního webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b40a5-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b40a5-194">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b40a5-194">Next Steps</span></span>

- [<span data-ttu-id="b40a5-195">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="b40a5-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
