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
ms.openlocfilehash: d6f29d15297fc7faff6bb3bb07ee535647c2bb7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="reliability-best-practices"></a>Spolehlivost – doporučené postupy
Následující pravidla spolehlivost jsou orientované na SQL Server; však také použijí na všechny aplikace založené na hostiteli serveru. Je velmi důležité, aby servery, jako je SQL Server není úniku prostředky a nesmí být snížila.  Nicméně, nelze provést napsáním zálohující kód pro každou metodu, která mění stav daného objektu.  Cílem je nechcete napsat 100 procent spolehlivé spravovaný kód, který bude zotavit všechny chyby v každé umístění zálohující kód.  Který by složitý úkol s menší riziko úspěch.  Modul CLR (CLR) nelze snadno poskytnout dostatečně silné záruky do spravovaného kódu, aby zápis ideální kódu v rámci výpočetních procesů.  Všimněte si, že na rozdíl od ASP.NET, používá systém SQL Server pouze jeden proces, který nemůže být recyklována bez nutnosti převádět databáze nepřijatelně dlouhou dobu.  
  
 Tyto slabší záruky a spuštěn v jednom procesu je spolehlivost založené na ukončení vláken nebo recyklace aplikační domény, pokud nejsou neuniknou potřebné a přijímá opatření, aby prostředky operačního systému, například obslužné rutiny, paměť.  I když toto omezení jednodušší spolehlivost stále existuje požadavek významné spolehlivosti:  
  
-   Nikdy se nevrací prostředky operačního systému.  
  
-   Identifikujte všechny spravované uzamčená všech formulářů modulu CLR.  
  
-   Nikdy zalomení domény mezi aplikacemi – sdílené stavu, což <xref:System.AppDomain> recyklace řádně fungovat.  
  
 Přestože je možné teoreticky napsat spravovaný kód pro zpracování <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, a <xref:System.OutOfMemoryException> výjimky, byla očekávána vývojářům psát nepřiměřený takový robustní kód v celé aplikaci.  Z tohoto důvodu out-of-band výjimky za následek provádění vlákna ukončovány; a pokud ukončil podproces byl úpravy sdílený stav, který lze určit podle jestli vlákno obsahuje zámek, pak se <xref:System.AppDomain> je odpojen.  Při ukončení metodu, která je úpravy sdíleného stavu, bude stav poškozen, protože není možné zapsat do sdíleného stavu spolehlivé zálohující kód pro aktualizace.  
  
 V rozhraní .NET Framework verze 2.0 je jediným hostitele, který vyžaduje spolehlivost systému SQL Server.  Pokud vaše sestavení bude spuštěna v systému SQL Server, měli byste udělat pracovní spolehlivost pro každou součást sestavení, i když nejsou specifické funkce, které jsou zakázány při spuštění v databázi.  Toto není nutná modulu analýzy kódu zkontroluje kód na úrovni sestavení a nelze rozlišit zakázané kódu. Jiný Server SQL programovací problém je, že systém SQL Server všechno běží v jednom procesu, a <xref:System.AppDomain> recyklace se používá pro čištění všechny prostředky, jako je například obslužné rutiny paměti a operačního systému.  
  
 Nemůže záviset na finalizační metody nebo destruktory nebo `try/finally` bloků zálohující kód. Může být přerušeny nebo není volána.  
  
 Může být vyvolána asynchronní výjimky v neočekávaných umístěních, může být každý počítač instrukcí: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, a <xref:System.OutOfMemoryException>.  
  
 Spravovaných vláknech, nemusí nutně být Win32 vláken v SQL; mohou být jsou vlákna.  
  
 Měnitelný sdílený stav procesy nebo mezi aplikacemi domény je velmi obtížné alter bezpečně a je nutno kdykoli je to možné.  
  
 Z důvodu nedostatku paměti podmínky nejsou výjimečných v systému SQL Server.  
  
 Pokud knihovny hostované v systému SQL Server správně nelze aktualizovat jejich sdíleného stavu, je vysoká pravděpodobnost, že nebude obnovit kód až po restartování databáze.  Kromě toho v některých výjimečných případech je možné, že to může způsobit chybu procesu systému SQL Server způsobuje databázi na restartování.  Restartování databáze můžete vypnout webovou stránku nebo ovlivnily provoz společnosti, nespokojené dostupnosti.  Pomalé úniku prostředků operačního systému, třeba paměti nebo popisovače může způsobit selhání nakonec vyhrazování popisovače s žádná možnost obnovení serveru nebo potenciálně pomalou může snížit výkon serveru a snižuje zákazníka aplikace dostupnost.  Jasně chceme, aby se zabránilo tyto scénáře.  
  
