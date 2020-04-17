---
title: Nasazení modelu do Azure Functions
description: Obsluhujte ML.NET modelu strojového učení analýzy mínění pro předpověď přes internet pomocí Azure Functions
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f340805200a14e0e145ffe1bf20f8059df63555
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608046"
---
# <a name="deploy-a-model-to-azure-functions"></a>Nasazení modelu do Azure Functions

Zjistěte, jak nasadit předem trénovaný model ML.NET strojového učení pro předpovědi přes HTTP prostřednictvím prostředí Bez serveru Azure Functions.

> [!NOTE]
> Tato ukázka spustí verzi `PredictionEnginePool` náhledu služby.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanými úlohami "Vývoj napříč platformami.NET Core" a "Azure Development".
- [Nástroje pro funkce Azure](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Předem vycvičený model. Použijte [kurz ML.NET analýzy mínění](../tutorials/sentiment-analysis.md) k vytvoření vlastního modelu nebo ke stažení tohoto [předem vytrénovaného modelu strojového učení analýzy mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="azure-functions-sample-overview"></a>Přehled ukázkových funkcí Azure

Tato ukázka je **aplikace C# HTTP Trigger Azure Functions,** která používá předem trénovaný binární klasifikační model ke kategorizaci mínění textu jako kladné nebo negativní. Funkce Azure poskytuje snadný způsob, jak spustit malé části kódu ve velkém měřítku ve spravovaném prostředí bez serveru v cloudu. Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) na GitHubu.

## <a name="create-azure-functions-project"></a>Vytvoření projektu Azure Functions

1. Otevřete sadu Visual Studio 2017. Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.** V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **Cloud.** Pak vyberte šablonu projektu **Azure Functions.** Do textového pole **Název** zadejte "SentimentAnalysisFunctionsApp" a vyberte tlačítko **OK.**
1. V dialogovém okně **Nový projekt** otevřete rozbalovací okno nad možnostmi projektu a vyberte Azure **Functions v2 (.NET Core).** Potom vyberte spouštěcí projekt **Http** a pak vyberte tlačítko **OK.**
1. Vytvořte adresář s názvem *MLModels* v projektu pro uložení modelu:

    V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**. Zadejte "MLModels" a stiskněte enter.

1. Nainstalujte **Microsoft.ML balíček NuGet** verze **1.3.1**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

1. Nainstalujte **balíček Microsoft.Azure.Functions.Extensions NuGet**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **microsoft.azure.functions.extensions**, vyberte tento balíček v seznamu a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

1. Nainstalujte **Microsoft.Extensions.ML balíček NuGet** verze **0.15.1**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

1. Nainstalujte **balíček Microsoft.NET.Sdk.Functions NuGet verze** **1.0.31**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Nainstalováno, vyhledejte **sadu Microsoft.NET.Sdk.Functions**, vyberte tento balíček v seznamu, vyberte **1.0.31** v rozevíracím seznamu Verze a vyberte tlačítko **Aktualizovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

## <a name="add-pre-trained-model-to-project"></a>Přidání předem trénovaného modelu k projektu

1. Zkopírujte předem sestavený model do složky *MLModels.*
1. V Průzkumníku řešení klepněte pravým tlačítkem myši na předem sestavený soubor modelu a vyberte **příkaz Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Vytvoření funkce Azure pro analýzu mínění

Vytvořte třídu pro předpověď mínění. Přidání nové třídy do projektu:

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Funkci Azure** a změňte pole **Název** na *AnalyzeSentiment.cs*. Potom vyberte tlačítko **Přidat.**

1. V dialogovém okně **Nová funkce Azure** vyberte Http **Trigger**. Potom vyberte tlačítko **OK.**

    V editoru kódu se otevře *soubor AnalyzeSentiment.cs.* Na začátek `using` *AnalyzeSentiment.cs*přidejte následující příkaz :

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Ve výchozím `AnalyzeSentiment` nastavení `static`je třída . Nezapomeňte odebrat `static` klíčové slovo z definice třídy.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Vytváření datových modelů

Je třeba vytvořit některé třídy pro vaše vstupní data a předpovědi. Přidání nové třídy do projektu:

1. Vytvořte adresář s názvem *DataModels* v projektu pro uložení datových modelů: V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > novou složku**. Zadejte "DataModels" a stiskněte klávesu Enter.
2. V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *DataModels* a pak vyberte **příkaz Přidat > novou položku**.
3. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentData.cs*. Potom vyberte tlačítko **Přidat.**

    Soubor *SentimentData.cs* se otevře v editoru kódu. Přidejte následující příkaz using na začátek *SentimentData.cs*:

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Odeberte existující definici třídy a do *souboru SentimentData.cs* přidejte následující kód:

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *DataModels* a pak vyberte **příkaz Přidat > novou položku**.
5. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentPrediction.cs*. Potom vyberte tlačítko **Přidat.** Soubor *SentimentPrediction.cs* se otevře v editoru kódu. Přidejte následující příkaz using na začátek *SentimentPrediction.cs*:

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Odeberte existující definici třídy a přidejte do *SentimentPrediction.cs* souboru následující kód:

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction`dědí, `SentimentData` z nichž poskytuje přístup `SentimentText` k původní data ve vlastnosti, stejně jako výstup generovaný modelem.

## <a name="register-predictionenginepool-service"></a>Zaregistrovat službu PredictionEnginePool

Chcete-li provést jednu předpověď, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musíte vytvořit . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Navíc je nutné vytvořit instanci všude, kde je potřeba v rámci aplikace. Jak vaše aplikace roste, tento proces může být nezvladatelný. Pro zvýšení výkonu a bezpečnosti podprocesů použijte `PredictionEnginePool` kombinaci vkládání [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) závislostí a služby, která vytvoří objekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.

Následující odkaz obsahuje další informace, pokud chcete získat další informace o [vkládání závislostí](https://en.wikipedia.org/wiki/Dependency_injection).

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *Startup.cs*. Potom vyberte tlačítko **Přidat.**
1. Přidejte následující příkazy using na začátek *Startup.cs*:

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

1. Definujte proměnné pro uložení prostředí, ve kterém aplikace běží, a `Startup` cestu k souboru, kde je model umístěn uvnitř třídy

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Pod tím vytvořte konstruktor pro nastavení `_environment` `_modelPath` hodnot a proměnných. Pokud je aplikace spuštěna místně, výchozí prostředí je *Vývoj*.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Potom přidejte novou `Configure` metodu `PredictionEnginePool` volanou k registraci služby pod konstruktorem.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Na vysoké úrovni tento kód inicializuje objekty a služby automaticky pro pozdější použití na požádání aplikace namísto nutnosti ručně provést.

Modely strojového učení nejsou statické. Jako nová trénovací data k dispozici, model je retrained a znovu nasadit. Jedním ze způsobů, jak získat nejnovější verzi modelu do aplikace, je znovu nasadit celou aplikaci. To však zavádí prostoje aplikace. Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti snížit počet aplikací.

Nastavte `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) spustí, který naslouchá systému souborů změnit oznámení a vyvolá události, když dojde ke změně souboru. To vyzve `PredictionEnginePool` k automatickému opětovnému načtení modelu.

Model je identifikován `modelName` parametrem tak, aby více než jeden model na aplikaci lze znovu načíst při změně.

> [!TIP]
> Alternativně můžete použít `FromUri` metodu při práci s modely uloženými vzdáleně. Místo sledování změn souborů `FromUri` se vyhodnoťuje změny ve vzdáleném umístění. Interval dotazování je výchozí na 5 minut. Můžete zvýšit nebo snížit interval dotazování na základě požadavků vaší aplikace. V ukázce `PredictionEnginePool` kódu níže uskutečuje model uložený na zadaném identifikátoru URI každou minutu.
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

Tento kód přiřadí `PredictionEnginePool` předáním konstruktoru funkce, který získáte prostřednictvím vkládání závislostí.

## <a name="use-the-model-to-make-predictions"></a>Použití modelu k předpovědi

Nahraďte existující implementaci metody *Run* ve třídě *AnalyzeSentiment* následujícím kódem:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Při `Run` spuštění metody jsou příchozí data z požadavku HTTP deknokrenována a použita `PredictionEnginePool`jako vstup pro soubor . Metoda `Predict` je pak volána k `SentimentAnalysisModel` předpovědi `Startup` pomocí registrované ve třídě a vrátí výsledky zpět uživateli v případě úspěchu.

## <a name="test-locally"></a>Testování místně

Nyní, když je vše nastaveno, je čas otestovat aplikaci:

1. Spuštění aplikace
1. Otevřete PowerShell a zadejte kód do výzvy, kde PORT je port, na kterém je aplikace spuštěna. Port je obvykle 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    V případě úspěchu by výstup měl vypadat podobně jako v níže uvedeném textu:

    ```powershell
    Negative
    ```

Blahopřejeme! Úspěšně obsluhoval model, aby předpovědi přes internet pomocí funkce Azure.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
