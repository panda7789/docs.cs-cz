---
title: SOS.dll (rozšíření ladění SOS)
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0821b4a680db4822cea1787edb095309e6333cbf
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690164"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (rozšíření ladění SOS)

Nástroj SOS Debugging Extension (SOS.dll) pomáhá při ladění spravovaných programů v sadě Visual Studio a v ladicím programu sady Windows (WinDbg.exe) poskytováním informací o vnitřním prostředí modulu Common Language Runtime (CLR). Tento nástroj vyžaduje, aby měl projekt povoleno nespravované ladění. Knihovna SOS.dll je automaticky nainstalována společně s rozhraním .NET Framework. Pro použití knihovny SOS.dll v sadě Visual Studio, nainstalujte [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

## <a name="syntax"></a>Syntaxe

```shell
![command] [options]
```

## <a name="commands"></a>Příkazy

|Příkaz|Popis|
|-------------|-----------------|
|**AnalyzeOOM** (**ao**)|Zobrazí informace o poslední nedostatek paměti (OOM), ke které došlo na požadavek na přidělení na haldě uvolňování paměti. (Při uvolňování paměti serveru se případná chyba v důsledku vyčerpání paměti (OOM) zobrazí u každé haldy uvolňování paměti zvlášť.)|
|**BPMD** [ **- nofuturemodule**] [\<*název modulu*> \<*název metody*>] [ **- md**   < `MethodDesc`>] **– seznam** **-vymazat** \< *čekající zarážka číslo* >  **- clearall**|Vytvoří ve zvoleném modulu zarážku u určené metody.<br /><br /> Pokud nebyl načten zvolený modul ani metoda, počká tento příkaz na notifikaci, že byl modul načten a zkompilován za běhu (JIT) před vytvořením zarážky.<br /><br /> Seznam nevyřízených zarážek lze spravovat pomocí **– seznam**, **-vymazat**, a **- clearall** možnosti:<br /><br /> **– Seznam** možnost vytvoří seznam všech čekajících zarážek. Pokud má čekající zarážka nenulovou hodnotu ID modulu, pak je tato zarážka určena pro konkrétní funkci v konkrétním načteném modulu. Pokud má čekající zarážka nulovou hodnotu ID modulu, pak je tato zarážka určena modulům, které ještě nebyly načteny.<br /><br /> Použití **-vymazat** nebo **- clearall** možnost k odstranění čekajících zarážek ze seznamu.|
|**CLRStack** [ **–** ] [ **-l**] [ **-p**] [ **- n**]|Poskytne trasování zásobníku pouze pro spravovaný kód.<br /><br /> **-P** možnost zobrazí argumenty spravované funkce.<br /><br /> **-L** možnost s informacemi o lokálních proměnných v objektu frame. Nástroj SOS Debugging Extension nemůže získat místní názvy, takže je výstup pro místní názvy ve formátu \< *místních adres* >  **=** \< *hodnotu*>.<br /><br /> **–** Možnost (vše) je zkratkou pro **-l** a **-p** kombinovat.<br /><br /> **- N** možnost zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. **- N** (bez čísel řádků) parametr je možné zadat pro toto chování zakázat.<br /><br /> Nástroj SOS Debugging Extension nezobrazuje přechodné rámce pro platformy založené na architekturách x64 a IA-64.|
|**COMState**|Obsahuje model COM typu apartment pro každé vlákno a `Context` ukazatele, pokud je k dispozici.|
|**DumpArray** [ **-start** \< *startIndex*>] [ **– délka** \< *délka*>] [ **– podrobnosti**] [ **- nofields**] \< *pole Adresa objektu*><br /><br /> -nebo-<br /><br /> **DA** [ **-start** \< *startIndex*>] [ **– délka** \< *délka*>] [ **-detail**] [ **- nofields**] *pole Adresa objektu*>|Prozkoumá prvky objektu pole (typ array).<br /><br /> **-Start** možnost určí počáteční index, ve kterém se mají prvky zobrazovat.<br /><br /> **– Délka** parametr určuje počet prvků, chcete-li zobrazit.<br /><br /> **– Podrobnosti** možnost se zobrazí podrobnosti o používání elementu **DumpObj** a **DumpVC** formátů.<br /><br /> **- Nofields** možnost zabrání zobrazení polí. Tato možnost je dostupná jenom v případě **– podrobnosti o** je zadána možnost.|
|**DumpAssembly** \< *adres sestavení*>|Zobrazí informace o sestavení.<br /><br /> **DumpAssembly** příkaz vypíše seznam několika modulů, pokud existují.<br /><br /> Adresu sestavení lze získat pomocí **DumpDomain** příkazu.|
|**DumpClass** \< *EEClass adresu*>|Zobrazí informace o `EEClass` přidružený k typu Struktura.<br /><br /> **DumpClass** příkaz zobrazí hodnoty statických polí, ale nezobrazí hodnoty nestatických polí.<br /><br /> Použití **Eeclass**, **DumpObj**, **Name2EE**, nebo **name2ee** příkazu získejte `EEClass` adresy struktury.|
|**DumpDomain** [\<*adresy domény*>]|Vytvoří výčet všech <xref:System.Reflection.Assembly> objektu, který je načten v rámci zadaného <xref:System.AppDomain> adresy objektu.  Při volání bez parametrů, **DumpDomain** příkaz vypíše všechny <xref:System.AppDomain> objekty v procesu.|
|**DumpHeap** [ **-stat**] [ **-řetězců**] [ **-krátký**] [ **-min** \< *velikost*>] [ **-max** \< *velikost*>] [ **- thinlock**] [ **- startAtLowerBound**] [ **- mt** \< *MethodTable adresu*>] [ **– typ** \< *název částečného typu*>] [*start* [*end*]]|Zobrazí informace o haldě uvolnění paměti a statistiky uvolňování objektů.<br /><br /> **DumpHeap** příkaz zobrazí upozornění, pokud zjistí nadměrnou fragmentaci v haldě systému uvolňování paměti.<br /><br /> **-Stat** omezí výstup na zobrazení statistického shrnutí typů.<br /><br /> **-Řetězců** omezí výstup na souhrnné statistické řetězcovou hodnotu.<br /><br /> **-Krátký** možnost omezí výstup na pouhé zobrazení adresy každého objektu. To umožňuje automatizovat snadným vytvořením kanálu pro výstup z příkazu do dalšího příkazu ladicího programu.<br /><br /> **-Min** možnost ignoruje objekty, které jsou menší než `size` parametr zadáno v bajtech.<br /><br /> **-Max** možnost ignoruje objekty, které jsou větší, než `size` parametr zadáno v bajtech.<br /><br /> **- Thinlock** možnost sestavy ThinLocks.  Další informace najdete v tématu **SyncBlk** příkazu.<br /><br /> `-startAtLowerBound` Možnost vynutí procházení haldy má začít ve dolní mez zadaného rozsahu adres. Během fáze plánování často nelze haldu projít, jelikož je s objekty pohybováno. Tato možnost vynutí **DumpHeap** zahájíte její procházení na zadané dolní mezi. Aby tato možnost fungovala, je třeba zadat adresu platného objektu jako dolní mez. Na adrese chybného objektu lze zobrazit paměť a vyhledat další tabulky metody ručně. Pokud se uvolňování paměti kolekce je momentálně ve volání `memcopy`, je také možné najít adresu dalšího objektu přidáním velikosti na počáteční adresu, která je předána jako parametr.<br /><br /> **- Mt** možnost vypíše pouze ty objekty, které odpovídají zadané `MethodTable` struktury.<br /><br /> **– Typ** možnost vypíše pouze ty objekty, jejichž název typu je odpovídají podřetězci zadaného řetězce.<br /><br /> `start` Parametr začne vypisovat ze zadané adresy.<br /><br /> `end` Parametr zastaví vypisování na zadané adrese.|
|**DumpIL** \< *spravované DynamicMethod objekt*> &#124; \< *DynamicMethodDesc ukazatel*> &#124; \<  *MethodDesc ukazatele*>|Zobrazí kód v jazyce MSIL (Microsoft Intermediate Language) přidružený ke spravované metodě.<br /><br /> Dynamický kód jazyka MSIL je vysílán jinak, než kód jazyka MSIL, který je načten ze sestavení. Dynamický kód jazyka MSIL odkazuje spíše na objekty v poli spravovaných objektů, než na tokeny metadat.|
|**DumpLog** [ **-addr** \<*addressOfStressLog*>] [<*Filenam*`e`>]|Zapíše obsah zátěžového protokolu uloženého v paměti do zadaného souboru. Pokud nebude název zadán, vytvoří příkaz v aktuálním adresáři soubor s názvem StressLog.txt.<br /><br /> Zátěžový protokol uložený v paměti pomáhá diagnostikovat zátěžová selhání bez pomoci zámků nebo vstupů a výstupů. Pro povolení zátěžového protokolu, nastavit následující klíče registru pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> Volitelný `-addr` umožní zadat jiný než výchozí zátěžový protokol.|
|**DumpMD** \< *MethodDesc adresu*>|Zobrazí informace o `MethodDesc` struktury na zadané adrese.<br /><br /> Můžete použít **IP2MD** příkazu získejte `MethodDesc` adresy ze spravované funkce struktury.|
|**Eeclass** [ **-MD**] \< *MethodTable adresu*>|Zobrazí informace o tabulce metod na zadané adrese. Zadání **-MD** možnost zobrazí seznam všech metod definovaných s objektem.<br /><br /> Každý spravovaný objekt obsahuje ukazatel tabulky metod.|
|**DumpMethodSig** \< *sigaddr*><*moduleadd*`r`>|Zobrazí informace o `MethodSig` struktury na zadané adrese.|
|**DumpModule** [ **- mt**] \< *adresy modulu*>|Zobrazí informace o modulu na zadané adrese. **- Mt** možnost se zobrazí typy definované v modulu a typy odkazované modulem<br /><br /> Můžete použít **DumpDomain** nebo **DumpAssembly** příkaz, který načte adresy modulu.|
|**DumpObj** [ **- nofields**] \< *adresy objektu*><br /><br /> -nebo-<br /><br /> **PROVEĎTE** \< *adresy objektu*>|Zobrazí informace o objektu na zadané adrese. **DumpObj** příkaz zobrazí pole, `EEClass` struktury informace, tabulku metody a velikost objektu.<br /><br /> Můžete použít **DumpStackObjects** příkaz, který načte adresu objektu.<br /><br /> Všimněte si, že můžete spustit **DumpObj** příkaz na pole typu `CLASS` vzhledem k tomu, že jsou také objekty.<br /><br /> `-` **Nofields** možnost zabraňuje pole objektu, který se zobrazí, což je užitečné pro objekty, jako jsou řetězce.|
|**DumpRuntimeTypes**|Zobrazí objekty typu runtime z haldy systému uvolňování paměti a vypíše názvy s nimi asociovaných typů a tabulky metod.|
|**DumpStack** [ **- EE**] [ **- n**] [`top` *zásobníku* [`bottom` *zásobní*`k`]]|Zobrazí trasování zásobníku.<br /><br /> **- EE** možnost způsobí, že **DumpStack** příkazu můžete zobrazit pouze spravované funkce. Použití `top` a `bottom` parametry pro omezení zobrazených na x86 rámců platformy.<br /><br /> **- N** možnost zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. **- N** (bez čísel řádků) parametr je možné zadat pro toto chování zakázat.<br /><br /> Na platformách x86 a x64 **DumpStack** příkaz vytvoří podrobné trasování zásobníku.<br /><br /> Na platformách založené na IA-64 **DumpStack** napodobí příkaz ladicího programu **K** příkazu. `top` a `bottom` parametry budou ignorovány na platformách založené na IA-64.|
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|Zobrazí informace o `Sig` struktury na zadané adrese.|
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Zobrazí jediný prvek objektu podpisu. Ve většině případů byste měli použít **DumpSig** podívat se na jednotlivých objektů podpisu. Nicméně, pokud byla poškozena podpis nějakým způsobem, můžete použít **DumpSigElem** ke čtení jeho platných částí.|
|**DumpStackObjects** [ **– ověření**] [`top` *zásobníku* [`bottom` *zásobníku*]]<br /><br /> -nebo-<br /><br /> **DSO** [ **– ověření**] [`top` *zásobníku* [`bottom` *zásobníku*]]|Zobrazí všechny spravované objekty nalezené v rámci aktuálního zásobníku.<br /><br /> **– Ověření** validuje každé nestatické `CLASS` pole objektu pole.<br /><br /> Použití **DumpStackObject** příkaz pomocí příkazů trasování zásobníku, jako **K** příkazu a **CLRStack** příkaz k určení hodnot místních proměnných a Parametry.|
|**DumpVC** \< *MethodTable adresu*> \<*adresu*>|Zobrazí informace o polích třídy hodnot na konkrétní adrese.<br /><br /> **MethodTable** parametr povoluje **DumpVC** příkaz správně interpretovat pole. Třídy hodnot nemají jako první pole tabulku metod.|
|**EEHeap** [ **-gc**] [ **-loader**]|Zobrazí informace o paměti procesu spotřebované vnitřními datovými strukturami modulu CLR.<br /><br /> **-Gc** a **-loader** možnosti omezují výstup tohoto příkazu na datové struktury systému uvolňování paměti nebo zavaděče.<br /><br /> Informace pro systém uvolňování paměti obsahují rozsahy každého segmentu ve spravované haldě.  Pokud ukazatel spadá do rozsahu segmentu zadaného možností **-gc**, je ukazatel ukazatelem na objekt.|
|**EEStack** [ **-krátký**] [ **- EE**]|Spuštění **DumpStack** příkaz na všech vláknech v procesu.<br /><br /> **- EE** možnost je předána přímo **DumpStack** příkazu. **-Krátký** parametr omezí výstup na následující typy vláken:<br /><br /> Vlákna, která byla uzamknuta.<br /><br /> Vlákna, která byla kvůli uvolňování paměti pozastavena.<br /><br /> Vlákna, která jsou aktuálně ve spravovaném kódu.|
|**EEVersion**|Zobrazí verzi modulu CLR.|
|**EHInfo** [\<*MethodDesc adresu*>] [\<*kód adresa*>]|Zobrazí bloky zpracování výjimek v zadané metodě.  Tento příkaz zobrazí adresy kódu a posun pro blok klauzule ( `try` bloku) a blok zpracování ( `catch` bloku).|
|**Nejčastější dotazy**|Zobrazí nejčastější dotazy.|
|**FinalizeQueue** [ **-detail**] &#124; [ **- allReady**] [ **-krátký**]|Zobrazí všechny objekty, které jsou registrovány pro dokončení.<br /><br /> **-Detail** možnost se zobrazí další informace o jakýchkoli `SyncBlocks` , které je potřeba vyčistí a všechny `RuntimeCallableWrappers` (RCW), které čekají na vyčištění. Obě tyto datové struktury jsou uloženy do mezipaměti a vyčištěny finalizačním vláknem při spuštění.<br /><br /> `-allReady` Možnost zobrazí všechny objekty, které jsou připraveny k dokončení, bez ohledu na to, zda jsou již označen jako například kolekci uvolňování paměti, nebo budou označeny v dalším uvolňování. Objekty, které jsou na seznamu objektů připravených k dokončení, jsou dokončitelné objekty, které již nezačínají kořenem. Tato možnost může být velice nákladná, jelikož ověřuje, zda všechny objekty ve frontě dokončitelných objektů stále začínají kořenem.<br /><br /> `-short` Možnost omezuje výstup na zobrazení adresy každého objektu. Pokud se používá ve spojení s **- allReady**, vypíše všechny objekty, které mají finalizační metody, které již nezačínají kořenem. Pokud je použita nezávisle, vypíše všechny objekty ve frontách s dokončitelnými objekty a objekty připravenými k dokončení.|
|**FindAppDomain** \< *adresy objektu*>|Určuje doménu aplikace objektu na zadané adrese.|
|**FindRoots** **-gen** \< *N*> &#124; **-gen žádné** &#124; \< *adresy objektu*>|Způsobí přerušení ladicího programu během ladění při dalším shromáždění zadané generace. Efekt se obnoví, jakmile dojde k přerušení. Pro přerušení dalšího shromažďování je třeba znovu zadat tento příkaz. *\<Adresy objektu>* formu tento příkaz se používá po přerušení způsobeném příkazem **-gen** nebo **–některé obecné** došlo k chybě. V tu chvíli laděný proces je ve správném stavu, aby **FindRoots** mohl identifikovat kořeny pro objekty z aktuální tom generací.|
|**GC** [ **- perdomain**]|Zobrazí statistické údaje o popisovačích systému uvolňování paměti v procesu.<br /><br /> **- Perdomain** možnost uspořádá statistické údaje podle domény aplikace.<br /><br /> Použití **GCHandles** příkazu k vyhledání nevrácení paměti způsobených nevrácením popisovačů uvolňování paměti. Neuvolnění paměti například nastane, když kód zachová velké pole, protože silný popisovač systému uvolňování paměti na něj stále ukazuje, zatímco je zrušen, aniž by bylo uvolněno pole.|
|**GCHandleLeaks**|Vyhledá v paměti jakékoli odkazy na silné a připojené popisovače systému uvolňování paměti v procesu a zobrazí výsledky. Pokud je popisovač nalezen, **GCHandleLeaks** příkaz zobrazí adresu odkazu. Pokud není popisovač v paměti nalezen, zobrazí tento příkaz upozornění.|
|**GCInfo** \< *MethodDesc adresu*>\<*kód adresa*>|Zobrazí data, která označují, kdy registry nebo umístění zásobníku obsahují spravované objekty. Pokud dojde k uvolnění paměti, musí uvolňovač vědět o umístění odkazů na objekty, aby je bylo možné aktualizovat novou hodnotou ukazatele na objekt.|
|**GCRoot** [ **- nostacks**] \< *adresy objektu*>|Zobrazí informace o odkazech (nebo kořenech) na objekt na zadané adrese.<br /><br /> **GCRoot** příkaz prověří celou spravovanou haldu a tabulku popisovačů pro popisovače uvnitř jiných objektů a popisovače v zásobníku. Každý zásobník následně vyhledá ukazatele na objekty a rovněž je prohledána fronta finalizační metody.<br /><br /> Tento příkaz neurčuje, zda je kořen zásobníku platný nebo zrušený. Použít **CLRStack** a **U** příkazy rámce, kterému patří hodnota místní proměnnou nebo argument, aby bylo možné zjistit, zda je kořen zásobníku stále používán.<br /><br /> **- Nostacks** možnost omezuje vyhledávání na popisovače systému uvolňování paměti a dostupné objekty.|
|**GCWhere**  *\<adresy objektu>*|Zobrazí umístění a velikost předaného argumentu v haldě uvolňování paměti. Pokud argument leží ve spravované haldě, ale není platnou adresou objektu, je zobrazena velikost 0 (nula).|
|**Nápověda** [\<*příkaz*>] [`faq`]|Zobrazí všechny dostupné příkazy, pokud není zadán žádný parametr, nebo zobrazí detailní informace nápovědy o zadaném příkazu.<br /><br /> `faq` Zobrazí odpovědi na nejčastější dotazy.|
|**HeapStat** [ **- inclUnrooted** &#124; **-iu**]|Zobrazí velikosti generací pro každou haldu a celkové volné místo v každé generaci v každé haldě. Pokud-**inclUnrooted** zadána, sestava obsahuje informace o spravovaných objektech z haldy uvolňování paměti kolekce, která je již nezačínají kořenem.|
|**HistClear**|Uvolní všechny prostředky používané v řady `Hist` příkazy.<br /><br /> Obecně platí, není potřeba explicitně volat `HistClear`, protože každý `HistInit` vyčistí předchozí zdroje.|
|**HistInit**|Inicializuje struktury SOS ze zátěžového protokolu uloženého v laděné položce.|
|**HistObj** *\<obj_address>*|Zkontroluje všechny záznamy přemístění zátěžového protokolu a zobrazí řetězec přemísťování uvolňování paměti, který může vést na adresu předanou jako argument.|
|**HistObjFind**  *\<obj_address>*|Zobrazí všechny položky protokolu, které odkazují na objekt na zadané adrese.|
|**HistRoot** *\<root>*|Zobrazí informace týkající se propagace a přemístění zadaného kořenu.<br /><br /> Hodnotu kořenu lze použít ke sledování pohybu objektu skrz uvolňování paměti.|
|**IP2MD** \< *kód adresa*>|Zobrazí `MethodDesc` struktury na zadané adrese v kódu, který byl zkompilován JIT Kompilátorem.|
|`ListNearObj` (`lno`) *\<obj_address>*|Zobrazí objekty před a za zadanou adresou. Tento příkaz vyhledá adresu v haldě uvolňování paměti vypadající jako platný začátek spravovaného objektu (podle platné tabulky metod) a objekt následující za adresou argumentu.|
|**MinidumpMode** [**0**] [**1**]|Zabrání ve spuštění nebezpečných příkazů pomocí minimálního výpisu.<br /><br /> Předejte **0** chcete zakázat tuto funkci nebo **1** tuto funkci povolil. Ve výchozím nastavení **MinidumpMode** nastavena na hodnotu **0**.<br /><br /> Vytvořený pomocí **.dump /m** příkazu nebo **.dump** příkaz mají omezenou data specifická pro modul CLR a bylo možné správně spustit pouze podmnožinu příkazů SOS. Některé příkazy mohou selhat s neočekávanými chybami, jelikož požadované oblasti paměti nejsou zmapovány nebo jsou zmapovány pouze částečně. Tato možnost zabraňuje ve spuštění nebezpečných příkazů s minimálním výpisem.|
|**Name2EE** \< *název modulu*> \<*název typu nebo metodě*><br /><br /> -nebo-<br /><br /> **Name2EE** \< *název modulu*> **!** \< *název typu nebo metodě*>|Zobrazí `MethodTable` strukturu a `EEClass` strukturu pro zadaný typ nebo metodu v zadaném modulu.<br /><br /> Zadaný modul musí být načten v procesu.<br /><br /> K získání správného názvu typu, procházení s využitím modulu [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). Můžete také předat `*` jako modul parametr name vyhledat všechny načtené spravované moduly. *Název modulu* parametr může být také název ladicího programu pro modul, jako například `mscorlib` nebo `image00400000`.<br /><br /> Tento příkaz podporuje syntaxi ladicího programu Windows <`module`>`!`<`type`>. Typ musí být plně kvalifikovaný.|
|**ObjSize** [\<*adresy objektu*>] &#124; [ **-agregační**] [ **-stat**]|Zobrazí velikost zadaného objektu. Pokud nezadáte žádné parametry, **ObjSize** příkaz zobrazuje velikost všech objektů nalezených ve spravovaných vláknech, zobrazí všechny popisovače systému uvolňování paměti v procesu a sečte velikost všech objektů, na které odkazují tyto popisovače. **ObjSize** příkaz zahrnuje velikost všech podřízených objektů včetně objektu nadřazeného.<br /><br /> **-Agregační** možnost se dá použít ve spojení s **-stat** argument pro získání podrobného zobrazení typů, které stále začínají kořenem. S použitím **! dumpheap-stat** a **! objsize-aggregate - stat**, můžete určit, které objekty již nezačínají kořenem a diagnostikovat různé problémy s pamětí.|
|**PrintException** [ **-vnořené**] [ **-řádky**] [\<*adresa objektu výjimky*>]<br /><br /> -nebo-<br /><br /> **PE** [ **-vnořené**] [\<*adresa objektu výjimky*>]|Zobrazí a zformátuje pole jakéhokoli objektu odvozeného od <xref:System.Exception> třídy na zadané adrese. Pokud nezadáte adresu, **PrintException** příkaz zobrazí poslední vyvolanou výjimku u aktuálního vlákna.<br /><br /> **-Vnořené** možnost se zobrazí podrobnosti o objektech vnořených výjimek.<br /><br /> **-Řádky** možnost zobrazí informace o zdroji, pokud je k dispozici.<br /><br /> Můžete použít tento příkaz ke zformátování a zobrazení `_stackTrace` pole, což je binární pole.|
|**ProcInfo** [ **- env**] [ **– čas**] [ **– paměť**]|Zobrazí proměnné prostředí pro proces, čas jádra CPU a statistiky využití paměti.|
|**RCWCleanupList** \< *RCWCleanupList adresu*>|Zobrazí seznam obálek volatelných za běhu (RCW), které čekají na vyčištění, na zadané adrese.|
|**SaveModule** \< *základní adresa*> \<*název souboru*>|Zapíše bitovou kopii, která je načtena do paměti na zadané adrese, do zadaného souboru.|
|**SOSFlush**|Vyprázdní interní mezipaměť SOS.|
|**StopOnException** [ **-odvozené**] [ **– vytvořit** &#124; **-create2**] \< *výjimka* >  \< *Pseudoregistr číslo*>|Způsobí, že se ladicí program zastaví, pokud je vyvolána zadaná výjimka, ale bude pokračovat, pokud je vyvolána jiná výjimka.<br /><br /> **-Odvozené** možnost zachytí zadanou výjimku a každou výjimku odvozenou od zadané výjimky.|
|**SyncBlk** [ **-all** &#124; \<*syncblk number*>]|Zobrazí zadanou `SyncBlock` struktura nebo všechny `SyncBlock` struktury.  Pokud nepředáte žádné argumenty, **SyncBlk** příkaz zobrazí `SyncBlock` struktury odpovídající objektům, které jsou vláknem vlastněny.<br /><br /> A `SyncBlock` struktura je kontejner pro další informace, které nemusí být vytvořeny pro každý objekt. Může obsahovat data zprostředkovatele komunikace s objekty COM, hodnoty hash a informace o zamykání pro operace bezpečné pro přístup z více vláken.|
|**ThreadPool**|Zobrazí informace o spravovaném fondu vláken, včetně počtu pracovních požadavků ve frontě, počtu vláken portů dokončení a počtu časovačů.|
|**Name2ee** \< *název modulu*> \<*tokenu*>|Zadaná metadata se změní v zadaného modulu do tokenu `MethodTable` struktury nebo `MethodDesc` struktury.<br /><br /> Můžete předat `*` pro parametr názvu modulu najít, co tento token mapuje v každý načtený spravovaný modul. Můžete také předat název ladicího programu pro modul, jako například `mscorlib` nebo `image00400000`.|
|**Vlákna** [ **-live**] [ **-speciální**]|Zobrazí všechna spravovaná vlákna v procesu.<br /><br /> **Vlákna** příkaz zobrazí ladicí program zkrácené ID, ID vlákna modulu CLR a ID vlákna operačního systému.  Kromě toho **vlákna** příkaz zobrazí sloupec doména, která určuje doménu aplikace, ve kterém je vlákno prováděno, sloupec APT, který zobrazuje režim apartment modelu COM a sloupec výjimka, která zobrazuje poslední ve vlákně došlo k výjimce.<br /><br /> **-Live** možnost zobrazí vlákna asociovaná se živým vláknem.<br /><br /> **-Speciální** možnost zobrazí všechna speciální vlákna vytvořená modulem CLR. Mezi speciální vlákna patří vlákna uvolňování paměti (v současných a server uvolnění paměti), pomocná vlákna ladicího programu, finalizační vlákna, <xref:System.AppDomain> uvolnit vlákna a vlákna časovače fondu vláken.|
|**ThreadState \<**  *pole hodnoty stavu* **>**|Zobrazí stav vlákna. `value` Parametr je hodnota `State` pole **vlákna** výstupu sestavy.<br /><br /> Příklad:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [ **- xml**] \< *název souboru*>|Zapíše informace o haldě do zadaného souboru ve formátu srozumitelném pro profiler modulu CLR. **- Xml** možnost způsobí, že **TraverseHeap** příkaz, který zformátuje soubor jako XML.<br /><br /> Profiler CLR z si můžete stáhnout [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=67325).|
|**U** [ **- gcinfo**] [ **- ehinfo**] [ **- n**] \< *MethodDesc adresu*> &#124; \< *Kód adresa*>|Zobrazí komentovaný zpětný překlad spravované metody zadané buď `MethodDesc` ukazatelem struktury v případě metody nebo adresou kódu uvnitř těla metody. **U** příkaz zobrazí celou metodu od začátku do konce společně s poznámkami, které převedou tokeny metadat na názvy.<br /><br /> **- Gcinfo** možnost způsobí, že **U** příkazu můžete zobrazit `GCInfo` strukturu pro metodu.<br /><br /> **- Ehinfo** možnost zobrazí informace o výjimce pro metodu. Můžete také získat tyto informace se **EHInfo** příkazu.<br /><br /> **- N** možnost zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud má ladicí program zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. Můžete zadat **- n** možnost toto chování zakázat.|
|**VerifyHeap**|Zkontroluje, zda halda systému uvolňování paměti vykazuje známky poškození a zobrazí všechny nalezené chyby.<br /><br /> Poškození haldy může být způsobeno voláními vyvolání platformy, která nejsou správně vytvořena.|
|**VerifyObj** \< *adresy objektu*>|Zkontroluje, zda objekt, který je předán jako argument, jeví známky poškození.|
|**VMMap**|Projde prostor virtuálních adres a zobrazí typy ochran aplikované na jednotlivé oblasti.|
|**VMStat**|Poskytuje souhrnné zobrazení prostoru virtuálních adres, seřazených podle typů ochran aplikovaných na danou paměť (volná, rezervovaná, potvrzená, soukromá, mapovaná, bitová kopie). Sloupec TOTAL obsahuje hodnotu ze sloupce AVERAGE vynásobenou hodnotou ze sloupce BLK COUNT.|

## <a name="remarks"></a>Poznámky

Nástroj SOS Debugging Extension umožňuje zobrazit informace o kódu, který je spuštěn uvnitř modulu CLR. Nástroj SOS Debugging Extension lze například použít k zobrazení informací o spravované haldě, vyhledání poškození haldy, zobrazení vnitřních datových typů používaných modulem runtime a zobrazení informací o spravovaném kódu běžícím uvnitř modulu runtime.

Chcete-li použít nástroj SOS Debugging Extension v sadě Visual Studio, nainstalujte [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk). Informace o integrovaném ladicím prostředí v sadě Visual Studio najdete v tématu [ladicí prostředí](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package).

Můžete použít také nástroj SOS Debugging Extension do jeho načtením [ladicího programu WinDbg.exe](/windows-hardware/drivers/debugger/debugger-download-tools) a provádění příkazů v rámci WinDbg.exe.

K načtení nástroje SOS Debugging Extension do ladicího programu WinDbg.exe je třeba v tomto nástroji zadat následující příkaz:

```
.loadby sos clr
```

Nástroj WinDbg.exe i sada Visual Studio používají verzi knihovny SOS.dll odpovídající aktuálně používané verzi knihovny Mscorwks.dll. Ve výchozím nastavení by měla být použita verze knihovny SOS.dll, která odpovídá aktuální verzi knihovny Mscorwks.dll.

Pro zpracování souboru výpisu paměti vytvořeného na jiném počítači je třeba se ujistit, že soubor Mscorwks.dll, který byl distribuován s instalací, je v cestě k symbolům, a že je načtena odpovídající verze knihovny SOS.dll.

Pro načtení konkrétní verze knihovny SOS.dll je třeba do ladicího programu systému Windows zadat následující příkaz:

```
.load <full path to sos.dll>
```

## <a name="examples"></a>Příklady

Následující příkaz zobrazí obsah pole na adrese `00ad28d0`.  Zobrazí se druhý prvek a pět následujících.

```
!dumparray -start 2 -length 5 -detail 00ad28d0
```

Následující příkaz zobrazí obsah sestavení na adrese `1ca248`.

```
!dumpassembly 1ca248
```

Následující příkaz zobrazí informace o haldě systému uvolňování paměti.

```
!dumpheap
```

Následující příkaz zapíše obsah zátěžového protokolu z paměti do (výchozího) souboru s názvem StressLog.txt v aktuálním adresáři.

```
!DumpLog
```

Následující příkaz zobrazí `MethodDesc` struktury na adrese `902f40`.

```
!dumpmd 902f40
```

Následující příkaz zobrazí informace o modulu na adrese `1caa50`.

```
!dumpmodule 1caa50
```

Následující příkaz zobrazí informace o objektu na adrese `a79d40`.

```
!DumpObj a79d40
```

Následující příkaz zobrazí pole třídy hodnoty na adrese `00a79d9c` pomocí tabulky metod na adrese `0090320c`.

```
!DumpVC 0090320c 00a79d9c
```

Následující příkaz zobrazí paměť procesu využitou systémem uvolňování paměti.

```
!eeheap -gc
```

Následující příkaz zobrazí všechny objekty, které jsou naplánovány k dokončení.

```
!finalizequeue
```

Následující příkaz určuje doménu aplikace objektu na adrese `00a79d98`.

```
!findappdomain 00a79d98
```

Následující příkaz zobrazí všechny popisovače systému uvolňování paměti v aktuálním procesu.

```
!gcinfo 5b68dbb8
```

Následující příkaz zobrazí `MethodTable` a `EEClass` struktur `Main` metody ve třídě `MainClass` v modulu `unittest.exe`.

```
!name2ee unittest.exe MainClass.Main
```

Následující příkaz zobrazí informace o tokenu metadat na adrese `02000003` v modulu `unittest.exe`.

```
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
