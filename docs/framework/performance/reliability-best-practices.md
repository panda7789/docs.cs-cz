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
ms.openlocfilehash: 280e73ccd3d8a90b2f2b3a485d3f4240b434359b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714851"
---
# <a name="reliability-best-practices"></a>Spolehlivost – doporučené postupy
Následující pravidla spolehlivosti jsou orientované na SQL serveru. Nicméně jsou také použity jakékoli aplikace založené na hostiteli serveru. Je velmi důležité, aby servery, jako je SQL Server není způsobit únik těchto prostředků a nebudou snížila.  Který však nelze provést napsáním zálohující kód pro každou metodu, která mění stav objektu.  Cílem je nikoli k zápisu na 100 % spolehlivý spravovaný kód, který bude obnoven. všechny chyby v jakémkoliv místě s zálohující kód.  Bylo by složitý úkol s malou pravděpodobnost úspěchu.  Modul CLR (CLR) nemůže poskytnout snadno dostatečně silné záruky pro spravovaný kód k psaní udělá v kódu proveditelné.  Všimněte si, že na rozdíl od technologie ASP.NET, používá systém SQL Server pouze jednoho procesu, kterou nelze recyklovat, a to bez nutnosti přepínat databázi nepřijatelně dlouhou dobu.  
  
 Tyto slabší záruky a spuštěné v jednom procesu spolehlivost podle ukončení vláken nebo recyklaci aplikační domény, pokud nedošlo k úniku nezbytné a přijímá opatření k zajištění prostředky operačního systému, jako je například obslužné rutiny nebo paměti.  Dokonce i s tímto omezením jednodušší spolehlivost stále existuje výrazné spolehlivost požadavek:  
  
-   Nikdy způsobit únik těchto prostředků operačního systému.  
  
-   Identifikujte všechny spravované uzamčení v všechny formuláře modulu CLR.  
  
-   Nikdy přerušení domény mezi aplikacemi – sdílené stavu, což <xref:System.AppDomain> recyklace fungovat bez problémů.  
  
 I když je teoreticky může, psaní spravovaného kódu pro zpracování <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, a <xref:System.OutOfMemoryException> výjimky, očekává se vývojářům umožňuje psát takového robustního kódu v rámci celé aplikace je odpor.  Z tohoto důvodu out-of-band výjimky za následek spuštěné vlákno ukončí; a pokud ukončení vlákna byl úpravy sdílený stav, které se dají určit pomocí Určuje, zda vlákno drží zámek, pak bude <xref:System.AppDomain> je uvolněna.  Při ukončení metodu, která upravuje sdílený stav, stav bude poškozený, protože není možné k zápisu do sdíleného stavu reliable zálohující kód pro aktualizace.  
  
 V rozhraní .NET Framework verze 2.0 je jediným hostitelem, která vyžaduje spolehlivost systému SQL Server.  Pokud vaše sestavení se spustí na SQL serveru byste měli dělat spolehlivost práce pro každý jsou součástí sestavení, i v případě, že existují určité funkce, které jsou zakázané při provozování v databázi.  Se totiž v modulu analýzy kódu zkontroluje kód na úrovni sestavení a nelze rozlišit zakázané kódu. Jiné programovací aspektem je, že SQL Server všechno, co běží v jednom procesu systému SQL Server a <xref:System.AppDomain> recyklace se používá pro všechny prostředky, jako je například paměť a operační systém zpracovává čištění.  
  
 Nemůže záviset na finalizační metody a destruktory nebo `try/finally` bloků zálohující kód. Může být přerušeno nebo se nevolala.  
  
 Mohou být vyvolány asynchronní výjimky v neočekávaných umístěních, může být každý počítač instrukce: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, a <xref:System.OutOfMemoryException>.  
  
 Spravovaná vlákna, nemusí nutně být Win32 vlákna v SQL, mohou být vlákna.  
  
 Proměnlivé sdílený stav celého procesu nebo meziaplikační doménu je velmi obtížné alter bezpečně a mělo by se vyhnout, kdykoli je to možné.  
  
 Limit paměti nejsou výjimečných v systému SQL Server.  
  
 Pokud knihovny hostované v systému SQL Server správně neaktualizuje jejich sdílený stav, je vysoká pravděpodobnost, že kód neobnoví až po restartování databáze.  Kromě toho někdy extreme je možné, že tato akce může způsobit selhání, procesu systému SQL Server způsobuje, že databáze k restartování.  Restartování databáze můžete vypnout webový server nebo by ovlivnily provoz společnosti, nespokojené dostupnosti.  Pomalé nevrácení prostředků operačního systému, jako jsou paměti nebo popisovače může způsobit, že server nakonec selhání přidělení popisovače se žádná možnost obnovení nebo potenciálně serveru pomalu může snížit výkon a snižuje na základě aplikace dostupnost.  Chceme, aby jasně, aby tyto scénáře.  
  
