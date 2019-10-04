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
ms.openlocfilehash: 40c1b98f82fe53819edc437bbac575c1df206496
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834541"
---
# <a name="reliability-best-practices"></a>Spolehlivost – doporučené postupy

Následující pravidla spolehlivosti se orientují na SQL Server; vztahují se ale také na všechny serverové aplikace založené na hostiteli. Je velmi důležité, aby servery, jako SQL Server, neunikly prostředky a nemohly být zavedeny.  To však nelze provést zápisem zpětného zápisu kódu pro každou metodu, která mění stav objektu.  Cílem není zapsat 100% spolehlivého spravovaného kódu, který se bude obnovovat ze všech chyb v každém umístění s back-výstupním kódem.  To by byl úkol těžké s nízkou pravděpodobností úspěchu.  Modul CLR (Common Language Runtime) nemůže snadno poskytnout dostatečně velkou záruku pro spravovaný kód, aby bylo možné psát dokonalý kód.  Všimněte si, že na rozdíl od ASP.NET SQL Server používá pouze jeden proces, který nelze recyklovat, aniž by došlo k nepřijatelně dlouhé době databáze.

S těmito slabšími zárukami a provozováním v jednom procesu je spolehlivost založena na ukončení vláken nebo recyklace domén aplikace, pokud je to nutné, a přijímá opatření k zajištění toho, aby prostředky operačního systému, jako jsou například popisovače nebo paměť, nebyly Nevráceny.  I s tímto jednodušším omezením spolehlivosti stále platí významný požadavek na spolehlivost:

- Nikdy neúnik prostředků operačního systému.

- Identifikujte všechny spravované zámky ve všech formulářích pro CLR.

- Nikdy Nerušit sdílený stav domény mezi aplikacemi, což umožňuje plynule fungovat <xref:System.AppDomain> recyklace.

I když je teoreticky možné napsat spravovaný kód pro zpracování výjimek <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException> a <xref:System.OutOfMemoryException>, očekává se, že vývojáři zapisují takový robustní kód do celé aplikace je nedůvodně.  Z tohoto důvodu vyplývají z nedostatku pásma vykonávání zpracovávaného vlákna; a pokud ukončené vlákno upravovalo sdílený stav, které lze určit podle toho, zda vlákno drží zámek, je <xref:System.AppDomain> uvolněn.  Když je metoda, která upravuje sdílený stav, ukončená, stav bude poškozený, protože není možné zapsat spolehlivý back-výstupní kód pro aktualizace do sdíleného stavu.

V .NET Framework verze 2,0 je jediným hostitelem, který vyžaduje spolehlivost, SQL Server.  Pokud bude vaše sestavení spuštěno na SQL Server měli byste provádět spolehlivost v každé části tohoto sestavení, a to i v případě, že existují konkrétní funkce, které jsou při spuštění v databázi zakázané.  To je vyžadováno, protože modul pro analýzu kódu kontroluje kód na úrovni sestavení a nemůže odlišit zakázaný kód. Dalším aspektem SQL Server programování je to, že SQL Server spouští vše v jednom procesu a k vyčištění všech prostředků, jako jsou třeba obslužné rutiny paměti a operačního systému, se používá <xref:System.AppDomain> recyklace.

Nemůžete záviset na finalizační nebo destruktorech ani `try/finally` bloků pro back-výstupní kód. Mohou být přerušeny nebo volány.

Asynchronní výjimky lze vyvolat v neočekávaných umístěních, případně v každé instrukci počítače: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException> a <xref:System.OutOfMemoryException>.

Spravovaná vlákna nejsou nutně vlákny Win32 v SQL; můžou být vlákny.

Proměnlivý sdílený stav domény v úrovni procesu nebo meziaplikace je velmi obtížně pozměňován a je třeba se jim vyhnout, kdykoli je to možné.

Podmínky nedostatku paměti nejsou v SQL Server zřídka.

Pokud knihovny hostované v SQL Server správně neaktualizují svůj sdílený stav, je vysoká pravděpodobnost, že kód nebude obnoven, dokud nebude databáze restartována.  V některých extrémních případech to může způsobit selhání procesu SQL Server, což způsobí, že se databáze restartuje.  Restartování databáze může převzít web nebo ovlivnit operace společnosti, neubližujeme dostupnost.  Pomalé úniky prostředků operačního systému, jako je například paměť nebo popisovače, může způsobit, že server nakonec selže při přidělování obslužných rutin bez možnosti obnovení, nebo může server pomalu snížit výkon a omezit aplikaci zákazníka. dostupnosti.  Jasně chceme, abyste se vyhnuli těmto scénářům.