## <a name="best-practice-rules"></a>Pravidly osvědčených postupů  
 Zavedení zaměřuje na co by mít revize kódu pro spravovaný kód, který běží na serveru k zachycení ke zvýšení stability a spolehlivost rozhraní. Všechny tyto kontroly jsou obecně osvědčených postupů a absolutní musí na serveru.  
  
 Při krátkodobém neaktivní uzamčení nebo prostředek omezení systému SQL Server bude zrušení vlákna nebo přerušit <xref:System.AppDomain>.  V takovém případě pouze zálohující kód v oblasti omezeného provádění (CER) záruku, že chcete spustit.  
  
### <a name="use-safehandle-to-avoid-resource-leaks"></a>Použijte SafeHandle předejdete nedostatku prostředků  
 U <xref:System.AppDomain> uvolnění, nemůže záviset na `finally` bloky nebo finalizační metody spouštění, proto je důležité abstraktní veškerý přístup prostředek operačního systému pomocí <xref:System.Runtime.InteropServices.SafeHandle> třída místo <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>, nebo Podobně jako třídy. To umožňuje CLR sledovat a zavřete obslužné rutiny, můžete použít i při <xref:System.AppDomain> úplné rozbalovací případu.  <xref:System.Runtime.InteropServices.SafeHandle> budou používat kritické finalizační metodu, která modul CLR bude vždy spuštěn.  
  
 Popisovač operačního systému jsou uloženy v bezpečné popisovač od okamžiku, kdy se vytvoří až do okamžiku, kdy je vydání.  Během kterého není okno <xref:System.Threading.ThreadAbortException> může dojít k úniku popisovač.  Kromě toho vyvolání platformy bude odkaz count popisovač, což umožňuje zavřít sledování doba života popisovače, brání chyba zabezpečení s časování mezi `Dispose` a metodu, která je aktuálně používá popisovač.  
  
 Většina tříd, které máte aktuálně finalizační metodu jednoduše vyčištění operační systém zpracování finalizační metodu už nepotřebují. Místo toho finalizační metodu bude na <xref:System.Runtime.InteropServices.SafeHandle> odvozené třídy.  
  
 Všimněte si, že <xref:System.Runtime.InteropServices.SafeHandle> není to náhrada za <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Má stále potenciální prostředků kolizí a výkonu výhod explicitně dispose prostředky operačního systému.  Právě Pamatujte si, že `finally` dokončení nemusí provést bloků, které explicitně uvolnění prostředků.  
  
 <xref:System.Runtime.InteropServices.SafeHandle> umožňuje implementovat vlastní <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda, která provede práci na uvolnění popisovač, jako je například stav předávání popisovač operačního systému uvolnění rutiny nebo uvolnění sada popisovačů ve smyčce.  Modul CLR zaručuje, že se tato metoda spustit.  Je zodpovědností autora <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementace zajistit, že popisovač vydání za všech okolností. Tak neučiníte způsobí, že popisovač uniknout, což často vede k úniku nativní prostředky přidružené k popisovač. Proto je důležité pro strukturu <xref:System.Runtime.InteropServices.SafeHandle> odvozených třídách tak, aby <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementace nevyžaduje přidělení všechny prostředky, které nemusí být k dispozici v čase volání. Všimněte si, že je přípustné volání metody, které může dojít k selhání v rámci implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> za předpokladu, že váš kód může zpracovat takové chyby a dokončení smlouvy k uvolnění nativní popisovač. Pro účely ladění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> má <xref:System.Boolean> vrátit hodnotu, která může být nastavena na `false` Pokud tomu vydání prostředku je došlo k závažné chybě. Díky tomu se budou aktivovat [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) (mda), pokud je povoleno, které pomáhají při identifikaci problému. Nemá vliv na modulu runtime jiným způsobem; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nebude volán znovu pro stejný prostředek a v důsledku toho budou úniku popisovač.  
  
 <xref:System.Runtime.InteropServices.SafeHandle> není vhodné v některých kontextech.  Vzhledem k tomu <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda se dá spustit na <xref:System.GC> finalizační metodu přístup z více vláken, všechny popisovače, které je potřeba uvolnit na konkrétní vlákno by neměl být uzavřen do <xref:System.Runtime.InteropServices.SafeHandle>.  
  
 Běhové obálky s možností (RCWs) mohou být vyčištěny CLR bez další kód.  Pro kód, který používá platformy vyvolání a jsou považovány za objektu COM `IUnknown*` nebo <xref:System.IntPtr>, kód by měl být přepsána pro použití RCW.  <xref:System.Runtime.InteropServices.SafeHandle> nemusí být pro tento scénář z důvodu možnost metodu nespravované verze zpětné volání do spravovaného kódu.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Použití <xref:System.Runtime.InteropServices.SafeHandle> pro zapouzdření prostředky operačního systému. Nepoužívejte <xref:System.Runtime.InteropServices.HandleRef> nebo pole typu <xref:System.IntPtr>.  
  
### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Ujistěte se, že finalizační metody není nutné spustit, aby se zabránilo úniku prostředky operačního systému  
 Zkontrolujte vaše finalizační metody pečlivě a ujistěte se, že i v případě, že se nespustí, není k úniku prostředek kritické operačního systému.  Na rozdíl od normální <xref:System.AppDomain> uvolnění, když se aplikace spouští v stabilního stavu, nebo když serveru, jako je vypnutí systému SQL Server, objekty nejsou dokončené během náhlému <xref:System.AppDomain> uvolnit.  Zajistěte, aby prostředky nejsou úniku v případě náhlému odpojit, protože nejde zaručit správnost aplikace, ale musí být zachová integrita serveru tím, že není vracena prostředky.  Použití <xref:System.Runtime.InteropServices.SafeHandle> uvolnit všechny prostředky operačního systému.  
  
### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Ujistěte se, že nakonec klauzule není nutné spustit a zabránit úniku prostředky operačního systému  
 `finally` klauzule se nezaručuje, že ke spuštění mimo CERs, vyžadování vývojářům knihovna není závislý na kód v rámci `finally` blok k uvolnění nespravovaných prostředků.  Pomocí <xref:System.Runtime.InteropServices.SafeHandle> je doporučená řešení.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Použití <xref:System.Runtime.InteropServices.SafeHandle> pro čištění prostředky operačního systému místo `Finalize`. Nepoužívejte <xref:System.IntPtr>; použít <xref:System.Runtime.InteropServices.SafeHandle> k zapouzdření prostředky. Pokud nakonec klauzule musí spustit, umístěte CER.  
  
### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Všechny zámky by měl projít existující spravovaného kódu uzamčení  
 Modul CLR musí vědět, pokud kód je v zámek tak, aby věděli, aby byl <xref:System.AppDomain> místo právě probíhá rušení vlákno.  Přerušení vlákno může být nebezpečný, protože data provozují na vlákno může být v nekonzistentním stavu. Proto celý <xref:System.AppDomain> má recyklace.  Důsledky selhání k identifikaci zámek může být blokování nebo nesprávné výsledky. Použít metody <xref:System.Threading.Thread.BeginCriticalRegion%2A> a <xref:System.Threading.Thread.EndCriticalRegion%2A> k identifikaci uzamčení oblasti.  Jsou statické metody na <xref:System.Threading.Thread> třídu, která se vztahují pouze na aktuální vlákno, pomáhá zabránit v úpravách počet zámků jiné vlákno jedno vlákno.  
  
 <xref:System.Threading.Monitor.Enter%2A> a <xref:System.Threading.Monitor.Exit%2A> mají toto oznámení CLR integrovanou, takže jejich použití se doporučuje a také použití [lock – příkaz](~/docs/csharp/language-reference/keywords/lock-statement.md), který používá tyto metody.  
  
 Další uzamčení mechanismy, například otočení zámky a <xref:System.Threading.AutoResetEvent> musí volat tyto metody oznámit modulu CLR zadávání kritická sekce.  Tyto metody nepřebírají žádné zámky; informovat o tom, spuštění kódu v kritická sekce modulu CLR a přerušení vlákno může způsobit sdíleného stavu nekonzistentní.  Pokud jste definovali vlastní typ zámku, jako je například vlastní <xref:System.Threading.ReaderWriterLock> třídy, použijte tyto metody počtu uzamčení.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Označit a identifikovat všechny zámky pomocí <xref:System.Threading.Thread.BeginCriticalRegion%2A> a <xref:System.Threading.Thread.EndCriticalRegion%2A>. Nepoužívejte <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>, a <xref:System.Threading.Interlocked.Decrement%2A> ve smyčce.  Udělat platformu vyvolání variant Win32 z těchto metod.  Nepoužívejte <xref:System.Threading.Thread.Sleep%2A> ve smyčce.  Nepoužívejte volatile pole.  
  
### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Vyčištění kód musí být v a nakonec nebo catch bloku není následující catch  
 Kód čištění nikdy postupujte podle `catch` blokovat; musí být ve `finally` nebo `catch` blokovat sám sebe.  To by měl být normální vhodné.  A `finally` bloku je obecně preferovaná, protože běží stejný kód, pokud je vyvolána výjimka i když konec `try` bloku je obvykle došlo.  V případě k neočekávané výjimce se, například <xref:System.Threading.ThreadAbortException>, je kód čištění, nelze spustit.  Všechny prostředky, které by vyčištění v nespravované `finally` v ideálním případě by měl být uzavřen ve <xref:System.Runtime.InteropServices.SafeHandle> k prevence úniků.  Všimněte si, jazyka C# `using` – klíčové slovo lze účinně k uvolnění objektů, včetně obslužné rutiny.  
  
 I když <xref:System.AppDomain> recyklace může odstranit systémové prostředky ve vlákně finalizační metodu, je důležité put kód čištění na správné místo.  Všimněte si, že pokud vlákno obdrží výjimku asynchronní bez zámek, modulu CLR pokusí o ukončení vlákna samotné bez nutnosti recyklace <xref:System.AppDomain>.  Zajištění, že prostředky jsou vyčistit dříve místo novější pomáhá tím, že k dispozici více prostředků a lepší správu dobu životnosti.  Pokud explicitně nezavřete popisovač pro soubor v cestě kódu některé chyby potom počkejte <xref:System.Runtime.InteropServices.SafeHandle> finalizační metodu pro při příštím spuštění kódu čištění, může dojít k selhání pokusu o přístup k přesně stejný soubor, pokud finalizační metodu již nebyla spuštěna.  Z tohoto důvodu vám pomůže zajistit, že kód čištění existuje a zda správně funguje obnovení v případě selhání více řádně a rychle, i když není nezbytně nutné.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Kód čištění po `catch` musí být ve `finally` bloku. Volání k uvolnění v a nakonec blokovat.  `catch` bloky musí končit throw nebo opětovné.  Zatímco bude výjimky, například kód zjišťování, zda lze vytvořit připojení k síti kde může získat žádné velký počet výjimek, kód, který vyžaduje zachytávání počet výjimek za normálních okolností měl dát indikace toho, zda kód by měl být testována, pokud chcete zobrazit, pokud bude úspěšné.  
  
### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Měnitelný sdíleného stavu procesy mezi doménami aplikací by měly být odstraněny nebo použijte oblasti omezeného provádění  
 Jak je popsáno v úvodu, může být velmi obtížné napsat spravovaného kódu, který monitoruje procesy sdíleného stavu napříč doménami aplikací spolehlivé způsobem.  Sdílený stav procesy je žádné řazení struktura dat, které jsou sdílené mezi doménami aplikací, buď v kódu Win32 uvnitř modulu CLR nebo ve spravovaném kódu pomocí vzdálené komunikace.  Žádný měnitelný sdílený stav je velmi obtížné správně zápisu ve spravovaném kódu a všechny statické sdíleného stavu může provést pouze s pozor.  Pokud máte procesy nebo celého systému sdíleného stavu, najděte některé způsob, jak jej odstranit nebo chránit sdílené stavu pomocí oblasti omezeného provádění (CER).  Všimněte si, že všechny knihovny s sdíleného stavu, který není zjistila a opravila by mohlo způsobit hostitele, jako je SQL Server, který vyžaduje čištění <xref:System.AppDomain> uvolnění chyby.  
  
 Pokud kód používá objekt modelu COM, vyhněte se sdílení tohoto objektu COM mezi doménami aplikací.  
  
### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Zámky nefungují procesy nebo mezi doménami aplikací.  
 V minulosti <xref:System.Threading.Monitor.Enter%2A> a [lock – příkaz](~/docs/csharp/language-reference/keywords/lock-statement.md) byl použit pro vytvoření globální proces zámky.  Například k tomu dojde při zamykání na <xref:System.AppDomain> agilní třídy, jako například <xref:System.Type> instancí z nesdílené sestavení, <xref:System.Threading.Thread> interned řetězce, objektů a některé řetězce sdílené mezi doménami aplikací pomocí vzdálené komunikace.  Tyto zámky již nejsou procesy.  K identifikaci přítomnost uzamčení procesy domény mezi aplikacemi, zjistit, zda kód v rámci zámek používá jakémukoli prostředku, externí, trvalé jako je soubor na disku, nebo může být databáze.  
  
 Všimněte si, trvá zámku v rámci <xref:System.AppDomain> může způsobit problémy, pokud kód chráněné používá externí zdroj, protože tento kód může běžet současně napříč více domén aplikací.  To může být problém při zápisu do jednoho souboru protokolu nebo vazbu na soket pro celý proces.  Tyto změny znamenají, neexistuje žádný snadný způsob, pomocí spravovaného kódu, získat zámek globální proces, než pomocí pojmenovaná <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore> instance.  Vytvoření kódu, který není v dvě domény aplikace běžet současně, nebo použijte <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore> třídy.  Pokud existující kód nemůže být změněn, nepoužívejte k dosažení této synchronizace, protože spuštěna v režimu vlákének znamená, že nebudete moct zaručit stejném vlákně, v operačním systému bude získat a verzí mutex Win32, pojmenovaný vzájemně vyloučený přístup.  Je nutné použít spravovaný <xref:System.Threading.Mutex> třídu nebo pojmenovaná <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, nebo <xref:System.Threading.Semaphore> synchronizovat zámek kód tak, aby si je vědoma namísto synchronizace ze zařízení zámek pomocí nespravovaného kódu modulu CLR.  
  
