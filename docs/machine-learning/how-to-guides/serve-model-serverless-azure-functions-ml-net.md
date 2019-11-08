---
title: Nasazení modelu do Azure Functions
description: Obsluha modelu ML.NET mínění Analysis Machine Learning pro předpověď přes Internet pomocí Azure Functions
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 5ef6331950845b2900e33b2c51c308644ba17fd6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733349"
---
# <a name="deploy-a-model-to-azure-functions"></a>Nasazení modelu do Azure Functions

Naučte se, jak nasadit předem vyškolený model ML.NET Machine Learning pro předpovědi přes protokol HTTP prostřednictvím prostředí bez serveru Azure Functions.

> [!NOTE]
> Tato ukázka spustí verzi Preview služby `PredictionEnginePool`.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "vývoj pro různé platformy .NET Core" a "vývoj pro Azure".
- [Nástroje Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Prostředí
- Předem vyškolený model. Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s představitelnou mínění analýzou](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) .

## <a name="azure-functions-sample-overview"></a>Přehled ukázek Azure Functions

Tato ukázka je  **C# triggerem http Azure Functions aplikaci** , která používá předmínění binární klasifikační model pro kategorizaci textu jako kladné nebo záporné. Azure Functions poskytuje snadný způsob, jak na spravovaném prostředí bez serveru v cloudu spouštět malé části kódu se škálováním. Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) na GitHubu.

## <a name="create-azure-functions-project"></a>Vytvořit Azure Functions projekt

1. Otevřete Visual Studio 2017. Z řádku nabídek vyberte **soubor** > **Nový** **projekt**  > . V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **cloudu** . Pak vyberte šablonu projektu **Azure Functions** . Do textového pole **název** zadejte "SentimentAnalysisFunctionsApp" a pak vyberte tlačítko **OK** .
1. V dialogovém okně **Nový projekt** otevřete rozevírací seznam nad možnostmi projektu a vyberte **Azure Functions v2 (.NET Core)** . Pak vyberte projekt **triggeru http** a pak klikněte na tlačítko **OK** .
1. Vytvořte v projektu adresář s názvem *MLModels* a uložte svůj model:

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **přidat** **novou složku** > . Zadejte "MLModels" a stiskněte klávesu ENTER.

1. Nainstalujte **balíček NuGet Microsoft.ml** verze **1.3.1**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

1. Nainstalujte **balíček NuGet Microsoft. Azure. Functions. Extensions**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft. Azure. Functions. Extensions**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

1. Nainstalujte **balíček NuGet Microsoft.Extensions.ml** verze **0.15.1**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

1. Nainstalujte **balíček NuGet Microsoft. NET. SDK. Functions** verze **1.0.28 +** :

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu nainstalované, vyhledejte **Microsoft. NET. SDK. Functions**, vyberte tento balíček v seznamu, vyberte v rozevírací nabídce verze možnost **1.0.28 nebo novější** a klikněte na tlačítko **aktualizovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

## <a name="add-pre-trained-model-to-project"></a>Přidat předem vyškolený model do projektu

1. Do složky *MLModels* zkopírujte předem sestavený model.
1. V Průzkumník řešení klikněte pravým tlačítkem na předem sestavený soubor modelu a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Vytvoření funkce Azure pro analýzu mínění

Vytvořte třídu pro předpověď mínění. Přidejte do projektu novou třídu:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .

1. V dialogovém okně **Přidat novou položku** vyberte možnost **Azure Functions** a změňte pole **název** na *AnalyzeSentiment.cs*. Pak vyberte tlačítko **Přidat** .

1. V dialogovém okně **Nová funkce Azure** vyberte **Trigger http**. Pak vyberte tlačítko **OK** .

    V editoru kódu se otevře soubor *AnalyzeSentiment.cs* . Přidejte následující příkaz `using` do horní části *AnalyzeSentiment.cs*:

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Ve výchozím nastavení je třída `AnalyzeSentiment` `static`. Nezapomeňte z definice třídy odebrat klíčové slovo `static`.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Vytváření datových modelů

Musíte vytvořit některé třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