## <a name="best-practice-rules"></a>Pravidla osvědčených postupů

Úvod se zaměřuje na to, co kontrola kódu pro spravovaný kód, který běží na serveru, by musela zachytit, aby se zvýšila stabilita a spolehlivost rozhraní. Všechny tyto kontroly jsou obecně osvědčené a na serveru musí být absolutní.

V případě nedoručeného zámku nebo omezení prostředku SQL Server přeruší vlákno nebo odhlásí <xref:System.AppDomain>.  Pokud k tomu dojde, je zaručeno spuštění pouze back-výstupních kódů v oblasti s omezením spuštění (CER).

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Použití třídy SafeHandle k zamezení nevracení prostředků

V případě <xref:System.AppDomain> uvolnění nemůžete záviset na tom, že jsou spuštěny bloky nebo finalizační metody `finally`, takže je důležité, aby byl veškerý přístup k prostředkům operačního systému abstraktní přes třídu <xref:System.Runtime.InteropServices.SafeHandle> spíše než <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef> nebo podobné třídy. To umožňuje, aby modul CLR sledoval a zavřel táhla, která používáte, i v případech <xref:System.AppDomain> odtrhnout.  <xref:System.Runtime.InteropServices.SafeHandle> bude používat kritický finalizační metodu, kterou bude modul CLR vždy spuštěn.

Popisovač operačního systému je uložen v bezpečném popisovači od okamžiku, kdy je vytvořen až do chvíle, kdy se uvolnil.  K dispozici není žádné okno, během kterého by @no__t k dispozici k úniku popisovače.  Kromě toho vyvolá vyvolání platformy odkaz – vyhodnotí popisovač, který umožňuje zavřít sledování životnosti popisovače a zabránit potížím se zabezpečením s podmínkou časování mezi `Dispose` a metodou, která aktuálně používá popisovač.

Většina tříd, které v současné době mají finalizační metodu pro jednoduše vyčištění popisovače operačního systému, nebude potřebovat finalizační metodu. Místo toho bude finalizační metoda na odvozené třídě <xref:System.Runtime.InteropServices.SafeHandle>.

Všimněte si, že <xref:System.Runtime.InteropServices.SafeHandle> není náhradou za <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Stále existují potenciální problémy s kolizem prostředků a výkonem, aby bylo možné explicitně uvolnit prostředky operačního systému.  Stačí si uvědomit, že @no__t bloky-0, které by explicitně vyrovnaly prostředky, se nemusí provádět k dokončení.

@no__t – 0 umožňuje implementovat vlastní metodu <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, která provede práci k uvolnění popisovače, jako je například předávání stavu do rutiny pro uvolnění operačního systému nebo uvolnění sady popisovačů ve smyčce.  Modul CLR garantuje, že je tato metoda spuštěna.  Je zodpovědností autora implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, aby se zajistilo, že se tento popisovač uvolní za všech okolností. V takovém případě dojde k nevrácení popisovače, což často vede k úniku nativních prostředků přidružených k popisovači. Proto je důležité se strukturou odvozených tříd <xref:System.Runtime.InteropServices.SafeHandle>, takže implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nevyžaduje přidělení všech prostředků, které nemusí být k dispozici v době vyvolání. Všimněte si, že je dovoleno volat metody, které mohou selhat v rámci implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> za předpokladu, že váš kód může zpracovat taková selhání a dokončit kontrakt k uvolnění nativního popisovače. Pro účely ladění má <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> návratovou hodnotu <xref:System.Boolean>, která může být nastavena na `false`, pokud dojde k závažné chybě, která brání vydání prostředku. Tím se aktivuje [releaseHandleFailed](../debug-trace-profile/releasehandlefailed-mda.md) MDA, pokud je tato možnost povolená, aby bylo možné tento problém identifikovat. Neovlivňuje modul runtime žádným jiným způsobem; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> se pro stejný prostředek znovu nevolá, a v důsledku toho nebude popisovač vrácen.

<xref:System.Runtime.InteropServices.SafeHandle> není v některých kontextech vhodný.  Vzhledem k tomu, že metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> může být spuštěna v finalizační vlákně <xref:System.GC>, nesmí být všechny popisovače, které jsou požadovány pro uvolnění určitého vlákna, zabaleny do <xref:System.Runtime.InteropServices.SafeHandle>.

Běhové obálky pro volání (RCW) lze vyčistit modulem CLR bez dalšího kódu.  Pro kód, který používá vyvolání platformy a který zpracovává objekt modelu COM jako `IUnknown*` nebo <xref:System.IntPtr>, by měl být kód přepsán, aby používal RCW.  <xref:System.Runtime.InteropServices.SafeHandle> nemusí být pro tento scénář vhodné, protože se možnost nespravované verze vyvolala zpět do spravovaného kódu.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