#### <a name="avoid-locktypeofmytype"></a>Vyhněte se lock(typeof(MyType))  
 Privátní a veřejné <xref:System.Type> objekty v sdílená sestavení s pouze jedné kopie kód sdílený všechny domény aplikace k dispozici také problémy.  Sdílená sestavení je pouze jedna instance <xref:System.Type> podle procesu, což znamená, že více domén aplikací sdílet přesný stejné <xref:System.Type> instance.  Pořízení Zámek <xref:System.Type> instance trvá zámku, která má vliv na celý proces, není právě v <xref:System.AppDomain>.  Pokud <xref:System.AppDomain> přebírá Zámek <xref:System.Type> objektu pak, získá náhle přerušena přístup z více vláken, nebude ho uvolní zámek.  Tato zámku pak může způsobit jiných domén aplikace k zablokování.  
  
 Dobrým způsobem, jak provádět zámky v statických metod zahrnuje přidání objektu statické vnitřní synchronizace ke kódu.  To může být inicializován v konstruktoru třídy, pokud je k dispozici, ale pokud ho nelze inicializovat takto:  
  
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
  
 Potom při přepnutí zámek, použijte `InternalSyncObject` vlastnost k získání objektu k uzamčení na.  Není nutné používat vlastnost, když jste inicializovali objekt interní synchronizace v konstruktoru vaší třídy.  Dvojité kontrola, zda kód inicializace zámku by měl vypadat jako tento ukázkový:  
  
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
  
#### <a name="a-note-about-lockthis"></a>Poznámka o Lock(this)  
 Je obecně přijatelné trvat zámek na jednotlivé objekt, který je veřejně přístupná.  Pokud se objekt typu singleton objektu, který může dojít celé subsystému ke vzájemnému zablokování, zvažte však pomocí také výše vzoru návrhu.  Například zámku na ten <xref:System.Security.SecurityManager> objekt může způsobit zablokování v rámci <xref:System.AppDomain> provedení celý <xref:System.AppDomain> nepoužitelný. Je dobrým zvykem nemusí provádět žádné zámek na veřejně přístupný objekt tohoto typu.  Uzamčení na jednotlivé kolekce nebo pole nesmí ale obecně dostupné k problému.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Nepřebírají typy, které by mohly používat napříč doménami aplikací nebo nemáte silné smysl identity zámky. Nevolejte <xref:System.Threading.Monitor.Enter%2A> na <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread>, nebo libovolný objekt, který je odvozen od <xref:System.MarshalByRefObject>.  
  
### <a name="remove-gckeepalive-calls"></a>Odeberte GC. Volání funkce KeepAlive  
 Významné množství existující kód buď nepoužívá <xref:System.GC.KeepAlive%2A> , pokud by měl nebo použije, když není vhodné.  Po převodu na <xref:System.Runtime.InteropServices.SafeHandle>, není nutné volat třídy <xref:System.GC.KeepAlive%2A>, za předpokladu, že nemají finalizační metody, ale závisí na <xref:System.Runtime.InteropServices.SafeHandle> finalizace operační systém zpracovává.  Při zachování volání náklady výkonu <xref:System.GC.KeepAlive%2A> může být nepatrné, vnímání, volání <xref:System.GC.KeepAlive%2A> je nezbytné nebo dostatečná vyřešit problém, který již neexistuje díky kód obtížnější údržbu životnost.  Ale, že při použití modelu COM spolupráce CLR obálky s možností (RCWs), <xref:System.GC.KeepAlive%2A> stále vyžadují kódu.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Odebrat <xref:System.GC.KeepAlive%2A>.  
  
