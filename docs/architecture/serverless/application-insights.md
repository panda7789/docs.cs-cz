---
title: Aplikace bez serveru Application Insights
description: Application Insights je platforma pro diagnostiku bez serveru, která umožňuje vývojářům rozpoznávat, třídit a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522747"
---
# <a name="telemetry-with-application-insights"></a>Telemetrie s Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights) je platforma pro diagnostiku bez serveru, která umožňuje vývojářům rozpoznávat, třídit a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách. Můžete zapnout Application Insights pro aplikace Function App pouhým překlopením přepínače na portálu. Application Insights poskytuje všechny tyto možnosti, aniž byste museli konfigurovat server nebo nastavit vlastní databázi. Všechny možnosti Application Insights se poskytují jako služba, která se automaticky integruje s vašimi aplikacemi.

![Logo Application Insights](./media/application-insights-logo.png)

Přidání Application Insights do stávajících aplikací je stejně snadné jako přidání klíče instrumentace do nastavení aplikace. Pomocí Application Insights můžete:

- Vytvářejte vlastní grafy a výstrahy na základě metrik, jako je počet volání funkce, čas potřebný ke spuštění funkce a výjimky.
- Analýza selhání a výjimek serveru
- Procházejte k podrobnostem o výkonu podle provozu a změřte čas potřebný k volání závislostí třetích stran.
- Monitorování využití procesoru, paměti a sazeb napříč všemi servery, které hostují aplikace Function App
- Zobrazení živého datového proudu metrik, včetně počtu požadavků a latence pro aplikace Function App
- Využijte funkci [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) k hledání, dotazování a vytváření vlastních grafů přes data funkcí

![Průzkumník metrik](./media/metrics-explorer.png)

Kromě integrované telemetrie je také možné vygenerovat vlastní telemetrii. Následující fragment kódu vytvoří vlastního klienta telemetrie pomocí klíče instrumentace nastaveného pro aplikaci Function App:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Následující kód měří, jak dlouho trvá vložení nového řádku do instance služby [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) :

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Zobrazí se výsledný graf výkonu:

![Vlastní telemetrie](./media/custom-telemetry.png)

Vlastní telemetrie odhalí průměrnou dobu vložení nového řádku je 32,6 milisekund.

Application Insights poskytuje výkonný a pohodlný způsob, jak protokolovat podrobnou telemetrii k aplikacím bez serveru. Máte plnou kontrolu nad úrovní trasování a protokolování, které je k dispozici. Můžete sledovat vlastní statistiku, jako jsou události, závislosti a zobrazení stránky. A konečně výkonná analýza vám umožní psát dotazy, které klást důležité otázky a generují grafy a rozšířené přehledy.

Další informace najdete v tématu [monitorování Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Předchozí](azure-functions.md)
>[Další](logic-apps.md)