1. Vytvořte v projektu adresář s názvem *Datamodels* pro uložení datových modelů: v Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**. Zadejte "datamodels" a stiskněte ENTER.
2. V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.
3. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *SentimentData.cs* . Do horní části *SentimentData.cs*přidejte následující příkaz using:

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentData.cs* :

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.
5. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*. Pak vyberte tlačítko **Přidat** . V editoru kódu se otevře soubor *SentimentPrediction.cs* . Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentPrediction.cs* :

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction` dědí z `SentimentData`, který poskytuje přístup k původním datům ve vlastnosti `SentimentText` a také výstup generovaný modelem.

## <a name="register-predictionenginepool-service"></a>Zaregistrovat službu PredictionEnginePool

Chcete-li udělat jednu předpověď, je nutné vytvořit [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken. Kromě toho musíte vytvořit instanci, která je všude, kde je to potřeba v rámci vaší aplikace. Jak vaše aplikace roste, tento proces může být nespravovatelný. Pro zlepšení výkonu a zabezpečení vlákna použijte kombinaci injektáže a `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.

Následující odkaz poskytuje další informace, pokud se chcete dozvědět víc o [vkládání závislostí](https://en.wikipedia.org/wiki/Dependency_injection).

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *Startup.cs*. Pak vyberte tlačítko **Přidat** .
1. Do horní části *Startup.cs*přidejte následující příkazy using:

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Odeberte existující kód pod příkazy using a přidejte následující kód:

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Definujte proměnné pro ukládání prostředí, ve kterém je aplikace spuštěná, a cesta k souboru, kde je model umístěný uvnitř `Startup` třídy.

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Níže Vytvořte konstruktor pro nastavení hodnot `_environment` a `_modelPath` proměnných. Když je aplikace spuštěná místně, je výchozím prostředím *vývoj*.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Pak přidejte novou metodu nazvanou `Configure` k registraci služby `PredictionEnginePool` pod konstruktorem.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Na vysoké úrovni tento kód automaticky inicializuje objekty a služby pro pozdější použití v případě, že je aplikace požaduje místo ručního provedení.

Modely strojového učení nejsou statické. Jakmile budou k dispozici nová školicí data, model se přeškolí a znovu nasadí. Jedním ze způsobů, jak získat nejnovější verzi modelu do vaší aplikace, je znovu nasadit celou aplikaci. Tím se ale zavádí výpadek aplikace. Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti pořizovat aplikaci.

Nastavte parametr `watchForChanges` na `true` a `PredictionEnginePool` spustí [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , které naslouchají oznámením o změnách systému souborů a vyvolává události, když dojde ke změně souboru. Tím se zobrazí výzva `PredictionEnginePool` pro automatické opětovné načtení modelu.

Model je identifikován parametrem `modelName`, aby bylo při změně možné znovu načíst více než jeden model na aplikaci.

> [!TIP]
> Alternativně můžete použít metodu `FromUri` při práci s místně uloženými modely. Místo sledování událostí změněných souborů `FromUri` se dotazuje na vzdálené umístění pro změny. Interval dotazování je ve výchozím nastavení nastaven na 5 minut. Interval dotazování můžete zvýšit nebo snížit na základě požadavků vaší aplikace. V níže uvedeném příkladu kódu `PredictionEnginePool` cyklické dotazování modelu uloženého v zadaném identifikátoru URI každou minutu.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Načtení modelu do funkce

Do třídy *AnalyzeSentiment* vložte následující kód:

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Tento kód přiřadí `PredictionEnginePool` předáním do konstruktoru funkce, který získáte prostřednictvím vkládání závislostí.

## <a name="use-the-model-to-make-predictions"></a>Použití modelu k vytvoření předpovědi

Nahraďte stávající implementaci metody *Run* ve třídě *AnalyzeSentiment* následujícím kódem:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Když se spustí metoda `Run`, jsou příchozí data z požadavku HTTP deserializovaná a slouží jako vstup pro `PredictionEnginePool`. Metoda `Predict` se pak zavolá, aby předpovědi pomocí `SentimentAnalysisModel` zaregistrovaného ve třídě `Startup` a vrátí výsledky zpátky uživateli, pokud je úspěšný.

## <a name="test-locally"></a>Test lokálně

Teď, když je všechno nastavené, je čas otestovat aplikaci:

1. Spuštění aplikace
1. Otevřete PowerShell a zadejte kód do příkazového řádku, kde PORT je port, na kterém je vaše aplikace spuštěná. Obvykle je port 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:

    ```powershell
    Negative
    ```

Blahopřejeme! Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí funkce Azure Functions.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
