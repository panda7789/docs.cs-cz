---
title: Application Insights – aplikace bez serveru
description: Application Insights je diagnostická platforma bez serveru, která vývojářům umožňuje detekovat, tíspat a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522747"
---
# <a name="telemetry-with-application-insights"></a>Telemetrie s Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights) je diagnostická platforma bez serveru, která vývojářům umožňuje detekovat, tíspat a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách. Application Insights pro funkční aplikace můžete zapnout jednoduše přepnutím přepínače na portálu. Application Insights poskytuje všechny tyto funkce, aniž byste museli konfigurovat server nebo nastavit vlastní databázi. Všechny funkce Application Insights jsou poskytovány jako služba, která se automaticky integruje s vašimi aplikacemi.

![Logo Application Insights](./media/application-insights-logo.png)

Přidání Application Insights do existujících aplikací je stejně snadné jako přidání klíče instrumentace do nastavení vaší aplikace. S Application Insights můžete:

- Vytvoření vlastních grafů a výstrah na základě metrik, jako je počet vyvolání funkcí, doba potřebný ke spuštění funkce a výjimky
- Analýza chyb a výjimek serveru
- Procházet výkon podle provozu a měřit čas potřebný k volání závislostí třetích stran
- Sledování využití procesoru, paměti a sazeb na všech serverech, které hostují vaše funkční aplikace
- Zobrazení živého datového proudu metrik včetně počtu žádostí a latence pro aplikace funkcí
- Použití [služby Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) k vyhledávání, dotazování a vytváření vlastních grafů nad daty funkcí

![Průzkumník metrik](./media/metrics-explorer.png)

Kromě vestavěné telemetrie je také možné generovat vlastní telemetrii. Následující fragment kódu vytvoří vlastní klienta telemetrie pomocí sady klíčů instrumentace pro aplikaci funkce:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Následující kód měří, jak dlouho trvá vložení nového řádku do instance [Azure Table Storage:](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Výsledný graf výkonu je zobrazen:

![Vlastní telemetrická data](./media/custom-telemetry.png)

Vlastní telemetrie odhaluje průměrná doba pro vložení nového řádku je 32,6 milisekund.

Application Insights poskytuje výkonný a pohodlný způsob protokolování podrobné telemetrie o aplikacích bez serveru. Máte plnou kontrolu nad úrovní trasování a protokolování, která je k dispozici. Můžete sledovat vlastní statistiky, jako jsou události, závislosti a zobrazení stránky. A konečně, výkonná analytika umožňuje psát dotazy, které kladou důležité otázky a generují grafy a pokročilé přehledy.

Další informace naleznete v [tématu Sledování funkcí Azure](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Předchozí](azure-functions.md)
>[další](logic-apps.md)