K zapouzdření prostředků operačního systému použijte <xref:System.Runtime.InteropServices.SafeHandle>. Nepoužívejte <xref:System.Runtime.InteropServices.HandleRef> nebo pole typu <xref:System.IntPtr>.

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Zajistěte, aby finalizační metody nemusely běžet, aby se zabránilo úniku prostředků operačního systému

Pečlivě zkontrolujte své finalizační metody a ujistěte se, že i v případě, že nejsou spuštěné, není nevrácen důležitý prostředek operačního systému.  Na rozdíl od normálního @no__t 0, pokud je aplikace spuštěna v stabilním stavu, nebo když se server, jako je SQL Server vypnutý, objekty nejsou finalizován během náhlého <xref:System.AppDomain> uvolnění.  Zajistěte, aby v případě náhlého uvolnění prostředků nedošlo k úniku prostředků, protože není zaručená správnost aplikace, ale integrita serveru musí být udržována nevracením prostředků.  K uvolnění jakýchkoli prostředků operačního systému použijte <xref:System.Runtime.InteropServices.SafeHandle>.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Zajistěte, aby klauzule finally nemusely běžet, aby se zabránilo úniku prostředků operačního systému

klauzule `finally` není zaručena spouštění mimo CERs, což vyžaduje, aby vývojáři knihovny nemuseli spoléhat na kód v rámci bloku `finally` k uvolnění nespravovaných prostředků.  Použití <xref:System.Runtime.InteropServices.SafeHandle> je doporučené řešení.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Místo `Finalize` použijte <xref:System.Runtime.InteropServices.SafeHandle> pro čištění prostředků operačního systému. Nepoužívat <xref:System.IntPtr>; k zapouzdření prostředků použijte <xref:System.Runtime.InteropServices.SafeHandle>. Pokud je nutné použít klauzuli finally, umístěte ji do CER.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Všechny zámky by měly projít existujícím spravovaným kódem pro uzamykání

Modul CLR musí znát, pokud je kód v zámku, takže bude znát <xref:System.AppDomain> namísto pouhého přerušení vlákna.  Přerušení vlákna může být nebezpečné, protože data provozovaná vláknem by mohla být ponechána v nekonzistentním stavu. Proto je nutné provést recyklaci celého <xref:System.AppDomain>.  Důsledky selhání identifikace zámku můžou být buď zablokované, nebo nesprávné výsledky. Použijte metody <xref:System.Threading.Thread.BeginCriticalRegion%2A> a <xref:System.Threading.Thread.EndCriticalRegion%2A> k identifikaci oblastí zámku.  Jsou to statické metody pro třídu <xref:System.Threading.Thread>, která se vztahuje pouze na aktuální vlákno, což pomáhá zabránit jednomu vláknu v úpravě počtu zámků jiného vlákna.

<xref:System.Threading.Monitor.Enter%2A> a <xref:System.Threading.Monitor.Exit%2A> mají tato oznámení CLR vestavěná, takže jejich použití se doporučuje a také použití [příkazu Lock](../../csharp/language-reference/keywords/lock-statement.md), který tyto metody používá.

Jiné mechanismy uzamykání, jako jsou například zámky a <xref:System.Threading.AutoResetEvent>, musí volat tyto metody pro informování CLR o zadání kritického oddílu.  Tyto metody nevyužívají žádné zámky. informují CLR, že kód je spuštěn v kritickém oddílu a přerušení vlákna může opustit sdílený stav nekonzistentní.  Pokud jste definovali vlastní typ zámku, například vlastní třídu <xref:System.Threading.ReaderWriterLock>, použijte tyto metody čítače uzamčení.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Označte a identifikujte všechny zámky pomocí <xref:System.Threading.Thread.BeginCriticalRegion%2A> a <xref:System.Threading.Thread.EndCriticalRegion%2A>. Ve smyčce nepoužívejte <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A> a <xref:System.Threading.Interlocked.Decrement%2A>.  Neprovádějte vyvolání platformy z variant těchto metod Win32.  Ve smyčce nepoužívejte <xref:System.Threading.Thread.Sleep%2A>.  Nepoužívejte nestálá pole.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Kód pro vyčištění musí být v bloku finally nebo catch, který není po catch.

