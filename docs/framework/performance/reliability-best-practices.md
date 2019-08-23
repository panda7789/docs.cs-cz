---
title: Spolehlivost – doporučené postupy
ms.date: 03/30/2017
helpviewer_keywords:
- marking locks
- rebooting databases
- denial of service attacks
- back-out code
- SQL Server [.NET Framework], reliability
- synchronization, reliability
- single-threaded COM components
- slow leaks
- suspending threads
- asynchronous exception handling
- leaked resources [.NET Framework]
- unmanaged memory
- memory, reliability
- threading [.NET Framework], reliability
- process-wide domain shared states
- shared states
- SafeHandle class, reliability
- reliability contracts [.NET Framework]
- cleanup operations
- constrained execution regions
- CERs
- finalizers, reliability
- reliability [.NET Framework]
- blocks, reliability
- finally clauses
- cross-application domain shared states
- catch blocks
- identifying locks
- writing reliable code
- impersonation
- GC.KeepAlive method
- managed threading
- locks, reliability
- STA-dependent features
- fibers
ms.assetid: cf624c1f-c160-46a1-bb2b-213587688da7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e24cd05bb1c1ed9425c9be8bc02cb92dc488005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935728"
---
# <a name="reliability-best-practices"></a>Spolehlivost – doporučené postupy

Následující pravidla spolehlivosti se orientují na SQL Server; vztahují se ale také na všechny serverové aplikace založené na hostiteli. Je velmi důležité, aby servery, jako SQL Server, neunikly prostředky a nemohly být zavedeny.  To však nelze provést zápisem zpětného zápisu kódu pro každou metodu, která mění stav objektu.  Cílem není zapsat 100% spolehlivého spravovaného kódu, který se bude obnovovat ze všech chyb v každém umístění s back-výstupním kódem.  To by byl úkol těžké s nízkou pravděpodobností úspěchu.  Modul CLR (Common Language Runtime) nemůže snadno poskytnout dostatečně velkou záruku pro spravovaný kód, aby bylo možné psát dokonalý kód.  Všimněte si, že na rozdíl od ASP.NET SQL Server používá pouze jeden proces, který nelze recyklovat, aniž by došlo k nepřijatelně dlouhé době databáze.

S těmito slabšími zárukami a provozováním v jednom procesu je spolehlivost založena na ukončení vláken nebo recyklace domén aplikace, pokud je to nutné, a přijímá opatření k zajištění toho, aby prostředky operačního systému, jako jsou například popisovače nebo paměť, nebyly Nevráceny.  I s tímto jednodušším omezením spolehlivosti stále platí významný požadavek na spolehlivost:

- Nikdy neúnik prostředků operačního systému.

- Identifikujte všechny spravované zámky ve všech formulářích pro CLR.

- Nikdy Nerušit sdílený stav domény mezi aplikacemi, což <xref:System.AppDomain> umožňuje hladce pracovat v recyklaci.

I když je teoreticky možné napsat spravovaný kód pro zpracování <xref:System.Threading.ThreadAbortException> <xref:System.StackOverflowException>výjimek, a <xref:System.OutOfMemoryException> , očekávají vývojářům, aby takový robustní kód napsal v celé aplikaci, je nepřípustný.  Z tohoto důvodu vyplývají z nedostatku pásma vykonávání zpracovávaného vlákna; a pokud ukončené vlákno upravovalo sdílený stav, což může být určeno, zda vlákno drží zámek, pak dojde k <xref:System.AppDomain> uvolnění.  Když je metoda, která upravuje sdílený stav, ukončená, stav bude poškozený, protože není možné zapsat spolehlivý back-výstupní kód pro aktualizace do sdíleného stavu.

V .NET Framework verze 2,0 je jediným hostitelem, který vyžaduje spolehlivost, SQL Server.  Pokud bude vaše sestavení spuštěno na SQL Server měli byste provádět spolehlivost v každé části tohoto sestavení, a to i v případě, že existují konkrétní funkce, které jsou při spuštění v databázi zakázané.  To je vyžadováno, protože modul pro analýzu kódu kontroluje kód na úrovni sestavení a nemůže odlišit zakázaný kód. Dalším aspektem SQL Server programování je to, že SQL Server spouští vše v jednom <xref:System.AppDomain> procesu a recyklace se používá pro vyčištění všech prostředků, jako jsou například obslužné rutiny paměti a operačního systému.

Nemůžete záviset na finalizační nebo destruktorech `try/finally` nebo blocích pro back-výstupní kód. Mohou být přerušeny nebo volány.

Asynchronní výjimky lze vyvolat v neočekávaných umístěních, případně v každé <xref:System.Threading.ThreadAbortException>instrukci počítače <xref:System.OutOfMemoryException>:, <xref:System.StackOverflowException>a.

Spravovaná vlákna nejsou nutně vlákny Win32 v SQL; můžou být vlákny.

Proměnlivý sdílený stav domény v úrovni procesu nebo meziaplikace je velmi obtížně pozměňován a je třeba se jim vyhnout, kdykoli je to možné.

