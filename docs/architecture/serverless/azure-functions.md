---
title: Funkce Azure – aplikace bez serveru
description: Funkce Azure poskytují funkce bez serveru ve více jazycích (C#, JavaScript, Java) a platformách, které poskytují okamžitý škálovací kód řízený událostmi.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401611"
---
# <a name="azure-functions"></a>Azure Functions

Funkce Azure poskytují výpočetní prostředí bez serveru. Funkce je vyvolána *aktivační událostí* (například přístup ke koncovému bodu HTTP nebo časovači) a spustí blok kódu nebo obchodní logiky. Funkce také podporují specializované *vazby,* které se připojují k prostředkům, jako je úložiště a fronty.

![Logo funkcí Azure](./media/azure-functions-logo.png)

Existují dvě verze architektury Azure Functions. Starší verze podporuje úplnou architekturu .NET Framework a nový runtime podporuje aplikace .NET Core pro různé platformy. Další jazyky kromě Jazyka C#, například JavaScript, F# a Java, jsou podporovány. Funkce vytvořené na portálu poskytují bohatou syntaxi skriptování. Funkce vytvořené jako samostatné projekty lze nasadit s plnou podporou platformy a možnostmi.

Další informace naleznete v [dokumentaci k funkcím Azure](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funkce v1 vs. v2

Existují dvě verze runtime Funkce Azure: 1.x a 2.x. Verze 1.x je obecně dostupná (GA). Podporuje vývoj rozhraní .NET z portálu nebo počítačů se systémem Windows a používá rozhraní .NET Framework. 1.x podporuje C#, JavaScript a F#, s experimentální podporou Pythonu, PHP, TypeScriptu, Batch, Bash a PowerShellu.

[Verze 2.x je také obecně k dispozici nyní](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Využívá rozhraní .NET Core a podporuje vývoj napříč platformami na počítačích se systémem Windows, macOS a Linux. 2.x přidává prvotřídní podporu pro Javu, ale zatím přímo nepodporuje žádný z experimentálních jazyků. Verze 2.x používá nový model rozšiřitelnosti vazby, který umožňuje rozšíření třetích stran na platformu, nezávislé správy verzí vazeb a efektivnější spuštění prostředí.

> **Je známý problém v 1.x s [podporou přesměrování vazby](https://github.com/Azure/azure-functions-host/issues/992).** Problém je specifický pro vývoj rozhraní .NET. Projekty se závislostmi na knihovnách, které jsou jinou verzí než knihovny zahrnuté v běhu, jsou ovlivněny. Tým funkcí se zavázal k dosažení konkrétního pokroku v řešení problému. Tým bude řešit vazby přesměrování v 2.x před přejde do obecné dostupnosti. Oficiální prohlášení týmu s navrhovanými opravami a řešeními je k dispozici zde: [Řešení sestavení ve funkcích Azure](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Další informace naleznete [v tématech Porovnání 1.x a 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Podpora programovacích jazyků

Následující jazyky jsou podporovány buď v obecné dostupnosti (GA), náhledu nebo experimentální.

|Jazyk      |1.x         |2.x      |
|--------------|------------|---------|
|**C #**        |GA          |Preview  |
|**Javascript**|GA          |Preview  |
|**F #**        |GA          |         |
|**Java**      |            |Preview  |
|**Python**    |Experimentální|         |
|**PHP**       |Experimentální|         |
|**TypeScript**|Experimentální|         |
|**Batch**     |Experimentální|         |
|**Bash**      |Experimentální|         |
|**PowerShell**|Experimentální|         |

Další informace najdete v tématu [Podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plány služeb aplikace

Funkce jsou zálohovány *plánem služby App Service*. Plán definuje prostředky používané aplikací funkce. Můžete přiřadit plány k oblasti, určit velikost a počet virtuálních počítačů, které budou použity, a vyberte cenovou úroveň. Pro skutečný přístup bez serveru aplikace funkce můžete použít plán **spotřeby.** Plán spotřeby automaticky změní velikost back-endu na základě zatížení.

Další informace naleznete v tématu [Plány služeb aplikace](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Vytvoření první funkce

Existují tři běžné způsoby, jak můžete vytvářet aplikace funkcí.

- Skript funguje na portálu.
- Vytvořte potřebné prostředky pomocí azure cli.
- Vytvářejte funkce místně pomocí oblíbeného prostředí IDE a publikujte je do Azure.

Další informace o vytvoření skriptované funkce na portálu najdete v [tématu Vytvoření první funkce na webu Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Pokud chcete vytvořit z azure cli, najdete [v tématu vytvoření první funkce pomocí příkazového příkazu k onomu azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Pokud chcete vytvořit funkci z Visual Studia, [přečtěte si](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)informace o vytvoření první funkce pomocí sady Visual Studio .

## <a name="understand-triggers-and-bindings"></a>Principy aktivačních událostí a vazeb

Funkce jsou vyvolány *aktivační událostí* a mohou mít přesně jednu. Kromě vyvolání funkce, některé aktivační události slouží také jako vazby. Můžete také definovat více vazeb kromě aktivační události. *Vazby* poskytují deklarativní způsob připojení dat k kódu. Mohou být předány (vstup) nebo přijímat data (výstup). Spouštěaaa a vazby usnadňují práci s funkcemi. Vazby odeberou režii ručního vytváření připojení databáze nebo systému souborů. Všechny informace potřebné pro vazby je obsažena ve speciálním souboru *functions.json* pro skripty nebo deklarované s atributy v kódu.

Některé běžné aktivační události zahrnují:

- Úložiště objektů blob: vyvolá funkci při nahrání nebo změně souboru nebo složky v úložišti.
- HTTP: vyvolat funkci jako rozhraní REST API.
- Fronta: vyvolá funkci, pokud položky existují ve frontě.
- Časovač: vyvolat svou funkci na pravidelné kadence.

Příklady vazeb:

- CosmosDB: snadno se připojit k databázi načíst nebo uložit soubory.
- Table Storage: práce s úložištěm klíč/hodnota z vaší aplikace funkce.
- Skladování front: snadno načíst položky z fronty nebo umístit nové položky do fronty.

Následující příklad *souboru functions.json* definuje aktivační událost a vazbu:

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

V tomto příkladu je funkce spuštěna změnou `images` úložiště objektů blob v kontejneru. Informace pro soubor je předán, takže aktivační událost také funguje jako vazba. Existuje jiná vazba pro zařazení informací `images`do fronty s názvem .

Zde je skript C# pro funkci:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Příkladem je jednoduchá funkce, která přebírá název souboru, který byl upraven nebo odeslán do úložiště objektů blob, a umístí jej do fronty pro pozdější zpracování.

Úplný seznam aktivačních událostí a vazeb najdete v [tématu Azure Functions aktivační události a koncepty vazby](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxy

Servery proxy poskytují funkce přesměrování pro vaši aplikaci. Proxy servery vystavit koncový bod a mapování tohoto koncového bodu na jiný prostředek. S proxy servery můžete:

- Přesměrovat příchozí požadavek do jiného koncového bodu.
- Upravte příchozí požadavek před jeho předáním.
- Upravte nebo poskytněte odpověď.

Proxy servery se používají pro scénáře, jako jsou:

- Zjednodušení, zkrácení nebo změna adresy URL.
- Poskytuje konzistentní předponu rozhraní API pro více back-endových služeb.
- Zesměšňování odpověď na koncový bod vyvíjené.
- Poskytuje statickou odpověď na známý koncový bod.
- Udržování koncového bodu rozhraní API konzistentní při přesunutí nebo migraci back-endu.

Proxy servery jsou uloženy jako definice JSON. Zde naleznete příklad:

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

Proxy `Domain Redirect` server provede zkrácenou trasu a mapuje ji na prostředek delší funkce. Transformace vypadá takto:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Proxy `Root` server přenese vše`https://--shorturl--/`odeslané na kořenovou adresu URL ( ) a přesměruje ji na dokumentační web.

Příklad použití proxy serverů se zobrazí ve videu [Azure: Přeneste svou aplikaci do cloudu s funkcemi Azure bez serveru](https://channel9.msdn.com/events/Connect/2017/E102). V reálném čase se do Cloudu Azure cloudu migruje ASP.NET základní aplikace spuštěná na místním SQL Serveru. Proxy servery se používají k refaktoringu tradiční hostoje webAPI projekt používat funkce.

Další informace o proxy serverech najdete v [tématu Práce s azure functions proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Předchozí](azure-serverless-platform.md)
>[další](application-insights.md)