Kód pro vyčištění by nikdy neměl následovat @no__t blok-0; měl by být v `finally` nebo v samotném bloku `catch`. To by mělo být normální dobrý postup. Blok `finally` je obecně upřednostňovaný, protože spouští stejný kód v případě, že je vyvolána výjimka a při normálním výskytu bloku `try`.  V případě vyvolání neočekávané výjimky, například <xref:System.Threading.ThreadAbortException>, nebude kód pro vyčištění spuštěn.  Všechny nespravované prostředky, které byste vyčistili v `finally`, by měly být v ideálním případě zabaleny do <xref:System.Runtime.InteropServices.SafeHandle>, aby se předešlo nevracení.  Poznámka: C# klíčové slovo `using` lze efektivně použít k Dispose objektů, včetně obslužných rutin.

I když <xref:System.AppDomain> recyklování může vyčistit prostředky ve vlákně finalizační metody, je stále důležité umístit kód vyčištění na správné místo. Všimněte si, že pokud vlákno obdrží asynchronní výjimku bez držení zámku, modul CLR se pokusí ukončit samotný podproces bez nutnosti recyklovat <xref:System.AppDomain>.  Zajistěte, aby se prostředky vyčistily dříve než později, a to díky tomu, že bude k dispozici více prostředků a lepší správa životního cyklu. Pokud explicitně neuzavřete popisovač do souboru v nějaké cestě kódu chyby, počkejte, až @no__t finalizační rutina vyčistí. při dalším spuštění kódu se může pokusit o přístup k přesnému stejnému souboru, pokud se ještě nespustí finalizační metoda.  Z tohoto důvodu je potřeba zajistit, aby kód pro čištění existoval a správně fungoval, a to i v případě, že není nezbytně nutné.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Kód pro vyčištění po `catch` musí být v bloku `finally`. Umístit volání k Dispose v bloku finally. bloky `catch` by měly končit throwem nebo znovu vyvoláním. I když dojde k výjimkám, jako je například zjištění kódu, zda je možné vytvořit síťové připojení, kde se může zobrazit nějaký velký počet výjimek, jakýkoli kód, který vyžaduje zachycení určitého počtu výjimek za normálních okolností, by měl poskytnout označení, že by měl být testován kód, aby bylo možné zjistit, zda bude úspěšný.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Proměnlivý sdílený stav na úrovni procesu mezi doménami aplikace by se měl vyloučit nebo použít oblast omezeného provádění.

Jak je popsáno v úvodu, může být velmi obtížné napsat spravovaný kód, který monitoruje sdílený stav napříč doménami aplikace spolehlivým způsobem.  Sdílený stav v rámci procesu je jakýkoli druh dat, který je sdílen mezi doménami aplikace, buď v kódu Win32, uvnitř CLR, nebo ve spravovaném kódu pomocí vzdálené komunikace.  Libovolný proměnlivý sdílený stav je velmi obtížné správně psát ve spravovaném kódu a jakýkoliv statický sdílený stav může být proveden pouze s velkou péčí.  Pokud máte sdílený stav na úrovni procesu nebo počítače, najděte nějaký způsob, jak ho odstranit, nebo chránit sdílený stav pomocí omezené oblasti provádění (CER).  Všimněte si, že jakákoliv knihovna se sdíleným stavem, který není identifikovaný a opravená, by mohla způsobit, že hostitel, jako je například SQL Server, potřebuje k chybě vyčištění <xref:System.AppDomain>.

Pokud kód používá objekt modelu COM, vyhněte se sdílení tohoto objektu COM mezi doménami aplikace.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Zámky nefungují v rámci aplikačních domén nebo mezi nimi.

V minulosti byl pro vytvoření globálních zámků procesů použit <xref:System.Threading.Monitor.Enter%2A> a [příkaz Lock](../../csharp/language-reference/keywords/lock-statement.md) .  K tomu dochází například při uzamykání na agilních třídách <xref:System.AppDomain>, jako jsou například instance <xref:System.Type> z nesdílených sestavení, objekty <xref:System.Threading.Thread>, internované řetězce a některé řetězce sdílené napříč doménami aplikace pomocí vzdálené komunikace.  Tyto zámky již nejsou v procesu nadále platné.  Chcete-li zjistit přítomnost zámku meziaplikační domény v rámci procesu, určete, zda kód v zámku používá jakýkoliv externí, trvalý prostředek, jako je například soubor na disku nebo případně databáze.