Podmínky nedostatku paměti nejsou v SQL Server zřídka.

Pokud knihovny hostované v SQL Server správně neaktualizují svůj sdílený stav, je vysoká pravděpodobnost, že kód nebude obnoven, dokud nebude databáze restartována.  V některých extrémních případech to může způsobit selhání procesu SQL Server, což způsobí, že se databáze restartuje.  Restartování databáze může převzít web nebo ovlivnit operace společnosti, neubližujeme dostupnost.  Pomalé úniky prostředků operačního systému, jako je například paměť nebo popisovače, může způsobit, že server nakonec selže při přidělování obslužných rutin bez možnosti obnovení, nebo může server pomalu snížit výkon a omezit aplikaci zákazníka. dostupnosti.  Jasně chceme, abyste se vyhnuli těmto scénářům.

## <a name="best-practice-rules"></a>Pravidla osvědčených postupů

Úvod se zaměřuje na to, co kontrola kódu pro spravovaný kód, který běží na serveru, by musela zachytit, aby se zvýšila stabilita a spolehlivost rozhraní. Všechny tyto kontroly jsou obecně osvědčené a na serveru musí být absolutní.

V případě nedoručeného zámku nebo omezení prostředku SQL Server přeruší vlákno nebo <xref:System.AppDomain>odhlásí.  Pokud k tomu dojde, je zaručeno spuštění pouze back-výstupních kódů v oblasti s omezením spuštění (CER).

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Použití třídy SafeHandle k zamezení nevracení prostředků

V <xref:System.AppDomain> případě uvolnění nemůžete záviset na <xref:System.Runtime.InteropServices.SafeHandle> `finally` blocích nebo finalizační metody, takže je důležité, aby byl veškerý přístup k prostředkům operačního systému abstraktní prostřednictvím třídy spíše než <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>nebo podobné třídy. To umožňuje, aby modul CLR sledoval a zavřel táhla, která používáte, <xref:System.AppDomain> i v případě nenáročného případu.  <xref:System.Runtime.InteropServices.SafeHandle>bude používat kritický finalizační metodu, kterou bude modul CLR vždy spuštěn.

Popisovač operačního systému je uložen v bezpečném popisovači od okamžiku, kdy je vytvořen až do chvíle, kdy se uvolnil.  Neexistuje žádné okno, ve <xref:System.Threading.ThreadAbortException> kterém by mohlo dojít k úniku popisovačů.  Kromě toho vyvolá vyvolání platformy odkaz – vyhodnotí popisovač, který umožňuje zavřít sledování životnosti popisovače a zabránit bezpečnostnímu problému s podmínkou časování mezi `Dispose` a metodou, která aktuálně používá popisovač.

Většina tříd, které v současné době mají finalizační metodu pro jednoduše vyčištění popisovače operačního systému, nebude potřebovat finalizační metodu. Místo toho bude finalizační metoda na <xref:System.Runtime.InteropServices.SafeHandle> odvozené třídě.

Všimněte si <xref:System.Runtime.InteropServices.SafeHandle> , že není náhradou <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>za.  Stále existují potenciální problémy s kolizem prostředků a výkonem, aby bylo možné explicitně uvolnit prostředky operačního systému.  Stačí si uvědomit `finally` , že bloky, které explicitně odstraňují prostředky, se nemusí provádět k dokončení.

<xref:System.Runtime.InteropServices.SafeHandle>umožňuje implementovat vlastní <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodu, která provede práci k uvolnění popisovače, jako je například předání stavu do rutiny pro uvolnění operačního systému nebo uvolnění sady popisovačů ve smyčce.  Modul CLR garantuje, že je tato metoda spuštěna.  Je zodpovědností autora <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementace, aby bylo zajištěno, že se popisovač uvolní za všech okolností. V takovém případě dojde k nevrácení popisovače, což často vede k úniku nativních prostředků přidružených k popisovači. Proto je důležité strukturovat <xref:System.Runtime.InteropServices.SafeHandle> odvozené třídy tak <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> , aby implementace nevyžadovala přidělení všech prostředků, které nemusí být k dispozici v době vyvolání. Všimněte si, že je dovoleno volat metody, které mohou selhat v rámci <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementace za předpokladu, že váš kód může zpracovat taková selhání a dokončit kontrakt k uvolnění nativního popisovače. Pro účely ladění <xref:System.Boolean> má <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> návratovou hodnotu, která může být nastavena na `false` hodnotu, pokud dojde k závažné chybě, která brání vydání prostředku. Tím se aktivuje [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) MDA, pokud je tato možnost povolená, aby bylo možné tento problém identifikovat. Neovlivňuje modul runtime žádným jiným způsobem; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nebude volána znovu pro stejný prostředek, a v důsledku toho nebude popisovač vrácen.

<xref:System.Runtime.InteropServices.SafeHandle>není v některých kontextech vhodný.  Vzhledem k tomu, že <xref:System.GC> <xref:System.Runtime.InteropServices.SafeHandle>metodu lze spustit v finalizační vlákně, nesmí být všechny popisovače, které jsou požadovány pro uvolnění určitého vlákna, zabaleny do. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>