## <a name="best-practice-rules"></a>Pravidel osvědčených postupů  
 Zavedení, zaměřuje na co revize kódu pro spravovaný kód, který běží na serveru museli byste zachytit pro zvýšení stability a spolehlivosti rozhraní Framework. Všechny tyto kontroly jsou obecně vhodné a absolutní musí na serveru.  
  
 I v případě dead uzamčení nebo prostředek omezení systému SQL Server bude přerušit vlákno nebo dovolí <xref:System.AppDomain>.  Pokud k tomu dojde pouze zálohující kód v oblasti omezeného provádění (CER) je zaručen běh.  
  
### <a name="use-safehandle-to-avoid-resource-leaks"></a>Použijte SafeHandle pro zabránit nedostatku prostředků  
 V případě třídy <xref:System.AppDomain> uvolnění, nemohou záviset na `finally` bloků nebo finalizační metody prováděný, takže je důležité abstraktní veškerý přístup prostředek operačního systému přes <xref:System.Runtime.InteropServices.SafeHandle> třídy spíše než <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>, nebo Podobně jako třídy. To umožňuje sledovat a uzavření popisovače použijete i v modulu CLR <xref:System.AppDomain> vše případ.  <xref:System.Runtime.InteropServices.SafeHandle> budete používat kritickou finalizační metodu, která modul CLR bude vždy spuštěn.  
  
 Popisovač operačního systému se ukládají do bezpečného popisovače od okamžiku, kdy se vytvoří až do okamžiku, kdy se uvolní.  Neexistuje žádný časový interval naruší <xref:System.Threading.ThreadAbortException> může dojít k úniku popisovač.  Kromě toho vyvolání platformy se-počet odkazů popisovač, který umožňuje zavřít sledování životnosti popisovač, brání potíže se zabezpečením pomocí časování mezi `Dispose` a metodu, která se právě používá popisovač.  
  
 Většina tříd, které v tuto chvíli nemáte finalizační metody, jednoduše vyčistit operační systém zpracovávat už nebudete potřebovat finalizační metodu. Místo toho finalizační metodu bude <xref:System.Runtime.InteropServices.SafeHandle> odvozené třídy.  
  
 Všimněte si, že <xref:System.Runtime.InteropServices.SafeHandle> není náhradou za <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Existují stále potenciální prostředku kolize a výkonu výhody explicitně uvolnit prostředky operačního systému.  Pamatujte, že právě `finally` bloky, které explicitně uvolnění prostředků nemusí provést do dokončení.  
  
 <xref:System.Runtime.InteropServices.SafeHandle> umožňuje implementovat vlastní <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodu, která provádí uvolnit popisovač, jako je například stav předávání na popisovač operačního systému uvolnění rutiny nebo uvolnění sady obslužné rutiny ve smyčce.  Modul CLR zaručuje, že tato metoda je spustit.  Zodpovídá za autora <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementace Ujistěte se, že popisovač vydání za všech okolností. Pokud tak neučiníte způsobí, že popisovač uniknout, což často vede k úniku nativní prostředky spojené s popisovačem. Proto je důležité pro strukturu <xref:System.Runtime.InteropServices.SafeHandle> odvozené třídy tak, aby <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementace nevyžaduje přidělení všechny prostředky, které nemusí být k dispozici v době vyvolání. Všimněte si, že se dosáhlo volání metody, které může dojít k selhání v rámci implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> za předpokladu, že váš kód může zpracovávat takové chyby a dokončete smlouvy k uvolnění nativní popisovač. Pro účely ladění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> má <xref:System.Boolean> návratovou hodnotu, která může být nastavená na `false` Pokud katastrofální chyba dochází, která znemožňuje uvolnění prostředku. Tím se budou aktivovat [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) MDA, pokud je povoleno, které vám pomůže odhalit příčinu problému. Nemá vliv na modul runtime žádným jiným způsobem; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nebude volána znovu pro stejný prostředek a v důsledku toho budou nevrácení popisovače.  
  
 <xref:System.Runtime.InteropServices.SafeHandle> není vhodné v některých kontextech.  Protože <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodu je možné spustit v <xref:System.GC> vlákna finalizační metody, všechny obslužné rutiny, které jsou vyžadovány k uvolnění na konkrétní vlákno by neměl být uzavřen do <xref:System.Runtime.InteropServices.SafeHandle>.  
  
 Pomocí modulu CLR bez dalšího kódu je možné vymazat obálek volatelných za běhu (RCW).  Pro kód, který používá platformu vyvolání a považuje za objekt modelu COM `IUnknown*` nebo <xref:System.IntPtr>, kód by měl být přepsán použití obálky RCW.  <xref:System.Runtime.InteropServices.SafeHandle> nemusí být vhodný pro tento scénář z důvodu možnost nespravovaná verze metody zpětné volání do spravovaného kódu.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Použití <xref:System.Runtime.InteropServices.SafeHandle> k zapouzdření prostředky operačního systému. Nepoužívejte <xref:System.Runtime.InteropServices.HandleRef> nebo pole typu <xref:System.IntPtr>.  
  
### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Ujistěte se, že finalizační metody není nutné spustit, aby se zabránilo nevrácení prostředků operačního systému  
 Zkontrolujte vaše finalizační metody pečlivě zajistit, že i v případě, že nemají systém, není nevrácení prostředků kritické operačního systému.  Na rozdíl od normální <xref:System.AppDomain> uvolnění z paměti aplikace spouští v stabilním stavem nebo serveru, jako je SQL Server se vypne a objekty nejsou dokončeny během náhlému <xref:System.AppDomain> uvolnit.  Ujistěte se, že prostředky nedošlo k úniku v případě náhlé uvolnit, protože aplikace správnosti nemůže být zaručena, ale musí být zachová integrita serveru podle není nevrácení prostředků.  Použití <xref:System.Runtime.InteropServices.SafeHandle> uvolnit všechny prostředky operačního systému.  
  
### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Ujistěte se, který nakonec klauzule není nutné spustit zabránilo nevrácení prostředků operačního systému  
 `finally` klauzule se zaručeně spustí mimo CERs, vyžadování vývojářům knihovny nespoléhala se na kód v rámci `finally` bloku pro uvolnění nespravovaných prostředků.  Pomocí <xref:System.Runtime.InteropServices.SafeHandle> je doporučené řešení.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Použití <xref:System.Runtime.InteropServices.SafeHandle> pro vyčištění prostředků operačního systému místo `Finalize`. Nepoužívejte <xref:System.IntPtr>; použijte <xref:System.Runtime.InteropServices.SafeHandle> pro zapouzdření prostředků. Pokud nakonec klauzule musí spustit, umístěte CER.  
  
### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Všech zámků by měl projít existující spravované uzamčení kód  
 Modul CLR, musíte vědět, pokud kód je v zámek, bude věděli, že dovolí <xref:System.AppDomain> namísto pouze přerušení vlákna.  Přerušuje se vlákno může být nebezpečný, jak data provozovaná vlákno by mohla zůstat v nekonzistentním stavu. Proto se celý <xref:System.AppDomain> má provedení recyklace.  Následky selhání k identifikaci zámku může být zablokování nebo nesprávné výsledky. Použijte metody <xref:System.Threading.Thread.BeginCriticalRegion%2A> a <xref:System.Threading.Thread.EndCriticalRegion%2A> k identifikaci oblastí zámku.  Jsou statické metody <xref:System.Threading.Thread> třídu, která se vztahují jenom na aktuální vlákno, a usnadnit tak bránit jedno vlákno v úpravách počet zámků jiné vlákno.  
  
 <xref:System.Threading.Monitor.Enter%2A> a <xref:System.Threading.Monitor.Exit%2A> mít toto oznámení CLR integrovanou, proto se doporučuje jejich používání a také použití [lock – příkaz](~/docs/csharp/language-reference/keywords/lock-statement.md), který používá tyto metody.  
  
 Další zamykání mechanismy, jako je typu číselník zámky a <xref:System.Threading.AutoResetEvent> musí volat tyto metody oznámit CLR zadání kritický oddíl.  Tyto metody nepřebírají žádné zámky; informují CLR, který je kód spouštěn v kritický oddíl a přerušení vlákna mohou způsobit sdílený stav nekonzistentní.  Pokud jste definovali vlastní typ zámku, jako jsou vlastní <xref:System.Threading.ReaderWriterLock> třídy, použijte tyto metody zamykací počet.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Označit a identifikaci všech zámků pomocí <xref:System.Threading.Thread.BeginCriticalRegion%2A> a <xref:System.Threading.Thread.EndCriticalRegion%2A>. Nepoužívejte <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>, a <xref:System.Threading.Interlocked.Decrement%2A> ve smyčce.  Neprovádějte platformu vyvolání variant Win32 z těchto metod.  Nepoužívejte <xref:System.Threading.Thread.Sleep%2A> ve smyčce.  Nepoužívejte pole s modifikátorem volatile.  
  
### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Vyčištění kód musí být v nakonec nebo catch bloku, nikoli následující bloku catch.  
 Kód pro vyčištění nikdy postupujte podle `catch` blokovat; by měla být v `finally` nebo v `catch` blokovat samotný.  To by měl být normální vhodné.  A `finally` blok je obecně upřednostňované, protože spouští stejný kód, když je vyvolána výjimka i když na konec `try` bloku obvykle dochází.  V případě neočekávané výjimky, například <xref:System.Threading.ThreadAbortException>, je kód čištění nelze spustit.  Žádné nespravované prostředky, které by vyčištění v `finally` v ideálním případě by měl být uzavřen v <xref:System.Runtime.InteropServices.SafeHandle> zabránit úniku informací.  Poznámka: C# `using` – klíčové slovo lze účinně uvolnila objekty, včetně obslužné rutiny.  
  
 I když <xref:System.AppDomain> recyklace můžete vyčistit prostředků na finalizační podproces, je stále potřeba vložit kód pro vyčištění na správné místo.  Všimněte si, že pokud vlákno obdrží asynchronní výjimky bez zámek, CLR se pokusí ukončit vlákno, samotný bez nutnosti recyklovat <xref:System.AppDomain>.  Zajištění, že prostředky se vyčistí dříve místo novější pomáhá tím, že k dispozici více prostředků a tím, že lepší spravuje životnost.  Pokud je explicitně nezavře popisovač souboru v cestě kódu některé chyby potom počkejte <xref:System.Runtime.InteropServices.SafeHandle> finalizační metody, při příštím spuštění kódu čištění, může dojít k selhání pokusu o přístup k přesně stejný soubor, pokud ještě nebyla spuštěna finalizační metodu.  Z tohoto důvodu se vám pomůže zajistit, že kód pro vyčištění existuje a zda správně funguje zotavení z chyb při více čistě a rychle, i když to není nezbytně nutné.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Kód pro vyčištění po `catch` musí být v `finally` bloku. Umístěte volání zlikvidujte bloku finally.  `catch` pozastaví spuštění, by měl končit vyvolání nebo znovu vyvolejte.  Zatímco bude existovat výjimky, jako je například zjišťování, zda lze navázat připojení k síti kód kde některé z velkého počtu výjimek, veškerý kód, který vyžaduje zachytávání počet výjimek za normálních okolností může získat měl dát indikaci toho, že kód by měl být testován, pokud bude úspěšné.  
  
### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Celého procesu proměnlivý stav sdílené mezi doménami aplikace by měly být odstraněny nebo použijte oblasti omezeného provádění  
 Jak je popsáno v úvodu, může být velmi obtížné je napsat spravovaný kód, který monitoruje sdílený stav celého procesu napříč doménami aplikace spolehlivé způsobem.  Sdílený stav celého procesu je jakýkoli druh datové struktury, které jsou sdílené mezi doménami aplikace, buď v kódu Win32, platformou CLR, nebo ve spravovaném kódu pomocí vzdálené komunikace.  Žádné proměnlivé sdílený stav je velmi obtížné je napsat správně ve spravovaném kódu a všechny statické sdílený stav může být provedeno pouze velmi opatrně.  Pokud máte celého procesu nebo celý počítač sdílený stav, najdete způsob, jak jejich odstranění nebo chránit sdílený stav pomocí oblasti omezeného provádění (CER).  Všimněte si, že všechny knihovny s sdílený stav, který není zjistila a opravila může způsobit, že hostitele, jako je SQL Server, který vyžaduje čištění <xref:System.AppDomain> uvolnění selhání.  
  
 Pokud kód používá objekt modelu COM, vyhněte se sdílení tohoto objektu COM mezi doménami aplikace.  
  
### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Zámky nebudou fungovat celého procesu nebo mezi doménami aplikace.  
 V minulosti <xref:System.Threading.Monitor.Enter%2A> a [lock – příkaz](~/docs/csharp/language-reference/keywords/lock-statement.md) byla použita k vytvoření globální procesu zámky.  Například k tomu dojde při zamykání <xref:System.AppDomain> agilní třídy, například <xref:System.Type> instancí z nesdílené sestavení <xref:System.Threading.Thread> objekty, internovány řetězců a některé řetězce sdíleny napříč doménami aplikace pomocí vzdálené komunikace.  Tyto zámky už nejsou celého procesu.  K určení přítomnosti zámek domén přes procesy mezi aplikacemi, zjistit, zda kód v rámci zámek používá všechny externí, trvalý prostředků jako je soubor na disku nebo databáze.  
  
 Mějte na paměti, přičemž zámek v rámci <xref:System.AppDomain> může způsobit potíže, pokud chráněný kód používá externí zdroj, vzhledem k tomu, že kód může současně spustit napříč několika doménami aplikace.  To může být problém při zápisu do jednoho souboru protokolu nebo vazbu na soket pro celý proces.  Tyto změny znamenají, neexistuje žádný snadný způsob, pomocí spravovaného kódu, proces globální zámek, než pomocí pojmenovaná <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore> instance.  Vytvořit kód, který nepodporuje souběžně v obou aplikačních doménách, nebo použít <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore> třídy.  Pokud stávající kód nemůže být změněn, nepoužívejte k dosažení této synchronizace, protože spuštěn v režimu vlákének znamená, že nebudete moct zaručit, bude získat a uvolnění objektu mutex, na stejném vlákně operačního systému Win32 pojmenovaný vzájemně vyloučený přístup.  Je nutné použít spravovanou <xref:System.Threading.Mutex> třídy nebo pojmenovaná <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, nebo <xref:System.Threading.Semaphore> synchronizovat kód zámek způsobem, který si je vědoma namísto synchronizace zámek pomocí nespravovaného kódu CLR.  
  