Počítejte s tím, že při použití zámku v rámci <xref:System.AppDomain> může dojít k problémům, pokud chráněný kód používá externí prostředek, protože tento kód může běžet současně napříč více aplikačními doménami.  Může se jednat o problém při zápisu do jednoho souboru protokolu nebo k vytvoření vazby na soket pro celý proces.  Tato změna znamená, že neexistuje jednoduchý způsob použití spravovaného kódu pro získání globálního zámku procesu, který je jiný než použití pojmenované instance <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore>.  Vytvořte kód, který neběží současně se dvěma aplikačními doménami, nebo použijte třídy <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore>.  Pokud existující kód nelze změnit, k dosažení této synchronizace nepoužívejte Win32 pojmenovaný mutex, protože je spuštěn v režimu Fiber-in znamená, že nemůžete zaručit, že stejné vlákno operačního systému získá a uvolní mutex.  Je nutné použít spravovanou třídu <xref:System.Threading.Mutex>, nebo pojmenovanou <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> nebo <xref:System.Threading.Semaphore> pro synchronizaci zámku kódu způsobem, který je o tom, že CLR ví, namísto synchronizace zámku pomocí nespravovaného kódu.

#### <a name="avoid-locktypeofmytype"></a>Nepoužívat zámek (typeof (MyType))

Soukromé a veřejné objekty <xref:System.Type> ve sdílených sestaveních s pouze jednou kopií kódu sdílené napříč všemi doménami aplikace také představují problémy.  U sdílených sestavení existuje pouze jedna instance <xref:System.Type> na proces, což znamená, že více domén aplikací sdílí stejnou instanci <xref:System.Type>.  Když zámek na instanci <xref:System.Type> převezme zámek, který má vliv na celý proces, nikoli jenom na <xref:System.AppDomain>.  Pokud jeden <xref:System.AppDomain> převezme zámek na objektu <xref:System.Type>, bude vlákno přerušeno, ale zámek neuvolní.  Tento zámek pak může způsobit zablokování jiných aplikačních domén.

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

Pak při pořizování zámku použijte vlastnost `InternalSyncObject` k získání objektu, který se má zamknout.  Tuto vlastnost nemusíte používat, pokud jste v konstruktoru třídy provedli inicializaci objektu interní synchronizace.  Inicializační kód zámku pro dvojité zaškrtnutí by měl vypadat jako v tomto příkladu:

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

Obecně je přijatelné přijmout zámek na individuálním objektu, který je veřejně přístupný.  Pokud je však objekt objekt typu Singleton, který by mohl způsobit zablokování celého subsystému, zvažte použití výše uvedeného vzoru návrhu také.  Například zámek na jednom objektu <xref:System.Security.SecurityManager> může způsobit zablokování v rámci <xref:System.AppDomain>, které provádí celý <xref:System.AppDomain> nepoužitelné. Není vhodné pořizovat zámek u veřejně přístupného objektu tohoto typu.  Zámek u jednotlivých kolekcí nebo polí by však neměl obvykle představovat problém.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Neprovádějte zámky u typů, které by mohly být použity napříč doménami aplikace, nebo nemají silný smysl identity. Nevolejte <xref:System.Threading.Monitor.Enter%2A> na <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread> nebo jakýkoli objekt, který je odvozený z <xref:System.MarshalByRefObject>.

### <a name="remove-gckeepalive-calls"></a>Odeberte GC. Volání kontroly udržení naživu

Významné množství stávajícího kódu buď nepoužívá <xref:System.GC.KeepAlive%2A>, pokud by ho mělo nebo používá, pokud není vhodné.  Po převedení na @no__t 0 třídy nemusí volat <xref:System.GC.KeepAlive%2A> za předpokladu, že nemají finalizační metodu, ale spoléhat na <xref:System.Runtime.InteropServices.SafeHandle> k finalizaci popisovačů operačního systému.  I když náklady na výkon při zachování volání <xref:System.GC.KeepAlive%2A> mohou být zanedbatelné, vnímání, že volání <xref:System.GC.KeepAlive%2A> je buď nezbytné, nebo postačuje k vyřešení potíží s životností, která již možná neexistuje, způsobuje, že se kód obtížně udržuje.  Pokud však použijete obálky volání CLR Interop CLR (RCW), <xref:System.GC.KeepAlive%2A> stále požaduje kód.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Odeberte <xref:System.GC.KeepAlive%2A>.

### <a name="use-the-hostprotection-attribute"></a>Použití atributu HostProtection

@No__t-0 (HPA) poskytuje použití deklarativních akcí zabezpečení k určení požadavků na ochranu hostitele, takže hostitel může zabránit tomu, aby si i plně důvěryhodný kód vyvolal určité metody, které jsou pro daného hostitele nevhodné, jako je například <xref:System.Environment.Exit%2A> nebo @no__ t-2 pro SQL Server.