### <a name="use-the-host-protection-attribute"></a>Použít atribut ochrany hostitele  
 <xref:System.Security.Permissions.HostProtectionAttribute> (HPA) poskytuje použití akce deklarativní zabezpečení určit požadavky na ochranu hostitele, umožňuje na hostiteli a zabránit i plně důvěryhodný kód volání některé metody, které nejsou vhodné pro daného hostitele, jako je například <xref:System.Environment.Exit%2A>nebo <xref:System.Windows.Forms.MessageBox.Show%2A> pro SQL Server.  
  
 HPA ovlivňuje pouze nespravovaná aplikace, které hostují běžné language runtime a implementace hostitele ochranu, jako je SQL Server. Při použití výsledky akce zabezpečení při vytváření požadavku na propojení na základě prostředky hostitele zpřístupňuje třída nebo metoda. Pokud je kód spuštěn v aplikaci klienta nebo na serveru, který není chráněný hostitele, atribut "se odpaří"; to není zjištěna a proto nebyly použity.  
  
> [!IMPORTANT]
>  Účelem tohoto atributu je vynutit konkrétního hostitele programovací model pokyny, není chování zabezpečení.  I když požadavek propojení se používá k ověření pro shodu programovací model požadavky <xref:System.Security.Permissions.HostProtectionAttribute> není oprávnění zabezpečení.  
  
 Pokud hostitel nemá programovací model požadavky, nedojde k požadavky propojení.  
  
 Tento atribut určuje následující:  
  
-   Metody nebo třídy, které se nehodí hostitele programovací model, ale jinak jsou neškodné.  
  
-   Metody nebo třídy, které se nehodí programovací model hostitele a může vést k destabilizing serveru spravované uživatelského kódu.  
  
-   Metody nebo třídy, které se nehodí hostitele programování modelu a může vést k destabilizaci samotný proces serveru.  
  
> [!NOTE]
>  Pokud vytváříte třídy knihovny, která je k volání aplikace, které může být spuštěn v prostředí hostitele chráněné, byste měli použít tento atribut na členy, které zveřejňují <xref:System.Security.Permissions.HostProtectionResource> prostředků kategorií. Členové knihovny tříd rozhraní .NET Framework se tento atribut způsobit pouze bezprostředního volajícího ke kontrole.  Vaše knihovna člen musí také způsobit kontrolu jeho bezprostředního volajícího stejným způsobem.  
  
 Prosím najít další informace o HPA v <xref:System.Security.Permissions.HostProtectionAttribute>.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Pro systém SQL Server musí všechny metody použité k zavedení synchronizace nebo dělení na vlákna označeny HPA. To zahrnuje metody, které sdílejí stavu, jsou synchronizovány nebo spravovat externí procesy. <xref:System.Security.Permissions.HostProtectionResource> Hodnoty, které mají vliv systému SQL Server jsou <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>, a <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Ale libovolné metody, která zveřejňuje žádné <xref:System.Security.Permissions.HostProtectionResource> by měl být identifikovaný HPA, nikoli pouze ty pomocí prostředků, které mají vliv na SQL.  
  
### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Po neomezenou dobu nebrání v nespravovaném kódu  
 Blokování v nespravovaném kódu místo ve spravovaném kódu může způsobit odepření služby, protože není možné přerušit vlákno modulu CLR.  Blokované vlákno brání uvolnění modulu CLR <xref:System.AppDomain>, alespoň bez provádění některých operací velmi nebezpečné.  Blokování používání Win32 synchronizace primitivní je zrušte příklad něco, co jsme nelze povolit.  Blokování v nástroji volání `ReadFile` na soket je nutno Pokud je to možné – v ideálním případě by měl rozhraní API Win32 poskytují mechanismus pro určité operace, jako je to vypršení časového limitu.  
  
 Libovolné metody, která volá do nativní by v ideálním případě pomocí přiměřené omezený časový limit volání Win32.  Pokud uživatel může určit časový limit, by neměl být uživatel moci zadat neomezený časový limit bez některé konkrétní bezpečnostní oprávnění.  Jako vodítko Pokud metoda bude blokovat pro více než ~ 10 sekund, musíte používat verzi, která podporuje vypršení časových limitů nebo potřebujete pomoc CLR.  
  
 Zde jsou některé příklady problematické rozhraní API.  Kanály (anonymní i s názvem) může být vytvořen pomocí vypršení časového limitu; ale kódu musí měli jistotu, že nikdy volání `CreateNamedPipe` ani `WaitNamedPipe` s NMPWAIT_WAIT_FOREVER.  Kromě toho může neočekávaná blokování i v případě, že je zadaný časový limit.  Volání metody `WriteFile` na anonymní kanálu se zablokuje, dokud se zapisují všechny bajtů, což znamená, pokud má vyrovnávací paměť nepřečtená data v něm `WriteFile` volání zablokuje, dokud má čtečka uvolnění místa ve vyrovnávací paměti do kanálu.  Sokety měli vždycky používat některé rozhraní API, které ctí mechanismus časový limit.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Blokování bez vypršení časového limitu v nespravovaném kódu se útoku DOS. Neprovádějte platformy vyvolat volání `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects`, a `MsgWaitForMultipleObjectsEx`.  Nepoužívejte NMPWAIT_WAIT_FOREVER.  
  
