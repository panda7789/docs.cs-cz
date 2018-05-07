---
title: Odolnost proti chybám a vysoké dostupnosti v mikroslužeb
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Odolnost proti chybám a vysoké dostupnosti v mikroslužeb
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 1cdd938fb53e194a80f0eb3e6bc82ebed271af49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odolnost proti chybám a vysoké dostupnosti v mikroslužeb

Práci s neočekávanými chybami je jedním z nejtěžší problémů, které mají vyřešit, zejména v distribuovaného systému. Většinu kódu, který vývojáři psát zahrnuje zpracování výjimek, a to je také kde je nejvíce času stráveného při testování. Problém je složitější než psaní kódu pro zpracování chyby. Co se stane, když je počítač se spuštěným mikroslužbu nezdaří? Nejen potřebujete zjistit toto selhání mikroslužbu (pevné potíže na vlastní), ale budete potřebovat ještě něco restartovat vaší mikroslužby.

Mikroslužbu musí být odolné vůči selhání a nebude možné spustit často na jiném počítači, pro zajištění dostupnosti. Tato odolnosti také obsahuje do stavu, který byl uložen jménem mikroslužbu, kde mikroslužbu můžete obnovit tento stav z, a jestli mikroslužbu můžete restartovat úspěšně. Jinými slovy je potřeba odolnosti funkce výpočetní (Tento proces můžete restartovat kdykoli) a také odolnost proti stavu, nebo data (nedošlo ke ztrátě dat a konzistentní data zůstanou).

Problémy odolnosti jsou kombinovaných během dalších scénářích, třeba když dojde k selhání při upgradu aplikace. Mikroslužbu, práce s nasazení systému, je potřeba určit, zda můžete nadále přejít na novější verzi nebo místo toho vrátit k předchozí verzi udržovat konzistentním stavu. Je potřeba zvážit otázky, jako je například jestli je možné zachovat přesunutí dál dost počítačů a jak obnovit předchozí verze mikroslužby. To vyžaduje mikroslužbu pro vydávání informace o stavu tak, aby celkový aplikace a orchestrator můžete provést tato rozhodnutí.