Běhové obálky pro volání (RCW) lze vyčistit modulem CLR bez dalšího kódu.  Pro kód, který používá vyvolání platformy a pracuje s objektem com jako `IUnknown*` <xref:System.IntPtr>nebo, by měl být kód přepsán, aby používal RCW.  <xref:System.Runtime.InteropServices.SafeHandle>nemusí být vhodné pro tento scénář z důvodu možnosti nespravované metody verze zpětné volání zpět do spravovaného kódu.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Slouží <xref:System.Runtime.InteropServices.SafeHandle> k zapouzdření prostředků operačního systému. Nepoužívejte <xref:System.Runtime.InteropServices.HandleRef> ani pole typu <xref:System.IntPtr>.

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Zajistěte, aby finalizační metody nemusely běžet, aby se zabránilo úniku prostředků operačního systému

Pečlivě zkontrolujte své finalizační metody a ujistěte se, že i v případě, že nejsou spuštěné, není nevrácen důležitý prostředek operačního systému.  Na rozdíl od normálního <xref:System.AppDomain> uvolnění v případě, kdy je aplikace spuštěna v stabilním stavu, nebo pokud server, jako je například SQL Server vypnutí, objekty nejsou dokončeny během náhlého <xref:System.AppDomain> uvolnění.  Zajistěte, aby v případě náhlého uvolnění prostředků nedošlo k úniku prostředků, protože není zaručená správnost aplikace, ale integrita serveru musí být udržována nevracením prostředků.  Použijte <xref:System.Runtime.InteropServices.SafeHandle> k uvolnění všech prostředků operačního systému.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Zajistěte, aby klauzule finally nemusely běžet, aby se zabránilo úniku prostředků operačního systému

`finally`není zaručeno spouštění klauzulí mimo CERs, což vyžaduje, aby vývojáři knihovny nespoléhat na kód v rámci `finally` bloku k uvolnění nespravovaných prostředků.  Použití <xref:System.Runtime.InteropServices.SafeHandle> je doporučené řešení.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Použijte <xref:System.Runtime.InteropServices.SafeHandle> k čištění prostředků operačního systému `Finalize`místo. Nepoužívejte <xref:System.IntPtr>, použijte <xref:System.Runtime.InteropServices.SafeHandle> k zapouzdření prostředků. Pokud je nutné použít klauzuli finally, umístěte ji do CER.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Všechny zámky by měly projít existujícím spravovaným kódem pro uzamykání

CLR musí znát, pokud je kód v zámku, aby věděl <xref:System.AppDomain> , že by se místo pouhého přerušení vlákna přerušilo.  Přerušení vlákna může být nebezpečné, protože data provozovaná vláknem by mohla být ponechána v nekonzistentním stavu. Proto je nutné provést <xref:System.AppDomain> recyklaci celého.  Důsledky selhání identifikace zámku můžou být buď zablokované, nebo nesprávné výsledky. Použijte metody <xref:System.Threading.Thread.BeginCriticalRegion%2A> a <xref:System.Threading.Thread.EndCriticalRegion%2A> k identifikaci oblastí zámku.  Jsou to statické metody pro <xref:System.Threading.Thread> třídu, která se vztahuje pouze na aktuální vlákno, což pomáhá zabránit jednomu vláknu v úpravě počtu zámků jiného vlákna.

<xref:System.Threading.Monitor.Enter%2A>a <xref:System.Threading.Monitor.Exit%2A> mít tato oznámení CLR vestavěnou, takže jejich použití se doporučuje a také použití [příkazu Lock](../../csharp/language-reference/keywords/lock-statement.md), který tyto metody používá.

Jiné mechanismy zamykání, jako jsou zámky <xref:System.Threading.AutoResetEvent> a musí volat tyto metody pro informování CLR o tom, že je zadávána kritická část.  Tyto metody nevyužívají žádné zámky. informují CLR, že kód je spuštěn v kritickém oddílu a přerušení vlákna může opustit sdílený stav nekonzistentní.  Pokud jste definovali vlastní typ zámku, například vlastní <xref:System.Threading.ReaderWriterLock> třídu, použijte tyto metody čítače uzamčení.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Označte a identifikujte všechny zámky <xref:System.Threading.Thread.EndCriticalRegion%2A>pomocí <xref:System.Threading.Thread.BeginCriticalRegion%2A> a. Nepoužívejte <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>a <xref:System.Threading.Interlocked.Decrement%2A> ve smyčce.  Neprovádějte vyvolání platformy z variant těchto metod Win32.  Nepoužívejte <xref:System.Threading.Thread.Sleep%2A> ve smyčce.  Nepoužívejte nestálá pole.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Kód pro vyčištění musí být v bloku finally nebo catch, který není po catch.