#### <a name="avoid-locktypeofmytype"></a>Vyhněte se lock(typeof(MyType))  
 Privátní a veřejné <xref:System.Type> objektů v sdílená sestavení s jenom jednu kopii kódu sdílené ve všech doménách aplikace jsou k dispozici také problémy.  Sdílená sestavení, je pouze jedna instance <xref:System.Type> na proces, což znamená, že více domén aplikace sdílet přesně stejné <xref:System.Type> instance.  Tak zámek na <xref:System.Type> instance převezme zámek, který má vliv na celý proces, ne jenom <xref:System.AppDomain>.  Pokud <xref:System.AppDomain> převezme Zámek <xref:System.Type> pak objektu, že vlákno náhle přeruší, neuvolní zámek.  Tohoto uzamknout pak může způsobit další aplikační domény k zablokování.  
  
 Dobrý způsob, jak zámky v statické metody zahrnuje přidání statické interní synchronizační objekt do kódu.  To může být inicializována v konstruktoru třídy, pokud je k dispozici, ale pokud ho nelze inicializovat tímto způsobem:  
  
```  
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
  
 Pak při přijímání zámku, použijte `InternalSyncObject` získat objekt k uzamčení na vlastnost.  Nemusíte použít vlastnost, pokud mají inicializovat interní synchronizační objekt ve vaší konstruktoru třídy.  Dvojitá kontrola, zda kód inicializace uzamčení by měl vypadat jako v tomto příkladu:  
  
```  
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
  
#### <a name="a-note-about-lockthis"></a>Poznámka k Lock(this)  
 Je obecně přijatelné zámek jednotlivého objektu, který je veřejně přístupný.  Pokud je objekt typu singleton objektu, který může způsobit, že celý subsystému k vzájemnému zablokování, zvažte ale použití také výše vzoru návrhu.  Například zámek na ten <xref:System.Security.SecurityManager> objekt by mohl způsobit zablokování v rámci <xref:System.AppDomain> provedení celé <xref:System.AppDomain> nepoužitelné. Je dobrým zvykem není zámek na veřejně přístupný objekt tohoto typu.  Ale zámek na jednotlivé kolekce nebo pole by neměla obecně dostupné na problém.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Nepřebírají zámky na typy, které mohou být použity napříč doménami aplikace nebo nemají představu silné identity. Nevolejte <xref:System.Threading.Monitor.Enter%2A> na <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread>, nebo libovolný objekt, který je odvozen od <xref:System.MarshalByRefObject>.  
  
### <a name="remove-gckeepalive-calls"></a>Odeberte uvolňování paměti. KeepAlive volání  
 Významné množství existující kód buď nepoužívá <xref:System.GC.KeepAlive%2A> , pokud by měl nebo používá, když není vhodné.  Po převedení na <xref:System.Runtime.InteropServices.SafeHandle>, není potřeba volat třídy <xref:System.GC.KeepAlive%2A>, za předpokladu, že nemají finalizační metodu, ale spoléhají na <xref:System.Runtime.InteropServices.SafeHandle> pro dokončení operační systém zpracovává.  Při snížení výkonu zachování volání <xref:System.GC.KeepAlive%2A> může být nepatrné, vnímání, který volání <xref:System.GC.KeepAlive%2A> je nezbytné nebo dostatečná k vyřešení problému, který už nemusí existovat provede kód obtížné udržovat životnost.  Nicméně, při použití vzájemné spolupráce CLR obálky volatelné modelem COM (RCW), <xref:System.GC.KeepAlive%2A> stále potřebuje kódu.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Odebrat <xref:System.GC.KeepAlive%2A>.  
  