HPA ovlivňuje pouze nespravované aplikace, které hostují modul CLR (Common Language Runtime) a implementují ochranu hostitele, například SQL Server. Při použití akce zabezpečení má za následek vytvoření požadavku propojení na základě prostředků hostitele, které třída nebo metoda zveřejňuje. Pokud je kód spuštěn v klientské aplikaci nebo na serveru, který není chráněn hostitelem, atribut "vypařování"; nedetekuje se, a proto se nepoužije.

> [!IMPORTANT]
> Účelem tohoto atributu je vynutilit pokyny pro programovací model specifický pro hostitele, nikoli chování zabezpečení.  Přestože požadavek propojení slouží ke kontrole shody s požadavky na programovací model, <xref:System.Security.Permissions.HostProtectionAttribute> není oprávnění zabezpečení.

Pokud hostitel nemá požadavky na programovací model, nejsou k dispozici žádné požadavky propojení.

Tento atribut identifikuje následující:

- Metody nebo třídy, které se nevejdou do programovacího modelu hostitele, ale jsou jinak neškodné.

- Metody nebo třídy, které se nevejdou do programovacího modelu hostitele a můžou vést k destabilizující uživatelského kódu spravovaného serverem.

- Metody nebo třídy, které se nevejdou do programovacího modelu hostitele a mohou vést k destabilizaci samotného procesu serveru.

> [!NOTE]
> Pokud vytváříte knihovnu tříd, která má být volána aplikacemi, které mohou být spuštěny v hostitelském prostředí, měli byste tento atribut použít pro členy, které zveřejňují kategorie prostředků <xref:System.Security.Permissions.HostProtectionResource>. .NET Framework členové knihovny tříd s tímto atributem způsobí, že bude zaškrtnuto pouze bezprostředního volajícího.  Váš člen knihovny musí také způsobit kontrolu svého bezprostředního volajícího stejným způsobem.

Další informace o HPA naleznete v <xref:System.Security.Permissions.HostProtectionAttribute>.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Pro SQL Server se všechny metody použité k zavedení synchronizace nebo dělení na vlákna musí identifikovat pomocí HPA. Patří sem metody, které sdílejí stav, jsou synchronizovány nebo spravují externí procesy. Hodnoty <xref:System.Security.Permissions.HostProtectionResource>, které ovlivňují SQL Server jsou <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization> a <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Jakákoliv metoda, která zveřejňuje libovolné <xref:System.Security.Permissions.HostProtectionResource>, by však měla být identifikována HPA, nikoli pouze pomocí prostředků ovlivňujících SQL.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Neblokovat po neomezenou dobu v nespravovaném kódu

Blokování v nespravovaném kódu namísto ve spravovaném kódu může způsobit útok na dostupnost služby, protože modul CLR nemůže přerušit vlákno.  Blokované vlákno zabraňuje CLR v uvolňování <xref:System.AppDomain>, přinejmenším bez provedení některých extrémně nebezpečných operací.  Blokování použití primitiva synchronizace systému Windows je jasným příkladem něčeho, co nemůžeme dovolit.  Blokování volání `ReadFile` na soketu by se mělo vyhnout, pokud je to možné – v ideálním případě by rozhraní Windows API mělo poskytovat mechanismus pro operaci, jako je například vyprší časový limit.

Jakákoli metoda, která volá do nativního, by ideálním způsobem používala volání Win32 s přiměřeným, konečným časovým limitem.  Pokud má uživatel povolený časový limit, neměl by mít uživatel povoleno zadat neomezený časový limit bez určitého konkrétního oprávnění zabezpečení.  V případě, že je metoda zablokovaná na více než ~ 10 sekund, je třeba použít verzi, která podporuje vypršení časových limitů, nebo potřebujete další podporu CLR.

Tady je několik příkladů problematických rozhraní API.  Kanály (anonymní i pojmenované) se dají vytvořit s časovým limitem. kód však musí zajistit, aby nikdy nevolal `CreateNamedPipe` ani `WaitNamedPipe` s NMPWAIT_WAIT_FOREVER.  Kromě toho může být neočekávané blokování i v případě, že je zadán časový limit.  Volání `WriteFile` na anonymním kanálu bude blokovat až do zápisu všech bajtů. to znamená, že pokud má vyrovnávací paměť nepřečtená data, bude zablokované volání `WriteFile`, dokud čtecí modul neuvolní místo ve vyrovnávací paměti kanálu.  Sokety by měly vždycky používat rozhraní API, které respektují mechanismus časového limitu.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Blokování bez časového limitu v nespravovaném kódu je útok s cílem odepření služby. Neprovádějte volání vyvolání platformy `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects` a `MsgWaitForMultipleObjectsEx`.  Nepoužívejte NMPWAIT_WAIT_FOREVER.

