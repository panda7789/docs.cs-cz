---
title: Kolekce paměti a výkon
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69a11e99966467de005ab92d3dcdebaa70bbdbe4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44265166"
---
# <a name="garbage-collection-and-performance"></a>Kolekce paměti a výkon
<a name="top"></a> Toto téma popisuje problémy spojené s uvolňování paměti kolekce a využití paměti. Řeší problémy, které se vztahují na spravované haldě a vysvětluje, jak minimalizovat dopad uvolňování paměti u svých aplikací. Všechny problémy obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Nástroje pro analýzu výkonu](#performance_analysis_tools)  
  
-   [Řešení potíží s problémy s výkonem](#troubleshooting_performance_issues)  
  
-   [Řešení potíží](#troubleshooting_guidelines)  
  
-   [Výkon zaškrtněte procedury](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a>Nástroje pro analýzu výkonu  
 Následující části popisují nástroje, které jsou k dispozici pro zkoumání problémů paměti využití a uvolňování paměti kolekce. [Postupy](#performance_check_procedures) najdete dál v tomto tématu najdete v těchto nástrojů.  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a>Čítače výkonu paměti  
 Pomocí čítačů výkonu pro shromažďování dat výkonu. Pokyny najdete v tématu [běhová profilace](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Paměť .NET CLR kategorie čítačů výkonu, jak je popsáno v [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o systému uvolňování paměti.  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a>Ladění pomocí SOS  
 Můžete použít [ladicí program Windows (WinDbg)](/windows-hardware/drivers/debugger/index) pro kontrolu objektů na spravované haldě.
 
 Chcete-li program WinDbg nainstalovat, nainstalujte ladění nástroje pro Windows z [stáhnout ladění nástroje pro Windows](/windows-hardware/drivers/debugger/debugger-download-tools) stránky.
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a>Události Trasování událostí pro Windows kolekci paměti  
 Trasování událostí pro Windows (ETW) je systém trasování, které doplňují profilování a ladění v rozhraní .NET Framework poskytuje podporu. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md) zachycení užitečné informace pro spravované haldy z hlediska statistickou analýzu. Například `GCStart_V1` událost, která se vyvolá, když uvolňování paměti se použije, obsahuje následující informace:  
  
-   Které generování objektů se shromažďují.  
  
-   Co spustí uvolnění.  
  
-   Typ uvolňování paměti (souběžné nebo není souběžných).  
  
 Protokolování událostí trasování událostí pro Windows je efektivní a nebude maskují všechny problémy s výkonem, který je přidružený k uvolnění paměti. Proces může poskytnout vlastní události ve spojení s událostmi trasování událostí pro Windows. Při přihlášení, můžete určit, jak a kdy dojít k problémům haldy korelaci událostí v aplikaci a události kolekce paměti. Serverová aplikace může například poskytovat události na začátku a konci požadavku klienta.  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a>Rozhraní API pro profilaci  
 Common language runtime (CLR) rozhraní profilování poskytují podrobné informace o objektech, které byly ovlivněny během uvolňování paměti. Profiler můžete být upozorněni, když uvolňování paměti začíná a končí. To může poskytovat sestavy o objekty na spravované haldě, včetně identifikaci objektů v každé generaci. Další informace najdete v tématu [přehled profilace](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).  
  
 Profilovací programy mohou poskytnout komplexní informace. Komplexní profilovací programy však můžete případně upravit chování aplikace.  
  
### <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], (ARM) sledování prostředků domény aplikace umožňuje hostitelům k monitorování využití procesoru a paměti doménou aplikace. Další informace najdete v tématu [sledování prostředků aplikační domény](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).  
  
 [Zpět na začátek](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a>Řešení potíží s problémy s výkonem  
 Prvním krokem je [zjistit, jestli tento problém je ve skutečnosti uvolňování](#IsGC). Pokud zjistíte, že se jedná, vyberte z následujícího seznamu k vyřešení tohoto problému.  
  
-   [Dojde k výjimce na více instancí z důvodu nedostatku paměti](#Issue_OOM)  
  
-   [Proces využívá příliš mnoho paměti](#Issue_TooMuchMemory)  
  
-   [Uvolňování nezíská objekty dostatečně rychle](#Issue_NotFastEnough)  
  
-   [Spravovaná halda je příliš fragmentovaná.](#Issue_Fragmentation)  
  
-   [Pozastaví kolekce uvolnění paměti jsou příliš dlouhé](#Issue_LongPauses)  
  
-   [Generace 0 je moc velká.](#Issue_Gen0)  
  
-   [Využití procesoru během uvolňování paměti je příliš vysoká.](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problém: Limit paměti se vyvolá výjimka  
 Existují dva případy legitimní pro spravované <xref:System.OutOfMemoryException> vyvolání:  
  
-   Nedostatek virtuální paměti.  
  
     Uvolňování paměti přidělí paměť ze systému v příslušných segmentech v předem určeným rozsahu. Pokud přidělení vyžaduje další segment, ale neexistuje žádná souvislých volný blok ve virtuální paměti prostoru procesu, se nezdaří přidělení pro spravované haldě.  
  
-   Nemají dostatek fyzické paměti k přidělení.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určete, jestli je spravované výjimky na více instancí z důvodu nedostatku paměti.](#OOMIsManaged)<br /><br /> [Určete, kolik virtuální paměti je možné vyhradit.](#GetVM)<br /><br /> [Určení, zda je dostatek fyzické paměti.](#Physical)|  
  
 Pokud zjistíte, že výjimka není oprávněné, obraťte se na Microsoft zákaznický servis a podporu s následujícími informacemi:  
  
-   Do zásobníku s spravované výjimky na více instancí z důvodu nedostatku paměti.  
  
-   Úplný výpis paměti.  
  
-   Data, která prokáže vaše oprávnění, že se nejedná o legitimní-paměti výjimky, včetně dat, která ukazuje, že virtuální nebo fyzická paměť není problém.  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a>Problém: Proces využívá příliš mnoho paměti  
 Běžné předpokladem je, že zobrazí využití paměti na **výkonu** karty ve Správci úloh Windows můžete určit, kdy se používá příliš mnoho paměti. Nicméně, které zobrazují se vztahují na pracovní sadu; neposkytuje informace o využití virtuální paměti.  
  
 Pokud zjistíte, že problém je způsoben spravované haldě, musí spravované haldě měření průběžným monitorováním určete všechny vzorky.  
  
 Pokud zjistíte, jestli problém nezpůsobuje ve spravované haldě, je nutné použít nativní ladění.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určete, kolik virtuální paměti je možné vyhradit.](#GetVM)<br /><br /> [Určete, kolik paměti potvrzuje spravované haldě.](#ManagedHeapCommit)<br /><br /> [Určete, kolik paměti rezervuje spravované haldě.](#ManagedHeapReserve)<br /><br /> [Určení velké objekty v 2. generace.](#ExamineGen2)<br /><br /> [Určete odkazy na objekty.](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problém: Systému uvolňování paměti nezíská objekty dostatečně rychle  
 Když se objeví jako objekty nejsou jsou uvolněny podle očekávání pro uvolnění paměti, je nutné určit, jestli jsou všechny silné odkazy na tyto objekty.  
  
 Tento problém se můžete setkat také v případě žádná kolekce uvolnění paměti pro generování, který obsahuje objekt mrtvý, což znamená, že nebyla spuštěna finalizační metodu pro objekt mrtvý. Například to je možné při spouštění aplikace jednovláknový apartment (STA) a vlákno této služby, které frontě finalizační metodu nejde volat metodu do něj.  
  
|Kontroly výkonu|  
|------------------------|  
|[Zkontrolujte odkazy na objekty.](#ObjRef)<br /><br /> [Určení, zda byla spuštěna finalizační metodu.](#Induce)<br /><br /> [Určení, zda jsou objekty čekání na jejich dokončení.](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problém: Na spravované haldě je příliš fragmentovaná.  
 Úroveň fragmentace se počítá jako poměr volného místa za Celková přidělená paměť pro generování. Přijatelnou úroveň fragmentace pro 2. generace, je více než 20 %. Protože 2. generace můžete získat velmi velký poměr fragmentace je mnohem důležitější než absolutní hodnota.  
  
 Máte velké množství volného místa v 0. generace není problém vzhledem k tomu, že to je generace, kde jsou přiděleny nové objekty.  
  
 Fragmentace vždy dojde v haldy pro velké objekty, protože není setřepána. Volné objekty, které jsou sousedící jsou přirozeně sbaleny do jednoho místa pro splnění požadavků na přidělení velkého objektu.  
  
 Fragmentace stát problémem v 1 a generace 2. Pokud tyto generace velké množství volného místa po uvolnění, použití objektu aplikace může být nutné změny a měli byste zvážit znovu vyhodnotit životnosti dlouhodobé objektů.  
  
 Nadměrné Připnutí objektů můžete zvýšit fragmentace. Pokud fragmentace je vysoké, může připnout příliš mnoho objektů.  
  
 Pokud fragmentace paměti virtuální brání systému uvolňování paměti daných segmentů, mohou být jeden z následujících akcí:  
  
-   Časté načítání a uvolňování mnoha malých sestavení.  
  
-   Příliš mnoho odkazů na objekty modelu COM drží, když spolupráce s nespravovaným kódem.  
  
-   Vytvoření velké přechodné objektů, což způsobí, že haldy pro velké objekty na přidělují a uvolňují haldy segmenty často.  
  
     Při hostování CLR, může aplikace vyžadovat, že uvolňování zachovat jeho segmentů. Tím se snižuje frekvence přidělení segmentu. To lze provést pomocí příznaku STARTUP_HOARD_GC_VM v [startup_flags – výčet](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
|Kontroly výkonu|  
|------------------------|  
|[Určení množství volného místa ve spravované haldě.](#Fragmented)<br /><br /> [Určete počet připojených objektů.](#Pinned)|  
  
 Pokud se domníváte, že neexistuje žádná legitimní příčinou fragmentaci, obraťte se na Microsoft zákaznický servis a podporu.  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problém: Pozastavení kolekce uvolnění paměti jsou příliš dlouhé  
 Uvolňování paměti funguje v obnovitelně v reálném čase, takže aplikace musí být schopné tolerovat některé pozastaví. Kritéria pro obnovitelné reálném čase je, že 95 % operací musí dokončit včas.  
  
 V souběžné uvolňování paměti spravovaná vlákna je možné spustit shromažďování, což znamená, že je možné je minimální.  
  
 Pouze několik milisekund, než poslední dočasnému uvolnění (generace 0 a 1), to snižuje pozastaví obvykle není vhodná. Však může snížit pozastaví v 2. generace kolekce tak, že změníte model požadavků na přidělení aplikací.  
  
 Jiný, přesnější, metoda se má používat [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md). Časování pro kolekce můžete najít tak, že přidáte tyto časové razítko rozdíly pro posloupnost událostí. Pořadí celé kolekce obsahuje pozastavení prováděcího modulu, uvolňování paměti kolekce a opětovné prováděcího modulu.  
  
 Můžete použít [oznámení pro kolekci paměti](../../../docs/standard/garbage-collection/notifications.md) k určení, zda je server ke kolekci generace 2, a určuje, zda přesměrování požadavků na jiný server by mělo odlehčit jakékoliv potíže se pozastaví.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určuje délku času v uvolňování paměti.](#TimeInGC)<br /><br /> [Určete, co způsobilo uvolnění paměti.](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a>Problém: 0. generace je moc velká.  
 Generace 0 by mohla mít větší počet objektů v 64bitovém systému, zejména v případě, že místo uvolnění paměti pracovní stanice použijete uvolnění paměti serveru. Je to proto, že je prahová hodnota pro aktivaci 0 uvolnění paměti generace vyšší v těchto prostředích a kolekcemi generace 0 můžete získat mnohem větší. Výkon je vyšší, pokud aplikace přiděluje víc paměti než se aktivuje uvolňování paměti.  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problém: Využití procesoru během uvolňování paměti je příliš vysoká.  
 Během uvolňování paměti bude vysoké využití procesoru. Pokud značné množství času zpracování se stráven v procesu uvolnění paměti, počtu kolekcí je moc často nebo kolekce je trvají příliš dlouho. Zvýšení přidělení počet objektů na spravované haldě způsobí, že uvolňování paměti dochází častěji. Snížení frekvence přidělení snižuje frekvence uvolnění paměti.  
  
 Přidělení kurzů můžete sledovat pomocí `Allocated Bytes/second` čítače výkonu. Další informace najdete v tématu [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
 Doba trvání kolekce je primárně faktorem počet objektů, které byly zachovány při po přidělení. Uvolňování paměti musí projít velké množství paměti, pokud zůstanou velký počet objektů, které se mají shromažďovat. Je časově náročné práce ke komprimaci zachované objekty. Pokud chcete zjistit, kolik objektů zpracovávaly během kolekci, nastavte zarážku v ladicím programu na konci uvolnění pro zadané generace.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určete, pokud je způsobena vysoké využití procesoru uvolňování paměti.](#HighCPU)<br /><br /> [Nastavení zarážky na konci uvolňování paměti.](#GenBreak)|  
  
 [Zpět na začátek](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a>Řešení potíží  
 Tato část popisuje pokyny, které byste měli zvážit při začnete vaše šetření.  
  
### <a name="workstation-or-server-garbage-collection"></a>Pracovní stanice nebo uvolnění paměti serveru  
 Určete, pokud používáte správný typ uvolňování paměti. Pokud vaše aplikace používá více vláken a instance objektů, použijte místo uvolnění paměti pracovní stanice uvolnění paměti serveru. Uvolnění paměti serveru funguje ve více vláknech, zatímco uvolňování paměti pracovní stanice vyžaduje více instancí aplikace ke spuštění vlastních vláken pro uvolnění a soutěží o čas procesoru.  
  
 Aplikace, který má nízkou zatížení a, který provádí úlohy zřídka na pozadí, třeba služby, může použít uvolnění paměti pracovní stanice se zakázaným souběžným uvolňováním.  
  
### <a name="when-to-measure-the-managed-heap-size"></a>Kdy k měření velikosti spravované haldy  
 Pokud nepoužíváte profiler, budete muset vytvořit konzistentní měření vzor efektivně diagnostikovat problémy s výkonem. Vezměte v úvahu následující body k vytvoření plánu:  
  
-   Pokud budete vyhodnocovat po uvolnění paměti generace 2, bude celou spravovanou haldu zdarma uvolňování paměti (neživými objekty).  
  
-   Pokud budete vyhodnocovat ihned po uvolnění paměti generace 0, nebudou shromažďovat ještě objekty v generace 1 a 2.  
  
-   Pokud budete vyhodnocovat bezprostředně před uvolňování paměti, budete měřit tolik přidělení nejvíce předtím, než spustí uvolnění paměti.  
  
-   Měření během uvolňování paměti jen těžko, protože datové struktury systému uvolňování paměti nejsou v platném stavu pro procházení a nemusí být schopen poskytnout úplné výsledky. Jedná se o účel.  
  
-   Při použití uvolnění paměti pracovní stanice s souběžné uvolňování paměti, nejsou uvolňovaného objekty komprimovat, takže velikost haldy může být stejná nebo větší (fragmentace může vypadat větší).  
  
-   Souběžné uvolňování paměti v generaci 2 je zpožděno při fyzické paměti je příliš vysoké.  
  
 Následující postup popisuje, jak nastavit zarážku, můžete změřit spravované haldě.  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Chcete-li nastavit zarážku na konci uvolňování paměti  
  
-   V rámci WinDbg s příponou SOS ladicího programu, načíst zadejte následující příkaz:  
  
     **BP mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2) "kb"; " g ""**  
  
     kde **GcCondemnedGeneration** nastavená na požadované generace. Tento příkaz vyžaduje soukromé symboly.  
  
     Tento příkaz vynutí zalomení **RestartEE** se spustí po objektů 2. generace mají byla získána pro uvolnění.  
  
     Uvolňování paměti serveru pouze jedno vlákno volá **RestartEE**, takže zarážka dojde pouze jednou během uvolnění paměti generace 2.  
  
 [Zpět na začátek](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a>Výkon zaškrtněte procedury  
 Tato část popisuje následující postupy k izolaci příčina potíží s výkonem:  
  
-   [Určí, zda je problém způsoben uvolňování paměti.](#IsGC)  
  
-   [Určete, jestli je spravované výjimky na více instancí z důvodu nedostatku paměti.](#OOMIsManaged)  
  
-   [Určete, kolik virtuální paměti je možné vyhradit.](#GetVM)  
  
-   [Určení, zda je dostatek fyzické paměti.](#Physical)  
  
-   [Určete, kolik paměti potvrzuje spravované haldě.](#ManagedHeapCommit)  
  
-   [Určete, kolik paměti rezervuje spravované haldě.](#ManagedHeapReserve)  
  
-   [Určení velké objekty v 2. generace.](#ExamineGen2)  
  
-   [Určete odkazy na objekty.](#ObjRef)  
  
-   [Určení, zda byla spuštěna finalizační metodu.](#Induce)  
  
-   [Určení, zda jsou objekty čekání na jejich dokončení.](#Finalize)  
  
-   [Určení množství volného místa ve spravované haldě.](#Fragmented)  
  
-   [Určete počet připojených objektů.](#Pinned)  
  
-   [Určuje délku času v uvolňování paměti.](#TimeInGC)  
  
-   [Zjistěte, co vyvolalo uvolňování paměti.](#Triggered)  
  
-   [Určete, jestli způsobuje vysoké využití procesoru uvolňování paměti.](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Chcete-li zjistit, zda je problém způsoben uvolňování paměti  
  
-   Zkontrolujte následující čítače výkonu paměti dvě:  
  
    -   **% Času v uvolňování paměti**. Zobrazuje procentuální hodnotu uplynulého času, který byl vynaložen provádění uvolnění posledního cyklu uvolňování paměti kolekce. Tento čítač použijte k určení, zda systému uvolňování paměti spotřebuje uběhla spousta času uvolněte místo na spravované haldě. Pokud doba trvání uvolňování paměti je relativně nízký, to by mohlo znamenat problém prostředků mimo spravované haldě. Tento čítač nemusí být přesné při souběžné nebo je zahrnuta uvolňování paměti na pozadí.  
  
    -   **Celkový počet svěřených bajtů**. Zobrazuje velikost virtuální paměti aktuálně potvrzené systémem uvolňování paměti. Tento čítač použijte k určení, zda je paměť systému uvolňování paměti používané nadměrné část paměti, která vaše aplikace používá.  
  
     Většina čítačů výkonu paměti se aktualizují na konci každé uvolňování paměti. Proto že nemusí odrážet aktuální podmínky, které se mají informace o.  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Chcete-li zjistit, jestli je spravované výjimky na více instancí z důvodu nedostatku paměti  
  
1.  V ladicím programu WinDbg nebo Visual Studio s rozšířením ladicí program SOS načíst, zadejte tisku výjimky (**pe**) příkaz:  
  
     **! pe**  
  
     Pokud je spravované výjimky, <xref:System.OutOfMemoryException> se zobrazí jako typ výjimky, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2.  Pokud výstup neurčuje výjimku, budete muset určit, které vlákno výjimky na více instancí z důvodu nedostatku paměti je z. Zadejte následující příkaz v ladicím programu, který chcete zobrazit všechna vlákna s jejich zásobníky volání:  
  
     **~\*znalostní báze**  
  
     Vlákno se zásobníkem, který má volání výjimky je indikován `RaiseTheException` argument. Toto je objektu spravované výjimky.  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3.  Můžete použít následující příkaz pro výpis vnořené výjimky.  
  
     **! pe-vnořené**  
  
     Pokud nenajdete žádné výjimky, výstup z důvodu nedostatku paměti výjimka pochází z nespravovaného kódu.  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Chcete-li zjistit, je možné vyhradit velikost virtuální paměti  
  
-   V rámci WinDbg s příponou SOS ladicího programu, načíst zadejte následující příkaz získat největší bezplatná oblasti:  
  
     **! adres – souhrn**  
  
     Největší bezplatná oblasti se zobrazí, jak je znázorněno v následujícím výstupu.  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové hodnotě). Tato oblast je mnohem menší, než které systému uvolňování paměti, musí mít segmentu.  
  
     -nebo-  
  
-   Použití **vmstat** příkaz:  
  
     **! vmstat**  
  
     Největší bezplatná oblasti je největší hodnotu ve sloupci maximální, jak je znázorněno v následujícím výstupu.  
  
    ```  
    TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL  
    ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~  
    Free:  
    Small       8K        64K         46K       36          1,671K  
    Medium      80K       864K        349K      3           1,047K  
    Large       1,384K    1,278,848K  151,834K  12          1,822,015K  
    Summary     8K        1,278,848K  35,779K   51          1,824,735K  
    ```  
  
<a name="Physical"></a>   
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Určuje, jestli je dostatečná fyzická paměť  
  
1.  Spuštění Správce úloh Windows.  
  
2.  Na **výkonu** kartu, podívejte se na potvrzená hodnota. (Ve Windows 7, podívejte se na **potvrzení (KB)** v **systémové skupiny**.)  
  
     Pokud **celkový** blízko **Limit**, máte málo na fyzické paměti.  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Chcete-li určit, kolik paměti potvrzuje spravované haldy  
  
-   Použití `# Total committed bytes` čítače výkonu paměti se získat počet bajtů, které se provádí spravované haldě. Uvolňování potvrzení bloků v segmentu, podle potřeby, nikoli všechny najednou.  
  
    > [!NOTE]
    >  Nepoužívejte `# Bytes in all Heaps` čítače výkonu, protože nepředstavuje skutečné využití paměti ve spravované haldě. Velikost generace je součástí tuto hodnotu a je ve skutečnosti jeho prahová hodnota velikosti, to znamená, velikost, který indukuje uvolňování paměti, pokud generování je vyplněna objekty. Proto se tato hodnota je obvykle nula.  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Chcete-li určit, kolik paměti rezervuje spravované haldy  
  
-   Použití `# Total reserved bytes` čítače výkonu paměti.  
  
     Rezervuje uvolňování paměti v příslušných segmentech a můžete určit, kde segment, který spustí na základě **eeheap** příkazu.  
  
    > [!IMPORTANT]
    >  I když můžete určit množství paměti, které systému uvolňování paměti přiděluje každého segmentu, velikost segmentu je specifický pro implementaci a může se změnit kdykoli, včetně v pravidelné aktualizace. Vaše aplikace by nikdy vytvořit předpoklady o nebo závisí na velikosti konkrétního segmentu, ani snažit konfigurace množství paměti k přidělení segmentu.  
  
-   V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:  
  
     **! eeheap -gc**  
  
     Výsledek je následující.  
  
    ```  
    Number of GC Heaps: 2  
    ------------------------------  
    Heap 0 (002db550)  
    generation 0 starts at 0x02abe29c  
    generation 1 starts at 0x02abdd08  
    generation 2 starts at 0x02ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    02ab0000 02ab0038  02aceff4 0x0001efbc(126908)  
    Large object heap starts at 0x0aab0038  
     segment    begin allocated     size  
    0aab0000 0aab0038  0aab2278 0x00002240(8768)  
    Heap Size   0x211fc(135676)  
    ------------------------------  
    Heap 1 (002dc958)  
    generation 0 starts at 0x06ab1bd8  
    generation 1 starts at 0x06ab1bcc  
    generation 2 starts at 0x06ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    06ab0000 06ab0038  06ab3be4 0x00003bac(15276)  
    Large object heap starts at 0x0cab0038  
     segment    begin allocated     size  
    0cab0000 0cab0038  0cab0048 0x00000010(16)  
    Heap Size    0x3bbc(15292)  
    ------------------------------  
    GC Heap Size   0x24db8(150968)  
    ```  
  
     Adresy indikován "segmentu" jsou počáteční adresy segmentů.  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a>Chcete-li zjistit velké objekty v 2. generace  
  
-   V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:  
  
     **! dumpheap-stat**  
  
     Pokud je spravované haldy velkých objemů, **dumpheap** může chvíli trvat dokončení.  
  
     Je mohli začít analyzovat během posledních několik řádků výstupu, protože jsou vypsány objekty, které používají nejvíce místa. Příklad:  
  
    ```  
    2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo  
    00155f80      533     15216804      Free  
    7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary  
    2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo  
    79124228   121143     29064120 System.Object[]  
    035f0ee4    81626     35588936 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    40182     90664128 System.Collections.Hashtable+bucket[]  
    790fa3e0  3154024    137881448 System.String  
    Total 8454945 objects  
    ```  
  
     Poslední objekt uvedené je řetězec a zabírá nejvíce místa. Můžete zkontrolovat aplikace, abyste viděli, jak se dá optimalizovat řetězcových objektů. Zobrazit řetězce, které jsou v rozmezí od 150 až 200 bajtů, zadejte následující příkaz:  
  
     **! dumpheap-zadejte 150 - max -min System.String 200**  
  
     Příklad výsledků je následujícím způsobem.  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     Místo celého čísla na řetězec pro ID může být efektivnější. Pokud stejný řetězec je opakováno tisíce časy, vezměte v úvahu interning řetězce. Další informace o interning řetězce, naleznete v referenčním tématu pro <xref:System.String.Intern%2A?displayProperty=nameWithType> metody.  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a>Chcete-li zjistit odkazy na objekty.  
  
-   V rámci WinDbg s příponou SOS ladicího programu, načíst zadejte následující příkaz pro seznam odkazů na objekty:  
  
     **! gcroot**  
  
     `-or-`  
  
-   Pokud chcete zjistit odkazy pro konkrétní objekt, patří adresu:  
  
     **! gcroot 1c37b2ac**  
  
     Kořeny na zásobníky může být falešně pozitivních výsledků. Další informace získáte pomocí příkazu `!help gcroot`.  
  
    ```  
    ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->  
    19010b78(DemoApp.FormDemoApp)->  
    19011158(System.Windows.Forms.PropertyStore)->  
    … [omitted]  
    1c3745ec(System.Data.DataTable)->  
    1c3747a8(System.Data.DataColumnCollection)->  
    1c3747f8(System.Collections.Hashtable)->  
    1c376590(System.Collections.Hashtable+bucket[])->  
    1c376c98(System.Data.DataColumn)->  
    1c37b270(System.Data.Common.DoubleStorage)->  
    1c37b2ac(System.Double[])  
    Scan Thread 0 OSTHread 99c  
    Scan Thread 6 OSTHread 484  
    ```  
  
     **Gcroot** příkazu může trvat delší dobu. Libovolný objekt, který není uvolněn systémem uvolňování paměti je objekt za provozu. To znamená, že některé kořenové je přímo nebo nepřímo držení objektu, takže **gcroot** by měl vrátit informace o cestě k objektu. By měl prozkoumat grafy vrátil a zobrazit, proč jsou tyto objekty stále odkazuje.  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Chcete-li zjistit, zda byla spuštěna finalizační metodu  
  
-   Spustit testovací program, který obsahuje následující kód:  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     Pokud test řeší problém, znamená to, že nebyl systému uvolňování paměti uvolní objektů, protože byla pozastavena finalizační metody týkajících se těchto objektů. <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metoda umožňuje finalizační metody pro dokončení úloh a vyřeší daný problém.  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Chcete-li zjistit, zda jsou objekty čekání na jejich dokončení  
  
1.  V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:  
  
     **! finalizequeue**  
  
     Podívejte se na počet objektů, které jsou připraveny k dokončení. Pokud je vysoké číslo, musíte prozkoumat proč tyto finalizační metody nemůže vůbec průběh nebo nelze průběh rychlé dostatečně.  
  
2.  Pokud chcete získat výstup vláken, zadejte následující příkaz:  
  
     **vlákna – speciální**  
  
     Tento příkaz zjistí výstupu, jako je následující.  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     Vlákno finalizační metody Určuje, které finalizační metodu, pokud existuje, je právě spuštěna. Pokud vlákno finalizační metodu neběží žádné finalizační metody, čeká událost určit, ke své práci. Ve většině případů se zobrazí vlákna finalizační metody v tomto stavu protože běží na THREAD_HIGHEST_PRIORITY a by měl dokončit spuštění finalizační metody, pokud existuje, velmi rychle.  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Chcete-li zjistit množství volného místa ve spravované haldě  
  
-   V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:  
  
     **! dumpheap-zadejte zdarma - stat**  
  
     Tento příkaz zobrazí celkovou velikost volné objekty na spravované haldě, jak je znázorněno v následujícím příkladu.  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   Pokud chcete zjistit volné místo v generaci 0, zadejte následující příkaz pro informace o využití paměti podle generace:  
  
     **! eeheap -gc**  
  
     Tento příkaz zobrazí výstup podobný následujícímu. Poslední řádek zobrazuje dočasný segment.  
  
    ```  
    Heap 0 (0015ad08)  
    generation 0 starts at 0x49521f8c  
    generation 1 starts at 0x494d7f64  
    generation 2 starts at 0x007f0038  
    ephemeral segment allocation context: none  
    segment  begin     allocated  size  
    00178250 7a80d84c  7a82f1cc   0x00021980(137600)  
    00161918 78c50e40  78c7056c   0x0001f72c(128812)  
    007f0000 007f0038  047eed28   0x03ffecf0(67103984)  
    3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)  
    46120000 46120038  49e05d04   0x03ce5ccc(63855820)  
    ```  
  
-   Vypočítejte místo používané 0. generace:  
  
     **? 49e05d04 0x49521f8c**  
  
     Výsledek je následující. Generace 0 je přibližně 9 MB.  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   Následující příkaz vypíše volného místa v rozsahu 0. generace:  
  
     **! dumpheap-zadejte zdarma - stat 0x49521f8c 49e05d04**  
  
     Výsledek je následující.  
  
    ```  
    ------------------------------  
    Heap 0  
    total 409 objects  
    ------------------------------  
    Heap 1  
    total 0 objects  
    ------------------------------  
    Heap 2  
    total 0 objects  
    ------------------------------  
    Heap 3  
    total 0 objects  
    ------------------------------  
    total 409 objects  
    Statistics:  
          MT    Count TotalSize Class Name  
    0015a498      409   7296540      Free  
    Total 409 objects  
    ```  
  
     Tento výstup ukazuje, že část haldy 0. generace používá 9 MB volného místa pro objekty a je 7 MB volného místa. Tato analýza ukazuje rozsahu, ke které generace 0 přispívá k fragmentaci. Toto množství využití haldy by měl odečtena od celkové částky jako Příčina fragmentace dlouhodobé objekty.  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a>Počet nepřesunutelných objektů  
  
-   V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:  
  
     **! GC**  
  
     Statistické údaje zobrazené zahrnuje počet připojených popisovačů, jak ukazuje následující příklad.  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>K určení délky času v uvolňování paměti  
  
-   Zkontrolujte `% Time in GC` čítače výkonu paměti.  
  
     Hodnota se počítá pomocí časový interval vzorku. Protože čítače se aktualizují na konci každé uvolňování paměti, aktuální ukázky budou mít stejnou hodnotu jako předchozí ukázce, pokud žádné kolekce došlo k chybě během intervalu.  
  
     Časem shromáždění vynásobením časový interval vzorku s procentuální hodnotu.  
  
     Následující data se zobrazí dvě sekund u 8 druhé studie čtyři intervalů vzorkování. `Gen0`, `Gen1`, A `Gen2` sloupce zobrazují počet uvolnění paměti, ke kterým došlo během tohoto intervalu pro tuto generaci.  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     Tyto informace se nezobrazuje, když došlo k uvolnění paměti, ale můžete určit počet uvolnění paměti, ke kterým došlo v časový interval. Za předpokladu, že nejhorší případ, desátý uvolnění paměti generace 0 dokončeno na začátku druhé interval a dokončení jedenáctý uvolnění paměti generace 0 na konci páté interval. Doba mezi koncem na desetinu a konec jedenáctý kolekce uvolnění paměti je přibližně 2 sekund a čítač výkonu zobrazuje 3 %, proto byla trvání jedenáctý kolekce uvolnění paměti generace 0 (% 2 sekundy * 3 = 60ms).  
  
     V tomto příkladu jsou 5 období.  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     Druhé generace 2 kolekce paměti během intervalu třetí a dokončení v pátém intervalu. Za předpokladu, že nejhorším případě, byl poslední uvolnění paměti 0. generace kolekce, který skončil na začátku druhý interval a generace 2 uvolňování dokončeno v čase konce páté intervalu. Doba mezi koncem kolekce uvolnění paměti generace 0 a na konci uvolnění paměti generace 2 je proto 4 sekundy. Vzhledem k tomu, `% Time in GC` čítač je 20 %, maximální množství času se generaci uvolňování paměti 2 mohou trvalo (4 sekundy * 20 % = 800ms).  
  
-   Alternativně můžete zjistit délku kolekce uvolnění paměti pomocí [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace k určení doby trvání uvolňování paměti.  
  
     Například následující data zobrazují sekvenci událostí, ke které došlo během nesouběžné uvolňování paměti.  
  
    ```  
    Timestamp    Event name  
    513052        GCSuspendEEBegin_V1  
    513078        GCSuspendEEEnd  
    513090        GCStart_V1  
    517890        GCEnd_V1  
    517894        GCHeapStats  
    517897        GCRestartEEBegin  
    517918        GCRestartEEEnd  
    ```  
  
     Pozastavování spravovaná vlákna trvalo 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).  
  
     Skutečné uvolňování trvalo 4.8ms (`GCEnd_V1` – `GCStart_V1`).  
  
     Obnovení spravovaných vláken trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).  
  
     Následující výstup představuje příklad, uvolňování paměti na pozadí a obsahuje pole procesu, vlákna a události. (Zobrazují se všechna data.)  
  
    ```  
    timestamp(us)    event name            process    thread    event field  
    42504385        GCSuspendEEBegin_V1    Test.exe    4372             1  
    42504648        GCSuspendEEEnd         Test.exe    4372          
    42504816        GCStart_V1             Test.exe    4372        102019  
    42504907        GCStart_V1             Test.exe    4372        102020  
    42514170        GCEnd_V1               Test.exe    4372          
    42514204        GCHeapStats            Test.exe    4372        102020  
    42832052        GCRestartEEBegin       Test.exe    4372          
    42832136        GCRestartEEEnd         Test.exe    4372          
    63685394        GCSuspendEEBegin_V1    Test.exe    4744             6  
    63686347        GCSuspendEEEnd         Test.exe    4744          
    63784294        GCRestartEEBegin       Test.exe    4744          
    63784407        GCRestartEEEnd         Test.exe    4744          
    89931423        GCEnd_V1               Test.exe    4372        102019  
    89931464        GCHeapStats            Test.exe    4372          
    ```  
  
     `GCStart_V1` Událost v 42504816 ukazuje na to, že se jedná uvolňování paměti na pozadí, protože poslední pole má `1`. Toto číslo změní uvolňování paměti 102019.  
  
     `GCStart` Události dochází, protože je potřeba pro kolekci uvolnění dočasné paměti před zahájením uvolňování na pozadí. Toto číslo změní uvolňování paměti 102020.  
  
     Při uvolňování paměti 42514170, číslo. 102020 dokončí. Spravovaná vlákna jsou v tomto okamžiku restartuje. To je dokončen ve vlákně 4372, která spustí tuto uvolňování paměti na pozadí.  
  
     Ve vlákně 4744 dojde k pozastavení. Toto je pouze doba, jakou má pozastavit spravovaná vlákna uvolňování na pozadí. Tato doba je přibližně 99ms ((63784407-63685394)/1000).  
  
     `GCEnd` Na 89931423 je událost pro uvolňování na pozadí. To znamená, že uvolňování na pozadí trvalo o 47seconds ((89931423-42504816)/1000).  
  
     Zatímco spravovaná vlákna jsou spuštěné, zobrazí se libovolný počet kolekcí uvolnění dočasné paměti, ke kterým dochází.  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a>Chcete-li zjistit, co vyvolalo uvolňování paměti  
  
-   V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz, který zobrazit všechna vlákna s jejich zásobníky volání:  
  
     **~\*znalostní báze**  
  
     Tento příkaz zobrazí výstup podobný následujícímu.  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     Pokud kolekce paměti bylo způsobené nedostatečnou pamětí oznámení z operačního systému, zásobník volání je podobné, s tím rozdílem, že vlákno je vlákna finalizační metody. Vlákno finalizační metodu získá oznámení o asynchronní nedostatek paměti a indukuje kolekce uvolnění paměti.  
  
     Pokud se uvolňování paměti kolekce byla způsobena přidělení paměti zásobníku se zobrazí takto:  
  
    ```  
    0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration  
    0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1  
    0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18  
    0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b  
    0012f310 7a02ae4c mscorwks!Alloc+0x60  
    0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd  
    0012f424 300027f4 mscorwks!JIT_NewArr1+0x148  
    000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c  
    0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153  
    ```  
  
     Pomocné rutiny just-in-time (`JIT_New*`) nakonec volá `GCHeap::GarbageCollectGeneration`. Pokud zjistíte, že kolekce uvolnění paměti generace 2 jsou způsobeny přidělení, je třeba určit objektů, které byly shromážděny sadou 2 uvolnění paměti generace a jak se jim vyhnout. To znamená, že budete chtít zjistit rozdíl mezi začátkem a koncem 2 uvolnění paměti generace a objekty, které způsobily 2. generace kolekce.  
  
     Například zadejte následující příkaz v ladicím programu zobrazíte od 2. generace kolekce:  
  
     **! dumpheap-stat**  
  
     Příklad výstupu (zkrácený komentář pro zobrazení objektů, které používají nejvíce místa):  
  
    ```  
    79124228    31857      9862328 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    00155f80    21248     12256296      Free  
    79103b6c   297003     13068132 System.Threading.ReaderWriterLock  
    7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary  
    7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    035f0ee4    89192     38887712 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    7912c444    91616     71887080 System.Double[]  
    791242ec    32451     82462728 System.Collections.Hashtable+bucket[]  
    790fa3e0  2459154    112128436 System.String  
    Total 6471774 objects  
    ```  
  
     Zopakujte příkaz na konci 2. generace:  
  
     **! dumpheap-stat**  
  
     Příklad výstupu (zkrácený komentář pro zobrazení objektů, které používají nejvíce místa):  
  
    ```  
    79124228    26648      9314256 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    79103b6c   296770     13057880 System.Threading.ReaderWriterLock  
    7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary  
    7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    00155f80    13806     34007212      Free  
    035f0ee4    89187     38885532 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    32370     82359768 System.Collections.Hashtable+bucket[]  
    790fa3e0  2440020    111341808 System.String  
    Total 6417525 objects  
    ```  
  
     `double[]` Objekty zmizí konci výstupu, což znamená, že byly shromážděny. Tyto objekty zohlednily přibližně 70 MB. Většinu zbývajících objektech nezměnil. Proto tyto `double[]` objekty byly důvod, proč došlo k této kolekce uvolnění paměti generace 2. Dalším krokem je zjistit, proč `double[]` objekty jsou existuje a proč se ukončila. Můžete požádat o kód vývojáře, kde tyto objekty pochází, nebo můžete použít **gcroot** příkazu.  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Chcete-li zjistit, jestli způsobuje vysoké využití procesoru uvolňování paměti  
  
-   Korelace `% Time in GC` hodnota čítače výkonu paměti s časem procesu.  
  
     Pokud `% Time in GC` hodnotu špičky ve stejnou dobu jako čas procesu, uvolňování paměti je příčinou vysoké využití procesoru. V opačném případě profilujte aplikaci, najít, kde dochází k vysoké využití.  
  
## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
