---
title: Uvolnění paměti a výkon
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 72cf742aae26f9441229b355dc6e70da7a5fc9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75900585"
---
# <a name="garbage-collection-and-performance"></a>Uvolnění paměti a výkon

Toto téma popisuje problémy související s uvolňovánípaměti a využití paměti. Řeší problémy, které se týká spravované haldy a vysvětluje, jak minimalizovat vliv uvolňování paměti na vaše aplikace. Každý problém obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.

## <a name="performance-analysis-tools"></a>Nástroje pro analýzu výkonu

Následující části popisují nástroje, které jsou k dispozici pro zkoumání využití paměti a uvolňování paměti problémy. [Postupy](#performance-check-procedures) uvedené dále v tomto tématu odkazují na tyto nástroje.

### <a name="memory-performance-counters"></a>Čítače výkonu paměti

Čítače výkonu můžete použít ke shromažďování dat o výkonu. Pokyny naleznete v [tématu Runtime Profilování](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Kategorie výkonu .NET CLR memory, jak je popsáno v [čítačích výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o systému uvolňování paměti.

### <a name="debugging-with-sos"></a>Ladění pomocí SOS

Ladicí [program systému Windows (WinDbg)](/windows-hardware/drivers/debugger/index) můžete použít ke kontrole objektů na spravované haldě.

Chcete-li nainstalovat aplikaci WinDbg, nainstalujte nástroje pro ladění pro systém Windows na stránce [Nástroje pro stažení ladění pro systém Windows.](/windows-hardware/drivers/debugger/debugger-download-tools)

### <a name="garbage-collection-etw-events"></a>Události Trasování událostí pro Windows uvolnění paměti

Trasování událostí pro Windows (ETW) je systém trasování, který doplňuje podporu profilování a ladění poskytovanou rozhraním .NET Framework. Počínaje rozhraním .NET Framework 4, [události uvolňování paměti ETW](../../../docs/framework/performance/garbage-collection-etw-events.md) zachycují užitečné informace pro analýzu spravované haldy ze statistického hlediska. Například `GCStart_V1` událost, která je vyvolána, když dojde k uvolnění paměti, poskytuje následující informace:

- Generování objektů jsou shromažďovány.

- Co spustilo uvolňování paměti.

- Typ uvolňování paměti (souběžné nebo ne souběžné).

Protokolování událostí ETW je efektivní a nebude maskovat žádné problémy s výkonem spojené s uvolňování paměti. Proces může poskytnout své vlastní události ve spojení s událostmi ETW. Při protokolování události aplikace a události uvolňování paměti může být korelován k určení, jak a kdy dochází k problémům haldy. Serverová aplikace může například poskytnout události na začátku a na konci požadavku klienta.

### <a name="the-profiling-api"></a>Rozhraní API profilování

Rozhraní profilování clr (COMMON Language runtime) poskytují podrobné informace o objektech, které byly ovlivněny během uvolňování paměti. Profiler může být upozorněni při uvolnění paměti začíná a končí. Může poskytovat sestavy o objektech na spravované haldě, včetně identifikace objektů v každé generaci. Další informace naleznete [v tématu Přehled profilování](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).

Profilovací programy mohou poskytovat komplexní informace. Komplexní profilovací programy však mohou potenciálně upravit chování aplikace.

### <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace

Počínaje rozhraním .NET Framework 4 umožňuje monitorování prostředků domény aplikace (ARM) hostitelům monitorovat využití procesoru a paměti podle domény aplikace. Další informace naleznete v [tématu Application Domain Resource Resource .](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)

## <a name="troubleshooting-performance-issues"></a>Poradce při potížích s výkonem

Prvním krokem je [zjistit, zda je problém skutečně uvolňování paměti](#IsGC). Pokud zjistíte, že tomu tak je, vyberte z následujícího seznamu k řešení problému.

- [Je vyvolána výjimka z nedostatku paměti.](#Issue_OOM)

- [Tento proces používá příliš mnoho paměti](#Issue_TooMuchMemory)

- [Systém uvolňování paměti neuvolněny objekty dostatečně rychle](#Issue_NotFastEnough)

- [Spravovaná halda je příliš fragmentovaná.](#Issue_Fragmentation)

- [Pozastavení uvolňování paměti jsou příliš dlouhé](#Issue_LongPauses)

- [Generace 0 je příliš velká](#Issue_Gen0)

- [Využití procesoru během uvolňování paměti je příliš vysoká](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problém: Je vyvolána výjimka z nedostatku paměti.

Existují dva legitimní případy <xref:System.OutOfMemoryException> pro podařilo být hozen:

- Dochází virtuální paměť.

  Systém uvolňování paměti přiděluje paměť ze systému v segmentech předem určené velikosti. Pokud přidělení vyžaduje další segment, ale v prostoru virtuální paměti procesu nezbývá žádný souvislý volný blok, přidělení spravované haldy se nezdaří.

- Nemají dostatek fyzické paměti k přidělení.

|Kontroly výkonnosti|
|------------------------|
|[Určete, zda je spravována výjimka z nedostatku paměti.](#OOMIsManaged)<br /><br /> [Určete, kolik virtuální paměti lze rezervovat.](#GetVM)<br /><br /> [Zjistěte, zda je dostatek fyzické paměti.](#Physical)|

Pokud zjistíte, že výjimka není legitimní, obraťte se na oddělení služeb zákazníkům a podpory společnosti Microsoft s následujícími informacemi:

- Zásobník se spravovanou výjimkou z nedostatku paměti.

- Úplný výpis paměti.

- Data, která dokazují, že se nejedná o legitimní výjimku z nedostatku paměti, včetně dat, která ukazují, že virtuální nebo fyzická paměť není problém.

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a>Problém: Proces používá příliš mnoho paměti

Běžným předpokladem je, že zobrazení využití paměti na kartě **Výkon** správce úloh systému Windows může indikovat, kdy je používáno příliš mnoho paměti. Toto zobrazení se však toto zobrazení netožuje s pracovní sadou; neposkytuje informace o využití virtuální paměti.

Pokud zjistíte, že problém je způsoben spravované haldy, je nutné měřit spravované haldy v průběhu času k určení všechny vzory.

Pokud zjistíte, že problém není způsoben spravované haldy, je nutné použít nativní ladění.

|Kontroly výkonnosti|
|------------------------|
|[Určete, kolik virtuální paměti lze rezervovat.](#GetVM)<br /><br /> [Určete, kolik paměti spravované haldy je potvrzení.](#ManagedHeapCommit)<br /><br /> [Určete, kolik paměti spravované haldy rezervy.](#ManagedHeapReserve)<br /><br /> [Určete velké objekty v generaci 2.](#ExamineGen2)<br /><br /> [Určete odkazy na objekty.](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problém: Uvolňování nezíská objekty dostatečně rychle

Když se zobrazí, jako kdyby objekty nejsou uvolněny podle očekávání pro uvolňování paměti, je nutné určit, zda existují nějaké silné odkazy na tyto objekty.

K tomuto problému může dojít také v případě, že pro generování, které obsahuje mrtvý objekt, nedošlo k žádnému uvolnění paměti, což znamená, že finalizační metoda pro mrtvý objekt nebyla spuštěna. Například je to možné, když spouštěte aplikaci s jedním vláknem (STA) a podproces, který služby finalizační fronty nemůže volat do něj.

|Kontroly výkonnosti|
|------------------------|
|[Zkontrolujte odkazy na objekty.](#ObjRef)<br /><br /> [Určete, zda byla spuštěna finalizační metoda.](#Induce)<br /><br /> [Zjistěte, zda existují objekty, které čekají na dokončení.](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problém: Spravované haldy je příliš fragmentované

Úroveň fragmentace se vypočítá jako poměr volného místa k celkové přidělené paměti pro generování. Pro generaci 2 není přijatelná úroveň fragmentace větší než 20%. Vzhledem k tomu, generace 2 může získat velmi velký, poměr fragmentace je důležitější než absolutní hodnota.

S velké množství volného místa v generaci 0 není problém, protože se jedná o generování, kde jsou přiděleny nové objekty.

Fragmentace vždy dochází v haldě velkého objektu, protože není komprimován. Volné objekty, které jsou přilehlé jsou přirozeně sbaleny do jednoho prostoru pro splnění požadavků na přidělení velkých objektů.

Fragmentace se může stát problémem v generaci 1 a generaci 2. Pokud tyto generace mají velké množství volného místa po uvolnění paměti, použití objektu aplikace může vyžadovat změny a měli byste zvážit přehodnocení životnosti dlouhodobé objekty.

Nadměrné připnutí objektů může zvýšit fragmentaci. Pokud je fragmentace vysoká, mohlo být připnuto příliš mnoho objektů.

Pokud fragmentace virtuální paměti brání uvolňování v přidání segmentů, příčinou může být jedna z následujících příčin:

- Časté nakládání a vykládání mnoha malých sestav.

- Při spolupráci s nespravovaným kódem je při držení příliš mnoho odkazů na objekty MODELU COM.

- Vytvoření velkých přechodných objektů, což způsobuje, že haldy velkých objektů často přidělují a volí segmenty haldy.

  Při hostování CLR, aplikace může požádat, aby systém uvolňování paměti zachovat své segmenty. Tím se snižuje četnost přidělení segmentu. Toho lze dosáhnout pomocí příznaku STARTUP_HOARD_GC_VM ve [výčtu STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).

|Kontroly výkonnosti|
|------------------------|
|[Určete velikost volného místa ve spravované haldě.](#Fragmented)<br /><br /> [Určete počet připnutých objektů.](#Pinned)|

Pokud se domníváte, že neexistuje žádný legitimní důvod pro fragmentaci, obraťte se na oddělení služeb zákazníkům společnosti Microsoft a podpory.

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problém: Pozastavení uvolňování paměti jsou příliš dlouhé

Uvolňování paměti pracuje v měkké reálném čase, takže aplikace musí být schopen tolerovat některé pauzy. Kritériem pro měkký reálný čas je, že 95% operací musí být dokončeno včas.

V souběžné uvolňování paměti spravovaných podprocesů je povoleno spustit během kolekce, což znamená, že pauzy jsou velmi minimální.

Dočasné uvolňování paměti (generace 0 a 1) trvat pouze několik milisekund, takže snížení pauzy obvykle není možné. Můžete však snížit pauzy v kolekcích generace 2 změnou vzoru požadavků na přidělení aplikací.

Další, přesnější, metoda je použití [uvolnění paměti ETW události](../../../docs/framework/performance/garbage-collection-etw-events.md). Časování kolekcí můžete najít přidáním rozdílů časového razítka pro posloupnost událostí. Celá sekvence kolekce zahrnuje pozastavení spuštění motoru, uvolnění paměti sám a obnovení spuštění motoru.

[Oznámení uvolňování paměti](../../../docs/standard/garbage-collection/notifications.md) můžete použít k určení, zda server má mít kolekci generace 2 a zda přesměrování požadavků na jiný server může zmírnit problémy s pozastavení.

|Kontroly výkonnosti|
|------------------------|
|[Určete dobu v uvolňování paměti.](#TimeInGC)<br /><br /> [Zjistěte, co způsobilo uvolnění paměti.](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a>Problém: Generace 0 je příliš velká

Generace 0 je pravděpodobně mít větší počet objektů v 64bitovém systému, zejména při použití uvolňování paměti serveru namísto uvolňování paměti pracovní stanice. Důvodem je, že prahová hodnota pro aktivaci uvolnění paměti generace 0 je vyšší v těchto prostředích a kolekce generace 0 může získat mnohem větší. Výkon je lepší, když aplikace přiděluje více paměti před uvolnění paměti se aktivuje.

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problém: Využití procesoru během uvolňování paměti je příliš vysoká

Využití procesoru bude vysoká během uvolňování paměti. Pokud značné množství času procesu je vynaloženo v uvolňování paměti, počet kolekcí je příliš časté nebo kolekce trvá příliš dlouho. Zvýšená míra přidělení objektů na spravované haldě způsobí, že uvolňování paměti dochází častěji. Snížení míry přidělení snižuje četnost uvolňování paměti.

Sazby přidělení můžete sledovat `Allocated Bytes/second` pomocí čítače výkonu. Další informace naleznete [v tématu Čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).

Doba trvání kolekce je především faktor počtu objektů, které přežívají po přidělení. Systém uvolňování paměti musí projít velké množství paměti, pokud mnoho objektů zůstávají shromažďovat. Práce na zhutnění přeživších je časově náročná. Chcete-li zjistit, kolik objektů bylo zpracováno během kolekce, nastavte zarážku v ladicím programu na konci uvolňování paměti pro zadanou generaci.

|Kontroly výkonnosti|
|------------------------|
|[Zjistěte, zda je vysoké využití procesoru způsobeno uvolňováním paměti.](#HighCPU)<br /><br /> [Nastavte zarážku na konci uvolňování paměti.](#GenBreak)|

## <a name="troubleshooting-guidelines"></a>Pokyny pro řešení potíží

Tato část popisuje pokyny, které byste měli zvážit při zahájení vyšetřování.

### <a name="workstation-or-server-garbage-collection"></a>Uvolňování paměti pracovní stanice nebo serveru

Zjistěte, zda používáte správný typ uvolňování paměti. Pokud vaše aplikace používá více vláken a instancí objektů, použijte místo uvolňování paměti pracovní stanice uvolňování paměti serveru. Uvolňování paměti serveru pracuje na více vláknech, zatímco uvolňování paměti pracovní stanice vyžaduje více instancí aplikace ke spuštění vlastních vláken uvolňování paměti a soutěžit o čas procesoru.

Aplikace, která má nízké zatížení a která provádí úkoly zřídka na pozadí, jako je například služba, může použít uvolňování paměti pracovní stanice s souběžným uvolňováním paměti zakázáno.

### <a name="when-to-measure-the-managed-heap-size"></a>Kdy měřit velikost spravované haldy

Pokud používáte profiler, budete muset vytvořit konzistentní vzor měření efektivně diagnostikovat problémy s výkonem. Zvažte následující body pro vytvoření plánu:

- Pokud měříte po uvolnění paměti generace 2, celá spravovaná halda bude bez odpadků (mrtvé objekty).

- Pokud měříte ihned po uvolnění paměti generace 0, objekty v generacích 1 a 2 ještě nebudou shromažďovány.

- Pokud měříte bezprostředně před uvolnění paměti, budete měřit co nejvíce přidělení, jak je to možné před spuštěním uvolňování paměti.

- Měření během uvolňování paměti je problematické, protože datové struktury systému uvolňování paměti nejsou v platném stavu pro průchod a nemusí být schopen poskytnout úplné výsledky. Toto chování je úmyslné.

- Pokud používáte uvolňování paměti pracovní stanice s souběžným uvolňováním paměti, uvolněné objekty nejsou komprimovány, takže velikost haldy může být stejná nebo větší (fragmentace může způsobit, že se zdá být větší).

- Souběžné uvolňování paměti na generaci 2 je zpožděno, když je zatížení fyzické paměti příliš vysoké.

Následující postup popisuje, jak nastavit zarážku tak, aby bylo možné měřit spravované haldy.

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Nastavení zarážky na konci uvolňování paměti

- Do windbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **bp mscorwks! WKS::GCHeap::RestartEE "j (dwo(mscorwks! WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';' g'"**

  kde **GcCondemnedGeneration** je nastavena na požadovanou generaci. Tento příkaz vyžaduje soukromé symboly.

  Tento příkaz vynutí přerušení, pokud **restartEE** je spuštěn po generace 2 objekty byly uvolněny pro uvolnění paměti.

  V uvolňování paměti serveru pouze jedno vlákno volá **RestartEE**, takže zarážka dojde pouze jednou během uvolňování paměti generace 2.

## <a name="performance-check-procedures"></a>Postupy kontroly výkonu

Tato část popisuje následující postupy pro izolaci příčiny problému s výkonem:

- [Zjistěte, zda je problém způsoben uvolňování paměti.](#IsGC)

- [Určete, zda je spravována výjimka z nedostatku paměti.](#OOMIsManaged)

- [Určete, kolik virtuální paměti lze rezervovat.](#GetVM)

- [Zjistěte, zda je dostatek fyzické paměti.](#Physical)

- [Určete, kolik paměti spravované haldy je potvrzení.](#ManagedHeapCommit)

- [Určete, kolik paměti spravované haldy rezervy.](#ManagedHeapReserve)

- [Určete velké objekty v generaci 2.](#ExamineGen2)

- [Určete odkazy na objekty.](#ObjRef)

- [Určete, zda byla spuštěna finalizační metoda.](#Induce)

- [Zjistěte, zda existují objekty, které čekají na dokončení.](#Finalize)

- [Určete velikost volného místa ve spravované haldě.](#Fragmented)

- [Určete počet připnutých objektů.](#Pinned)

- [Určete dobu v uvolňování paměti.](#TimeInGC)

- [Zjistěte, co vyvolalo uvolňování paměti.](#Triggered)

- [Zjistěte, zda je vysoké využití procesoru způsobeno uvolňováním paměti.](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Chcete-li zjistit, zda je problém způsoben uvolňování paměti

- Prozkoumejte následující dva čítače výkonu paměti:

  - **% času v GC**. Zobrazí procento uplynulého času stráveného prováděním uvolňování paměti po posledním cyklu uvolňování paměti. Tento čítač slouží k určení, zda uvolňování systému tráví příliš mnoho času, aby spravované haldy místo k dispozici. Pokud je čas strávený v uvolňování paměti relativně nízký, může to znamenat problém s prostředky mimo spravovanou haldu. Tento čítač nemusí být přesné, pokud se jedná o souběžné nebo pozadí uvolňování paměti.

  - **# Celkem potvrzené bajty**. Zobrazuje množství virtuální paměti aktuálně potvrzené systémem uvolňování paměti. Tento čítač slouží k určení, zda paměť spotřebované systémem uvolňování paměti je nadměrná část paměti, která používá vaše aplikace.

  Většina čítačů výkonu paměti jsou aktualizovány na konci každé uvolnění paměti. Proto nemusí odrážet aktuální podmínky, o kterých chcete získat informace.

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Chcete-li zjistit, zda je spravována výjimka z nedostatku paměti

1. Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte příkaz výjimka tisku (**pe):**

    **!pe**

    Pokud je výjimka <xref:System.OutOfMemoryException> spravována, zobrazí se jako typ výjimky, jak je znázorněno v následujícím příkladu.

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. Pokud výstup neurčuje výjimku, budete muset určit, které vlákno výjimka z paměti je z. Do ladicího programu zadejte následující příkaz, který zobrazí všechna vlákna s jejich zásobníky volání:

    **~\*Kb**

    Podproces s zásobníku, který má volání `RaiseTheException` výjimek je označen argumentem. Toto je objekt spravované výjimky.

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. Následující příkaz můžete použít k vysuševných výjimek.

    **!pe -vnořené**

    Pokud nenajdete žádné výjimky, výjimka z paměti pochází z nespravovaného kódu.

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Chcete-li zjistit, kolik virtuální paměti lze rezervovat

- Do windbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz, abyste získali největší volnou oblast:

  **!adresa -souhrn**

  Největší volná oblast je zobrazena tak, jak je znázorněno na následujícím výstupu.

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové). Tato oblast je mnohem menší než co systém uvolňování paměti potřebuje pro segment.

  -nebo-

- Použijte příkaz **vmstat:**

  **!vmstat**

  Největší volná oblast je největší hodnota ve sloupci MAXIMUM, jak je znázorněno na následujícím výstupu.

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Chcete-li zjistit, zda je dostatek fyzické paměti

1. Spusťte Správce úloh systému Windows.

2. Na kartě **Výkon** se podívejte na potvrzenou hodnotu. (V systému Windows 7, podívejte se na **potvrzení (KB)** ve **skupině System**.)

    Pokud **součet** je blízko **limit**, dochází fyzická paměť.

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Chcete-li zjistit, kolik paměti spravované haldy je potvrzení

- Pomocí `# Total committed bytes` čítače výkonu paměti získat počet bajtů, které spravované haldy je potvrzení. Systém uvolňování paměti odevzdvá bloky v segmentu podle potřeby, ne všechny současně.

  > [!NOTE]
  > Nepoužívejte čítač `# Bytes in all Heaps` výkonu, protože nepředstavuje skutečné využití paměti spravované haldy. Velikost generace je zahrnuta v této hodnotě a je ve skutečnosti jeho prahová velikost, to znamená velikost, která indukuje uvolnění paměti, pokud je generace vyplněna objekty. Proto je tato hodnota obvykle nula.

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Chcete-li zjistit, kolik paměti spravované haldy rezervy

- Použijte `# Total reserved bytes` čítač výkonu paměti.

  Systém uvolňování paměti rezervuje paměť v segmentech a můžete určit, kde segment začíná pomocí příkazu **eeheap.**

  > [!IMPORTANT]
  > I když můžete určit velikost paměti, kterou systém uvolňování paměti přiděluje pro každý segment, velikost segmentu je specifická pro implementaci a může se kdykoli změnit, včetně pravidelných aktualizací. Vaše aplikace by nikdy neměla dělat předpoklady o konkrétní velikosti segmentu nebo na ní záviset, ani by se neměla pokoušet nakonfigurovat množství paměti, která je k dispozici pro přidělení segmentu.

- Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **!eeheap -gc**

  Výsledek je následující.

  ```console
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

  Adresy označené "segmentem" jsou počáteční adresy segmentů.

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a>Určení velkých objektů v generaci 2

- Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **!dumpheap –stat**

  Pokud spravované haldy je velký, **dumpheap** může chvíli trvat až do konce.

  Můžete začít analyzovat z několika posledních řádků výstupu, protože seznam objektů, které používají nejvíce místa. Například:

  ```console
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

  Poslední uvedený objekt je řetězec a zabírá nejvíce místa. Můžete prozkoumat aplikace a zjistit, jak lze optimalizovat objekty řetězce. Chcete-li zobrazit řetězce, které jsou mezi 150 a 200 bajtů, zadejte následující:

  **!dumpheap -typ System.String -min 150 -max 200**

  Příklad výsledků je následující.

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  Použití celého čísla namísto řetězce pro ID může být efektivnější. Pokud stejný řetězec se opakuje tisíckrát, zvažte řetězec interning. Další informace o interning řetězce, naleznete <xref:System.String.Intern%2A?displayProperty=nameWithType> v referenční téma pro metodu.

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a>Určení odkazů na objekty

- Do windbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz pro seznam odkazů na objekty:

  **!gcroot**

  `-or-`

- Chcete-li určit odkazy na konkrétní objekt, uveďte adresu:

  **!gcroot 1c37b2ac**

  Kořeny nalezené na hromádkách mohou být falešně pozitivní. Další informace získáte pomocí `!help gcroot`příkazu .

  ```console
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

  Dokončení příkazu **gcroot** může trvat dlouhou dobu. Jakýkoli objekt, který není uvolněn a uvolnění paměti je živý objekt. To znamená, že některé root je přímo nebo nepřímo drží na objektu, takže **gcroot** by měl vrátit informace o cestě k objektu. Měli byste prozkoumat vrácené grafy a zjistit, proč jsou tyto objekty stále odkazovány.

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Chcete-li zjistit, zda byla spuštěna finalizační metoda

- Spusťte testovací program, který obsahuje následující kód:

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  Pokud test problém vyřeší, to znamená, že uvolňování paměti nebyl akultivace objektů, protože finalizační metody pro tyto objekty byla pozastavena. Metoda <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> umožňuje finalizační metody k dokončení svých úkolů a řeší problém.

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Chcete-li zjistit, zda existují objekty, které čekají na dokončení

1. Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

    **!finalizequeue**

    Podívejte se na počet objektů, které jsou připraveny k dokončení. Pokud je číslo vysoké, je nutné prozkoumat, proč tyto finalizační metody nelze postupovat vůbec nebo nemůže postupovat dostatečně rychle.

2. Chcete-li získat výstup vláken, zadejte následující příkaz:

    **závity -speciální**

    Tento příkaz poskytuje výstup, například následující.

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    Vlákno finalizační metody označuje, která finalizační metoda, pokud existuje, je právě spuštěna. Pokud vlákno finalizační metody nespouštějí žádné finalizační metody, čeká na událost, která mu řekne, aby dělala svou práci. Většinu času se zobrazí finalizační vlákno v tomto stavu, protože běží na THREAD_HIGHEST_PRIORITY a má dokončit spuštění finalizačních metod, pokud existuje, velmi rychle.

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Určení množství volného místa ve spravované haldě

- Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **!dumpheap -typ Free -stat**

  Tento příkaz zobrazí celkovou velikost všech volných objektů na spravované haldě, jak je znázorněno v následujícím příkladu.

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- Chcete-li určit volné místo v generaci 0, zadejte následující příkaz pro informace o spotřebě paměti podle generování:

  **!eeheap -gc**

  Tento příkaz zobrazí výstup podobný následujícímu. Poslední řádek zobrazuje dočasný segment.

  ```console
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

- Vypočítejte místo využité generací 0:

  **? 49e05d04-0x49521f8c**

  Výsledek je následující. Generace 0 je přibližně 9 MB.

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- Následující příkaz vypíše volné místo v rozsahu generace 0:

  **!dumpheap -typ Volný -stat 0x49521f8c 49e05d04**

  Výsledek je následující.

  ```console
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

  Tento výstup ukazuje, že generace 0 část haldy používá 9 MB místa pro objekty a má 7 MB zdarma. Tato analýza ukazuje, do jaké míry generace 0 přispívá k fragmentaci. Toto množství využití haldy by měla být diskontována z celkové částky jako příčina fragmentace dlouhodobými objekty.

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a>Určení počtu připnutých objektů

- Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **!gchandles**

  Zobrazené statistiky zahrnují počet připnutých popisovačů, jak ukazuje následující příklad.

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Chcete-li zjistit dobu v uvolňování paměti

- Zkontrolujte `% Time in GC` čítač výkonu paměti.

  Hodnota se vypočítá pomocí intervalu vzorku. Vzhledem k tomu, že čítače jsou aktualizovány na konci každé uvolnění paměti, aktuální vzorek bude mít stejnou hodnotu jako předchozí ukázka, pokud došlo k žádné kolekce během intervalu.

  Čas sběru se získá vynásobením intervalového času vzorku procentuální hodnotou.

  Následující údaje ukazují čtyři intervaly odběru vzorků po dvou sekundách pro 8sekundovou studii. V `Gen0` `Gen1`, `Gen2` a sloupce zobrazit počet uvolnění paměti, ke kterým došlo během tohoto intervalu pro tuto generaci.

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  Tyto informace nezobrazuje, kdy došlo k uvolnění paměti, ale můžete určit počet uvolnění paměti, ke kterým došlo v časovém intervalu. Za předpokladu, že nejhorší případ desáté generace 0 uvolňování paměti dokončena na začátku druhého intervalu a jedenácté generace 0 uvolňování paměti dokončena na konci pátého intervalu. Doba mezi koncem desátéa konce a koncem jedenáctého uvolňování paměti je přibližně 2 sekundy a čítač výkonu zobrazuje 3 %, takže doba trvání jedenácté generace 0 uvolňování paměti byla (2 sekundy * 3 % = 60 ms).

  V tomto příkladu je 5 období.

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  Druhá generace 2 uvolňování paměti zahájena během třetího intervalu a dokončena v pátém intervalu. Za předpokladu, že nejhorší případ, poslední uvolnění paměti byla pro kolekci generace 0, která byla dokončena na začátku druhého intervalu a uvolnění paměti generace 2 dokončena na konci pátého intervalu. Proto čas mezi koncem generace 0 uvolňování paměti a konec uvolnění paměti generace 2 je 4 sekundy. Vzhledem `% Time in GC` k tomu, že čítač je 20 %, maximální doba, po kterou může být trvalo uvolnění paměti generace 2 , je (4 sekundy * 20 % = 800 ms).

- Alternativně můžete určit délku uvolňování paměti pomocí [události uvolňování paměti ETW](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace k určení doby trvání uvolňování paměti.

  Například následující data zobrazuje posloupnost událostí, ke kterým došlo během nesouběžného uvolňování paměti.

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  Pozastavení spravovaného závitu trvalo`GCSuspendEEEnd` 26us ( – `GCSuspendEEBegin_V1`).

  Skutečné uvolňování paměti trvalo 4,8`GCEnd_V1` `GCStart_V1`ms ( – ).

  Obnovení spravovaných vláken trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).

  Následující výstup obsahuje příklad pro uvolňování paměti na pozadí a zahrnuje pole procesu, vlákna a události. (Ne všechna data jsou zobrazena.)

  ```console
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

  Událost `GCStart_V1` na 42504816 označuje, že se jedná o uvolňování `1`paměti na pozadí, protože poslední pole je . To se stane uvolnění paměti ne. 102019.

  K `GCStart` události dochází, protože je potřeba dočasné uvolnění paměti před spuštěním uvolňování paměti na pozadí. To se stane uvolnění paměti ne. 102020.

  Na 42514170, uvolňování paměti č. 102020 povrchových úprav. Spravovaná vlákna jsou v tomto okamžiku restartována. To je dokončeno ve vlákně 4372, který spustil toto uvolnění paměti na pozadí.

  Na závitu 4744 dochází k pozastavení. Toto je jediný čas, kdy pozadí uvolňování paměti má pozastavit spravovaná vlákna. Tato doba trvání je přibližně 99ms ((63784407-63685394)/1000).

  Událost `GCEnd` pro uvolňování paměti na pozadí je na 89931423. To znamená, že uvolňování paměti na pozadí trvalo asi 47 sekund ((89931423-42504816)/1000).

  Zatímco jsou spuštěna spravovaná vlákna, můžete zobrazit libovolný počet dočasných uvolňování paměti.

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a>Chcete-li zjistit, co vyvolalo uvolňování paměti

- V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz, který zobrazí všechna vlákna s jejich zásobníky volání:

  **~\*Kb**

  Tento příkaz zobrazí výstup podobný následujícímu.

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  Pokud uvolňování paměti byla způsobena oznámení nedostatku paměti z operačního systému, zásobník volání je podobný, s tím rozdílem, že vlákno je finalizační podproces. Finalizační podproces získá asynchronní oznámení nedostatku paměti a vyvolá uvolňování paměti.

  Pokud uvolňování paměti bylo způsobeno přidělení paměti, zásobníku se zobrazí takto:

  ```console
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

  Pomocník just-in-time (`JIT_New*`) nakonec `GCHeap::GarbageCollectGeneration`zavolá . Pokud zjistíte, že uvolnění paměti generace 2 jsou způsobeny přidělení, je nutné určit, které objekty jsou shromažďovány uvolnění paměti generace 2 a jak se jim vyhnout. To znamená, že chcete určit rozdíl mezi počáteční a konec uvolnění paměti generace 2 a objekty, které způsobily kolekci generace 2.

  Zadejte například následující příkaz do ladicího programu, který zobrazí začátek kolekce generace 2:

  **!dumpheap –stat**

  Příklad výstupu (zkrácený pro zobrazení objektů, které využívají nejvíce místa):

  ```console
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

  Opakujte příkaz na konci generace 2:

  **!dumpheap –stat**

  Příklad výstupu (zkrácený pro zobrazení objektů, které využívají nejvíce místa):

  ```console
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

  Objekty `double[]` zmizely z konce výstupu, což znamená, že byly shromážděny. Tyto objekty představují přibližně 70 MB. Zbývající objekty se příliš nezměnily. Proto tyto `double[]` objekty byly důvodem, proč došlo k této generování 2 uvolnění paměti. Dalším krokem je zjistit, `double[]` proč jsou tam objekty a proč zemřely. Můžete se zeptat vývojáře kódu, odkud tyto objekty pocházejí, nebo můžete použít příkaz **gcroot.**

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Chcete-li zjistit, zda je vysoké využití procesoru způsobeno uvolňovánípaměti

- Korelujte `% Time in GC` hodnotu čítače výkonu paměti s časem procesu.

  Pokud `% Time in GC` hodnota špičky ve stejnou dobu jako čas procesu, uvolňování paměti způsobuje vysoké využití procesoru. V opačném případě profil aplikace zjistit, kde dochází k vysoké využití.

## <a name="see-also"></a>Viz také

- [Kolekce paměti](../../../docs/standard/garbage-collection/index.md)
