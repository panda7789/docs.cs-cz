---
title: Nasazení modelu v ASP.NET základního webového rozhraní API
description: Obsluhovat ML.NET model strojového učení analýzy mínění přes internet pomocí ASP.NET Core Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 3f1ca48ab29b04931961b52743bb6c7fab70b06d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608072"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Nasazení modelu v ASP.NET základního webového rozhraní API

Naučte se, jak sloužit předem vyškolený ML.NET model strojového učení na webu pomocí ASP.NET základní webové rozhraní API. Obsluha modelu přes webové rozhraní API umožňuje předpovědi prostřednictvím standardních metod HTTP.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".
- Powershell.
- Předem vycvičený model. Použijte [kurz ML.NET analýzy mínění](../tutorials/sentiment-analysis.md) k vytvoření vlastního modelu nebo ke stažení tohoto [předem vytrénovaného modelu strojového učení analýzy mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Vytvořit ASP.NET projekt základního webového rozhraní API

1. Otevřete sadu Visual Studio 2017. Na řádku nabídek vyberte **Soubor > Nový > project.** V dialogovém okně Nový projekt vyberte uzel **Visual C#** následovaný **webovým** uzlem. Pak vyberte šablonu projektu **ASP.NET core webová aplikace.** Do textového pole **Název** zadejte "SentimentAnalysisWebAPI" a vyberte tlačítko **OK.**

1. V okně, které zobrazuje různé typy ASP.NET základní projekty, vyberte **rozhraní API** a vyberte tlačítko **OK.**

1. Vytvořte adresář s názvem *MLModels* v projektu pro uložení předem sestavených souborů modelů strojového učení:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > novou složku. Zadejte "MLModels" a stiskněte enter.

1. Nainstalujte **balíček nuget Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte tlačítko Instalovat. V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně Přijetí licence vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

1. Nainstalujte **balíček Microsoft.Extensions.ML Nuget**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a vyberte tlačítko Instalovat. V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně Přijetí licence vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Přidání modelu do projektu ASP.NET základního webového rozhraní API

1. Zkopírování předem sestaveného modelu do adresáře *MLModels*
1. V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor zip modelu a vyberte Vlastnosti. V části Upřesnit změňte hodnotu Kopírovat do výstupního adresáře, pokud je novější.

## <a name="create-data-models"></a>Vytváření datových modelů

Je třeba vytvořit některé třídy pro vaše vstupní data a předpovědi. Přidání nové třídy do projektu:

1. Vytvořte adresář s názvem *DataModels* v projektu pro uložení datových modelů:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > novou složku. Zadejte "DataModels" a stiskněte **klávesu Enter**.

2. V Průzkumníku řešení klikněte pravým tlačítkem myši na adresář *DataModels* a potom vyberte Přidat > novou položku.
3. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentData.cs*. Potom vyberte tlačítko **Přidat.** Soubor *SentimentData.cs* se otevře v editoru kódu. Přidejte následující příkaz using na začátek *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Odeberte existující definici třídy a do **souboru SentimentData.cs** přidejte následující kód:

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

4. V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *DataModels* a pak vyberte **příkaz Přidat > novou položku**.
5. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentPrediction.cs*. Potom vyberte tlačítko Přidat. Soubor *SentimentPrediction.cs* se otevře v editoru kódu. Přidejte následující příkaz using na začátek *SentimentPrediction.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Odeberte existující definici třídy a přidejte do *SentimentPrediction.cs* souboru následující kód:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction`dědí `SentimentData`od . To usnadňuje zobrazení původních dat `SentimentText` ve vlastnosti spolu s výstupem generovaným modelem.

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Registrovat PredictionEnginePool pro použití v aplikaci

Chcete-li provést jednu předpověď, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musíte vytvořit . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Navíc je nutné vytvořit instanci všude, kde je potřeba v rámci aplikace. Jak vaše aplikace roste, tento proces může být nezvladatelný. Pro zvýšení výkonu a bezpečnosti podprocesů použijte `PredictionEnginePool` kombinaci vkládání [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) závislostí a služby, která vytvoří objekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.

Následující odkaz obsahuje další informace, pokud se chcete dozvědět více o [vkládání závislostí v ASP.NET Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otevřete *Startup.cs* třídu a přidejte do horní části souboru následující příkaz using:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Přidejte následující kód do metody *ConfigureServices:*

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

Na vysoké úrovni tento kód inicializuje objekty a služby automaticky pro pozdější použití na požádání aplikace namísto nutnosti ručně provést.

Modely strojového učení nejsou statické. Jako nová trénovací data k dispozici, model je retrained a znovu nasadit. Jedním ze způsobů, jak získat nejnovější verzi modelu do aplikace, je znovu nasadit celou aplikaci. To však zavádí prostoje aplikace. Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti snížit počet aplikací.

Nastavte `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) spustí, který naslouchá systému souborů změnit oznámení a vyvolá události, když dojde ke změně souboru. To vyzve `PredictionEnginePool` k automatickému opětovnému načtení modelu.

Model je identifikován `modelName` parametrem tak, aby více než jeden model na aplikaci lze znovu načíst při změně.

> [!TIP]
> Alternativně můžete použít `FromUri` metodu při práci s modely uloženými vzdáleně. Místo sledování změn souborů `FromUri` se vyhodnoťuje změny ve vzdáleném umístění. Interval dotazování je výchozí na 5 minut. Můžete zvýšit nebo snížit interval dotazování na základě požadavků vaší aplikace. V ukázce `PredictionEnginePool` kódu níže uskutečuje model uložený na zadaném identifikátoru URI každou minutu.
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a>Vytvořit řadič predict

Chcete-li zpracovat příchozí požadavky HTTP, vytvořte řadič.

1. V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *Řadiče* a potom vyberte **příkaz Přidat > řadič .**
1. V dialogovém okně **Přidat novou položku** vyberte **Řadič rozhraní API Prázdný** a vyberte **Přidat**.
1. V řádku změňte pole **Název řadiče** na *PredictController.cs*. Potom vyberte tlačítko Přidat. V editoru kódu se otevře *soubor PredictController.cs.* Přidejte následující příkaz using na začátek *PredictController.cs*:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Odeberte existující definici třídy a do *PredictController.cs* souboru přidejte následující kód:

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

Tento kód přiřadí `PredictionEnginePool` předáním konstruktoru řadiče, který získáte prostřednictvím vkládání závislostí. `Predict` Potom `Post` metoda řadiče používá `PredictionEnginePool` k předpovědi pomocí `SentimentAnalysisModel` registrované `Startup` ve třídě a vrátí výsledky zpět uživateli v případě úspěchu.

## <a name="test-web-api-locally"></a>Testování webového rozhraní API místně

Jakmile je vše nastaveno, je čas otestovat aplikaci.

1. Spusťte aplikaci.
1. Otevřete powershell a zadejte následující kód, kde PORT je port, na kterém vaše aplikace naslouchá.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    V případě úspěchu by výstup měl vypadat podobně jako v níže uvedeném textu:

    ```powershell
    Negative
    ```

Blahopřejeme! Úspěšně jste obsluhovali model, abyste mohli provádět předpovědi přes Internet pomocí ASP.NET základního webového rozhraní API.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