Kromě toho je související odolnosti na tom, jak cloudové systémy musí chovat. Jak je uvedeno, systému cloudové musí zapojení selhání a musí automaticky pokusí z nich. Například v případě selhání síťové nebo kontejner, klientských aplikací nebo služeb klienta musí mít strategie opakovat odesílání zpráv nebo se můžete znovu požadavků, protože v mnoha případech jsou částečné selhání v cloudu. [Implementace odolná aplikace](#implementing_resilient_apps) části této příručky řeší, jak zpracovat částečné selhání. Popisuje techniky jako opakování exponenciálního omezení rychlosti nebo vzorem jistič v .NET Core pomocí knihovny jako [Polly](https://github.com/App-vNext/Polly), který nabízí širokou škálu zásady pro zpracování této subjektu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Stav správy a Diagnostika v mikroslužeb

To nemusí připadat zřejmé, bývá často přehlížen, ale mikroslužbu musí nahlásit jeho stav a Diagnostika. Jinak se jen málo informací z hlediska operace. Korelace diagnostických událostí mezi sadu nezávislých služeb a plánování práce s zkosí hodiny počítače k smysl pořadí událostí je náročná. Stejným způsobem, který budete používat mikroslužbu přes protokoly dohodnuté a formáty dat je zapotřebí standardizace v protokolování stavu a diagnostické události, které nakonec uložená v úložišti událostí pro dotazování a zobrazení. V rámci mikroslužeb přístupu je klíč, na formát jeden protokolování shodnou různé týmy. Je potřeba jednotný přístup k zobrazení diagnostických událostí v aplikaci.

### <a name="health-checks"></a>Kontroly stavu

Stav se liší od diagnostiky. Stav je o mikroslužbu jeho aktuální stav, provést příslušné akce pro vytváření sestav. Dobrým příkladem je práce pro upgrade a nasazení mechanismy pro zachování dostupnosti. I když služba aktuálně může být poškozen z důvodu selhání procesu nebo restartování počítače, může být služba přesto funkční. Poslední věcí, kterou je nutné je nastavit tento zhoršení provedením upgradu. Nejlepším postupem je nejdřív provést šetření, nebo můžete nastavit dobu mikroslužbu k obnovení. Stav události z mikroslužbu Pomozte nám informovaně rozhodnout a v důsledku toho vám pomohou vytvořit samoopravitelné služby.

V implementace kontroluje stav v ASP.NET Core services části této příručky vám vysvětlíme, jak používat novou knihovnu ASP.NET HealthChecks ve vaší mikroslužeb tak ohlásí jejich stavu monitorování službě, provést příslušné akce.

### <a name="using-diagnostics-and-logs-event-streams"></a>Pomocí nástroje pro diagnostiku a protokoly událostí datové proudy

Protokoly poskytují informace o tom, jak aplikace nebo služba běží, včetně výjimek, upozornění a informativní zprávy jednoduché. Každý protokol je obvykle ve formátu textu s jeden řádek na události, i když trasování zásobníku výjimky také často zobrazit na několika řádcích.

V monolitický serverové aplikace můžete jednoduše zapisuje protokoly do souboru na disku (soubor protokolu) a analyzujte je pomocí libovolného nástroje. Vzhledem k tomu, že provádění aplikací je omezený na pevné server nebo virtuální počítač, obvykle není příliš složitý pro analýzu v toku událostí. V distribuované aplikaci, kde jsou vykonány více služeb mezi mnoha uzly v clusteru služby orchestrator, schopnost korelovat distribuované události je však výzvu.

Aplikace založené na mikroslužbu na by měl není pokusí uložit do výstupního datového proudu událostí nebo logfiles sám o sobě a ani spravovat směrování události, které centrální místo. Musí být transparentní, což znamená, že každý proces právě zapíše jeho datového proudu událostí standardní výstup, které pod bude shromáždit pomocí infrastruktura provedení prostředí, kde je spuštěna. Příkladem těchto směrovače datového proudu událostí je [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), který shromažďuje streamů událostí z více zdrojů a vydává je výstup systémy. Může jít o jednoduché standardní výstup pro prostředí pro vývoj nebo cloudové systémy jako [Application Insights](https://azure.microsoft.com/services/application-insights/), [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) (pro místní aplikace), a [Azure Diagnostics](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). Existují také platformy analysis dobrou protokolů třetích stran a nástroje, které můžete hledat, výstrahy, sestavy a monitorování protokolů, i v reálném čase, jako jsou [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrators správu stavu a diagnostické informace

Když vytvoříte aplikaci na základě mikroslužbu, budete muset řešit složitost. Samozřejmě jeden mikroslužbu se snadno řešit, ale desítek nebo stovky typy a tisíce instance mikroslužeb je složitý problém. Ji není jenom o vytváření vaší architektury mikroslužby – také potřebujete vysokou dostupnost, adresovatelnosti, odolnost proti chybám, stav a Diagnostika Pokud máte v úmyslu stabilní a získá na ucelenosti systém.

![](./media/image22.png)

**Obrázek 4 – 22**. Mikroslužbu platformy je zásadní pro správu stavu aplikace

Složité problémy ukazuje obrázek 4 – 22 jsou velmi obtížné vyřešit sami. Vývojové týmy by měla soustředit na řešení obchodních problémů a vytváření vlastních aplikací s přístupy mikroslužby. Neměli soustředit na řešení problémů složitých infrastruktury; Pokud ano, bude náklady na všechny aplikace na základě mikroslužbu velký. Proto jsou zaměřené na konkrétní mikroslužbu platforem, označuje jako orchestrators nebo mikroslužbu clustery, které se snaží vyřešit pevný problémy sestavení a spuštění služby a efektivní použití prostředků infrastruktury. Tím se snižuje složité kroky vytváření aplikace, které používají mikroslužeb přístup.

Různé orchestrators může zvukových podobné, ale diagnostiky a kontroly stavu každého z nich nabízené lišit ve funkcích a stavu dospělosti někdy v závislosti na platformě operačního systému, jak je popsáno v následující části.

## <a name="additional-resources"></a>Další zdroje

-   **Aplikace Multi-Factor dvanácti. XI. Protokoly: Považovat za protokoly událostí datové proudy**
    [*https://12factor.net/logs*](https://12factor.net/logs)

-   **Knihovna EventFlow Microsoft diagnostiky.** Úložiště GitHub.

    [*https://github.com/Azure/diagnostics-eventflow*](https://github.com/Azure/diagnostics-eventflow)

-   **Co je Azure Diagnostics**
    [*https://docs.microsoft.com/azure/azure-diagnostics*](https://docs.microsoft.com/azure/azure-diagnostics)

-   **Připojení počítače se systémem Windows do služby analýzy protokolů Azure**
    [*https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents*](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

-   **Protokolování, co jste střední: Používání bloku sémantické protokolování aplikace**
    [*https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx*](https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx)

-   **Splunk.** Oficiální web.
    [*https://www.splunk.com/*](https://www.splunk.com/)

-   **EventSource – třída**. Rozhraní API pro události trasování událostí pro Windows (ETW) [*https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource*](xref:System.Diagnostics.Tracing.EventSource)




>[!div class="step-by-step"]
[Předchozí] (microservice-based-composite-ui-shape-layout.md) [Další] (scalable-available-multi-container-microservice-applications.md)
