---
title: Uvolnění paměti a výkon
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 72cf742aae26f9441229b355dc6e70da7a5fc9cd
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900585"
---
# <a name="garbage-collection-and-performance"></a>Uvolnění paměti a výkon

Toto téma popisuje problémy související s uvolňováním paměti a využití paměti. Řeší problémy, které se týkají spravované haldy, a vysvětluje, jak minimalizovat vliv uvolňování paměti v aplikacích. Každý problém obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.

## <a name="performance-analysis-tools"></a>Nástroje pro analýzu výkonu

V následujících částech jsou popsány nástroje, které jsou k dispozici pro zkoumání potíží s využitím paměti a uvolňování paměti. [Postupy](#performance-check-procedures) uvedené dále v tomto tématu se týkají těchto nástrojů.

### <a name="memory-performance-counters"></a>Čítače výkonu paměti

K shromažďování údajů o výkonu můžete použít čítače výkonu. Pokyny najdete v tématu [profilace modulu runtime](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Kategorie paměti .NET CLR čítače výkonu, jak je popsáno v tématu [čítače výkonu v .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o uvolňování paměti.

### <a name="debugging-with-sos"></a>Ladění pomocí SOS

K prozkoumání objektů na spravované haldě můžete použít [ladicí program systému Windows (WinDbg)](/windows-hardware/drivers/debugger/index) .

Chcete-li nainstalovat nástroj WinDbg, nainstalujte ladicí nástroje pro systém Windows ze stránky [Stáhnout ladicí nástroje pro Windows](/windows-hardware/drivers/debugger/debugger-download-tools) .

### <a name="garbage-collection-etw-events"></a>Události Trasování událostí pro Windows uvolnění paměti

Trasování událostí pro Windows (ETW) je systém trasování, který doplňuje podporu profilování a ladění poskytovanou .NET Framework. Počínaje .NET Framework 4, [události ETW uvolňování paměti](../../../docs/framework/performance/garbage-collection-etw-events.md) zaznamenávají užitečné informace pro analýzu spravované haldy ze statistického bodu zobrazení. Například událost `GCStart_V1`, která je vyvolána při výskytu uvolňování paměti, poskytuje následující informace:

- Které generace objektů se shromažďují.

- Co aktivovalo uvolňování paměti.

- Typ uvolňování paměti (souběžné nebo nesouběžné).

Protokolování událostí ETW je efektivní a nebude maskovat žádné problémy s výkonem spojené s uvolňováním paměti. Proces může poskytovat vlastní události ve spojení s událostmi ETW. Při protokolu mohou být události aplikace i události uvolňování paměti v souvislosti s určením, jak a kdy dochází k problémům s haldou. Například serverová aplikace může poskytovat události na začátku a konci žádosti klienta.

### <a name="the-profiling-api"></a>Rozhraní API profilování

Rozhraní pro profilaci modulu CLR (Common Language Runtime) poskytují podrobné informace o objektech, které byly ovlivněny během uvolňování paměti. Profiler může být upozorněn při zahájení a ukončení uvolňování paměti. Může poskytovat sestavy o objektech na spravované haldě, včetně identifikace objektů v každé generaci. Další informace najdete v tématu [profilace – přehled](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).

Profilery můžou poskytovat komplexní informace. Složité profilery ale můžou potenciálně upravit chování aplikace.

### <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace

Počínaje .NET Framework 4 umožňuje monitorování prostředků domény aplikace (ARM) hostitelům monitorovat využití procesoru a paměti podle aplikační domény. Další informace najdete v tématu [monitorování prostředků domény aplikace](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).

## <a name="troubleshooting-performance-issues"></a>Řešení potíží s výkonem

Prvním krokem je [určit, jestli je problém ve skutečnosti uvolňováním paměti](#IsGC). Pokud zjistíte, že je, vyberte z následujícího seznamu, abyste mohli problém vyřešit.

- [Je vyvolána výjimka nedostatek paměti.](#Issue_OOM)

- [Proces využívá příliš mnoho paměti.](#Issue_TooMuchMemory)

- [Systém uvolňování paměti neuvolňuje objekty dostatečně rychle](#Issue_NotFastEnough)

- [Spravovaná halda je příliš fragmentovaná.](#Issue_Fragmentation)

- [Pozastavení uvolňování paměti jsou příliš dlouhé.](#Issue_LongPauses)

- [Generace 0 je příliš velká.](#Issue_Gen0)

- [Využití CPU při uvolňování paměti je příliš vysoké.](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problém: je vyvolána výjimka nedostatek paměti.

Existují dva legitimní případy, kdy je možné vyvolané spravované <xref:System.OutOfMemoryException>:

- Nedostatek virtuální paměti.

  Systém uvolňování paměti přiděluje paměť ze systému v segmentech předem určené velikosti. Pokud přidělení vyžaduje další segment, ale v virtuální paměti procesu není k dispozici žádný souvislý bezplatný blok, přidělení pro spravovanou haldu se nezdaří.

- Není dostatek fyzické paměti k přidělení.

|Kontroly výkonu|
|------------------------|
|[Určete, zda je spravovaná výjimka nedostatku paměti.](#OOMIsManaged)<br /><br /> [Určete, kolik virtuální paměti lze rezervovat.](#GetVM)<br /><br /> [Určete, zda je k dispozici dostatek fyzické paměti.](#Physical)|

Pokud zjistíte, že výjimka není legitimní, obraťte se na zákaznickou službu a podporu Microsoftu s následujícími informacemi:

- Zásobník s nespravovanou výjimkou paměti.

- Úplný výpis paměti.

- Data, která ukážou, že se nejedná o legitimní výjimku při nedostatku paměti, včetně dat, která ukazují, že virtuální nebo fyzická paměť není problémem.

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a>Problém: proces využívá příliš mnoho paměti.

Běžným předpokladem je, že zobrazení využití paměti na kartě **výkon** ve Správci úloh systému Windows může indikovat, že se používá příliš mnoho paměti. Tento displej se však vztahuje k pracovní sadě; neposkytuje informace o využití virtuální paměti.

Pokud zjistíte, že problém je způsoben spravovanou haldou, je nutné změřit spravovanou haldu v čase a určit tak vzory.

Pokud zjistíte, že problém není způsoben spravovanou haldou, je nutné použít nativní ladění.

|Kontroly výkonu|
|------------------------|
|[Určete, kolik virtuální paměti lze rezervovat.](#GetVM)<br /><br /> [Určete, kolik paměti se spravovaná halda zavazuje.](#ManagedHeapCommit)<br /><br /> [Určete velikost paměti, kterou spravovaná halda rezervuje.](#ManagedHeapReserve)<br /><br /> [Určení velkých objektů v generaci 2.](#ExamineGen2)<br /><br /> [Určete odkazy na objekty.](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problém: systém uvolňování paměti neuvolňuje objekty dostatečně rychle

Pokud se zobrazí, jako by se objekty neuvolní, jak je očekáváno pro uvolňování paměti, je nutné určit, zda existují silné odkazy na tyto objekty.

K tomuto problému může dojít také v případě, že neexistuje uvolňování paměti pro generaci, která obsahuje nedoručený objekt, což znamená, že finalizační metoda pro mrtvý objekt nebyla spuštěna. To je možné například v případě, že používáte vícevláknovou aplikaci s jedním vláknem (STA) a vlákno, které služba Finalize Queue nemůže volat.

|Kontroly výkonu|
|------------------------|
|[Podívejte se na odkazy na objekty.](#ObjRef)<br /><br /> [Určete, zda byl spuštěn finalizační metoda.](#Induce)<br /><br /> [Určete, zda objekty čekají na dokončení.](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problém: spravovaná halda je moc fragmentovaná.

Úroveň fragmentace se počítá jako poměr volného místa v celkové přidělené paměti pro generaci. V případě generace 2 není přijatelná úroveň fragmentace více než 20%. Vzhledem k tomu, že generace 2 může dosáhnout hodně velkých, je poměr fragmentace důležitější než absolutní hodnota.

Vynulování volného místa v generaci 0 není problém, protože se jedná o generaci, kde jsou přiděleny nové objekty.

K fragmentaci vždy dochází v haldě velkých objektů, protože není komprimována. Bezplatné objekty, které jsou sousedící, jsou přirozeně sbaleny do jednoho prostoru pro splnění požadavků na přidělení velkých objektů.

Fragmentace se může stát problémem v generaci 1 a generaci 2. Pokud tyto generace mají velké množství volného místa po uvolnění paměti, použití objektu aplikace může vyžadovat úpravu a měli byste zvážit přehodnocení životnosti dlouhodobých objektů.

Nadměrné Připnutí objektů může zvýšit fragmentaci. Pokud je fragmentace vysoká, je možné, že bylo připnuté příliš mnoho objektů.

Pokud fragmentaci virtuální paměti brání v uvolňování paměti při přidávání segmentů, může to být jedna z následujících příčin:

- Časté načítání a uvolňování mnoha malých sestavení.

- Při spolupráci s nespravovaným kódem je uchováváno příliš mnoho odkazů na objekty COM.

- Vytváření velkých přechodných objektů, což způsobí, že halda velkých objektů často přiděluje a uvolňuje segmenty haldy.

  Při hostování modulu CLR může aplikace požádat, aby systém uvolňování paměti zachoval své segmenty. Tím se snižuje frekvence přidělení segmentů. Toho je možné dosáhnout použitím příznaku STARTUP_HOARD_GC_VM ve [výčtu STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).

|Kontroly výkonu|
|------------------------|
|[Určete množství volného místa ve spravované haldě.](#Fragmented)<br /><br /> [Určete počet připnutých objektů.](#Pinned)|

Pokud se domníváte, že neexistují žádné oprávněné příčiny pro fragmentaci, obraťte se na zákaznickou službu a podporu Microsoftu.

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problém: pozastavení uvolňování paměti jsou moc dlouhá.

Uvolňování paměti funguje v tichém reálném čase, takže aplikace musí být schopná tolerovat některá pozastavení. Kritériem pro měkký reálný čas je to, že 95% operací se musí dokončit včas.

V případě souběžného uvolňování paměti můžou spravovaná vlákna běžet během shromažďování, což znamená, že pozastavení jsou velmi minimální.

Dočasné uvolňování paměti (generace 0 a 1) jsou poslední jenom několik milisekund, takže snížení pauz většinou není proveditelné. Můžete ale snížit počet pozastavení v kolekcích 2. generace změnou vzoru požadavků na přidělení aplikací.

Další přesnější metodou je použít [události ETW pro uvolňování paměti](../../../docs/framework/performance/garbage-collection-etw-events.md). Časování pro kolekce můžete najít přidáním rozdílů časových razítek pro posloupnost událostí. Celá sekvence kolekce zahrnuje pozastavení prováděcího modulu, uvolňování paměti samotného a obnovení spouštěcího modulu.

Pomocí oznámení o [uvolňování paměti](../../../docs/standard/garbage-collection/notifications.md) můžete zjistit, jestli se server chystá mít kolekci 2. generace, a jestli žádosti o přesměrování na jiný server můžou způsobit problémy s pozastavením.

|Kontroly výkonu|
|------------------------|
|[Určete dobu v uvolňování paměti.](#TimeInGC)<br /><br /> [Určete, co způsobilo uvolňování paměti.](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a>Problém: generace 0 je moc velká.

Generace 0 pravděpodobně bude mít větší počet objektů v 64 systému, zvlášť když použijete uvolňování paměti serveru místo uvolnění paměti pracovní stanice. Důvodem je to, že prahová hodnota pro aktivaci uvolňování paměti generace 0 je v těchto prostředích vyšší, a kolekce generace 0 může být mnohem větší. Zvýšení výkonu je vylepšeno, pokud aplikace přiděluje více paměti před aktivací uvolňování paměti.

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problém: využití CPU během uvolňování paměti je příliš vysoké.

Využití CPU bude během uvolňování paměti vysoké. Pokud se v uvolňování paměti stráví významné množství času zpracování, počet kolekcí je příliš častý nebo kolekce je trvalá příliš dlouho. Zvýšená míra přidělení objektů na spravované haldě způsobuje, že se uvolňování paměti objevuje častěji. Snížení míry přidělení omezí četnost uvolňování paměti.

Sazby přidělení můžete sledovat pomocí čítače výkonu `Allocated Bytes/second`. Další informace najdete v tématu [čítače výkonu v .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).

Doba trvání kolekce je primárně faktorem počtu objektů, které jsou po přidělení zachovány. Systém uvolňování paměti musí projít velkým množstvím paměti, pokud je stále shromažďováno mnoho objektů. Práce na komprimaci pozůstalých je časově náročná. Chcete-li určit, kolik objektů bylo zpracováno během kolekce, nastavte zarážku v ladicím programu na konci uvolňování paměti pro zadanou generaci.

|Kontroly výkonu|
|------------------------|
|[Zjistěte, jestli je vysoké využití procesoru způsobeno uvolňováním paměti.](#HighCPU)<br /><br /> [Nastavte zarážku na konci uvolňování paměti.](#GenBreak)|

## <a name="troubleshooting-guidelines"></a>Pokyny pro řešení potíží

Tato část popisuje pokyny, které byste měli vzít v úvahu při zahájení šetření.

### <a name="workstation-or-server-garbage-collection"></a>Uvolnění paměti pracovní stanice nebo serveru

Určete, zda používáte správný typ uvolňování paměti. Pokud vaše aplikace používá více vláken a instancí objektů, použijte místo uvolňování paměti pracovních stanic Server uvolňování paměti serveru. Uvolňování paměti serveru funguje ve více vláknech, zatímco uvolňování paměti pracovní stanice vyžaduje více instancí aplikace, aby spouštěla vlastní vlákna uvolňování paměti a mohla konkurovat času procesoru.

Aplikace, která má nízké zatížení a provádí úlohy na pozadí, jako je například služba, může použít uvolňování paměti pracovní stanice se zakázaným souběžným uvolňováním paměti.

### <a name="when-to-measure-the-managed-heap-size"></a>Kdy změřit velikost spravované haldy

Pokud nepoužíváte Profiler, budete muset vytvořit jednotný měřicí vzor pro efektivní diagnostiku problémů s výkonem. Pro vytvoření plánu Vezměte v úvahu následující body:

- Pokud měříte po uvolnění paměti 2. generace, celá spravovaná halda bude bez uvolnění paměti (nedoručené objekty).

- Pokud měříte hned po uvolnění paměti generace 0, objekty v generacích 1 a 2 nebudou dosud shromažďovány.

- Pokud měříte těsně před uvolňováním paměti, měříte co nejvíce přidělení, než začne uvolňování paměti.

- Měření během uvolňování paměti je problematické, protože datové struktury uvolňování paměti nejsou v platném stavu pro procházení a nemusí být schopné poskytnout kompletní výsledky. Jedná se o účel.

- Pokud používáte uvolňování paměti pracovní stanice s souběžným uvolňováním paměti, uvolněné objekty se nekomprimuje, takže velikost haldy může být stejná nebo větší (fragmentace se může zdát, že je větší).

- Souběžné uvolňování paměti v generaci 2 je zpožděno, pokud je zatížení fyzické paměti příliš vysoké.

Následující postup popisuje, jak nastavit zarážku, abyste mohli změřit spravovanou haldu.

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Nastavení zarážky na konci uvolňování paměti

- V programu WinDbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **knihovny mscorwks BP WKS:: GCHeap:: RestartEE "j (DWO (knihovny Mscorwks! WKS:: GCHeap:: GcCondemnedGeneration) = = 2) ' KB '; ' g ' "**

  kde **GcCondemnedGeneration** je nastaveno na požadovanou generaci. Tento příkaz vyžaduje soukromé symboly.

  Tento příkaz vynutí přerušení, pokud je **RestartEE** provedeno po uvolnění objektů generace 2 pro uvolňování paměti.

  V uvolňování paměti serveru pouze jedno vlákno volá **RestartEE**, takže během uvolňování paměti 2. generace dojde k zarážce pouze jednou.

## <a name="performance-check-procedures"></a>Postupy kontroly výkonu

Tato část popisuje následující postupy k izolaci příčiny problému s výkonem:

- [Určete, zda je problém způsoben uvolňováním paměti.](#IsGC)

- [Určete, zda je spravovaná výjimka nedostatku paměti.](#OOMIsManaged)

- [Určete, kolik virtuální paměti lze rezervovat.](#GetVM)

- [Určete, zda je k dispozici dostatek fyzické paměti.](#Physical)

- [Určete, kolik paměti se spravovaná halda zavazuje.](#ManagedHeapCommit)

- [Určete velikost paměti, kterou spravovaná halda rezervuje.](#ManagedHeapReserve)

- [Určení velkých objektů v generaci 2.](#ExamineGen2)

- [Určete odkazy na objekty.](#ObjRef)

- [Určete, zda byl spuštěn finalizační metoda.](#Induce)

- [Určete, zda objekty čekají na dokončení.](#Finalize)

- [Určete množství volného místa ve spravované haldě.](#Fragmented)

- [Určete počet připnutých objektů.](#Pinned)

- [Určete dobu v uvolňování paměti.](#TimeInGC)

- [Určete, co aktivovalo uvolňování paměti.](#Triggered)

- [Určete, zda je vysoké využití procesoru způsobeno uvolňováním paměti.](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Zjištění, zda je problém způsoben uvolňováním paměti

- Prověřte následující dvě čítače výkonu paměti:

  - **% Času v GC**. Zobrazuje procento uplynulého času stráveného prováděním uvolňování paměti po posledním cyklu uvolňování paměti. Pomocí tohoto čítače určíte, zda je uvolňování paměti příliš mnoho času na zpřístupnění spravovaného prostoru haldy. Pokud je doba strávená uvolňováním paměti poměrně nízká, může to znamenat problém s prostředky mimo spravovanou haldu. Tento čítač nemusí být přesný, pokud je zapojeno souběžné a uvolňování paměti na pozadí.

  - **# Celkový počet potvrzených bajtů** Zobrazuje velikost virtuální paměti, která je aktuálně potvrzena systémem uvolňování paměti. Pomocí tohoto čítače určíte, zda paměť využívaná systémem uvolňování paměti je nadměrná část paměti, kterou vaše aplikace používá.

  Většina čítačů výkonu paměti se aktualizuje na konci každého uvolňování paměti. Proto nemusí odrážet aktuální podmínky, o kterých chcete získat informace.

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Chcete-li určit, zda je výjimka nedostatek paměti spravovaná

1. V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte příkaz pro výjimku tisku (**PE**):

    **! PE**

    Pokud je výjimka spravovaná, <xref:System.OutOfMemoryException> se zobrazí jako typ výjimky, jak je znázorněno v následujícím příkladu.

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. Pokud výstup neurčuje výjimku, je nutné určit, ze kterého vlákna je výjimka nedostatek paměti. Zadejte následující příkaz v ladicím programu pro zobrazení všech vláken s jejich zásobníky volání:

    **~\*kb**

    Vlákno se zásobníkem, který má volání výjimek, je určeno argumentem `RaiseTheException`. Toto je spravovaný objekt výjimky.

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. Pomocí následujícího příkazu můžete vypsat vnořené výjimky.

    **! PE – vnořené**

    Pokud nenajdete žádné výjimky, výjimka nedostatek paměti pochází z nespravovaného kódu.

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Určení velikosti virtuální paměti, která může být vyhrazena

- V programu WinDbg s načtením rozšíření ladicí program SOS zadejte následující příkaz, který získá největší volnou oblast:

  **! Adresa – souhrn**

  Zobrazí se největší volná oblast, jak je znázorněno v následujícím výstupu.

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové soustavě). Tato oblast je mnohem menší, než systém uvolňování paměti potřebuje pro segment.

  -nebo-

- Použijte příkaz **vmstat** :

  **! vmstat**

  Největší volná oblast je největší hodnota ve sloupci MAXIMUM, jak je znázorněno v následujícím výstupu.

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

### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Určení, zda je k dispozici dostatek fyzické paměti

1. Spusťte Správce úloh systému Windows.

2. Na kartě **výkon** se podívejte na potvrzenou hodnotu. (Ve Windows 7 se podívejte na **potvrzení změn (KB)** ve **skupině systém**.)

    Pokud je **Celkový součet** blízko **limitu**, dochází k nedostatku fyzické paměti.

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Určení množství paměti, kterou spravovaná halda potvrzování

- Pomocí čítače výkonu `# Total committed bytes` paměti můžete získat počet bajtů, které spravovaná halda potvrzování. Systém uvolňování paměti potvrdí bloky dat v segmentu podle potřeby, nikoli ve stejnou dobu.

  > [!NOTE]
  > Nepoužívejte čítač výkonu `# Bytes in all Heaps`, protože nepředstavuje skutečné využití paměti spravovanou haldou. Velikost generování je zahrnuta v této hodnotě a je to skutečná velikost prahové hodnoty, což je velikost, která vychází z uvolňování paměti, pokud je generování vyplněno objekty. Proto je tato hodnota obvykle nula.

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Určení velikosti paměti, kterou spravovaná halda vyhradí

- Použijte čítač výkonu `# Total reserved bytes` paměti.

  Systém uvolňování paměti rezervuje paměť v segmentech a můžete určit, kde se bude segment spouštět, pomocí příkazu **eeheap** .

  > [!IMPORTANT]
  > I když můžete určit velikost paměti, kterou systém uvolňování paměti přiděluje pro každý segment, velikost segmentu je specifická pro konkrétní implementaci a může se kdykoli změnit, a to i v pravidelných aktualizacích. Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.

- V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **! eeheap – GC**

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

  Adresy označené "segment" představují počáteční adresy segmentů.

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a>Určení velkých objektů v generaci 2

- V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **! dumpheap – stat**

  Pokud je spravovaná halda velká, může dokončení **dumpheap** chvíli trvat.

  Můžete zahájit analýzu z posledních několika řádků výstupu, protože obsahují seznam objektů, které používají nejvíce místa. Příklad:

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

  Poslední uvedený objekt je řetězec a zabírá nejvíce místa. Můžete kontrolovat svoji aplikaci, abyste viděli, jak lze optimalizovat objekty řetězců. Chcete-li zobrazit řetězce, které jsou v rozmezí 150 až 200 bajtů, zadejte následující příkaz:

  **! dumpheap-Type System. String-min 150-max 200**

  Příkladem výsledků je následující.

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  Použití celého čísla namísto řetězce pro ID může být efektivnější. Pokud se stejný řetězec opakuje v tisících, zvažte, že se bude považovat za interning. Další informace o použití řetězců naleznete v referenčním tématu pro metodu <xref:System.String.Intern%2A?displayProperty=nameWithType>.

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a>Určení odkazů na objekty

- V programu WinDbg s načtením rozšíření ladicí program SOS zadejte následující příkaz pro výpis odkazů na objekty:

  **! gcroot**

  `-or-`

- Chcete-li určit odkazy na konkrétní objekt, zadejte adresu:

  **! gcroot 1c37b2ac**

  Kořeny nalezené v zásobnících můžou být falešně pozitivní. Další informace získáte pomocí `!help gcroot`příkazu.

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

  Dokončení příkazu **gcroot** může trvat dlouhou dobu. Libovolný objekt, který není uvolněn uvolňováním paměti, je živý objekt. To znamená, že některé kořenové složky jsou přímo nebo nepřímo uchovávány na objekt, takže **gcroot** by měl vrátit informace o cestě k objektu. Měli byste prošetřit vrácené grafy a zjistit, proč se na tyto objekty stále odkazuje.

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Určení, zda byl spuštěn finalizační metoda

- Spusťte testovací program, který obsahuje následující kód:

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  Pokud test problém vyřeší, znamená to, že systém uvolňování paměti neuvolňuje objekty, protože byly pozastaveny finalizační metody pro tyto objekty. Metoda <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> umožňuje, aby finalizační metody dokončily své úkoly a vyřešily problém.

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Určení, zda objekty čekají na dokončení

1. V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

    **!finalizequeue**

    Podívejte se na počet objektů, které jsou připravené k dokončení. Pokud je číslo vysoké, je nutné prostudovat, proč tyto finalizační metody nemůžou průběžně postupovat, nebo nemůže rychle probíhat.

2. Výstup vláken získáte tak, že zadáte následující příkaz:

    **vlákna – speciální**

    Tento příkaz poskytuje výstup jako následující.

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    Finalizační vlákno indikuje, který finalizační metodu (pokud existuje) se právě spouští. Když finalizační vlákno nespouští žádné finalizační metody, čeká na událost, aby ji informovala o své práci. Ve většině případů se v tomto stavu zobrazí finalizační vlákna, protože se spustí na THREAD_HIGHEST_PRIORITY a má by se dokončit spouštění finalizační metody, pokud jsou nějaké velmi rychlé.

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Určení množství volného místa ve spravované haldě

- V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **! dumpheap – typ Free – stat**

  Tento příkaz zobrazí celkovou velikost všech bezplatných objektů na spravované haldě, jak je znázorněno v následujícím příkladu.

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- Chcete-li zjistit volné místo v generaci 0, zadejte následující příkaz pro informace o spotřebě paměti podle generace:

  **! eeheap – GC**

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

- Vypočítat místo využívané v generaci 0:

  **? 49e05d04-0x49521f8c**

  Výsledek je následující. Generace 0 je přibližně 9 MB.

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- Následující příkaz vypíše volné místo v rámci rozsahu generace 0:

  **! dumpheap-typ Free-stat 0x49521f8c 49e05d04**

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

  Tento výstup ukazuje, že část haldy generace 0 používá 9 MB prostoru pro objekty a má 7 MB volného místa. Tato analýza zobrazuje rozsah, ke kterému generace 0 přispívá ke fragmentaci. Tato velikost využití haldy by měla být zlevněná od celkové částky jako příčina fragmentace dlouhodobými objekty.

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a>Určení počtu připnutých objektů

- V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:

  **!gchandles**

  Zobrazené statistiky obsahují počet připnutých popisovačů, jak ukazuje následující příklad.

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Určení doby v uvolňování paměti

- Projděte si čítač výkonu `% Time in GC` paměti.

  Hodnota se vypočítává pomocí časového intervalu vzorkování. Vzhledem k tomu, že počítadla jsou aktualizována na konci každého uvolňování paměti, aktuální vzorek bude mít stejnou hodnotu jako předchozí vzorek, pokud během intervalu nedošlo k žádným kolekcím.

  Čas shromažďování dat je získán vynásobením času intervalu vzorkování s procentuální hodnotou.

  Následující data znázorňují čtyři intervaly vzorkování dvou sekund pro studii 8 sekund. Sloupce `Gen0`, `Gen1`a `Gen2` zobrazují počet uvolňování paměti, ke kterým došlo během daného intervalu pro danou generaci.

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  Tyto informace se nezobrazují, když dojde k uvolnění paměti, ale můžete určit počet uvolňování paměti, ke kterým došlo v časovém intervalu. V případě nejhoršího případu bylo dokončeno uvolňování paměti desáté generace 0 na začátku druhého intervalu a jedenácté uvolňování paměti 0 na konci pátého intervalu. Doba mezi koncem desátého a koncem jedenáctého uvolňování paměti je přibližně 2 sekundy a čítač výkonu zobrazuje 3%, takže doba trvání jedenáctého uvolňování paměti 0 (2 sekundy * 3% = 60ms).

  V tomto příkladu je 5 teček.

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  Druhá kolekce paměti 2. generace začala během třetího intervalu a skončila v pátém intervalu. Za nejhorší případ byl poslední uvolňování paměti pro kolekci generace 0, která skončila na začátku druhého intervalu, a uvolnění paměti 2. generace bylo dokončeno na konci pátého intervalu. Proto je čas mezi koncem uvolňování paměti generace 0 a koncem uvolňování paměti 2. generace 4 sekundy. Vzhledem k tomu, že čítač `% Time in GC` je 20%, maximální doba, po kterou by bylo možné učinit uvolňování paměti 2. generace, je (4 sekundy * 20% = 800ms).

- Alternativně můžete určit délku uvolňování paměti pomocí [událostí ETW pro uvolňování paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace a určit dobu trvání uvolňování paměti.

  Například následující data ukazují sekvenci události, ke které došlo během nesouběžného uvolňování paměti.

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

  Pozastavení spravovaného vlákna trvalo 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).

  Vlastní uvolňování paměti trvalo 4,8 ms (`GCEnd_V1` – `GCStart_V1`).

  Obnovení spravovaných vláken trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).

  Následující výstup poskytuje příklad pro uvolňování paměti na pozadí a obsahuje pole proces, vlákno a událost. (Ne všechna data jsou zobrazena.)

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

  Událost `GCStart_V1` v 42504816 označuje, že se jedná o uvolňování paměti na pozadí, protože poslední pole je `1`. To se v tomto případě stalo uvolňováním paměti. 102019.

  K události `GCStart` dojde, protože před spuštěním uvolňování paměti na pozadí je potřeba dočasné uvolňování paměti. To se v tomto případě stalo uvolňováním paměti. 102020.

  V 42514170, č. uvolnění paměti. 102020 dokončí. Spravovaná vlákna jsou v tuto chvíli restartována. Tato operace je dokončena ve vláknu 4372, které aktivovalo tuto kolekci paměti na pozadí.

  Na vlákně 4744 dojde k pozastavení. Toto je jediná doba, s jakou má uvolňování paměti na pozadí pozastavit spravovaná vlákna. Toto trvání je přibližně 99ms ((63784407-63685394)/1000).

  Událost `GCEnd` pro uvolňování paměti na pozadí je 89931423. To znamená, že uvolňování paměti na pozadí uplynulo pro přibližně 47seconds ((89931423-42504816)/1000).

  I když jsou spuštěná spravovaná vlákna, vidíte libovolný počet dočasných uvolňování paměti, ke kterým dochází.

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a>Určení toho, co vyvolalo uvolňování paměti

- V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz pro zobrazení všech vláken s jejich zásobníky volání:

  **~\*kb**

  Tento příkaz zobrazí výstup podobný následujícímu.

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  Pokud uvolňování paměti bylo způsobeno oznámením o nedostatku paměti z operačního systému, je zásobník volání podobný, s tím rozdílem, že vlákno je finalizační vlákno. Finalizační vlákno získá oznámení o asynchronní nedostatku paměti a vyřadí uvolňování paměti.

  Pokud uvolňování paměti bylo způsobeno přidělením paměti, zásobník se zobrazí takto:

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

  Pomocník za běhu (`JIT_New*`) nakonec volá `GCHeap::GarbageCollectGeneration`. Pokud zjistíte, že jsou uvolňovány paměti generace 2 způsobeny přidělením, je nutné určit, které objekty jsou shromažďovány uvolňováním paměti 2. generace a jak se jim vyhnout. To znamená, že chcete určit rozdíl mezi začátkem a koncem uvolňování paměti 2. generace a objekty, které způsobily kolekci 2. generace.

  Zadejte například následující příkaz v ladicím programu, který zobrazí začátek kolekce generace 2:

  **! dumpheap – stat**

  Příklad výstupu (zkráceně pro zobrazení objektů, které používají nejvíce místa):

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

  Opakujte tento příkaz na konci generace 2:

  **! dumpheap – stat**

  Příklad výstupu (zkráceně pro zobrazení objektů, které používají nejvíce místa):

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

  `double[]` objektů zmizely na konci výstupu, což znamená, že byly shromážděny. Tyto objekty jsou přibližně 70 MB. Zbývající objekty se nezměnily mnohem. Proto tyto `double[]` objekty byly důvodem, proč došlo k této chybě uvolňování paměti 2. generace. V dalším kroku zjistíte, proč `double[]` objekty jsou tam a proč uhynulé. Můžete požádat vývojáře kódu, ze kterého pocházejí tyto objekty, nebo můžete použít příkaz **gcroot** .

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Určení, zda vysoké využití procesoru je způsobeno uvolňováním paměti

- Proveďte korelaci hodnoty čítače výkonu `% Time in GC` paměti s časem procesu.

  Pokud `% Time in GC` hodnota špičky ve stejnou dobu jako čas zpracování, uvolňování paměti způsobuje vysoké využití procesoru. V opačném případě profilujte aplikaci, abyste zjistili, kde dochází k vysokému využití.

## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
