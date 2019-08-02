---
title: Aplikace bez serveru Azure Functions
description: Azure Functions poskytuje možnosti bez serveru napříč různými jazykyC#(, JavaScript, Java) a platformami k poskytování kódu okamžitého škálování založeného na událostech.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676805"
---
# <a name="azure-functions"></a>Azure Functions

Azure Functions poskytuje výpočetní prostředí bez serveru. Funkce je vyvolána triggerem ( například přístup ke koncovému bodu http nebo časovači) a spustí blok kódu nebo obchodní logiky. Funkce také podporují specializované *vazby* , které se připojují k prostředkům, jako jsou úložiště a fronty.

![Logo Azure Functions](./media/azure-functions-logo.png)

Existují dvě verze rozhraní Azure Functions Framework. Starší verze podporuje úplné .NET Framework a nový modul runtime podporuje aplikace .NET Core pro různé platformy. Podporují se další C# jazyky kromě jazyků JavaScript F#, a Java. Funkce vytvořené na portálu poskytují bohatou syntaxi skriptování. Funkce vytvořené jako samostatné projekty lze nasadit s využitím plné podpory platforem a možností.

Další informace najdete v [dokumentaci Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funkce v1 vs. v2

Existují dvě verze modulu runtime Azure Functions: 1. x a 2. x. Verze 1. x je všeobecně dostupná (GA). Podporuje vývoj pro .NET z portálu nebo počítačů s Windows a používá .NET Framework. 1. x podporuje C#, JavaScript a F#, s experimentální podporou pro Python, php, TypeScript, Batch, bash a PowerShell.

[Verze 2. x je také všeobecně dostupná](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Využívá .NET Core a podporuje vývoj pro různé platformy na počítačích s Windows, macOS a Linux. 2. x přidává špičkovou podporu pro Java, ale ještě nepřímo nepodporuje žádný z experimentálních jazyků. Verze 2. x používá nový model rozšiřitelnosti vazby, který umožňuje rozšíření jiných výrobců na platformu, nezávislé vytváření verzí vazeb a efektivnější prostředí pro provádění.

> **Došlo k známému problému v 1. x s [podporou přesměrování vazby](https://github.com/Azure/azure-functions-host/issues/992).** Tento problém je specifický pro vývoj pro .NET. Budou ovlivněny projekty se závislostmi na knihovnách, které jsou odlišnou verzí z knihoven obsažených v modulu runtime. Tým Functions se zavázal, že má na problému konkrétní pokrok. Tým bude adresovat přesměrování vazby v 2. x před tím, než se dostane do všeobecné dostupnosti. Oficiální prohlášení týmu s navrhovanými opravami a alternativní řešení jsou k dispozici zde: [Rozlišení sestavení v Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Další informace najdete v tématu [porovnání 1. x a 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Podpora programovacích jazyků

Následující jazyky jsou podporovány buď v obecné dostupnosti (GA), ve verzi Preview, nebo experimentální.

|Jazyk      |verze         |2.x      |
|--------------|------------|---------|
|**C#**        |GA          |Náhled  |
|**JavaScript**|GA          |Náhled  |
|**F#**        |GA          |         |
|**Java**      |            |Náhled  |
|**Python**    |Experimentální|         |
|**PHP**       |Experimentální|         |
|**TypeScript**|Experimentální|         |
|**Partie**     |Experimentální|         |
|**Bash**      |Experimentální|         |
|**PowerShell**|Experimentální|         |

Další informace najdete v tématu [podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plány služby App Service

Služba Functions se zálohuje podle *plánu služby App Service*. Plán definuje prostředky používané aplikací Functions. Můžete přiřadit plány k oblasti, určit velikost a počet virtuálních počítačů, které se budou používat, a vybrat cenovou úroveň. Pro skutečný přístup bez serveru můžou aplikace Function App používat plán **spotřeby** . Plán spotřeby bude automaticky škálovat back-end na základě zatížení.

Další informace najdete v tématu [plány služby App Service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Vytvoření první funkce

Existují tři běžné způsoby, jak můžete vytvářet aplikace Function App.

* Funkce skriptu na portálu.
* Vytvořte potřebné prostředky pomocí rozhraní příkazového řádku Azure (CLI).
* Vytvářejte funkce místně pomocí svého oblíbeného integrovaného vývojového prostředí a publikujte je do Azure.

Další informace o vytvoření skriptované funkce na portálu najdete v tématu [Vytvoření první funkce v Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Informace o tom, jak vytvořit z Azure CLI, najdete v tématu [Vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Chcete-li vytvořit funkci ze sady Visual Studio, přečtěte si téma [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Principy aktivačních událostí a vazeb

Funkce jsou vyvolány *triggerem* a mohou mít právě jednu. Kromě vyvolání funkce určité triggery slouží také jako vazby. Kromě triggeru můžete také definovat více vazeb. *Vazby* poskytují deklarativní způsob, jak připojit data k vašemu kódu. Můžou se předávat (zadávat) nebo přijímat data (výstup). Aktivační události a vazby usnadňují práci s funkcemi. Vazby odstraňují režii při ručním vytváření připojení databáze nebo systému souborů. Všechny informace potřebné pro vazby jsou obsaženy ve speciálním souboru functions *. JSON* pro skripty nebo deklarované pomocí atributů v kódu.

Mezi běžné triggery patří:

* Blob Storage: vyvolejte funkci, když se v úložišti nahraje nebo změní soubor nebo složka.
* HTTP: vyvolání funkce jako REST API.
* Queue: vyvolá funkci, když položky ve frontě existují.
* Timer: vyvolejte funkci v normálním tempo.

Mezi příklady vazeb patří:

* CosmosDB: snadno se připojte k databázi a načíst nebo uložit soubory.
* Table Storage: Pracujte s úložištěm klíč/hodnota z aplikace Function App.
* Queue Storage: snadno načíst položky z fronty nebo umístit nové položky do fronty.

Následující příklad souboru *Functions. JSON* definuje Trigger a vazbu:

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

V tomto příkladu je funkce aktivována změnou v úložišti objektů BLOB v `images` kontejneru. Informace pro soubor jsou předány, takže Trigger funguje také jako vazba. Existuje další vazba pro vložení informací do fronty s názvem `images`.

Tady je C# skript pro funkci:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Příkladem je jednoduchá funkce, která přebírá název souboru, který se změnil nebo nahrál do úložiště objektů blob, a umístí ho do fronty pro pozdější zpracování.

Úplný seznam triggerů a vazeb najdete v tématu [Azure Functions triggery a koncepty vazeb](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxy servery

Proxy poskytují funkce přesměrování vaší aplikace. Proxy zpřístupňují koncový bod a mapují tento koncový bod na jiný prostředek. U proxy serverů můžete provádět následující akce:

* Přesměrovat příchozí požadavek do jiného koncového bodu.
* Upravte příchozí požadavek předtím, než se předáte společně.
* Upravte nebo poskytněte odpověď.

Proxy servery se používají pro scénáře, jako například:

* Zjednodušení, zkrácení nebo změna adresy URL.
* Poskytování konzistentní předpony rozhraní API pro více back-endové služby.
* Napodobování odezvy na vyvíjený koncový bod.
* Poskytnutí statické odezvy na známý koncový bod.
* Udržování konzistentního koncového bodu rozhraní API v době, kdy je back-end přesunut nebo migrován.

Proxy servery jsou uloženy jako definice JSON. Tady je příklad:

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

`Domain Redirect` Proxy má zkrácenou trasu a mapuje ji na delší prostředek funkce. Transformace vypadá takto:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Proxy server přesměruje cokoli na kořenovou adresu`https://--shorturl--/`URL () a přesměruje ho na web dokumentace. `Root`

Příklad použití proxy serverů je zobrazený ve videu [Azure: Přeneste svou aplikaci do cloudu pomocí Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)bez serveru. V reálném čase je ASP.NET Core aplikace běžící v místním SQL Server migrována do cloudu Azure. Proxy servery slouží k refaktorování tradičního projektu webového rozhraní API, aby mohli používat funkce.

Další informace o proxy serverech najdete v tématu věnovaném [práci s proxy služby Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Předchozí](azure-serverless-platform.md)Další
>[](application-insights.md)
