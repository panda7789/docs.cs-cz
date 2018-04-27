---
title: Kolekce paměti a výkon
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: daf70cdb7344f895059d0bc8b986edddbf7d53bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="garbage-collection-and-performance"></a>Kolekce paměti a výkon
<a name="top"></a> Toto téma popisuje problémy týkající se shromažďování a paměti využití paměti. Ho řeší problémy, které se týkají spravovaná halda a vysvětluje, jak, aby se minimalizoval vliv uvolňování paměti na vaše aplikace. Každý problém obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Nástrojů pro analýzu výkonu](#performance_analysis_tools)  
  
-   [Řešení potíží s výkonem](#troubleshooting_performance_issues)  
  
-   [Řešení potíží](#troubleshooting_guidelines)  
  
-   [Postupy kontroly výkonu](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a>Nástrojů pro analýzu výkonu  
 Následující části popisují nástroje, které jsou k dispozici pro příčin problémů kolekce paměti a využití paměti. [Postupy](#performance_check_procedures) později v tomto tématu najdete na těchto nástrojů.  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a>Čítače výkonu paměti  
 Čítače výkonu můžete použít ke shromažďování dat výkonu. Pokyny najdete v tématu [běhová profilace](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Využívání paměti rozhraním .NET CLR kategorie čítačů výkonu, jak je popsáno v [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o systému uvolňování paměti.  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a>Ladění pomocí SOS  
 Můžete použít [ladicí program systému Windows (WinDbg)](/windows-hardware/drivers/debugger/index) kontrola objekty v spravovaná halda.
 
 Nainstalovat WinDbg, nainstalovat ladění nástrojů pro Windows z [stáhnout ladění nástrojů pro Windows](/windows-hardware/drivers/debugger/debugger-download-tools) stránky.
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a>Události Trasování událostí pro Windows kolekci paměti  
 Trasování událostí pro Windows (ETW) je systém trasování, které doplňují profilování a ladění v rozhraní .NET Framework poskytuje podporu. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md) zaznamenat užitečné informace pro spravovaná halda z hlediska statistické analýze. Například `GCStart_V1` událost, která se vyvolá, když je kolekce paměti dojde, obsahuje následující informace:  
  
-   Které generování objektů, které jsou shromažďována.  
  
-   Co aktivuje uvolnění paměti.  
  
-   Typ kolekce paměti (souběžných nebo není souběžných).  
  
 Protokolování událostí trasování událostí pro Windows je efektivní a nebude maskování žádné problémy s výkonem přidružené uvolňování paměti. Proces můžete zadat vlastní události ve spojení s události trasování událostí. Při přihlášení, můžete určit, jak a kdy dojde k problémům haldy korelační události aplikace a události kolekce paměti. Serverová aplikace může například zadat události na začátku a na konci požadavku klienta.  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a>Rozhraní API pro profilaci  
 Běžné language runtime (CLR) profilování rozhraní poskytují podrobné informace o objekty, které během uvolňování situace měla vliv na. Kolekce paměti zahájení a ukončení, můžete být upozorněni profileru. Na spravované haldě, včetně identifikaci objektů v každé generování může poskytovat sestavy o objektech. Další informace najdete v tématu [přehled profilace](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).  
  
 Profilery může poskytovat komplexní informace. Komplexní profilery však mohou potenciálně změnit chování aplikace.  
  
### <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], prostředků domény aplikace monitorování (ARM) umožňuje hostitelům sledování využití procesoru a paměti aplikační doménou. Další informace najdete v tématu [sledování prostředků domény aplikace](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).  
  
 [Zpět na začátek](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a>Řešení potíží s výkonem  
 Prvním krokem je [určit, zda problém je ve skutečnosti uvolňování](#IsGC). Pokud zjistíte, že se jedná, vyberte z následujícího seznamu k vyřešení tohoto problému.  
  
-   [Je vyvolána výjimka z důvodu nedostatku paměti](#Issue_OOM)  
  
-   [Proces využívá příliš mnoho paměti](#Issue_TooMuchMemory)  
  
-   [Uvolňování paměti nezíská objekty dostatečně rychle](#Issue_NotFastEnough)  
  
-   [Spravovaná halda je příliš fragmentovaná.](#Issue_Fragmentation)  
  
-   [Jsou příliš dlouhé pozastaví kolekce paměti](#Issue_LongPauses)  
  
-   [Generace 0 je příliš velký.](#Issue_Gen0)  
  
-   [Využití procesoru během uvolňování paměti je příliš vysoká.](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problém: Je vyvolána výjimka z důvodu nedostatku paměti  
 Existují dvě legitimní případů pro spravované <xref:System.OutOfMemoryException> vyvolání:  
  
-   Nedostatek virtuální paměti.  
  
     Uvolňování paměti přidělí paměť ze systému v segmentech předem určená velikost. Pokud přidělení vyžaduje další segment, ale neexistuje žádné souvislý volné blok left v prostoru virtuální paměti procesu, přidělení pro spravovaná halda se nezdaří.  
  
-   Nemá dost fyzické paměti k přidělení.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určete, zda je spravovat výjimky nedostatku paměti.](#OOMIsManaged)<br /><br /> [Určete, kolik virtuální paměti může být vyhrazeno.](#GetVM)<br /><br /> [Určí, zda je dostatek fyzické paměti.](#Physical)|  
  
 Pokud zjistíte, že výjimka není oprávněné, obraťte se na Microsoft zákaznický servis a podporu s následujícími informacemi:  
  
-   Zásobník s spravované výjimky nedostatku paměti.  
  
-   Úplný výpis stavu paměti.  
  
-   Data, která prokáže, že se nejedná o potřebné výjimky nedostatku paměti, včetně dat, která ukazuje, že virtuální nebo fyzická paměť není problém.  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a>Problém: Proces využívá příliš mnoho paměti  
 Běžné předpokladem je, že zobrazení využití paměti na **výkonu** karty Správce úloh systému Windows může naznačit, když se používá příliš mnoho paměti. Ale zobrazované se vztahují na pracovní sady; neobsahuje informace o využití virtuální paměti.  
  
 Pokud zjistíte, že problém je způsoben spravovaná halda, musí měření spravovaná halda v čase k určení všech vzory.  
  
 Pokud zjistíte, že není spravovaná halda příčinou problému, je nutné použít nativní ladění.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určete, kolik virtuální paměti může být vyhrazeno.](#GetVM)<br /><br /> [Určete, kolik paměti je spravovaná halda potvrzení.](#ManagedHeapCommit)<br /><br /> [Určete, kolik paměti si vyhrazuje spravovaná halda.](#ManagedHeapReserve)<br /><br /> [Určení rozsáhlé objekty v 2. generace.](#ExamineGen2)<br /><br /> [Určí, odkazy na objekty.](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problém: Uvolňování nezíská objekty dostatečně rychle  
 Jakmile se zobrazí, jako kdyby objekty nejsou převzata podle očekávání pro uvolňování paměti, je třeba určit, zda jsou všechny silné odkazy na tyto objekty.  
  
 Tento problém může se zobrazit, pokud byl žádné uvolňování paměti pro generování, která obsahuje objekt neaktivní, který označuje, že finalizační metodu pro neaktivní objekt nebyl spuštěn. Například to je možné při spouštění aplikace single-threaded apartment (STA) a vlákno této služby, které nelze volat finalizační metodu fronty do ní.  
  
|Kontroly výkonu|  
|------------------------|  
|[Zkontrolujte odkazy na objekty.](#ObjRef)<br /><br /> [Určí, zda byl spuštěn finalizační metody.](#Induce)<br /><br /> [Zjistěte, jestli jsou objekty čekají na Dokončit.](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problém: Je spravovaná halda je příliš fragmentovaná.  
 Úroveň fragmentace se vypočítá jako podíl volné místo přes celkové přidělené paměti pro generování. Přijatelnou úroveň fragmentace pro 2. generace, je více než 20 %. Vzhledem k tomu, že generace 2 můžete získat velmi velkých poměr fragmentace je důležitější než absolutní hodnotu.  
  
 S velké množství volného místa ve generace 0 se nejedná o problém protože to je generace, kde jsou přiděleny nové objekty.  
  
 Není zkomprimovanou bude vždy fragmentace dochází v haldě velkého objektu. Volné objekty, které jsou přiléhající přirozeně sbalené do jednoho místa pro uspokojení požadavků na přidělení velkého objektu.  
  
 Fragmentace se může stát problém v generace 1 a generace 2. Pokud tyto generace máte velké množství volného místa po uvolnění paměti, využití aplikace objektu může být nutné změny a měli byste zvážit, znovu vyhodnocení dobu trvání dlouhodobé objektů.  
  
 Nadměrné Připnutí objektů může zvýšit fragmentace. Pokud fragmentace vysoké, může být připnuli příliš mnoho objektů.  
  
 Pokud fragmentace virtuální paměti znemožňuje přidávání segmenty uvolňování paměti, může být příčin jednu z těchto možností:  
  
-   Časté načítání a uvolňování mnoho malých sestavení.  
  
-   Když spolupráce s nespravovaným kódem, který uchovává příliš mnoho odkazů na objekty modelu COM.  
  
-   Vytváření rozsáhlé přechodný objekty, což způsobí, že velkého objektu haldy alokace a často volné haldy segmenty.  
  
     Aplikace hostování CLR, může požádat o, bude systém uvolňování zachovali jeho segmenty. Tím se snižuje frekvence přidělení segmentu. To lze provést pomocí příznaku STARTUP_HOARD_GC_VM v [STARTUP_FLAGS – výčet](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
|Kontroly výkonu|  
|------------------------|  
|[Určete množství volného místa v spravovaná halda.](#Fragmented)<br /><br /> [Určete počet připojených objektů.](#Pinned)|  
  
 Pokud si myslíte, že neexistuje žádná legitimní příčinu fragmentaci, obraťte se na oddělení zákaznických služeb a podpory.  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problém: Jsou příliš dlouhé pozastaví kolekce paměti  
 Uvolňování paměti funguje v reálném čase logicky, takže aplikace musí být schopen tolerovat možnost, zastaví se některé. Kritéria pro logicky reálném čase je, že 95 % operací musí dokončit v době.  
  
 V souběžné uvolňování paměti je povoleno spustit během kolekce, což znamená, že jsou velmi minimální pozastaví spravovaných vláknech.  
  
 Dočasné kolekce (generace 0 a 1) poslední pouze několik milisekund, takže snížení pozastaví obvykle není možné je. Však může snížit pozastaví v 2. generace kolekce tak, že změníte vzorec, podle požadavků na přidělení jiná aplikace.  
  
 Jiné, přesnější, metodou je použití [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md). Přidáním časové razítko rozdíly pro posloupnost událostí, můžete najít časování pro kolekce. Pořadí celé kolekce obsahuje pozastavení modul provádění, samotná kolekce paměti a obnovení modulu provádění.  
  
 Můžete použít [oznámení pro uvolňování paměti](../../../docs/standard/garbage-collection/notifications.md) určit, zda server dojde ke kolekci 2. generace a jestli přesměrování spojnic požadavky na jiný server by mělo odlehčit případné potíže s pozastaví.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určete dobu v uvolnění paměti.](#TimeInGC)<br /><br /> [Určete, co způsobilo uvolnění paměti.](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a>Problém: 0. generace je příliš velký.  
 Generace 0 je mohou mít větší počet objektů na 64bitovém systému, zejména v případě, že místo uvolňování paměti pracovních stanic použijete kolekce paměti na serveru. Je to proto, že je vyšší v těchto prostředích prahové hodnoty pro aktivaci uvolňování 0. generace a 0. generace kolekce může získat mnohem větší. Výkon je vyšší, pokud aplikace přiděluje víc paměti než se aktivuje uvolňování paměti.  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problém: Využití procesoru během uvolňování paměti je příliš vysoká.  
 Během uvolňování paměti bude vysoké využití procesoru. Pokud významné množství času procesu je věnovaný uvolnění paměti, počet kolekcí, je příliš časté nebo kolekce je trvá příliš dlouho. Počet objektů na spravovaná halda vyšší přidělení způsobí, že uvolňování paměti častěji. Snížení míry přidělení snižuje frekvence kolekce.  
  
 Přidělení sazby můžete monitorovat pomocí `Allocated Bytes/second` čítače výkonu. Další informace najdete v tématu [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
 Doba trvání v kolekci je primárně faktor počet objektů, které zůstanou platné i po po přidělení. Uvolňování paměti musí projít velké množství paměti, pokud zůstanou mnoho objektů, které se mají shromažďovat. Pracovní kompaktních přesun je časově náročná. Pokud chcete zjistit, kolik objekty byly zpracovány během kolekce, nastavte zarážky v ladicím programu na konci uvolňování paměti pro zadané generaci.  
  
|Kontroly výkonu|  
|------------------------|  
|[Určí, pokud vysoké využití procesoru je způsobena uvolňování paměti.](#HighCPU)<br /><br /> [Nastavte zarážky na konci uvolňování paměti.](#GenBreak)|  
  
 [Zpět na začátek](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a>Řešení potíží  
 Tato část popisuje pokyny, které byste měli zvážit při začnete vaší šetření.  
  
### <a name="workstation-or-server-garbage-collection"></a>Pracovní stanice nebo kolekce paměti na serveru  
 Určí, pokud používáte správný typ uvolňování paměti. Pokud vaše aplikace používá více vláken a instance objektů, použijte místo uvolňování paměti pracovních stanic kolekce paměti na serveru. Kolekce paměti na serveru funguje na více vláken, zatímco vyžaduje více instancí aplikace ke spuštění vlastní vláken kolekce paměti a pokouší o čas procesoru uvolňování paměti pracovních stanic.  
  
 Aplikace, který má nízkou zatížení a které provádí úlohy zřídka v pozadí, třeba služby, použít uvolňování paměti pracovních stanic s souběžné uvolňování zakázána.  
  
### <a name="when-to-measure-the-managed-heap-size"></a>Když pro měření velikosti spravovaná halda  
 Pokud používáte profileru, budete muset vytvořit konzistentní měřicí vzor efektivně diagnostikovat problémy s výkonem. Mějte na paměti následující body k vytvoření plánu:  
  
-   Pokud budete vyhodnocovat po uvolnění paměti generace 2, celý spravovaná halda je bezplatná paměti (neaktivní objekty).  
  
-   Pokud budete vyhodnocovat okamžitě po uvolnění paměti generace 0, nebudou shromažďovány ještě objekty v generace 1 a 2.  
  
-   Pokud budete vyhodnocovat bezprostředně před uvolnění paměti, budou měřit tolik přidělení nejdříve, před zahájením uvolnění paměti.  
  
-   Měření během uvolňování paměti je problematické, protože nejsou v platném stavu pro traversal datové struktury systém uvolňování paměti a nemusí být možné tak, abyste získali výsledků. Toto je záměrné.  
  
-   Při použití uvolňování paměti pracovních stanic s souběžné uvolňování paměti, nejsou regenerovaný objekty komprimován, takže velikost haldy může být stejné nebo větší (fragmentace může vypadat musí být větší).  
  
-   Souběžné uvolňování paměti v generaci 2 je zpožděno. při zatížení fyzická paměť je příliš vysoká.  
  
 Následující postup popisuje, jak nastavit bod přerušení, můžete změřit spravovaná halda.  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Chcete-li nastavit zarážky na konci uvolňování paměti  
  
-   V WinDbg s příponou ladicí program SOS načíst zadejte následující příkaz:  
  
     **BP mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2), kb';' g. "**  
  
     kde **GcCondemnedGeneration** nastavená na požadované generování. Tento příkaz vyžaduje soukromých symbolů.  
  
     Tento příkaz vynutí zalomení, když **RestartEE** se spustí po objekty 2. generace bylo uvolněno pro uvolňování paměti.  
  
     Kolekce paměti na serveru, volá pouze jedno vlákno **RestartEE**, takže zarážce během uvolňování paměti 2. generace dojde pouze jednou.  
  
 [Zpět na začátek](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a>Postupy kontroly výkonu  
 Tato část popisuje následující postup najít příčinu problém výkonu:  
  
-   [Určí, zda je problém způsoben uvolňování paměti.](#IsGC)  
  
-   [Určete, zda je spravovat výjimky nedostatku paměti.](#OOMIsManaged)  
  
-   [Určete, kolik virtuální paměti může být vyhrazeno.](#GetVM)  
  
-   [Určí, zda je dostatek fyzické paměti.](#Physical)  
  
-   [Určete, kolik paměti je spravovaná halda potvrzení.](#ManagedHeapCommit)  
  
-   [Určete, kolik paměti si vyhrazuje spravovaná halda.](#ManagedHeapReserve)  
  
-   [Určení rozsáhlé objekty v 2. generace.](#ExamineGen2)  
  
-   [Určí, odkazy na objekty.](#ObjRef)  
  
-   [Určí, zda byl spuštěn finalizační metody.](#Induce)  
  
-   [Zjistěte, jestli jsou objekty čekají na Dokončit.](#Finalize)  
  
-   [Určete množství volného místa v spravovaná halda.](#Fragmented)  
  
-   [Určete počet připojených objektů.](#Pinned)  
  
-   [Určete dobu v uvolnění paměti.](#TimeInGC)  
  
-   [Zjistěte, co aktivuje uvolnění paměti.](#Triggered)  
  
-   [Určí, zda vysoké využití procesoru je způsobena uvolňování paměti.](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Chcete-li zjistit, zda je problém způsoben uvolňování paměti  
  
-   Zkontrolujte následující čítače výkonu dvě paměti:  
  
    -   **Čas**. Zobrazuje procentuální hodnotu uplynulého času stráveného provádění úklidu po poslední cyklus sběru uvolňování paměti. Tento čítač slouží k určení, zda má systém uvolňování tráví příliš mnoho času, aby spravovaná halda místo k dispozici. Pokud čas strávený v uvolňování paměti je relativně nízký, který by to znamenat problém prostředků mimo spravovaná halda. Tento čítač nemusí být přesné při souběžných nebo je zahrnuta kolekce paměti na pozadí.  
  
    -   **# Celkový počet potvrzených bajtů**. Zobrazuje velikost virtuální paměti aktuálně potvrzeno modulem garbage collector. Tento čítač použijte k určení, zda je paměť spotřebovávají uvolňování nadměrné část paměti, která vaše aplikace používá.  
  
     Většina čítačů výkonu paměti jsou aktualizovány na konci každé uvolňování paměti. Proto nemusí odráží aktuální podmínky, které chcete získat informace o.  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Chcete-li zjistit, jestli je spravovaný výjimky nedostatku paměti  
  
1.  V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst, zadejte v tiskové výjimky (**pe**) příkaz:  
  
     **! pe**  
  
     Pokud je spravováno výjimku, <xref:System.OutOfMemoryException> zobrazí jako typ výjimky, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2.  Pokud výstup neurčuje výjimku, budete muset určit, které vlákno výjimky nedostatku paměti je z. Zadejte následující příkaz v ladicím programu zobrazíte všechna vlákna s jejich zásobníky volání:  
  
     **~\*kb**  
  
     Vlákno se zásobníkem, který má výjimka volání je indikován `RaiseTheException` argument. Toto je objekt spravované výjimky.  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3.  Tento příkaz můžete dump vnořené výjimky.  
  
     **! pe-vnořené**  
  
     Pokud nenajdete žádné výjimky, výjimky nedostatku paměti pochází z nespravovaného kódu.  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Chcete-li zjistit, kolik virtuální paměti může být vyhrazeno  
  
-   V WinDbg s příponou ladicí program SOS načíst zadejte následující příkaz k získání největší volné oblasti:  
  
     **! adres – souhrn**  
  
     Největší volné oblasti se zobrazí, jak je znázorněno v následující výstup.  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové). Tato oblast je mnohem menší než jaké uvolňování potřebuje pro segment.  
  
     -nebo-  
  
-   Použití **vmstat** příkaz:  
  
     **! vmstat**  
  
     Největší volné oblast je největší hodnotu ve sloupci maximální, jak je znázorněno v následující výstup.  
  
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
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Chcete-li určit, zda je dostatek fyzické paměti  
  
1.  Spuštění Správce úloh systému Windows.  
  
2.  Na **výkonu** kartě, podívejte se na potvrzení hodnotu. (V systému Windows 7, podívejte se na **potvrzení (KB)** v **systémové skupiny**.)  
  
     Pokud **celkový** blízko **Limit**, je málo na fyzické paměti.  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Chcete-li určit, kolik paměti je potvrzením spravovaná halda  
  
-   Použití `# Total committed bytes` čítače výkonu paměti získat počet bajtů, které je spravovaná halda potvrzení. Uvolňování paměti potvrdí bloků v segmentu, podle potřeby, ne všechny ve stejnou dobu.  
  
    > [!NOTE]
    >  Nepoužívejte `# Bytes in all Heaps` čítače výkonu, protože nepředstavuje skutečné využití paměti podle spravovaná halda. Velikost generace je součástí tuto hodnotu a je ve skutečnosti jeho velikost mezní hodnoty, to znamená, velikost, kterou indukuje uvolnění paměti-li generování objektů. Tato hodnota je proto obvykle nula.  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Chcete-li určit, kolik paměti si vyhrazuje spravovaná halda  
  
-   Použití `# Total reserved bytes` čítače výkonu paměti.  
  
     Rezervuje má systém uvolňování paměti v segmentech, a můžete určit, kde segment spustí pomocí **eeheap** příkaz.  
  
    > [!IMPORTANT]
    >  I když může určit množství paměti, kterou uvolňování paměti přidělí pro každý segment, velikost segmentu závisí na implementaci a mohou podléhat změnám kdykoli, včetně v pravidelné aktualizace. Vaše aplikace by nikdy Zkontrolujte předpoklady o nebo závisí na velikosti určitý segment, ani pokusit nakonfigurovat množství paměti k dispozici pro přidělení segmentu.  
  
-   V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:  
  
     **! eeheap – uvolňování paměti**  
  
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
  
     Adresy indikován "segment" jsou počáteční adresy segmentů.  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a>Chcete-li zjistit rozsáhlé objekty v 2. generace  
  
-   V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:  
  
     **! dumpheap – stat**  
  
     Pokud je příliš velká, spravovaná halda **dumpheap** může trvat dokončení.  
  
     Můžete začít analýza za posledních několika řádků výstupu, protože jejich seznam objektů, které používají nejvíce místa. Příklad:  
  
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
  
     Poslední objekt uvedené je řetězec a zabírá nejvíce místa. Můžete zkontrolovat aplikace, abyste viděli, jak lze optimalizovat řetězcových objektů. Pokud chcete zobrazit řetězce, které jsou v rozmezí od 150 až 200 bajtů, zadejte následující příkaz:  
  
     **! dumpheap-zadejte 150 - max -min System.String 200**  
  
     Příklad výsledků je následující.  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     Pomocí celé místo řetězec pro ID může být efektivnější. Pokud do jednoho řetězce je opakováno tisíce časy, vezměte v úvahu interning řetězec. Další informace o řetězce interning najdete v tématu referenční téma pro <xref:System.String.Intern%2A?displayProperty=nameWithType> metoda.  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a>Chcete-li zjistit odkazy na objekty  
  
-   V WinDbg s příponou ladicí program SOS načíst zadejte následující příkaz, který seznamu odkazů na objekty:  
  
     **! gcroot**  
  
     `-or-`  
  
-   Pokud chcete zjistit odkazy pro konkrétní objekt, patří adresu:  
  
     **! gcroot 1c37b2ac**  
  
     Kořeny najít na zásobníky může být falešně pozitivních zjištění. Další informace získáte pomocí příkazu `!help gcroot`.  
  
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
  
     **Gcroot** příkaz může trvat dlouhou dobu na Dokončit. Libovolný objekt, který není uvolněn systémem uvolňování paměti je objekt za provozu. To znamená, že některé kořenová je přímo nebo nepřímo přidržte na objekt, takže **gcroot** by měla vrátit informace o cestě k objektu. Měli byste zkontrolujte grafy vrátil a najdete v části Proč stále odkazují tyto objekty.  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Chcete-li zjistit, zda byl spuštěn finalizační metody  
  
-   Spusťte program test, který obsahuje následující kód:  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     Pokud test řeší problém, znamená to, zda má systém uvolňování nebyl opětovného získání objekty, protože finalizační metody pro tyto objekty měl bylo pozastaveno. <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metoda umožňuje finalizační metody k dokončení úkolů a opravy problému.  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Chcete-li určit, jestli jsou objekty čekají na Dokončit.  
  
1.  V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:  
  
     **! finalizequeue**  
  
     Podívejte se na počet objektů, které jsou připravené pro dokončení. Pokud je číslo vysoké, musíte prozkoumat Proč nelze tyto finalizační metody průběhu vůbec nebo nelze průběh rychlý dostatečně.  
  
2.  Chcete-li získat výstup vláken, zadejte následující příkaz:  
  
     **vláken - speciální**  
  
     Tento příkaz poskytuje výstupu, jako následující.  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     Vlákno finalizační metodu Určuje, které finalizační metodu, pokud existuje, je právě spuštěna. Pokud vlákno finalizační metodu neběží žádné finalizační metody, čeká na událost můžete určit, aby jeho práci. Ve většině případů se zobrazí finalizační metodu vlákno v tomto stavu protože spouští v THREAD_HIGHEST_PRIORITY a má spuštěn finalizační metody, pouze pokud existuje, velmi rychle.  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Chcete-li zjistit množství volného místa v spravovaná halda  
  
-   V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:  
  
     **! dumpheap-Free - zadejte stat**  
  
     Tento příkaz zobrazí celková velikost všech volné objektů na spravované haldě, jak je znázorněno v následujícím příkladu.  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   K určení volné místo v 0. generace, zadejte následující příkaz pro informace spotřeba paměti podle generace:  
  
     **! eeheap – uvolňování paměti**  
  
     Tento příkaz zobrazí výstup podobný následujícímu. Poslední řádek ukazuje dočasné segmentu.  
  
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
  
-   Vypočítejte místo využité generace 0:  
  
     **? 49e05d04 0x49521f8c**  
  
     Výsledek je následující. Generace 0 je přibližně 9 MB.  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   Tento příkaz vypíše volné místo v rozsahu 0. generace:  
  
     **! dumpheap-typu Free - stat 0x49521f8c 49e05d04**  
  
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
  
     Výstup ukazuje, že část generace 0 halda používá 9 MB volného místa pro objekty a že má 7 MB volného místa. Tato analysis zobrazuje v rozsahu, ke kterému generace 0 přispívá k fragmentace. Toto množství používání haldy by měl odečtena od celkové jako příčinu fragmentace dlouhodobé objekty.  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a>K určení počtu připojených objektů  
  
-   V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:  
  
     **! gchandles**  
  
     Statistické údaje zobrazené zahrnuje počet popisovačů definovaného, jak ukazuje následující příklad.  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Určit dobu v kolekci paměti  
  
-   Zkontrolujte `% Time in GC` čítače výkonu paměti.  
  
     Hodnota se počítá pomocí vzorovému časovému intervalu. Protože čítače jsou aktualizovány na konci každé uvolňování aktuální Ukázka bude mít stejnou hodnotu jako v předchozím příkladu, pokud žádné kolekce došlo k chybě během intervalu.  
  
     Čas kolekci je dána vynásobením časový interval vzorku s procentuální hodnotu.  
  
     Následující data znázorňuje čtyři během intervalů vzorkování dvou sekund pro studie 8 sekundu. `Gen0`, `Gen1`, A `Gen2` sloupcích se zobrazují počet kolekce, k nimž došlo během tohoto intervalu pro této generaci.  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     Tyto informace se nezobrazuje, pokud došlo k uvolnění paměti, ale můžete určit počet kolekce, k nimž došlo v časový interval. Za předpokladu, že nejhorším případě, desetinu 0 uvolnění paměti generace dokončen na začátku druhé intervalu a jedenáctá 0 uvolnění paměti generace dokončení na konci páté intervalu. Doba mezi koncem na desetinu a konec jedenáctá uvolňování je o 2 sekund a čítač výkonu zobrazuje 3 %, byl trvání jedenáctá 0. generace uvolňování (% 2 sekundy * 3 = 60ms).  
  
     V tomto příkladu jsou 5 tečky.  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     Druhé generace uvolňování 2 během třetí intervalu spuštění a dokončení v páté intervalu. Za předpokladu, že nejhorším případě, byl poslední uvolnění paměti pro generování 0 kolekci, která dokončení na začátku druhé interval a generace 2 uvolňování dokončil na konci páté interval. Doba mezi koncem uvolňování generace 0 a konec uvolňování generace 2 je proto 4 sekundy. Protože `% Time in GC` čítač je 20 %, maximální množství času je generace 2 uvolňování paměti může provedených (4 sekundy * 20 % = 800ms).  
  
-   Alternativně můžete zjistit délku uvolnění paměti pomocí [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace k určení doby trvání uvolnění paměti.  
  
     Například následující data zobrazují v sekvenci událostí, které došlo během nesouběžného uvolňování paměti.  
  
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
  
     Pozastavení spravované vlákno trvalo 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).  
  
     Skutečné uvolňování trvalo 4.8ms (`GCEnd_V1` – `GCStart_V1`).  
  
     Obnovení spravovaných vláknech trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).  
  
     Následující výstup představuje příklad kolekce paměti na pozadí a obsahuje proces, vlákna a pole událostí. (Všechna data budou zobrazeny.)  
  
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
  
     `GCStart_V1` Událost v 42504816 označuje, že to je uvolňování paměti na pozadí, protože je poslední pole `1`. To se stane uvolňování ne. 102019.  
  
     `GCStart` Události dojde, protože je potřeba uvolnění dočasné paměti před zahájením uvolňování paměti na pozadí. To se stane uvolňování ne. 102020.  
  
     Při uvolňování 42514170, číslo. 102020 dokončení. V tomto okamžiku se restartují spravovaných vláknech. To uděláte ve vlákně 4372, která spustí této kolekce paměti na pozadí.  
  
     Ve vlákně 4744 dojde k pozastavení. Toto je pouze čas, kdy má uvolňování paměti na pozadí na pozastavení spravovaných vláknech. Tato doba trvání je přibližně 99ms ((63784407-63685394)/1000).  
  
     `GCEnd` Je událost pro uvolňování paměti na pozadí na 89931423. To znamená, že uvolňování paměti na pozadí trvala o 47seconds ((89931423-42504816)/1000).  
  
     Při spravovaných vláknech, uvidíte libovolný počet kolekcí dočasné paměti, ke kterým dochází.  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a>Chcete-li zjistit, co aktivaci kolekce paměti  
  
-   V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz zobrazíte všechna vlákna s jejich zásobníky volání:  
  
     **~\*kb**  
  
     Tento příkaz zobrazí výstup podobný následujícímu.  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     Pokud kolekce paměti bylo způsobeno nedostatečnou pamětí oznámení z operačního systému, zásobníku volání je podobné, s tím rozdílem, že vlákno se vlákno finalizační metodu. Vlákno finalizační metodu získá oznámení o asynchronní nedostatek paměti a indukuje uvolnění paměti.  
  
     Pokud kolekce paměti bylo způsobeno přidělení paměti, zobrazí se následující zásobník:  
  
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
  
     Pomocné rutiny za běhu (`JIT_New*`) nakonec volá `GCHeap::GarbageCollectGeneration`. Pokud zjistíte, že generace 2 kolekce jsou způsobeny přidělení, musíte určit objektů, které byly shromážděny sadou uvolňování 2. generace a jak se vyhnout je. To znamená, že budete chtít určení rozdílu mezi začátku a konci generace 2 uvolňování paměti a objekty, které způsobilo 2. generace kolekce.  
  
     Například zadejte následující příkaz v ladicím programu zobrazíte začátek 2. generace kolekce:  
  
     **! dumpheap – stat**  
  
     Příklad výstupu (zkrácený komentář zobrazit objekty, které používají nejvíce místa na):  
  
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
  
     Zopakujte příkaz na konci generace 2:  
  
     **! dumpheap – stat**  
  
     Příklad výstupu (zkrácený komentář zobrazit objekty, které používají nejvíce místa na):  
  
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
  
     `double[]` Objekty smazán od konce výstup, což znamená, že byly shromážděny. Tyto objekty účtu pro přibližně 70 MB. Zbývající objekty mnohem nezměnila. Proto tyto `double[]` objekty byly z důvodu, proč tento 2. generace uvolňování paměti došlo k chybě. Dalším krokem je určit, proč `double[]` objekty jsou existuje a proč se ukončilo činnost. Můžete požádat kód vývojáře, kde tyto objekty pochází, nebo můžete použít **gcroot** příkaz.  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Chcete-li zjistit, zda vysoké využití procesoru je způsobena uvolňování paměti  
  
-   Korelovat `% Time in GC` hodnota čítače výkonu paměti s doba zpracování.  
  
     Pokud `% Time in GC` hodnota špičky ve stejnou dobu jako doba zpracování, uvolňování paměti je příčinou vysoké využití procesoru. Profil aplikace místo, kde dochází k vysoké využití, jinak hodnota  
  
## <a name="see-also"></a>Viz také  
 [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