Kód pro vyčištění by nikdy neměl `catch` následovat za blokem, měl by `finally` být v samotném `catch` bloku nebo.  To by mělo být normální dobrý postup.  Blok je obecně upřednostňovaný, protože spouští stejný kód v případě, že je vyvolána výjimka a při normálním `try` výskytu bloku. `finally`  V případě vyvolání neočekávané výjimky, například <xref:System.Threading.ThreadAbortException>, nebude kód pro vyčištění spuštěn.  Jakékoli nespravované prostředky, které byste měli vyčistit v `finally` rámci, by měly být <xref:System.Runtime.InteropServices.SafeHandle> v ideálním případě zabaleny do, aby se zabránilo únikům.  Všimněte si C# `using` , že klíčové slovo lze efektivně použít k Dispose objektů, včetně obslužných rutin.

I <xref:System.AppDomain> když recyklace může vyčistit prostředky ve vlákně finalizační metody, je stále důležité umístit kód vyčištění na správné místo.  Všimněte si, že pokud vlákno obdrží asynchronní výjimku bez držení zámku, modul CLR se pokusí ukončit samotný podproces bez nutnosti recyklovat <xref:System.AppDomain>.  Zajistěte, aby se prostředky vyčistily dříve než později, a to díky tomu, že bude k dispozici více prostředků a lepší správa životního cyklu.  Pokud explicitně neuzavřete popisovač do souboru v nějaké cestě kódu chyby, počkejte <xref:System.Runtime.InteropServices.SafeHandle> , až ho finalizační metoda vyčistí. při dalším spuštění kódu se může pokusit o přístup k přesnému stejnému souboru, pokud se ještě nespustí finalizační metoda.  Z tohoto důvodu je potřeba zajistit, aby kód pro čištění existoval a správně fungoval, a to i v případě, že není nezbytně nutné.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Kód pro vyčištění `catch` po dokončení musí být `finally` v bloku. Umístit volání k Dispose v bloku finally.  `catch`bloky by měly končit throw nebo Rethrow.  I když dojde k výjimkám, jako je například zjištění kódu, zda je možné vytvořit síťové připojení, kde se může zobrazit nějaký velký počet výjimek, jakýkoli kód, který vyžaduje zachycení určitého počtu výjimek za normálních okolností, by měl poskytnout označení, že by měl být testován kód, aby bylo možné zjistit, zda bude úspěšný.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Proměnlivý sdílený stav na úrovni procesu mezi doménami aplikace by se měl vyloučit nebo použít oblast omezeného provádění.

Jak je popsáno v úvodu, může být velmi obtížné napsat spravovaný kód, který monitoruje sdílený stav napříč doménami aplikace spolehlivým způsobem.  Sdílený stav v rámci procesu je jakýkoli druh dat, který je sdílen mezi doménami aplikace, buď v kódu Win32, uvnitř CLR, nebo ve spravovaném kódu pomocí vzdálené komunikace.  Libovolný proměnlivý sdílený stav je velmi obtížné správně psát ve spravovaném kódu a jakýkoliv statický sdílený stav může být proveden pouze s velkou péčí.  Pokud máte sdílený stav na úrovni procesu nebo počítače, najděte nějaký způsob, jak ho odstranit, nebo chránit sdílený stav pomocí omezené oblasti provádění (CER).  Všimněte si, že jakákoliv knihovna se sdíleným stavem, který není identifikovaný a opravená, by mohla způsobit, že hostitel <xref:System.AppDomain> , jako je například SQL Server, potřebuje k chybě čistou vykládku.

Pokud kód používá objekt modelu COM, vyhněte se sdílení tohoto objektu COM mezi doménami aplikace.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Zámky nefungují v rámci aplikačních domén nebo mezi nimi.

V minulosti <xref:System.Threading.Monitor.Enter%2A> a [příkaz Lock](../../csharp/language-reference/keywords/lock-statement.md) byl použit k vytvoření globálních zámků procesu.  K tomu dochází například při zamykání na <xref:System.AppDomain> agilních třídách, jako jsou <xref:System.Type> instance z nesdílených sestavení, <xref:System.Threading.Thread> objekty, internované řetězce a některé řetězce sdílené napříč doménami aplikace pomocí vzdálené komunikace.  Tyto zámky již nejsou v procesu nadále platné.  Chcete-li zjistit přítomnost zámku meziaplikační domény v rámci procesu, určete, zda kód v zámku používá jakýkoliv externí, trvalý prostředek, jako je například soubor na disku nebo případně databáze.

Počítejte s tím, že při použití <xref:System.AppDomain> zámku v rámci může dojít k potížím, pokud chráněný kód používá externí prostředek, protože tento kód může běžet současně napříč více aplikačními doménami.  Může se jednat o problém při zápisu do jednoho souboru protokolu nebo k vytvoření vazby na soket pro celý proces.  Tyto změny znamenají, že neexistuje jednoduchý způsob použití spravovaného kódu pro získání globálního zámku procesu, než použití pojmenovaného <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore> instance.  Vytvořte kód, který neběží současně se dvěma aplikačními doménami, nebo <xref:System.Threading.Mutex> použijte <xref:System.Threading.Semaphore> třídy nebo.  Pokud existující kód nelze změnit, k dosažení této synchronizace nepoužívejte Win32 pojmenovaný mutex, protože je spuštěn v režimu Fiber-in znamená, že nemůžete zaručit, že stejné vlákno operačního systému získá a uvolní mutex.  Je <xref:System.Threading.Mutex> nutné použít spravovanou třídu, nebo s názvem <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, nebo <xref:System.Threading.Semaphore> , chcete-li synchronizovat zámek kódu způsobem, který je v modulu CLR vědom, namísto synchronizace zámku pomocí nespravovaného kódu.

