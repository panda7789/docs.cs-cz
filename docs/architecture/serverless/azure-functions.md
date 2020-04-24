---
title: Aplikace bez serveru Azure Functions
description: Azure Functions poskytuje možnosti bez serveru v různých jazycích (C#, JavaScript, Java) a platformy pro poskytování kódu okamžitého škálování založeného na událostech.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 2dee60e3635be94a55ee26a7f04942bc59cb8dec
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135721"
---
# <a name="azure-functions"></a>Azure Functions

Azure Functions poskytuje výpočetní prostředí bez serveru. Funkce je vyvolána *triggerem* (například přístup ke koncovému bodu http nebo časovači) a spustí blok kódu nebo obchodní logiky. Funkce také podporují specializované *vazby* , které se připojují k prostředkům, jako jsou úložiště a fronty.

![Logo Azure Functions](./media/azure-functions-logo.png)

Aktuální verze modulu runtime 3,0 podporuje aplikace .NET Core 3,1 pro různé platformy. Podporují se další jazyky kromě C#, jako je JavaScript, F # a Java. Funkce vytvořené na portálu poskytují bohatou syntaxi skriptování. Funkce vytvořené jako samostatné projekty lze nasadit s využitím plné podpory platforem a možností.

Další informace najdete v [dokumentaci Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="programming-language-support"></a>Podpora programovacích jazyků

V rámci všeobecné dostupnosti (GA) jsou podporovány následující jazyky.

|Jazyk      |Podporované moduly runtime|
|--------------|------------------|
|**R #**        |.NET Core 3,1     |
|**JavaScript**|Uzel 10 & 12      |
|**F#**        |.NET Core 3,1     |
|**Java**      |Java 8            |
|**Python**    |Python 3,6, 3,7, & 3,8|
|**TypeScript**|Uzel 10 & 12 (přes JavaScript)|
|**PowerShell**|PowerShell Core 6|

Další informace najdete v tématu [Podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Plány služby App Service

Služba Functions se zálohuje podle *plánu služby App Service*. Plán definuje prostředky používané aplikací Functions. Můžete přiřadit plány k oblasti, určit velikost a počet virtuálních počítačů, které se budou používat, a vybrat cenovou úroveň. Pro skutečný přístup bez serveru můžou aplikace Function App používat plán **spotřeby** . Plán spotřeby bude automaticky škálovat back-end na základě zatížení.

Dalším parametrem hostování pro aplikace Function App je [Plán Premium](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan). Tento plán poskytuje instanci "Always On", aby se zabránilo studenému startu, podporuje pokročilé funkce, jako je připojení k virtuální síti, a běží na hardwaru Premium.

Další informace najdete v tématu [plány služby App Service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Vytvoření první funkce

Existují tři běžné způsoby, jak můžete vytvářet aplikace Function App.

- Funkce skriptu na portálu.
- Vytvořte potřebné prostředky pomocí Azure CLI.
- Vytvářejte funkce místně pomocí svého oblíbeného integrovaného vývojového prostředí a publikujte je do Azure.

Další informace o vytvoření skriptované funkce na portálu najdete v tématu [Vytvoření první funkce v Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Informace o tom, jak vytvořit z Azure CLI, najdete v tématu [Vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Chcete-li vytvořit funkci ze sady Visual Studio, přečtěte si téma [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Principy aktivačních událostí a vazeb

Funkce jsou vyvolány *triggerem* a mohou mít právě jednu. Kromě vyvolání funkce určité triggery slouží také jako vazby. Kromě triggeru můžete také definovat více vazeb. *Vazby* poskytují deklarativní způsob, jak připojit data k vašemu kódu. Můžou se předávat (zadávat) nebo přijímat data (výstup). Aktivační události a vazby usnadňují práci s funkcemi. Vazby odstraňují režii při ručním vytváření připojení databáze nebo systému souborů. Všechny informace potřebné pro vazby jsou obsaženy ve speciálním souboru *Functions. JSON* pro skripty nebo deklarované pomocí atributů v kódu.

Mezi běžné triggery patří:

- Blob Storage: vyvolejte funkci, když se v úložišti nahraje nebo změní soubor nebo složka.
- HTTP: vyvolání funkce jako REST API.
- Queue: vyvolá funkci, když položky ve frontě existují.
- Timer: vyvolejte funkci v normálním tempo.

Mezi příklady vazeb patří:

- CosmosDB: snadno se připojte k databázi a načíst nebo uložit soubory.
- Table Storage: Pracujte s úložištěm klíč/hodnota z aplikace Function App.
- Queue Storage: snadno načíst položky z fronty nebo umístit nové položky do fronty.

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

Zde je skript jazyka C# pro funkci:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Příkladem je jednoduchá funkce, která přebírá název souboru, který se změnil nebo nahrál do úložiště objektů blob, a umístí ho do fronty pro pozdější zpracování.

Úplný seznam triggerů a vazeb najdete v tématu [Azure Functions triggery a koncepty vazeb](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

>[!div class="step-by-step"]
>[Předchozí](azure-serverless-platform.md)
>[Další](application-insights.md)