### <a name="identify-any-sta-dependent-features"></a>Identifikujte všechny funkce závislé na STA

Identifikujte jakýkoli kód, který používá objekty Apartment s jedním vláknem modelu COM (STAs).  STAs jsou v procesu SQL Server zakázané.  Funkce, které závisí na `CoInitialize`, například čítače výkonu nebo schránka, musí být v rámci SQL Server zakázané.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Zajistěte, aby finalizační metody byly bez problémů s synchronizací.

V budoucích verzích .NET Framework může existovat více vláken finalizační metody, což znamená, že finalizační metody pro různé instance stejného typu běží současně.  Nemusí být zcela bezpečné pro přístup z více vláken; systém uvolňování paměti zaručuje, že pouze jedno vlákno spustí finalizační metodu pro danou instanci objektu.  Nicméně finalizační metody musí být kódované, aby nedocházelo ke konfliktům časování a zablokování při současném spuštění na více různých instancích objektů.  Při použití libovolného externího stavu, jako je například zápis do souboru protokolu, musí být v finalizační metodě zpracovávány problémy s vlákny.  Nespoléhá na finalizaci, aby se zajistila bezpečnost vlákna. Nepoužívejte thread local úložiště, spravované nebo nativní, k uložení stavu ve vlákně finalizační metody.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Finalizační metody musí být bez problémů s synchronizací. Nepoužívejte statický proměnlivý stav v finalizační metodě.

### <a name="avoid-unmanaged-memory-if-possible"></a>Pokud je to možné, vyhněte se nespravované paměti

Nespravovanou paměť lze zneniknout, stejně jako popisovač operačního systému. Pokud je to možné, zkuste použít paměť v zásobníku pomocí [stackalloc](../../csharp/language-reference/operators/stackalloc.md) nebo připnutého spravovaného objektu, jako je například [příkaz fixed](../../csharp/language-reference/keywords/fixed-statement.md) nebo <xref:System.Runtime.InteropServices.GCHandle> s použitím bajtu []. @No__t-0 je nakonec vyčistí. Pokud však musíte přidělit nespravovanou paměť, zvažte použití třídy, která je odvozena z <xref:System.Runtime.InteropServices.SafeHandle> pro zabalení přidělení paměti.

Všimněte si, že existuje alespoň jeden případ, kde <xref:System.Runtime.InteropServices.SafeHandle> není adekvátní. Pro volání metod COM, která přidělují nebo uvolňují paměť, je běžné, že jedna knihovna DLL přiděluje paměť prostřednictvím `CoTaskMemAlloc`, potom další knihovna DLL uvolní tuto paměť s `CoTaskMemFree`.  Použití <xref:System.Runtime.InteropServices.SafeHandle> na těchto místech by nebylo vhodné, protože se pokusí spojit životní cyklus nespravované paměti s životností <xref:System.Runtime.InteropServices.SafeHandle> místo toho, aby jiná knihovna DLL mohla řídit dobu života paměti.

### <a name="review-all-uses-of-catchexception"></a>Zkontrolovat všechna použití catch (výjimka)

Bloky catch, které zachycují všechny výjimky místo jedné konkrétní výjimky, teď budou zachytit i asynchronní výjimky. Prověřte každý blok catch (Exception), vyhledá žádné důležité uvolnění prostředků nebo kód back-výstup, který může být vynechán, a potenciálně nesprávné chování v rámci bloku catch pro zpracování <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException> nebo <xref:System.OutOfMemoryException>.  Všimněte si, že je možné, že tento kód může zaprotokolovat nebo vytvořit některé předpoklady, které mohou zobrazit pouze určité výjimky nebo které pokaždé, když dojde k výjimce, se nezdařila z přesně jednoho konkrétního důvodu.  Tyto předpoklady je potřeba aktualizovat, aby zahrnovaly <xref:System.Threading.ThreadAbortException>.