#### <a name="avoid-locktypeofmytype"></a>Nepoužívat zámek (typeof (MyType))

Soukromé a veřejné <xref:System.Type> objekty ve sdílených sestaveních s pouze jednou kopií kódu sdílené napříč všemi doménami aplikace také představují problémy.  Pro sdílená sestavení je k dispozici pouze jedna instance <xref:System.Type> pro každý proces, což znamená, že více domén aplikace sdílí <xref:System.Type> stejné instance.  Uzamčení <xref:System.Type> instance převezme zámek, který má vliv na celý proces, nikoli jenom na <xref:System.AppDomain>.  Pokud jeden <xref:System.AppDomain> z nich převezme zámek <xref:System.Type> na objektu, vlákno se náhle přeruší, ale zámek neuvolní.  Tento zámek pak může způsobit zablokování jiných aplikačních domén.

Dobrým způsobem, jak převzít zámky ve statických metodách, je přidání statického interního objektu synchronizace do kódu.  To může být inicializováno v konstruktoru třídy, pokud je k dispozici, ale pokud není možné ji inicializovat takto:

```csharp
private static Object s_InternalSyncObject;
private static Object InternalSyncObject
{
    get
    {
        if (s_InternalSyncObject == null)
        {
            Object o = new Object();
            Interlocked.CompareExchange(
                ref s_InternalSyncObject, o, null);
        }
        return s_InternalSyncObject;
    }
}
```

Pak při použití zámku použijte `InternalSyncObject` vlastnost k získání objektu, který se má zamknout.  Tuto vlastnost nemusíte používat, pokud jste v konstruktoru třídy provedli inicializaci objektu interní synchronizace.  Inicializační kód zámku pro dvojité zaškrtnutí by měl vypadat jako v tomto příkladu:

```csharp
public static MyClass SingletonProperty
{
    get
    {
        if (s_SingletonProperty == null)
        {
            lock(InternalSyncObject)
            {
                // Do not use lock(typeof(MyClass))
                if (s_SingletonProperty == null)
                {
                    MyClass tmp = new MyClass(…);
                    // Do all initialization before publishing
                    s_SingletonProperty = tmp;
                }
            }
        }
        return s_SingletonProperty;
    }
}
```

#### <a name="a-note-about-lockthis"></a>Poznámka o zámku (this)

Obecně je přijatelné přijmout zámek na individuálním objektu, který je veřejně přístupný.  Pokud je však objekt objekt typu Singleton, který by mohl způsobit zablokování celého subsystému, zvažte použití výše uvedeného vzoru návrhu také.  Například zámek na jednom <xref:System.Security.SecurityManager> objektu by mohl způsobit zablokování <xref:System.AppDomain> v rámci celého <xref:System.AppDomain> nepoužitelného nastavení. Není vhodné pořizovat zámek u veřejně přístupného objektu tohoto typu.  Zámek u jednotlivých kolekcí nebo polí by však neměl obvykle představovat problém.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Neprovádějte zámky u typů, které by mohly být použity napříč doménami aplikace, nebo nemají silný smysl identity. Nevolejte <xref:System.Threading.Monitor.Enter%2A> <xref:System.Type>na, ,,<xref:System.String> <xref:System.MarshalByRefObject>,, nebo<xref:System.Threading.Thread>žádný objekt, který je odvozen z. <xref:System.ValueType> <xref:System.Reflection.MethodInfo> <xref:System.Reflection.PropertyInfo>

### <a name="remove-gckeepalive-calls"></a>Odeberte GC. Volání kontroly udržení naživu

Významné množství stávajícího kódu buď nepoužívá <xref:System.GC.KeepAlive%2A> , pokud by ho mělo nebo používá, pokud není vhodné.  Po převodu na <xref:System.Runtime.InteropServices.SafeHandle>třídu není nutné volat <xref:System.GC.KeepAlive%2A>třídy za předpokladu, že nemají <xref:System.Runtime.InteropServices.SafeHandle> finalizační metodu, ale spoléhají na dokončení obslužných rutin operačního systému.  I když náklady na výkon při zachování volání <xref:System.GC.KeepAlive%2A> mohou být zanedbatelné, vnímání, že <xref:System.GC.KeepAlive%2A> volání je buď nezbytné, nebo dostačující k vyřešení potíží při životnosti, která již nemusí existovat, způsobuje, že kód bude obtížnější udržovat.  Pokud však použijete volání RCW (COM interop CLR), <xref:System.GC.KeepAlive%2A> je stále vyžadován kódem.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Odebrat <xref:System.GC.KeepAlive%2A>.

