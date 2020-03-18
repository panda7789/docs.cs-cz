---
title: Odolnost a vysoká dostupnost v mikroslužbách
description: Mikroslužby musí být navrženy tak, aby vydržely přechodné sítě a selhání závislostí, které musí být odolné k dosažení vysoké dostupnosti.
ms.date: 09/20/2018
ms.openlocfilehash: 1c0f75a8c68d1f84ba24c550e854edc5372cf7f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73094217"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odolnost a vysoká dostupnost v mikroslužbách

Řešení neočekávaných selhání je jedním z nejtěžších problémů, které je třeba vyřešit, zejména v distribuovaném systému. Velká část kódu, který vývojáři psát zahrnuje zpracování výjimek a to je také místo, kde nejvíce času strávíte testování. Problém je více než psaní kódu pro zpracování selhání. Co se stane, když se nezdaří počítač, ve kterém je spuštěná mikroslužba? Nejen, že potřebujete zjistit toto selhání mikroslužeb (pevný problém sám o sobě), ale také potřebujete něco restartovat mikroslužbu.

Mikroslužba musí být odolné vůči selhání a být schopen restartovat často v jiném počítači pro dostupnost. Tato odolnost proti chybám také přijde na stav, který byl uložen jménem mikroslužby, kde mikroslužeb můžete obnovit tento stav z a zda mikroslužeb můžete úspěšně restartovat. Jinými slovy, je třeba odolnost výpočetní schopnosti (proces lze kdykoli restartovat) stejně jako odolnost ve stavu nebo data (žádná ztráta dat a data zůstávají konzistentní).

Problémy odolnosti jsou umocněny během jiných scénářů, například když dojde k chybám během upgradu aplikace. Mikroslužba, pracující se systémem nasazení, musí určit, zda může pokračovat v přechodu na novější verzi nebo místo toho vrátit zpět na předchozí verzi k udržení konzistentního stavu. Otázky, jako je například zda dostatek počítačů jsou k dispozici, aby dál vpřed a jak obnovit předchozí verze mikroslužeb je třeba vzít v úvahu. To vyžaduje mikroslužby vyzařovat informace o stavu tak, aby celkové aplikace a orchestrator můžete provést tato rozhodnutí.

