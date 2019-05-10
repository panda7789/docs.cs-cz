---
title: Azure Functions – aplikace bez serveru
description: Služba Azure functions poskytuje funkce bez serveru v různých jazycích (C#, JavaScript, Javu) a škálovat kód platformy k poskytování okamžitého založený na událostech.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754229"
---
# <a name="azure-functions"></a>Azure Functions

Azure functions poskytuje výpočetní prostředí prostředí. Funkce vyvolá *aktivační událost* (jako je přístup k koncový bod HTTP nebo časovače) a provede blok kódu nebo obchodní logiku. Funkce také podporu specializované *vazby* , které se připojovat k prostředkům, jako jsou úložiště a front.

![Logo Azure functions](./media/azure-functions-logo.png)

Existují dvě verze architektury Azure Functions. Starší verze podporuje úplné rozhraní .NET Framework a nového modulu runtime aplikace .NET Core pro různé platformy. Další jazyky kromě C# jako je JavaScript, F#, a podporují Javu. Funkce vytvořené na portálu poskytují bohatou syntaxe skriptování. Funkce, které jsou vytvořeny jako samostatné projekty je možné nasadit s plnou platformu podporu a možnosti.

Další informace najdete v tématu [dokumentaci ke službě Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funkce v1 a v2

Existují dvě verze modulu runtime Azure Functions: 1.x a 2.x. Verzi 1.x je všeobecně dostupná (GA). Podporuje vývoj aplikací pro .NET z portálu nebo počítače Windows a používá rozhraní .NET Framework. 1.x podporuje C#, JavaScript, a F#, experimentální podporu pro Python, PHP, TypeScript, Batch, Bash a PowerShell.

[Verze 2.x je stejně všeobecně dostupná nyní](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Využívá rozhraní .NET Core a podporuje vývoj napříč platformami pro Windows, macOS a počítače s Linuxem. 2.x přidává prvotřídní podporu pro Javu, ale zatím nepodporuje přímo některý z následujících experimentálních jazyků. Verze 2.x používá nový model rozšiřitelnosti vazbu, která umožňuje rozšíření třetích stran na platformu, nezávislé správy verzí vazby, a vylepšené prostředí pro spuštění.

> **Je známý problém s 1.x [podpory přesměrování vazby](https://github.com/Azure/azure-functions-host/issues/992).** Tento problém je specifický pro vývoj na platformě .NET. Projekty se závislostmi na knihovny, které jsou jiné verzi z knihovny zahrnuté v modulu runtime se to týká. Funkce tým zavázal vidět konkrétní pokrok na příslušný problém. Tým bude zabývat přesměrování vazby v 2.x předtím, než se ukládá do všeobecné dostupnosti. Příkaz oficiální team s návrhy jejich oprav a alternativní řešení je k dispozici zde: [Sestavení řešení ve službě Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Další informace najdete v tématu [porovnání 1.x a 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Podpora jazyků programování

Jsou podporovány následující jazyky buď obecně dostupná (GA), ve verzi preview, nebo je experimentální.

|Jazyk      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |GA          |Náhled  |
|**JavaScript**|GA          |Náhled  |
|**F#**        |GA          |         |
|**Java**      |            |Náhled  |
|**Python**    |Experimentální|         |
|**PHP**       |Experimentální|         |
|**TypeScript**|Experimentální|         |
|**Služby batch**     |Experimentální|         |
|**Bash**      |Experimentální|         |
|**PowerShell**|Experimentální|         |

Další informace najdete v tématu [podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plány služby App service

Funkce se opírá *plán služby app service*. Plán definuje prostředky využívané třídou aplikaci functions. Můžete přiřadit plány v oblasti, určení velikosti a počtu virtuálních počítačů, které se použije a vyberte si cenovou úroveň. True přístup bez serveru, může používat aplikace function App **spotřeby** plánu. Plán consumption výkonu škálovaly back-endu automaticky na základě zatížení.

Další informace najdete v tématu [plány služby App service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Vytvoření první funkce

Existují tři běžné způsoby, jak můžete vytvářet aplikace function App.

* Funkce skriptu na portálu.
* Vytvořte prostředky potřebné pomocí rozhraní příkazového řádku Azure (CLI).
* Vytvoření funkcí pro místně pomocí oblíbeného prostředí IDE a publikovat je do Azure.

Další informace o vytváření skriptované funkce na portálu najdete v tématu [vytvoření první funkce na webu Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Chcete-li sestavení z příkazového řádku Azure, přečtěte si téma [vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Vytvoření funkce z Visual Studia, najdete v tématu [vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Vysvětlení aktivačními událostmi a vazbami

Funkce jsou vyvolány *aktivační událost* a může mít nastavený právě jeden. Kromě volání funkce, určitými aktivačními událostmi sloužit také jako vazby. Můžete také definovat víc vazeb kromě aktivační událost. *Vazby* poskytují deklarativní způsob, jak připojit data do vašeho kódu. Jsou mohou být předány (vstup) nebo přijímat data (výstup). Triggery a vazby vytvořit funkce usnadnění práce. Vazby odstranění nároky na ruční vytvoření databáze nebo souboru systému připojení. Všechny informace potřebné pro vazby je obsažen ve speciální *souboru functions.json* souborů skriptů nebo deklarované s atributy v kódu.

Některé běžné triggery patří:

* Úložiště objektů blob: vyvolejte funkci souboru nebo složky nahraje nebo změnit v úložišti.
* HTTP: vyvolání funkce jako rozhraní REST API.
* Fronta: vyvolání funkce při položky existují ve frontě.
* Časovače: vyvolejte funkci regulární čím dál.

Příklady vazby:

* Cosmos DB: snadno připojte k databázi k načtení nebo uložení souborů.
* Table Storage: práce s úložiště klíč/hodnota z aplikace function app.
* Queue Storage: můžete snadno získat položky z fronty nebo umístit nových položek do fronty.

Následující příklad *souboru functions.json* soubor definuje aktivační události a vazby:

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

V tomto příkladu se funkce aktivuje změn do úložiště objektů blob v `images` kontejneru. Informace pro soubor je předáno, aby aktivační událost se taky pracuje jako vazbu. Existuje jiný vazba vložit informace do fronty s názvem `images`.

Tady je skript jazyka C# pro funkci:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

V příkladu je jednoduchou funkci, která přebírá název souboru, který byl změněn nebo nahráli do úložiště objektů blob a umístí jej do fronty pro pozdější zpracování.

Úplný seznam triggerů a vazeb, naleznete v tématu [aktivace Azure Functions a vazby koncepty](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxy servery

Proxy servery poskytují funkce přesměrování pro aplikaci. Proxy servery zveřejnit koncový bod a mapování tohoto koncového bodu na jiný prostředek. Proxy služby, které vám umožní:

* Přesměrovat příchozí požadavek do jiného koncového bodu.
* Předtím, než se předají, upravte příchozího požadavku.
* Upravit nebo poskytovat odpověď.

Proxy servery se používají pro scénáře, jako například:

* Zjednodušení a zkrácení Změna adresy URL.
* Poskytuje konzistentní předpona rozhraní API pro více back endové služby.
* Napodobování odpovědí na koncový bod a proto produkt.
* Poskytuje statické odpovědi do známého koncového bodu.
* Koncový bod rozhraní API udržování souladu, zatímco back-endu je přesunovat nebo migrovat.

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

`Domain Redirect` Proxy používá zkrácený trasu a mapuje na delší funkce prostředků. Transformace vypadá takto:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

`Root` Proxy trvá nic odeslané na adresu URL kořenového (`https://--shorturl--/`) a přesměruje na web s dokumentací.

Příklad použití proxy se zobrazí ve videu [Azure: Přeneste svoje aplikace do cloudu s využitím Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102). V reálném čase se aplikace ASP.NET Core běží na místním serveru SQL Server migrovat do cloudu Azure. Proxy služby slouží k refaktorování tradiční projekt webového rozhraní API pro použití funkce.

Další informace o proxy serverů najdete v tématu [pracovat s proxy služby Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Předchozí](azure-serverless-platform.md)
>[další](application-insights.md)
