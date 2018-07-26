---
title: Application Insights – aplikace bez serveru
description: Application Insights je platforma bez serveru diagnostiku, která vývojářům umožňuje zjišťovat, posuzovat a diagnostikovat problémy ve webových aplikacích, mobilních aplikací, aplikací klasické pracovní plochy a mikroslužeb.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 57b1f70825251c48f720dcd78d094f5e8fb1edb8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404894"
---
# <a name="telemetry-with-application-insights"></a>Telemetrie pomocí Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights) je platforma bez serveru diagnostiku, která vývojářům umožňuje zjišťovat, posuzovat a diagnostikovat problémy ve webových aplikacích, mobilních aplikací, aplikací klasické pracovní plochy a mikroslužeb. Jednoduše tak, že slouží přepínač na portálu můžete zapnout Application Insights pro aplikace function App. Application Insights poskytuje všechny tyto funkce, aniž by bylo nutné nakonfigurovat server nebo nastavit vlastní databázi. Všechny funkce služby Application Insights jsou k dispozici jako služba, která se automaticky integruje s vašimi aplikacemi.

![Application Insights logo](./media/application-insights-logo.png)

Přidání Application Insights do stávajících aplikací je stejně jednoduché jako přidání Instrumentační klíč nastavení aplikace. Application Insights vám umožní:

* Vytvoření vlastních grafů a výstrah na základě metrik, jako je počet volání funkce, čas potřebný ke spuštění funkce a výjimky
* Analýza chyb a výjimek serveru
* Přejít k podrobnostem výkonu operací a měří čas potřebný k volání závislostí třetích stran
* Monitorování využití procesoru, paměti a rychlosti ve všech serverech, které jsou hostiteli vaše aplikace function App
* Zobrazit živý stream metrik, včetně počet požadavků a latencí pro vaše aplikace function App
* Použití [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) pro hledání, dotazování a vytvářet vlastní grafy vašich dat – funkce

![Průzkumník metrik](./media/metrics-explorer.png)

Kromě předdefinovaných telemetrická data je také možné generovat vlastní telemetrii. Následující fragment kódu vytvoří vlastní telemetrická data klienta pomocí Instrumentační klíč nastavení aplikace function App:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Následující kód opatření, jak dlouho trvá vložit nový řádek do [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Výsledný graf výkonu se zobrazí:

![Vlastní telemetrii](./media/custom-telemetry.png)

Vlastní telemetrii odhalí, že průměrná doba vložte nový řádek je 32.6 milisekund.

Application Insights poskytuje efektivní a pohodlný způsob, jak protokolovat podrobné telemetrie o vaší aplikace bez serveru. Máte plnou kontrolu nad úrovní trasování a protokolování, které je k dispozici. Můžete sledovat vlastní statistiky, jako jsou události, závislosti a zobrazení stránky. Nakonec výkonné analýzy vám umožňují psát dotazy, které důležité Ptejte se a generovat grafy a pokročilých přehledů.

Další informace najdete v tématu [monitorování Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
[Předchozí](azure-functions.md)
[další](logic-apps.md)