Odolnost proti chybám navíc souvisí s tím, jak se musí chovat cloudové systémy. Jak již bylo zmíněno, cloudový systém musí zahrnovat selhání a musí se pokusit automaticky zotavit z nich. Například v případě selhání sítě nebo kontejneru klientské aplikace nebo klientské služby musí mít strategii pro opakování odesílání zpráv nebo opakování požadavků, protože v mnoha případech jsou selhání v cloudu částečná. [Implementace odolných aplikací](../implement-resilient-applications/index.md) v této příručce se zabývá tím, jak zpracovat částečné selhání. Popisuje techniky, jako je opakování s exponenciální backoff nebo jistič vzor v .NET Core pomocí knihoven, jako [je Polly](https://github.com/App-vNext/Polly), který nabízí širokou škálu zásad pro zpracování tohoto předmětu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Řízení stavu a diagnostika v mikroslužbách

Může se to zdát zřejmé a často je přehlíženo, ale mikroslužba musí hlásit své zdraví a diagnostiku. V opačném případě je z hlediska operací malý vhled. Korelování diagnostických událostí v rámci sady nezávislých služeb a řešení zkosení hodin počítače, aby bylo možné pochopit pořadí událostí, je náročné. Stejným způsobem, že budete pracovat s mikroslužeb přes dohodnuté protokoly a formáty dat, je potřeba standardizace v tom, jak protokolovat stav a diagnostické události, které nakonec skončí v úložišti událostí pro dotazování a prohlížení. V přístupu mikroslužeb je klíčové, že různé týmy se dohodnou na jednom formátu protokolování. Je třeba konzistentní přístup k zobrazení diagnostických událostí v aplikaci.

### <a name="health-checks"></a>Kontroly stavu

Zdraví se liší od diagnostiky. Stav je o mikroslužbu hlášení jeho aktuální stav přijmout vhodná opatření. Dobrým příkladem je práce s mechanismy upgradu a nasazení k udržení dostupnosti. Přestože služba může být aktuálně není v pořádku z důvodu selhání procesu nebo restartování počítače, služba může být stále funkční. Poslední věc, kterou potřebujete, je, aby to ještě horší provedením upgrade. Nejlepším přístupem je provést šetření první nebo povolit čas pro mikroslužbu obnovit. Zdravotní události z mikroslužeb nám pomáhají činit informovaná rozhodnutí a ve skutečnosti pomáhají vytvářet samoléčebné služby.

V [části Implementace kontrol stavu v ASP.NET základní služby](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) v této příručce vysvětlujeme, jak používat novou knihovnu ASP.NET HealthChecks ve vašich mikroslužbách, aby mohli hlásit svůj stav monitorovací službě a přijmout příslušná opatření.

Máte také možnost používat vynikající open-source knihovnu s názvem Beat Pulse, která je k dispozici na [GitHubu](https://github.com/Xabaril/BeatPulse) a jako [balíček NuGet](https://www.nuget.org/packages/BeatPulse/). Tato knihovna také provádí kontroly stavu, s twist, zpracovává dva typy kontrol:

- **Liveness**: Zkontroluje, zda je aktivní mikroslužba, to znamená, pokud je schopna přijímat požadavky a reagovat.
- **Připravenost**: Zkontroluje, zda jsou závislosti mikroslužby (databáze, služby fronty atd.) samy připraveny, takže mikroslužba může dělat to, co má dělat.

### <a name="using-diagnostics-and-logs-event-streams"></a>Použití datových proudů událostí diagnostiky a protokolů

Protokoly poskytují informace o tom, jak je aplikace nebo služba spuštěna, včetně výjimek, upozornění a jednoduchých informačních zpráv. Obvykle každý protokol je v textovém formátu s jedním řádkem na událost, i když výjimky také často zobrazit trasování zásobníku přes více řádků.

V monolitické serverové aplikace, můžete jednoduše zapsat protokoly do souboru na disku (logfile) a pak analyzovat pomocí libovolného nástroje. Vzhledem k tomu, že spuštění aplikace je omezeno na pevný server nebo virtuální virtuální ms, obecně není příliš složité analyzovat tok událostí. V distribuované aplikaci, kde je více služeb spouštěno v mnoha uzlech v clusteru orchestrator, je však možnost korelovat distribuované události výzvou.

Aplikace založená na mikroslužbách by se neměla pokoušet ukládat výstupní datový proud událostí nebo souborů protokolu sama o sobě a ani se pokoušet spravovat směrování událostí na centrální místo. Měl by být transparentní, což znamená, že každý proces by měl pouze zapsat svůj datový proud událostí na standardní výstup, který pod ním budou shromažďovány infrastruktury prostředí spuštění, kde je spuštěn. Příkladem těchto směrovačů datového proudu událostí je [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), který shromažďuje datové proudy událostí z více zdrojů a publikuje je do výstupních systémů. Ty mohou zahrnovat jednoduchý standardní výstup pro vývojové prostředí nebo cloudové systémy, jako je [Azure Monitor](https://azure.microsoft.com/services/monitor//) a [Diagnostika Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview). Existují také dobré platformy a nástroje pro analýzu protokolů třetích stran, které mohou vyhledávat, upozorňovat, hlásit a monitorovat protokoly, a to i v reálném čase, jako [je Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestratoři spravující informace o zdraví a diagnostice

Při vytváření aplikace založené na mikroslužbách, je třeba řešit složitost. Samozřejmě, že jedna mikroslužba je jednoduché řešit, ale desítky nebo stovky typů a tisíce instancí mikroslužeb je složitý problém. Není to jen o vytváření architektury mikroslužeb – potřebujete také vysokou dostupnost, adresovatelnost, odolnost proti chybám, zdraví a diagnostiku, pokud máte v úmyslu mít stabilní a soudržný systém.

![Diagram clusterů poskytujících platformu podpory pro mikroslužby.](./media/resilient-high-availability-microservices/microservice-platform.png)

**Obrázek 4-22**. Platforma mikroslužeb je zásadní pro správu stavu aplikace

Složité problémy uvedené na obrázku 4-22 jsou velmi těžké vyřešit sami. Vývojové týmy by se měly zaměřit na řešení obchodních problémů a vytváření vlastních aplikací pomocí přístupů založených na mikroslužbách. Neměly by se zaměřovat na řešení složitých problémů infrastruktury; pokud ano, náklady na jakékoli aplikace založené na mikroslužbách by byly obrovské. Proto existují platformy orientované na mikroslužby, označované jako orchestrators nebo clustery mikroslužeb, které se pokoušejí vyřešit problémy s vytvářením a spouštěním služby a efektivním využitím prostředků infrastruktury. To snižuje složitost vytváření aplikací, které používají přístup mikroslužeb.

Různé orchestrátory mohou znít podobně, ale diagnostika a zdravotní kontroly nabízené každým z nich se liší ve vlastnostech a stavu zralosti, někdy v závislosti na platformě operačního systému, jak je vysvětleno v další části.

## <a name="additional-resources"></a>Další zdroje

- **Dvanáctifaktorová aplikace XI. Protokoly: Považovat protokoly za datové proudy událostí** \
  <https://12factor.net/logs>

- **Knihovna Microsoft Diagnostic EventFlow** Úložiště GitHub. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Co je diagnostika Azure** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Připojení počítačů s Windows ke službě Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Protokolování, co máte na mysli: Použití bloku aplikace sémantického protokolování** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** Oficiální stránky. \
  <https://www.splunk.com/>

- **Třída EventSource** Rozhraní API pro trasování událostí pro Systém Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Předchozí](microservice-based-composite-ui-shape-layout.md)
>[další](scalable-available-multi-container-microservice-applications.md)
