---
title: Odolnost a vysoká dostupnost v mikroslužbách
description: Mikroslužeb mají být navržena k odolat přechodných síťových a závislosti selhání, musí být odolné vůči dosáhnout vysoké dostupnosti.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: ebf3a81718cd3423d3c80edb9c2f5b10f4ef47da
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465812"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odolnost a vysoká dostupnost v mikroslužbách

Práci s neočekávanými chybami je jedním z těch nejtěžších problémy vyřešit, zejména v distribuovaném systému. Velká část kódu, který vývojáři psát zahrnuje zpracování výjimek, a to je také kde je nejvíce času stráveného při testování. Problém se tak zapojí víc než psaní kódu pro zpracování chyb. Co se stane, když selže na počítači, kde je spuštěná mikroslužbách? Jenom je potřeba k detekci této chyby mikroslužeb (pevné problém sama o sobě), ale budete potřebovat ještě něco, co můžete restartovat vaše mikroslužeb.

Mikroslužby musí být odolné vůči selhání a nebude možné spustit často na jiném počítači pro dostupnost. Tato odolnost proti chybám také se vrátí do stavu, který byl uložen jménem mikroslužeb, kde mikroslužbách můžete obnovit tento stav z, a zda mikroslužbách můžete restartovat úspěšně. Jinými slovy musí být odolnost proti chybám v výpočetní funkci (kdykoli můžete restartovat proces) a také odolnost stavu nebo data (bez ztráty dat a data zůstanou konzistentní vzhledem k aplikacím).

Problémy odolnosti proti chybám jsou compounded během ostatním scénářům, třeba když dojde k selhání během upgradu aplikace. Mikroslužeb, práce s nasazení systému, je potřeba určit, jestli můžete nadále posunout vpřed na novější verzi nebo místo toho vrátit zpět na předchozí verzi k zachování konzistentního stavu. Třeba zvážit otázky, jako je například, jestli je možné zachovat přesun vpřed dost počítačů a jak obnovit předchozí verze mikroslužbách. To vyžaduje mikroslužeb ke generování informací o stavu tak, aby výpočetní a orchestrator může tato rozhodnutí.