### <a name="identify-any-sta-dependent-features"></a>Identifikujte všechny STA – závislé funkce.  
 Určete kód, který používá COM single-threaded Apartment (STAs).  V procesu systému SQL Server jsou zakázány STAs.  Funkce, které jsou závislé na `CoInitialize`, jako například čítače výkonu nebo do schránky, musí se zakázat v rámci systému SQL Server.  
  
### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Ujistěte se, že jsou bez problémů synchronizace finalizační metody  
 Více vláken finalizační metodu může existovat v budoucích verzích rozhraní .NET Framework pro různé instance stejného typu běžet současně, což znamená finalizační metody.  Nemají být zcela vláken; uvolňování paměti zaručuje, že pouze jedno vlákno spustí finalizační metodu pro instanci daného objektu.  Však finalizační metody musí být zakódované vyhnout časování a blokování, pokud se používá současně na několik instancí jiný objekt.  Při použití jakékoli externí stavu, například zápis do souboru protokolu v finalizační metodu, problémy dělení na vlákna musí být zpracován.  Nespoléhejte na dokončení zajistit bezpečný přístup z více vláken. Lokální úložiště vláken, spravovaným nebo nativním, nepoužívejte k uložení stavu ve vlákně finalizační metodu.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Finalizační metody musí být bez problémů synchronizace. Nepoužívejte statické měnitelný stavu finalizační metody.  
  
### <a name="avoid-unmanaged-memory-if-possible"></a>Pokud je to možné vyhnout nespravované paměti  
 Nespravované paměti můžou uniknout, stejně jako popisovač operačního systému.  Pokud je to možné, zkuste použít paměti na použití zásobníku [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) nebo definovaného spravovaný objekt, jako [příkazu pevnou](~/docs/csharp/language-reference/keywords/fixed-statement.md) nebo <xref:System.Runtime.InteropServices.GCHandle> pomocí byte [].  <xref:System.GC> Nakonec tyto vyčistí.  Pokud však je třeba přiřadit nespravovanou paměť, zvažte použití třídy, která je odvozena od <xref:System.Runtime.InteropServices.SafeHandle> zabalit přidělení paměti.  
  
 Všimněte si, že je alespoň jeden případ kde <xref:System.Runtime.InteropServices.SafeHandle> není dostatečný.  Pro volání metod modelu COM, které přidělit nebo uvolnit paměť, je běžné pro jednu knihovnu DLL přidělit paměť prostřednictvím `CoTaskMemAlloc` pak jiné DLL uvolní této paměti se `CoTaskMemFree`.  Pomocí <xref:System.Runtime.InteropServices.SafeHandle> na těchto místech by nevhodných vzhledem k tomu, že se pokusí ke svázání životnost nespravované paměti pro dobu životnosti <xref:System.Runtime.InteropServices.SafeHandle> místo toho, abyste jiné knihovny DLL řízení životního cyklu paměti.  
  
### <a name="review-all-uses-of-catchexception"></a>Zkontrolujte všechny používá Catch(Exception)  
 Catch – bloky catch všechny výjimky místo jednu konkrétní výjimku bude nyní catch asynchronní výjimky.  Zkontrolujte všechny catch(Exception) bloku, hledá žádné důležité prostředků vydání nebo obnovení kód, který může být přeskočeny, a také potenciálně nesprávné chování v bloku catch pro zpracování <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, nebo <xref:System.OutOfMemoryException>.  Všimněte si, že je možné, může být tento kód protokolování nebo některé odhad, že se zobrazí pouze určité výjimky, nebo že vždy, když se stane výjimku, je pro právě jeden konkrétní důvod se nezdařilo.  Tyto předpoklady muset být aktualizováno, aby zahrnovalo <xref:System.Threading.ThreadAbortException>.  
  
 Vezměte v úvahu všechny změna umístí této catch všechny výjimky pro zachytávání určitý typ výjimky, které očekáváte, že bude vyvolána, například <xref:System.FormatException> z řetězce formátování metody.  Tento blok catch zabrání spuštění na neočekávané výjimky a pomůže zajistit, že kód není Skrýt chyby tak, že zachytávání neočekávané výjimky.  Obecně platí nikdy zpracování výjimky v kódu knihovny (kód, který vyžaduje, abyste k zachycení výjimek může znamenat závadu návrhu v kódu jsou volání).  V některých případech můžete chtít zachytit výjimku a vyvolat typ různé výjimky poskytující další data.  V takovém případě použijte vnořené výjimky ukládání skutečné příčinu selhání v <xref:System.Exception.InnerException%2A> vlastnost novou výjimku.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Zkontrolujte všechny bloky catch ve spravovaném kódu, že catch všechny objekty nebo catch všechny výjimky.  V jazyce C#, to znamená i označování `catch` {} a `catch(Exception)` {}.  Zvažte velmi konkrétní typ výjimky, nebo zkontrolujte kód, který Ujistěte se, že ho neprovede chybný způsob Pokud zachytávalo typ došlo k neočekávané výjimce.  
  
### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Nepředpokládejte, spravované vlákno je vlákna Win32 – je vlákna  
 Pomocí spravovaného místní úložiště funguje, ale nemusí použít místní úložiště vláken nespravované nebo předpokládají, že kód bude znovu spusťte na aktuální vlákno operačního systému pro přístup z více vláken.  Neměňte nastavení, jako je národní prostředí vlákna.  Nevolejte `InitializeCriticalSection` nebo `CreateMutex` prostřednictvím platformy vyvolat, protože vyžadují vláknu operačního systému, který zadá zámek také ukončete zámek.  Vzhledem k tomu, že to nebude tak při použití jsou vlákna, kritické oddíly Win32 a mutex – třídy nelze použít v SQL přímo.  Všimněte si, že spravovanou <xref:System.Threading.Mutex> třída nezpracovává tyto problémy spřažení podprocesu.  
  
 Většina stavu můžete bezpečně použít ve spravované <xref:System.Threading.Thread> objektu, včetně lokální úložiště vláken spravované a vlákna aktuální jazykové verze uživatelského rozhraní.  Můžete také <xref:System.ThreadStaticAttribute>, takže hodnotu existující proměnné statické přístupné jenom pomocí spravovaného aktuální vlákno (to je další způsob plnění fiber místní úložiště v modulu CLR).  Pro programování modelu důvodů, nelze změnit jazykové verze aktuálního vlákna při spuštění v systému SQL.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 SQL Server běží v režimu vlákének; Nepoužívejte lokální úložiště vláken. Vyhněte se platformy vyvolat volání `TlsAlloc`, `TlsFree`, `TlsGetValue`, a `TlsSetValue.`  
  
### <a name="let-sql-server-handle-impersonation"></a>Umožní zosobnění popisovač SQL serveru  
 Vzhledem k tomu, že zosobnění pracuje na úrovni přístup z více vláken a SQL můžete spustit v režimu vlákének, by neměl zosobnit uživatele spravovaného kódu a nesmí volání `RevertToSelf`.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Umožní zpracování zosobnění systému SQL Server. Nepoužívejte `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx`, nebo `SetThreadToken`.  
  
### <a name="do-not-call-threadsuspend"></a>Nevolejte Thread::Suspend  
 Umožňuje pozastavit vlákno, může se zobrazit jednoduchá operace, ale může to způsobit zablokování.  Pokud vlákno podržíte, že získá zámek pozastavil druhý vláken a pak druhý vlákno pokusí trvá stejné zámek, dojde k zablokování.  <xref:System.Threading.Thread.Suspend%2A> může narušovat zabezpečení, třída načítání, vzdálenou komunikaci a reflexe aktuálně.  
  
#### <a name="code-analysis-rule"></a>Pravidel nástroje Analýza kódu  
 Nevolejte <xref:System.Threading.Thread.Suspend%2A>. Zvažte použití skutečné synchronizace primitivní místo toho jako <xref:System.Threading.Semaphore> nebo <xref:System.Threading.ManualResetEvent> .  
  
### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Chránit kritické operace s omezené oblasti provádění a kontrakty spolehlivosti  
 Při provádění operace s komplexní, aktualizuje sdílený stav nebo potřebného pro nepodmíněně buď plně úspěšné nebo plně nezdaří, ujistěte se, že je chráněn v oblasti omezeného provádění (CER). To zaručuje, že spuštění kódu v každém případě i náhlému vlákno přerušení nebo náhlému <xref:System.AppDomain> uvolnit.  
  
 CER je konkrétní `try/finally` bloku bezprostředně před voláním <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.  
  
 To proto dá pokyn kompilátoru za běhu k přípravě všech kód v nakonec blokovat dřív, než spustíte `try` bloku. To zaručuje, že kód nakonec bloku vychází a spustí ve všech případech. Je běžné v CER mít prázdnou `try` bloku. Použití CER chrání před asynchronní vlákno přerušení a výjimky nedostatku paměti. V tématu <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> pro formulář CER, který kromě přetečení zásobníku obslužné rutiny pro mimořádně hloubkové kód.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.ConstrainedExecution>  
 [Programování serveru SQL Server a atributy ochrany hostitele](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
