---
title: Nasazení modelu v ASP.NET Core Web API
description: Poskytování modelu strojového učení ML.NET mínění analýzy prostřednictvím Internetu pomocí webového rozhraní API ASP.NET Core
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: f8b8f74f752aeb243d4a2987929bd28ddc5f7d5a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641086"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Nasazení modelu v ASP.NET Core Web API

Zjistěte, jak poskytovat předem vytrénovaných ML.NET model strojového učení na web pomocí ASP.NET Core Web API. Obsluhuje modelu přes webové rozhraní API umožňuje predikcí přes standardní HTTP metody.

> [!NOTE]
> `PredictionEnginePool` rozšíření služby je aktuálně ve verzi preview.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.
- Prostředí PowerShell.
- Předem natrénovaných modelů. Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestavovat vlastní model nebo stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Vytvořte projekt webového rozhraní API ASP.NET Core

1. Otevřete Visual Studio 2017. Vyberte **soubor > Nový > projekt** z řádku nabídek. V dialogovém okně Nový projekt, vyberte **Visual C#**  uzel, za nímž následuje **webové** uzlu. Vyberte **webové aplikace ASP.NET Core** šablony projektu. V **název** textového pole zadejte "SentimentAnalysisWebAPI" a pak vyberte **OK** tlačítko.

1. V okně, které zobrazuje různé typy projektů ASP.NET Core, vyberte **API** a vyberte položku **OK** tlačítko.

1. Vytvořte adresář *MLModels* ve vašem projektu a uložit předem sestavených strojového učení soubory modelu:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka. Zadejte "MLModels" a stiskněte Enter.

1. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko v dialogovém okně přijetí licence, pokud souhlasíte s licenčními podmínkami pro balíčky uvedené.

1. Nainstalujte **balíček Nuget Microsoft.Extensions.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko v dialogovém okně přijetí licence, pokud souhlasíte s licenčními podmínkami pro balíčky uvedené.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Přidání modelu do projektu webového rozhraní API ASP.NET Core

1. Zkopírujte předem sestavených model *MLModels* adresáře
1. V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor zip modelu a vyberte vlastnosti. V části Upřesnit změňte hodnotu kopírovat do výstupního adresáře ke zkopírování, pokud je novější.

## <a name="create-data-models"></a>Vytvoření datových modelů

Je potřeba vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka. Zadejte "DataModels" a stiskněte **Enter**.

2. V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost Přidat > Nová položka.
3. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko. *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    Odeberte stávající definice třídy a přidejte následující kód, který **SentimentData.cs** souboru:
    
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

4. V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.
5. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*. Vyberte tlačítko Přidat. *SentimentPrediction.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` dědí z `SentimentData`. To usnadňuje v původní data `SentimentText` vlastnost společně s výstupem generovaných modelu. 

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Zaregistrujte PredictionEnginePool pro použití v aplikaci

Chcete-li jeden predikcí, použijte [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602). Chcete-li použít [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) ve vaší aplikaci je třeba jej vytvořit když ho nepotřebují. V takovém případě je vhodné zvážit je vkládání závislostí.

Pod následujícím odkazem najdete další informace, pokud chcete další informace o [injektáž závislostí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otevřít *Startup.cs* třídu a přidejte následující příkaz do horní části souboru:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Přidejte následující kód, který *ConfigureServices* metody:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

Na vysoké úrovni tento kód inicializuje objekty a služby automaticky, pokud je požadovaná aplikací místo nutnosti ručně provést.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečné pro vlákna. Pro lepší výkon a bezpečný přístup z více vláken, použijte `PredictionEnginePool` službu, která vytvoří [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` objekty při použití aplikace. Přečtěte si další informace o následujícím příspěvku blogu [vytváření a používání `PredictionEngine` objektu fondů v ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).  

## <a name="create-predict-controller"></a>Vytvoření kontroleru Predict

Ke zpracování příchozích žádostí HTTP, vytvořte kontroleru.

1. V Průzkumníku řešení klikněte pravým tlačítkem myši *řadiče* adresář a potom vyberte možnost **Přidat > kontroler**.
1. V **přidat novou položku** dialogu **prázdný kontroler API** a vyberte **přidat**.
1. Příkazový řádek změnu **názvu Kontroleru** pole *PredictController.cs*. Vyberte tlačítko Přidat. *PredictController.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *PredictController.cs*:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Odeberte stávající definice třídy a přidejte následující kód, který *PredictController.cs* souboru:
    
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

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Tento kód přiřadí `PredictionEnginePool` předáním konstruktoru kontroleru, který můžete získat pomocí vkládání závislostí. Pak, bude `Predict` kontroleru `Post` metoda používá `PredictionEnginePool` k predikci a výsledek se vrátí zpět na uživatele v případě úspěšného ověření.

## <a name="test-web-api-locally"></a>Místní test webové rozhraní API

Jakmile je všechno nastavené, je čas k otestování aplikace.

1. Spusťte aplikaci.
1. Otevřete Powershell a zadejte následující kód, kde je port naslouchá vaše aplikace.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:
    
    ```powershell
    Negative
    ```

Blahopřejeme! Jste úspěšně obsluhovat model k predikci přes internet pomocí rozhraní API pro ASP.NET Core Web.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
