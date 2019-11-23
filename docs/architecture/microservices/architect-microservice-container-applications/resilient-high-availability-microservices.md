---
title: Odolnost a vysoká dostupnost v mikroslužbách
description: Mikroslužby musí být navržené tak, aby odolaly přechodným chybám sítě a závislostem, musí být odolné, aby dosáhli vysoké dostupnosti.
ms.date: 09/20/2018
ms.openlocfilehash: 1c0f75a8c68d1f84ba24c550e854edc5372cf7f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094217"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odolnost a vysoká dostupnost v mikroslužbách

Řešení neočekávaných selhání je jedním z nejzávažných problémů, které je potřeba vyřešit, zejména v distribuovaném systému. Většina kódu, který vývojáři pro psaní zahrnuje, spočívá v zpracování výjimek a to je také tam, kde je čas strávený při testování. Tento problém se týká více než psaní kódu pro zpracování selhání. Co se stane, když počítač, na kterém je mikroslužba spuštěná, se nezdařil? Nemusíte jenom detekovat tuto chybu mikroslužby (vlastní pevný problém), ale budete potřebovat něco k restartování mikroslužby.

Mikroslužba musí být odolná vůči selháním a je možné ji restartovat často na jiném počítači, který je k dispozici. Tato odolnost se také nachází ve stavu, který byl uložen jménem mikroslužby, kde může mikroslužba obnovit tento stav z a zda se mikroslužba může úspěšně restartovat. Jinými slovy, je nutné mít odolnost ve výpočetní schopnosti (proces může být kdykoli restartován) a také odolnost ve stavu nebo datech (žádná ztráta dat a data zůstávají konzistentní).

Problémy odolnosti proti chybám jsou během dalších scénářů složité, například když dojde k selhání během upgradu aplikace. Mikroslužba, která pracuje se systémem nasazení, musí určit, jestli se může dál přesouvat vpřed na novější verzi, nebo se místo toho vrátit k předchozí verzi, abyste zachovali konzistentní stav. Otázky, jako je například to, zda je k dispozici dostatek počítačů pro pokračování v předávání a jak obnovit předchozí verze mikroslužeb, je třeba zvážit. K tomu je potřeba, aby mikroslužba generovala informace o stavu, aby mohla tato rozhodnutí učinit celá aplikace a Orchestrator.