Zvažte změnu všech míst, která zachycují všechny výjimky pro zachycení konkrétního typu výjimky, kterou očekáváte, například <xref:System.FormatException> z metod formátování řetězce.  To zabrání spuštění bloku catch v neočekávaných výjimkách a pomůže zajistit, že kód nebude skrývat chyby tím, že se zachytí neočekávané výjimky.  Jako obecné pravidlo nikdy nezpracovává výjimku v kódu knihovny (kód, který vyžaduje, abyste zachytili výjimku, může znamenat chybu návrhu v kódu, který voláte).  V některých případech můžete chtít zachytit výjimku a vyvolat jiný typ výjimky, aby bylo možné poskytnout více dat.  V tomto případě použijte vnořené výjimky, čímž uložíte skutečnou příčinu selhání ve vlastnosti <xref:System.Exception.InnerException%2A> nové výjimky.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Zkontrolujte všechny bloky catch ve spravovaném kódu, které zachycují všechny objekty nebo zachytí všechny výjimky.  V C#systému to znamená označení `catch` {} a `catch(Exception)` {}.  Zvažte, zda je typ výjimky velmi specifický, nebo zkontrolujte kód, abyste se ujistili, že se nejedná o špatný způsob, pokud zachytává neočekávaný typ výjimky.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Nepředpokládat spravované vlákno je vlákno Win32 – jedná se o vlákno.

Použití spravovaného úložiště thread local funguje, ale nepoužíváte nespravované úložiště thread local nebo předpokládáte, že se kód v aktuálním vláknu operačního systému spustí znovu. Neměňte nastavení, jako je národní prostředí vlákna. Nevolejte `InitializeCriticalSection` nebo `CreateMutex` prostřednictvím volání platformy, protože vyžadují vlákno operačního systému, které zadává zámek, také ukončí zámek. Vzhledem k tomu, že se nejedná o případ použití vláken, důležité oddíly Win32 a mutex nelze použít přímo v SQL.  Počítejte s tím, že spravovaná třída <xref:System.Threading.Mutex> nezpracovává obavy týkající se spřažení vláken.

Většinu stavu můžete bezpečně použít na spravovaném objektu @no__t 0, včetně spravovaného úložiště thread local a aktuální jazykové verze uživatelského rozhraní vlákna. Můžete také použít <xref:System.ThreadStaticAttribute>, což umožňuje, aby byla hodnota existující statické proměnné přístupná pouze aktuálním spravovaným vláknem (Jedná se o další způsob, jak v modulu CLR provádět vlákna v místním úložišti). Pro účely programovacího modelu nemůžete změnit aktuální jazykovou verzi vlákna při spuštění v SQL.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

SQL Server běží v režimu Fiber; Nepoužívejte thread local Storage. Nevolejte volání platformy `TlsAlloc`, `TlsFree`, `TlsGetValue` a `TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>Povolit SQL Server manipulaci s zosobněním

Vzhledem k tomu, že zosobnění funguje na úrovni vlákna a SQL může běžet v vláknovém režimu, spravovaný kód by neměl zosobnit uživatele a nesmí volat `RevertToSelf`.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Umožněte SQL Server pořizování zosobnění. Nepoužívejte `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx` nebo 0.

### <a name="do-not-call-threadsuspend"></a>Nevolat vlákno:: Suspend

Schopnost pozastavit vlákno se může zobrazit jako jednoduchá operace, ale může způsobit zablokování.  Pokud vlákno drží zámek pozastaveno druhým vláknem a potom se druhé vlákno pokusí přebírat stejný zámek, dojde k zablokování.  <xref:System.Threading.Thread.Suspend%2A> může v současné době ovlivňovat zabezpečení, načítání tříd, vzdálenou komunikaci a reflexi.

#### <a name="code-analysis-rule"></a>Pravidlo analýzy kódu

Nevolejte <xref:System.Threading.Thread.Suspend%2A>. Místo toho zvažte použití reálného primitiva synchronizace, například <xref:System.Threading.Semaphore> nebo <xref:System.Threading.ManualResetEvent>.

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Chraňte kritické operace s omezenými oblastmi provádění a smlouvami o spolehlivosti.

Při provádění složitých operací, které aktualizují sdílený stav nebo které musí být deterministické buď zcela úspěšné nebo zcela neúspěšné, se ujistěte, že je chráněna pomocí omezené oblasti provádění (CER). To zaručuje, že kód se spustí v každém případě, dokonce i náhlé přerušení vlákna nebo náhlé <xref:System.AppDomain> uvolnění.

CER je konkrétní blok `try/finally` bezprostředně před voláním <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.

Tím se dá instruovat kompilátor za běhu, aby před spuštěním bloku `try` připravil veškerý kód v bloku finally. To zaručuje, že kód v bloku finally je sestaven a bude spuštěn ve všech případech. Není neobvyklé, že v CER může být prázdný blok `try`. Použití CER chrání proti přerušení asynchronního vlákna a výjimky z důvodu nedostatku paměti. V tématu <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> můžete vytvořit formulář CER, který navíc zpracovává přetečení zásobníku pro přesahující hlubokou hloubkový kód.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.ConstrainedExecution>
- [Programování serveru SQL Server a atributy ochrany hostitele](sql-server-programming-and-host-protection-attributes.md)