### <a name="use-the-host-protection-attribute"></a>Použít atribut ochrany hostitele

Rozhraní <xref:System.Security.Permissions.HostProtectionAttribute> (hPa) poskytuje použití deklarativních akcí zabezpečení k určení požadavků na ochranu hostitele, aby mohl hostitel zabránit tomu, aby před voláním určitých metod, které jsou pro daného hostitele nevhodným způsobem, mohl ještě plně důvěryhodný kód. například <xref:System.Environment.Exit%2A> nebo<xref:System.Windows.Forms.MessageBox.Show%2A> pro SQL Server.

HPA ovlivňuje pouze nespravované aplikace, které hostují modul CLR (Common Language Runtime) a implementují ochranu hostitele, například SQL Server. Při použití akce zabezpečení má za následek vytvoření požadavku propojení na základě prostředků hostitele, které třída nebo metoda zveřejňuje. Pokud je kód spuštěn v klientské aplikaci nebo na serveru, který není chráněn hostitelem, atribut "vypařování"; nedetekuje se, a proto se nepoužije.

> [!IMPORTANT]
> Účelem tohoto atributu je vynutilit pokyny pro programovací model specifický pro hostitele, nikoli chování zabezpečení.  Přestože požadavek na propojení slouží ke kontrole shody s požadavky na programovací model, <xref:System.Security.Permissions.HostProtectionAttribute> není oprávnění zabezpečení.

Pokud hostitel nemá požadavky na programovací model, nejsou k dispozici žádné požadavky propojení.

Tento atribut identifikuje následující:

- Metody nebo třídy, které se nevejdou do programovacího modelu hostitele, ale jsou jinak neškodné.

- Metody nebo třídy, které se nevejdou do programovacího modelu hostitele a můžou vést k destabilizující uživatelského kódu spravovaného serverem.

- Metody nebo třídy, které se nevejdou do programovacího modelu hostitele a mohou vést k destabilizaci samotného procesu serveru.

> [!NOTE]
> Pokud vytváříte knihovnu tříd, která bude volána aplikacemi, které mohou být spuštěny v hostitelském prostředí, měli byste tento atribut použít pro členy, kteří zveřejňují <xref:System.Security.Permissions.HostProtectionResource> kategorie prostředků. .NET Framework členové knihovny tříd s tímto atributem způsobí, že bude zaškrtnuto pouze bezprostředního volajícího.  Váš člen knihovny musí také způsobit kontrolu svého bezprostředního volajícího stejným způsobem.

Další informace najdete v HPA v <xref:System.Security.Permissions.HostProtectionAttribute>.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Pro SQL Server se všechny metody použité k zavedení synchronizace nebo dělení na vlákna musí identifikovat pomocí HPA. Patří sem metody, které sdílejí stav, jsou synchronizovány nebo spravují externí procesy. Hodnoty, které mají vliv na <xref:System.Security.Permissions.HostProtectionResource.SharedState>SQL Server <xref:System.Security.Permissions.HostProtectionResource.Synchronization>jsou, <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>a. <xref:System.Security.Permissions.HostProtectionResource> Nicméně jakákoli metoda, která zveřejňuje <xref:System.Security.Permissions.HostProtectionResource> nějaký, by měla být identifikována hPa, nikoli jenom pomocí prostředků ovlivňujících SQL.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Neblokovat po neomezenou dobu v nespravovaném kódu

Blokování v nespravovaném kódu namísto ve spravovaném kódu může způsobit útok na dostupnost služby, protože modul CLR nemůže přerušit vlákno.  Blokované vlákno zabraňuje CLR v uvolňování <xref:System.AppDomain>, přinejmenším bez provedení některých extrémně nebezpečných operací.  Blokování použití primitiva synchronizace systému Windows je jasným příkladem něčeho, co nemůžeme dovolit.  Blokování volání `ReadFile` na soketu by se mělo vyhnout, pokud je to možné – v ideálním případě rozhraní Windows API by mělo poskytovat mechanismus pro operaci, jako je například vyprší časový limit.

Jakákoli metoda, která volá do nativního, by ideálním způsobem používala volání Win32 s přiměřeným, konečným časovým limitem.  Pokud má uživatel povolený časový limit, neměl by mít uživatel povoleno zadat neomezený časový limit bez určitého konkrétního oprávnění zabezpečení.  V případě, že je metoda zablokovaná na více než ~ 10 sekund, je třeba použít verzi, která podporuje vypršení časových limitů, nebo potřebujete další podporu CLR.