Kromě toho je odolnost proti chybám týkající se musí chovat jak cloudových systémů. Jak už bylo zmíněno, cloudový systém musí využívat selhání a musí pokusit automaticky zotavte se z nich. Například v případě selhání sítě nebo kontejneru, klientských aplikací nebo služeb klienta musí mít strategii opakování odesílání zpráv nebo opakování žádosti, protože v mnoha případech jsou částečné selhání v cloudu. [Implementace odolných aplikací](../implement-resilient-applications/index.md) část v tomto průvodci se zabývá způsob zpracování částečného selhání. Popisuje postupů, jako jsou opakování pomocí exponenciálního omezení rychlosti nebo jističe v .NET Core s použitím knihovny jako [Polly](https://github.com/App-vNext/Polly), který nabízí širokou škálu zásady pro zpracování tohoto subjektu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Správa stavu a diagnostické nástroje v mikroslužbách

To se může zdát zřejmé a je často přehlédnuta, ale mikroslužby se musí hlásit svůj stav a Diagnostika. V opačném případě se jen málo informací z hlediska operace. Korelace mezi sadu nezávislých služeb diagnostických událostí a práci s počítači nepřesnostem dávat smysl pořadí událostí je náročná. Stejným způsobem, který budete moct používat mikroslužbě přes odsouhlaseným protokolů a datových formátů je třeba pro normalizaci v tom, jak stavu a diagnostické události, které nakonec ukládaly do úložiště událostí pro dotazování a zobrazení protokolu. V přístup založený na mikroslužbách, ji má klíče, které různé týmy se dohodly na formát jednoho protokolování. Musí být konzistentní vzhledem k aplikacím přístup k zobrazení diagnostických událostí v aplikaci.

### <a name="health-checks"></a>Kontroly stavu

Stav se liší od diagnostiky. Stav je o mikroslužbách jeho aktuální stav přijmout vhodná opatření pro vytváření sestav. Dobrým příkladem je práce s mechanismy upgradu a nasazení dostupnost. I když služba může být aktuálně v dobrém stavu z důvodu chybové ukončení procesu nebo počítač restartovat počítač, služba může být stále provozní. Poslední věcí, které potřebujete je, aby to horší provedením upgradu. Nejlepším řešením je nejdřív proveďte šetření nebo nějakou dobu počkat, mikroslužeb pro obnovení. Události stavu v mikroslužbě Pomozte nám umožňují přijímat informovaná rozhodnutí a v důsledku toho vám pomůžou vytvořit samoopravení služby.

V [implementace stavu v ASP.NET Core services zkontroluje](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) části této příručky, vám vysvětlíme, jak používat knihovnu ASP.NET HealthChecks nové mikroslužby tak ohlásí jejich stav monitorování službě, provést příslušné akce.

Máte také možnost používat vynikající open source knihovnu s názvem Beat Pulse, který je k dispozici na [Githubu](https://github.com/Xabaril/BeatPulse) a stejně jako [balíček NuGet](https://www.nuget.org/packages/BeatPulse/). Tato knihovna také provádí kontroly stavu s prvkem, zpracovává dvou typů kontrol:

- **Aktivity**: Zkontroluje, jestli mikroslužbách zachování připojení, to znamená, pokud je schopný přijímat požadavky a reagovat. 
- **Připravenost**: Kontroluje, pokud mikroslužbách závislosti (databáze, služba front, atd.) představují samy o sobě budete mít, tak můžete provést mikroslužbách, co se má provést. 

### <a name="using-diagnostics-and-logs-event-streams"></a>Pomocí diagnostiky a protokoly datových proudů událostí

Protokoly poskytují informace o tom, jak aplikace nebo služba běží, včetně výjimek, upozornění a jednoduché informační zprávy. Všechny protokoly je obvykle ve formátu textu s jedním řádkem na událost, i když trasování zásobníku výjimky také často zobrazit na několika řádcích.

V monolitické aplikace založené na serveru můžete jednoduše zapisují protokoly do souboru na disku (soubor protokolu) a analyzujte je pomocí libovolného nástroje. Od spuštění aplikace je omezen na pevnou server nebo virtuální počítač, obvykle není příliš složitý pro analýzu toku událostí. V distribuované aplikaci, ve kterých se spouští více služeb napříč mnoha uzly v clusteru služby orchestrator, nebudou moct porovnat distribuované události je však výzvu.

Aplikací založených na mikroslužbách by měl není pokusí uložit výstupního datového proudu událostí nebo logfiles sám o sobě a dokonce ani spravovat směrování událostí na centrální místo. Měla by být transparentní, což znamená, že každý proces by měl stačí napsat jeho datového proudu událostí na standardní výstup, který pod nebudou shromažďovat infrastruktura prostředí provádění, kde je spuštěná. Je například tyto směrovače datového proudu událostí [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), který shromažďuje streamů událostí z různých zdrojů a publikuje ji do výstupního systémy. Může jít o jednoduché standardního výstupu pro prostředí pro vývoj nebo cloudových systémů, jako je [Application Insights](https://azure.microsoft.com/services/application-insights/), [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) (pro místní aplikace), a [Azure Diagnostics](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). Existují také dobré protokolu třetích stran analýzy platformy a nástroje, které můžete vyhledat, výstrahy, sestavy, a monitorování protokolů, a to i v reálném čase, jako jsou [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrátorů, správu stavu a diagnostické informace

Při vytváření aplikací založených na mikroslužbách, budete muset řešit složité. Samozřejmě jeden mikroslužba je jednoduché řešení, ale jen pár nebo stovky typy a tisíce instancí mikroslužeb je komplexní problém. To není jen o vytváření architektury mikroslužeb, musíte také vysokou dostupnost, adresovatelnosti, odolnost proti chybám, stav a Diagnostika Pokud máte v úmyslu mít systém stabilní a cohesive.

![Orchestrátory poskytovat podporu platformy pro spouštění mikroslužby.](./media/image22.png)

**Obrázek 4 – 22**. Platformu Mikroslužeb je zásadní pro správu stavu aplikace.

Složité problémy uvedené v obrázek 4 – 22 jsou velmi obtížné vyřešit sami. Vývojové týmy byste se zaměřit na řešení obchodních problémů a vytváří vlastní aplikace s využitím mikroslužeb přístupy. Neměli soustředit na řešení složitých problémů s infrastrukturou; Pokud ano, by být obrovské náklady na všech aplikací založených na mikroslužbách. Proto jsou orientované na mikroslužby platformy, nazývá orchestrátorů nebo vyladěných clusterů, které se pokoušejí řeší těžké problémy sestavování a provoz služby a efektivní využívání prostředků infrastruktury. To snižuje složitým vytváření aplikací, které používají přístup založený na mikroslužbách.

Různé orchestrátory může zní podobně, ale diagnostiky a kontroly stavu nabízených každou z nich se liší v funkce a stav vyspělosti, někdy v závislosti na platformě operačního systému, jak je vysvětleno v další části.

## <a name="additional-resources"></a>Další zdroje

- **12 Factor App. XI. Protokoly: Považovat za protokoly datových proudů událostí** \
  [https://12factor.net/logs](https://12factor.net/logs)

- **Knihovna Microsoft diagnostických využitím EventFlow** úložiště GitHub. \
  [https://github.com/Azure/diagnostics-eventflow](https://github.com/Azure/diagnostics-eventflow)

- **Co je Azure Diagnostics** \
  [https://docs.microsoft.com/azure/azure-diagnostics](https://docs.microsoft.com/azure/azure-diagnostics)

- **Připojení počítačů s Windows ke službě Log Analytics v Azure** \
  [https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

- **Protokolování co Mean: Použití sémantického protokolování Application Block** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** oficiální web. \
  [https://www.splunk.com/](https://www.splunk.com/)

- **EventSource – třída** rozhraní API pro události trasování pro Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Předchozí](microservice-based-composite-ui-shape-layout.md)
>[další](scalable-available-multi-container-microservice-applications.md)