Odolnost proti chybám se navíc souvisí s tím, jak se cloudové systémy musí chovat. Jak bylo zmíněno, cloudový systém musí být součástí selhání a musí se pokusit o jeho automatické obnovení. Například v případě selhání sítě nebo kontejneru musí klientské aplikace nebo klientské služby mít strategii pro opakovaný pokus o posílání zpráv nebo opakované žádosti, protože v mnoha případech chyby v cloudu jsou částečné. Oddíl [implementující odolné aplikace](../implement-resilient-applications/index.md) v této příručce se zabývá tím, jak zpracovat částečnou chybu. Popisuje techniky, jako jsou opakování pomocí exponenciálního omezení rychlostiu nebo vzoru pro přerušení okruhů v .NET Core, pomocí knihoven, jako je [Polly](https://github.com/App-vNext/Polly), což nabízí velkou škálu zásad pro zpracování tohoto předmětu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Správa stavu a diagnostika mikroslužeb

Může se zdát být zřejmé a často je přehlédnutíná, ale mikroslužba musí hlásit svůj stav a diagnostiku. V opačném případě se z perspektivy operací vyskytuje malý přehled. Korelace diagnostických událostí v rámci sady nezávislých služeb a práce s hodinami strojového času je náročná na to, že je obtížné určit pořadí událostí. Stejným způsobem, jakým komunikujete s mikroslužbami přes dohodnuté protokoly a formáty dat, je potřeba standardizace v tom, jak protokolovat stav a diagnostické události, které nakonec skončí v úložišti událostí pro dotazování a zobrazení. V přístupu k mikroslužbám je klíč, který různé týmy souhlasí s jedním formátem protokolování. Pro zobrazení diagnostických událostí v aplikaci musí být nutný jednotný přístup.

### <a name="health-checks"></a>Kontroly stavu

Stav se liší od diagnostiky. Stav je o mikroslužbě, která hlásí svůj aktuální stav, aby mohla přijmout příslušné akce. Dobrým příkladem je práce s mechanismem upgradu a nasazení za účelem zachování dostupnosti. I když služba může být v současné době poškozená kvůli selhání procesu nebo restartování počítače, služba může pořád fungovat. Poslední věc, kterou potřebujete udělat, je to horší provedením upgradu. Nejlepším řešením je udělat nejprve šetření nebo povolit, aby se mikroslužba obnovila doba obnovení. Události stavu z mikroslužeb nám pomáhají dělat kvalifikovaná rozhodnutí a v důsledku toho pomáhat vytvářet samoobslužné služby.

V části [implementace kontrol stavu v rámci služby ASP.NET Core v](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) této příručce se dozvíte, jak ve svých mikroslužbách použít novou knihovnu HealthChecks ASP.NET, aby mohla jejich stav nahlásit službě monitorování, aby mohla provést příslušné akce.

Máte také možnost použít skvělou Open Source knihovnu s názvem otřesový Pulsi, která je k dispozici na [GitHubu](https://github.com/Xabaril/BeatPulse) a jako [balíček NuGet](https://www.nuget.org/packages/BeatPulse/). Tato knihovna také provádí kontroly stavu s otočením, zpracovává dva typy kontrol:

- **Živý**: kontroluje, jestli je mikroslužba aktivní, to znamená, že pokud je možné přijímat žádosti a reagovat na ně.
- **Připravenost**: kontroluje, jestli jsou závislosti mikroslužby (databáze, služby front atd.) připravené, takže mikroslužba může provést to, co má dělat.

### <a name="using-diagnostics-and-logs-event-streams"></a>Používání diagnostiky a protokolování datových proudů událostí

Protokoly obsahují informace o tom, jak běží aplikace nebo služba, včetně výjimek, upozornění a jednoduchých informativních zpráv. Každý protokol je obvykle v textovém formátu s jedním řádkem na událost, i když výjimky také často zobrazují trasování zásobníku v několika řádcích.

V aplikacích založených na serveru monolitické můžete jednoduše zapisovat protokoly do souboru na disku (logfile) a pak ho analyzovat libovolným nástrojem. Vzhledem k tomu, že je provádění aplikace omezené na pevný Server nebo virtuální počítač, není obvykle příliš složitá analýza toku událostí. V distribuované aplikaci, kde je spuštěno více služeb v rámci mnoha uzlů v clusteru Orchestrator, je však možné korelace distribuovaných událostí vyvolávat jako výzva.

Aplikace založené na mikroslužbách by se neměla pokoušet uložit výstupní proud událostí nebo protokolů samotného, a ne ani zkusit spravovat směrování událostí na centrální místo. Měl by být transparentní, což znamená, že každý proces by měl zapsat svůj datový proud události do standardního výstupu, který se bude shromažďovat v infrastruktuře prostředí pro spouštění, kde je spuštěný. Příkladem těchto směrovačů streamování událostí je [Microsoft. Diagnostics. využitím eventflow](https://github.com/Azure/diagnostics-eventflow), který shromažďuje datové proudy událostí z více zdrojů a publikuje ho do výstupních systémů. Můžou sem patřit jednoduché standardní výstupy pro vývojové prostředí nebo cloudové systémy, jako je [Azure monitor](https://azure.microsoft.com/services/monitor//) a [Azure Diagnostics](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview). K dispozici jsou také kvalitní platformy a nástroje pro analýzu protokolů třetích stran, které mohou hledat, upozorňovat, sestavovat a monitorovat protokoly, a to i v reálném čase, jako je [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrace správy informací o stavu a diagnostice

Když vytváříte aplikaci založenou na mikroslužbách, musíte se zabývat složitou složitostí. Jednou z těchto mikroslužeb je samozřejmě jednoduché řešení, ale desítky nebo stovky typů a tisíce instancí mikroslužeb jsou komplexní problém. Nejedná se jenom o vytváření architektury mikroslužeb. Pokud máte v úmyslu stabilní a soudržný systém, budete potřebovat vysokou dostupnost, adresovatelnost, odolnost, stav a diagnostiku.

![Diagram clusterů, které poskytují platformu podpory pro mikroslužby.](./media/resilient-high-availability-microservices/microservice-platform.png)

**Obrázek 4-22**. Platforma mikroslužeb je zásadní pro správu stavu aplikace.

Složité problémy zobrazené na obrázku 4-22 jsou velmi obtížně řešeny uživatelem. Vývojové týmy by se měly zaměřit na řešení obchodních problémů a vytváření vlastních aplikací pomocí přístupů založených na mikroslužbách. Neměly by se soustředit na řešení složitých problémů s infrastrukturou. Pokud byly, cena jakékoli aplikace založené na mikroslužbách by byla velmi velká. Proto existují platformy zaměřené na mikroslužby, označované jako orchestrace nebo clustery mikroslužeb, které se snaží vyřešit závažné problémy při sestavování a spouštění služby a efektivně využívat prostředky infrastruktury. Tím se omezí složitosti vytváření aplikací, které používají přístup k mikroslužbám.

Různé orchestrace můžou vypadat podobně, ale diagnostické a diagnostické kontroly, které každý z nich nabízí, se liší v funkcích a stavu zralosti, někdy v závislosti na platformě operačního systému, jak je vysvětleno v další části.

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Dvanáct-Factor App. XI. Protokoly: zpracování protokolů jako datových proudů událostí** \
  <https://12factor.net/logs>

- **Microsoft Diagnostic využitím eventflow Library** Úložiště GitHub. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Co je Azure Diagnostics** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Připojení počítačů s Windows ke službě Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Protokolování toho, co znamenáte: používání bloku aplikace sémantického protokolování** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** Oficiální lokalita. \
  <https://www.splunk.com/>

- **EventSource – třída** Rozhraní API pro trasování událostí pro Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Předchozí](microservice-based-composite-ui-shape-layout.md)
>[Další](scalable-available-multi-container-microservice-applications.md)