Tady je několik příkladů problematických rozhraní API.  Kanály (anonymní i pojmenované) se dají vytvořit s časovým limitem. kód však musí zajistit, aby nikdy `CreateNamedPipe` nevolal `WaitNamedPipe` ani s NMPWAIT_WAIT_FOREVER.  Kromě toho může být neočekávané blokování i v případě, že je zadán časový limit.  Volání `WriteFile` na anonymním kanálu se zablokuje, dokud se nezapisují všechny bajty, což znamená, že v ní dojde `WriteFile` k nedostatku dat, volání se zablokuje, dokud čtecí zařízení neuvolní místo ve vyrovnávací paměti kanálu.  Sokety by měly vždycky používat rozhraní API, které respektují mechanismus časového limitu.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Blokování bez časového limitu v nespravovaném kódu je útok s cílem odepření služby. Neprovádějte volání vyvolání platformy do `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects` `MsgWaitForMultipleObjects`, a `MsgWaitForMultipleObjectsEx`.  Nepoužívejte NMPWAIT_WAIT_FOREVER.

### <a name="identify-any-sta-dependent-features"></a>Identifikujte všechny funkce závislé na STA.

Identifikujte jakýkoli kód, který používá objekty Apartment s jedním vláknem modelu COM (STAs).  STAs jsou v procesu SQL Server zakázané.  Funkce, které jsou `CoInitialize`závislé na, například čítače výkonu nebo schránka, musí být v rámci SQL Server zakázané.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Zajistěte, aby finalizační metody byly bez problémů s synchronizací.

V budoucích verzích .NET Framework může existovat více vláken finalizační metody, což znamená, že finalizační metody pro různé instance stejného typu běží současně.  Nemusí být zcela bezpečné pro přístup z více vláken; systém uvolňování paměti zaručuje, že pouze jedno vlákno spustí finalizační metodu pro danou instanci objektu.  Nicméně finalizační metody musí být kódované, aby nedocházelo ke konfliktům časování a zablokování při současném spuštění na více různých instancích objektů.  Při použití libovolného externího stavu, jako je například zápis do souboru protokolu, musí být v finalizační metodě zpracovávány problémy s vlákny.  Nespoléhá na finalizaci, aby se zajistila bezpečnost vlákna. Nepoužívejte thread local úložiště, spravované nebo nativní, k uložení stavu ve vlákně finalizační metody.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Finalizační metody musí být bez problémů s synchronizací. Nepoužívejte statický proměnlivý stav v finalizační metodě.

### <a name="avoid-unmanaged-memory-if-possible"></a>Pokud je to možné, vyhněte se nespravované paměti

Nespravovanou paměť lze zneniknout, stejně jako popisovač operačního systému. Pokud je to možné, zkuste použít paměť v zásobníku pomocí [stackalloc](../../csharp/language-reference/operators/stackalloc.md) nebo připnutého spravovaného objektu, jako je například [pevný příkaz](../../csharp/language-reference/keywords/fixed-statement.md) nebo <xref:System.Runtime.InteropServices.GCHandle> s použitím bajtu []. Nakonec <xref:System.GC> je vyčistí. Pokud však musíte přidělit nespravovanou paměť, zvažte použití třídy, která je odvozena z <xref:System.Runtime.InteropServices.SafeHandle> pro zabalení přidělení paměti.

Všimněte si, že existuje alespoň jeden případ, <xref:System.Runtime.InteropServices.SafeHandle> kde není dostačující.  Pro volání metod modelu COM, které přidělují nebo uvolňují paměť, je běžné, že jedna knihovna `CoTaskMemAlloc` DLL přidělí paměť prostřednictvím jiné knihovny DLL `CoTaskMemFree`uvolní tuto paměť.  Použití <xref:System.Runtime.InteropServices.SafeHandle> na těchto místech by nebylo vhodné, protože se pokusí spojit životní cyklus nespravované paměti po celou dobu životnosti, <xref:System.Runtime.InteropServices.SafeHandle> místo aby jiná knihovna DLL mohla řídit dobu života paměti.

### <a name="review-all-uses-of-catchexception"></a>Zkontrolovat všechna použití catch (výjimka)

Bloky catch, které zachycují všechny výjimky místo jedné konkrétní výjimky, teď budou zachytit i asynchronní výjimky.  Prověřte každý blok catch (Exception), vyhledá žádné důležité uvolnění prostředků nebo kód back-výstup, který může být vynechán, a potenciálně nesprávné chování v rámci bloku catch pro zpracování <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>nebo <xref:System.OutOfMemoryException>.  Všimněte si, že je možné, že tento kód může zaprotokolovat nebo vytvořit některé předpoklady, které mohou zobrazit pouze určité výjimky nebo které pokaždé, když dojde k výjimce, se nezdařila z přesně jednoho konkrétního důvodu.  Tyto předpoklady je potřeba aktualizovat, aby zahrnovaly <xref:System.Threading.ThreadAbortException>.