### <a name="use-the-host-protection-attribute"></a>Použijte atribut ochrany hostitele  
 <xref:System.Security.Permissions.HostProtectionAttribute> (HPA) poskytuje akce deklarativní zabezpečení k určení požadavků na ochranu hostitele, umožňuje hostitele i plně důvěryhodného kódu zabránit volání určitých metod, které jsou pro daného hostitele, jako je například nevhodné<xref:System.Environment.Exit%2A>nebo <xref:System.Windows.Forms.MessageBox.Show%2A> pro SQL Server.  
  
 HPA ovlivní pouze nespravované aplikace, které hostují common language runtime a implementovat hostitele ochranu, jako je SQL Server. Při použití, výsledky akcí zabezpečení při vytváření požadavku propojení na základě zdroje hostitele, které zpřístupňuje třídy nebo metody. Pokud je kód spuštěn v klientské aplikaci nebo na serveru, který není chráněný hostitel, atribut "se odpaří"; není zjištěna a proto nebyly použity.  
  
> [!IMPORTANT]
>  Účelem tohoto atributu je vynucovat specifické pro hostitele programovací model pokyny, není chování zabezpečení.  I když požadavek propojení se používá ke kontrole pro soulad s požadavky model programování <xref:System.Security.Permissions.HostProtectionAttribute> není oprávnění zabezpečení.  
  
 Pokud hostitel nemá žádné programovací model požadavky, požadavky propojení nedojde.  
  
 Tento atribut určuje následující:  
  
-   Metody nebo třídy, které nebudou vyhovovat hostitele programovací model, ale jinak jsou neškodné.  
  
-   Metody nebo třídy, které nebudou vyhovovat programovací model hostitele a může vést k destabilizující server spravován uživatelského kódu.  
  
-   Metody nebo třídy, které nebudou vyhovovat hostitele programovací model a může vést k destabilizaci samotný proces serveru.  
  
> [!NOTE]
>  Pokud vytváříte knihovnu tříd, který má být volána aplikací, které mohou provést v prostředí hostitele chráněné, byste měli použít tento atribut na členy, které zpřístupňují <xref:System.Security.Permissions.HostProtectionResource> kategorie prostředků. Členové knihovny tříd rozhraní .NET Framework pomocí tohoto atributu způsobí pouze bezprostředního volajícího, která se má zkontrolovat.  Vaše knihovna člen musí také způsobit kontrolu jeho bezprostředního volajícího stejným způsobem.  
  
 Vyhledejte další informace o HPA v <xref:System.Security.Permissions.HostProtectionAttribute>.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Pro SQL Server musí HPA označeny všechny metody, které slouží k uvození synchronizace nebo dělení na vlákna. To zahrnuje metody, které sdílení stavu, jsou synchronizovány nebo spravovat externí procesy. <xref:System.Security.Permissions.HostProtectionResource> Hodnoty, které ovlivňují systému SQL Server jsou <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>, a <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Ale jakoukoli metodu, která zpřístupňuje všechny <xref:System.Security.Permissions.HostProtectionResource> by měly být identifikovány HPA, nejen těm, kteří používají prostředky, které mají vliv SQL.  
  
### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Po neomezenou dobu nebrání v nespravovaném kódu  
 Blokování v nespravovaném kódu místo ve spravovaném kódu může způsobit útoku DOS, protože modul CLR není možné přerušit vlákno.  Blokovaná vlákna zabraňuje uvolnění modulu CLR <xref:System.AppDomain>, alespoň bez provádění některých operací velmi nebezpečné.  Blokuje použití Win32 je primitiv synchronizace vymazat příkladem něco, co jsme nemůže povolit.  Při volání k blokování `ReadFile` na soketu mělo by se vyhnout Pokud je to možné – v ideálním případě by měl rozhraní Win32 API poskytují mechanismus pro vypršení časového limitu operace následujícím způsobem.  
  
 Jakoukoli metodu, která volá do nativní by měl v ideálním případě pomocí přiměřené omezený časový limit volání Win32.  Pokud uživatel může zadat časový limit, uživatel by neměl povoleno zadat neomezený časový limit bez nějaká konkrétní bezpečnostní oprávnění.  Jako vodítko Pokud metoda bude blokovat více než přibližně 10 sekund, budete muset používat verzi, která podporuje vypršení časového limitu nebo potřebujete další podporu modulu CLR.  
  
 Tady je několik příkladů problematické rozhraní API.  Kanály (anonymní a pojmenované) se dají vytvářet pomocí časového limitu; Nicméně kód musí měli jistotu, že nikdy volání `CreateNamedPipe` ani `WaitNamedPipe` s NMPWAIT_WAIT_FOREVER.  Kromě toho může neočekávané zablokování i v případě, že je zadaný časový limit.  Volání `WriteFile` na nepojmenovaného kanálu bude blokovat, dokud nejsou zapsány všechny bajty, což znamená, pokud má vyrovnávací paměť nepřečtená data, `WriteFile` volání bude blokovat, dokud čtecí modul má uvolnit místo ve vyrovnávací paměti do kanálu.  Sokety měli vždy používat některá rozhraní API, které uznává mechanismu vypršení časového limitu.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Blokování bez časového limitu v nespravovaném kódu je útoku DOS. Neprovádějte platformu vyvolání volání `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects`, a `MsgWaitForMultipleObjectsEx`.  Nepoužívejte NMPWAIT_WAIT_FOREVER.  
  
### <a name="identify-any-sta-dependent-features"></a>Identifikujte všechny STA – závislé funkce.  
 Identifikujte veškerý kód, který používá jednovláknový Apartment modelu COM (STAs).  V procesu serveru SQL Server jsou zakázány STAs.  Funkce, které závisí na `CoInitialize`, jako jsou čítače výkonu nebo do schránky, musí se zakázat v rámci SQL serveru.  
  
### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Ujistěte se, že finalizační metody jsou zdarma potíže se synchronizací  
 Více vláken finalizační metodu může existovat v budoucích verzích rozhraní .NET Framework, což znamená finalizační metody pro různé instance stejného typu běžet současně.  Nemají být zcela bezpečné; uvolňování zaručuje, že se spustí pouze jedno vlákno finalizační metodu pro daný objekt instance.  Ale finalizační metody musí být naprogramovány tak, aby nedošlo ke konfliktům časování a zablokování při spuštění současně na více instancí jiný objekt.  Při použití jakékoli externího stavu, jako je například zápis do souboru protokolu v finalizační metodu, potíže s vlákny musí být zpracován.  Nespoléhejte na dokončení zajistit bezpečný přístup z více vláken. Úložiště thread local, spravované nebo nativní, nepoužívejte k uložení stavu na finalizační podproces.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Finalizační metody musí být bez potíže se synchronizací. Nepoužívat statické proměnlivý stav v finalizační metodu.  
  
### <a name="avoid-unmanaged-memory-if-possible"></a>Pokud je to možné vyhnout nespravované paměti  
 Nespravované paměti může uniknout stejně jako popisovač operačního systému.  Pokud je to možné, zkuste použít paměti na zásobníku pomocí [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) nebo připojených spravovaný objekt, jako [fixed Statement](~/docs/csharp/language-reference/keywords/fixed-statement.md) nebo <xref:System.Runtime.InteropServices.GCHandle> pomocí byte [].  <xref:System.GC> Nakonec tyto vyčistí.  Pokud však je třeba přiřadit nespravovanou paměť, zvažte použití třídy, která je odvozena z <xref:System.Runtime.InteropServices.SafeHandle> zabalit přidělení paměti.  
  
 Všimněte si, že aspoň jeden případ kde <xref:System.Runtime.InteropServices.SafeHandle> není dostatečný.  Pro volání metody COM, které přidělit nebo uvolnit paměť, je běžné, že jedna knihovna DLL pro přidělení paměti prostřednictvím `CoTaskMemAlloc` pak jiné knihovně DLL se uvolní, tato paměť se `CoTaskMemFree`.  Pomocí <xref:System.Runtime.InteropServices.SafeHandle> v těchto umístěních by nevhodný vzhledem k tomu, že se pokusí spojit životnost nespravované paměti k době života <xref:System.Runtime.InteropServices.SafeHandle> namísto povolení druhý ovládací prvek knihovna DLL životnost paměť.  
  
### <a name="review-all-uses-of-catchexception"></a>Zkontrolujte všechna použití Catch(Exception)  
 Bloky catch, všechny výjimky namísto jedné určité výjimky se teď catch asynchronní výjimky a catch.  Zkontrolujte každý blok catch(Exception), hledá žádné důležité prostředků uvolnění nebo obnovení kód, který se možná přeskočí, a také potenciálně nesprávné chování v rámci bloku catch pro manipulaci <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, nebo <xref:System.OutOfMemoryException>.  Všimněte si, že je možné tento kód může protokolování nebo provádění některých předpokladů, že ho může zobrazit pouze určité výjimky, nebo že pokaždé, když dochází k výjimce se nepodařilo pro právě jeden konkrétní důvod.  Možná bude nutné aktualizovat tak, aby zahrnují tyto předpoklady <xref:System.Threading.ThreadAbortException>.  
  
 Vezměte v úvahu všechny změny umístí tento catch, všechny výjimky k zachytávaní konkrétní typ výjimky, které očekáváte, že budou vyvolány, například <xref:System.FormatException> z řetězce formátování metod.  To zabrání spuštění na neočekávané výjimky bloku catch a vám pomůže zajistit, že kód neskrývá pomocí zachycování výjimek neočekávané chyby.  Obecně nikdy zpracování výjimky v kódu knihovny (kód, který vyžaduje, abyste zachytit výjimku může znamenat chybu návrhu v kódu jsou volání).  V některých případech můžete chtít zachytit výjimku a vyvolat jiný typ výjimky poskytující další data.  Použití vnořené výjimky v tomto případě ukládání skutečné příčinu selhání v <xref:System.Exception.InnerException%2A> vlastnost novou výjimku.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Zkontrolujte všechny bloky catch ve spravovaném kódu tohoto catch všechny objekty nebo catch, všechny výjimky.  V C#, to znamená, že obě nastavení příznaku `catch` {} a `catch(Exception)` {}.  Zvažte učinění velmi specifický typ výjimky nebo podívejte do kódu a ujistěte se, že nepostupuje chybný způsobem, je-li zachycena typu došlo k neočekávané výjimce.  
  
### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Nepředpokládejte spravované vlákno je vlákno Win32 – je vlákno  
 Pomocí spravovaného vlákna místní úložiště funguje, ale nemusí používat místní úložiště nespravovaného vlákna nebo se předpokládá, že kód poběží v aktuálním vlákně operačního systému znovu.  Neměňte nastavení, jako je národní prostředí vlákna.  Nevolejte `InitializeCriticalSection` nebo `CreateMutex` prostřednictvím platformy vyvolat, protože vyžadují vláknu operačního systému, který zadá zámek také ukončení uzamčení.  Vzhledem k tomu, že to nebude tak při použití vlákének, kritické oddíly Win32 a vzájemně vyloučené přístupy nelze použít v SQL přímo.  Všimněte si, že spravovanou <xref:System.Threading.Mutex> třídy nezpracovává těchto úkonů spřažení vláken.  
  
 Lze bezpečně použít i většinu stavu na spravované <xref:System.Threading.Thread> objektu, včetně místním úložišti spravované vlákno a vlákna aktuální jazykové verze uživatelského rozhraní.  Můžete také použít <xref:System.ThreadStaticAttribute>, který zpřístupňuje hodnotu existující proměnné statické určená jenom pro aktuální vlákno spravovaná (to je další způsob provedení místní úložiště vlákna v modulu CLR).  Pro programovací model důvody, nelze změnit aktuální jazykové verze vlákna při spuštění v SQL.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 SQL Server běží v režimu vlákének; Nepoužívejte úložiště thread local. Vyhněte se platformu vyvolání volání `TlsAlloc`, `TlsFree`, `TlsGetValue`, a `TlsSetValue.`  
  
### <a name="let-sql-server-handle-impersonation"></a>Let SQL Server Handle Impersonation  
 Protože zosobnění funguje na úrovni vlákna a SQL můžete spustit v režimu vlákének, spravovaný kód nesmí vydávat za uživatele a neměl volat `RevertToSelf`.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Umožní zpracování zosobnění systému SQL Server. Nepoužívejte `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx`, nebo `SetThreadToken`.  
  
### <a name="do-not-call-threadsuspend"></a>Nevolejte Thread::Suspend  
 Možnost pozastavovat vlákno zdánlivě jednoduché operace, ale může to způsobit zablokování.  Pokud vlákno obsahující že zámek pozastaven vláknem, a pak druhého podprocesu pokusí trvá stejné zámek, dojde k zablokování.  <xref:System.Threading.Thread.Suspend%2A> může vést k potížím se zabezpečením, načtení třídy, vzdálené komunikace a reflexe aktuálně.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Nevolejte <xref:System.Threading.Thread.Suspend%2A>. Zvažte použití skutečné synchronizace primitivní místo toho, pokud například <xref:System.Threading.Semaphore> nebo <xref:System.Threading.ManualResetEvent> .  
  
### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Ochrana důležitých operací s oblasti omezeného provádění a kontrakty spolehlivosti  
 Při provádění složitá operace, která aktualizuje stav sdílení nebo, který potřebuje nedeterministicky buď zcela úspěšná nebo plně selhávat, ujistěte se, že je chráněn oblasti omezeného provádění (CER). Zaručí se tak, že kód se spustí ve všech případech i přerušení náhlé vlákna nebo náhlému <xref:System.AppDomain> uvolnit.  
  
 CER je konkrétní `try/finally` bloku bezprostředně před volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.  
  
 To uděláte tak instruuje kompilátor just-in-time Příprava veškerý kód v blok finally dřív, než spustíte `try` bloku. To zaručuje, že kód nakonec bloku je sestaven a spustí se ve všech případech. Není, v CER mít prázdnou `try` bloku. Použití CER chrání proti asynchronní vlákno přeruší a výjimky na více instancí z důvodu nedostatku paměti. Zobrazit <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> pro určitou formu CER, která kromě přetečení zásobníku obslužné rutiny pro mimořádně hloubkové kód.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.ConstrainedExecution>
- [Programování serveru SQL Server a atributy ochrany hostitele](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