Zvažte změnu všech míst, která zachycují všechny výjimky pro zachycení konkrétního typu výjimky, kterou očekáváte, například <xref:System.FormatException> z metod formátování řetězce.  To zabrání spuštění bloku catch v neočekávaných výjimkách a pomůže zajistit, že kód nebude skrývat chyby tím, že se zachytí neočekávané výjimky.  Jako obecné pravidlo nikdy nezpracovává výjimku v kódu knihovny (kód, který vyžaduje, abyste zachytili výjimku, může znamenat chybu návrhu v kódu, který voláte).  V některých případech můžete chtít zachytit výjimku a vyvolat jiný typ výjimky, aby bylo možné poskytnout více dat.  V tomto případě použijte vnořené výjimky a uložte skutečnou příčinu selhání do <xref:System.Exception.InnerException%2A> vlastnosti nové výjimky.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Zkontrolujte všechny bloky catch ve spravovaném kódu, které zachycují všechny objekty nebo zachytí všechny výjimky.  V C#systému `catch` to znamená označení příznakem `catch(Exception)` {} a {}.  Zvažte, zda je typ výjimky velmi specifický, nebo zkontrolujte kód, abyste se ujistili, že se nejedná o špatný způsob, pokud zachytává neočekávaný typ výjimky.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Nepředpokládat spravované vlákno je vlákno Win32 – jedná se o vlákno.

Použití spravovaného úložiště thread local funguje, ale nepoužíváte nespravované úložiště thread local nebo předpokládáte, že se kód v aktuálním vláknu operačního systému spustí znovu.  Neměňte nastavení, jako je národní prostředí vlákna.  Nevolejte nebo `InitializeCriticalSection` `CreateMutex` Nevolejte volání platformy, protože vyžadují vlákno operačního systému, které zadává zámek, také ukončí zámek.  Vzhledem k tomu, že se nejedná o případ použití vláken, důležité oddíly Win32 a mutex nelze použít přímo v SQL.  Všimněte si, že <xref:System.Threading.Mutex> spravovaná třída nezpracovává obavy tohoto spřažení vlákna.

Většinu stavu můžete bezpečně použít u spravovaného <xref:System.Threading.Thread> objektu, včetně spravovaného Thread localho úložiště a aktuální jazykové verze uživatelského rozhraní vlákna.  Můžete také použít <xref:System.ThreadStaticAttribute>, což umožňuje, aby byla hodnota existující statické proměnné přístupná pouze aktuálním spravovaným vláknem (Jedná se o další způsob, jak v modulu CLR provádět vlákna v místním úložišti).  Pro účely programovacího modelu nemůžete změnit aktuální jazykovou verzi vlákna při spuštění v SQL.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

SQL Server běží v režimu Fiber; Nepoužívejte thread local Storage. Vyhněte se vyvolání volání `TlsAlloc`platformy `TlsFree`, `TlsGetValue`, a`TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>Povolit SQL Server manipulaci s zosobněním

Vzhledem k tomu, že zosobnění funguje na úrovni vlákna a SQL může běžet v vláknovém režimu, spravovaný kód by neměl zosobnit uživatele a neměl by `RevertToSelf`volat.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Umožněte SQL Server pořizování zosobnění. `RevertToSelf`Nepoužívejte ,`ImpersonateSelf`, `ImpersonateAnonymousToken` ,`ImpersonateDdeClientWindow`,, ,,`RpcImpersonateClient`,,, nebo .`SetThreadToken` `RpcRevertToSelf` `RpcRevertToSelfEx` `ImpersonateLoggedOnUser` `ImpersonateNamedPipeClient` `DdeImpersonateClient`

### <a name="do-not-call-threadsuspend"></a>Nevolat vlákno:: Suspend

Schopnost pozastavit vlákno se může zobrazit jako jednoduchá operace, ale může způsobit zablokování.  Pokud vlákno drží zámek pozastaveno druhým vláknem a potom se druhé vlákno pokusí přebírat stejný zámek, dojde k zablokování.  <xref:System.Threading.Thread.Suspend%2A>může v současné době ovlivňovat zabezpečení, načítání tříd, vzdálenou komunikaci a reflexi.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Nevolejte <xref:System.Threading.Thread.Suspend%2A>. Zvažte místo toho použití reálného primitiva synchronizace, jako <xref:System.Threading.Semaphore> je <xref:System.Threading.ManualResetEvent> například nebo.

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Chraňte kritické operace s omezenými oblastmi provádění a smlouvami o spolehlivosti.

Při provádění složitých operací, které aktualizují sdílený stav nebo které musí být deterministické buď zcela úspěšné nebo zcela neúspěšné, se ujistěte, že je chráněna pomocí omezené oblasti provádění (CER). To zaručuje, že kód se spustí v každém případě, dokonce i náhlé přerušení vlákna nebo náhlé <xref:System.AppDomain> uvolnění.

CER je konkrétní `try/finally` blok hned před <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>voláním.

Tím se dá instruovat kompilátor za běhu pro přípravu veškerého kódu v bloku finally před spuštěním `try` bloku. To zaručuje, že kód v bloku finally je sestaven a bude spuštěn ve všech případech. Není neobvyklé, že v CER může být prázdný `try` blok. Použití CER chrání proti přerušení asynchronního vlákna a výjimky z důvodu nedostatku paměti. Přečtěte si téma <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> pro podobu formátu CER, která navíc zpracovává přetečení zásobníku pro překročení hloubkového kódu.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.ConstrainedExecution>
- [Programování serveru SQL Server a atributy ochrany hostitele](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
