---
title: SOS.dll (rozšíření ladění SOS)
description: Použijte SOS.dll ladicí rozšíření SOS. Ladění spravovaných programů v aplikaci Visual Studio a v WinDbg.exe získáním informací o interním prostředí CLR.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
ms.openlocfilehash: cc9fed8432b5b24c20c3c470a842895a901d9efb
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517175"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (rozšíření ladění SOS)

Rozšíření SOS Debugging Extension (SOS.dll) pomáhá ladit spravované programy v aplikaci Visual Studio a v ladicím programu systému Windows (WinDbg.exe) tím, že poskytuje informace o vnitřním prostředí modulu CLR (Common Language Runtime). Tento nástroj vyžaduje, aby měl projekt povoleno nespravované ladění. Knihovna SOS.dll je automaticky nainstalována společně s rozhraním .NET Framework. Chcete-li použít SOS.dll v sadě Visual Studio, nainstalujte [sadu Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

## <a name="syntax"></a>Syntax

```console
![command] [options]
```

## <a name="commands"></a>Příkazy

|Příkaz|Popis|
|-------------|-----------------|
|**AnalyzeOOM** (**Ao**)|Zobrazí informace pro poslední nedostatek paměti (OOM), k nimž došlo na žádosti o přidělení do haldy uvolňování paměti. (Při uvolňování paměti serveru se případná chyba v důsledku vyčerpání paměti (OOM) zobrazí u každé haldy uvolňování paměti zvlášť.)|
|**BPMD** [**-nofuturemodule**] [ \<*module name*> \<*method name*> ] [**-MD**  < `MethodDesc`>] **-list** **-clear** \<*pending breakpoint number*> **-ClearAll**|Vytvoří ve zvoleném modulu zarážku u určené metody.<br /><br /> Pokud nebyl načten zvolený modul ani metoda, počká tento příkaz na notifikaci, že byl modul načten a zkompilován za běhu (JIT) před vytvořením zarážky.<br /><br /> Seznam nevyřízených zarážek můžete spravovat pomocí možností **-list**, **-clear**a **-ClearAll** :<br /><br /> Možnost **-list** vygeneruje seznam všech nevyřízených zarážek. Pokud má čekající zarážka nenulovou hodnotu ID modulu, pak je tato zarážka určena pro konkrétní funkci v konkrétním načteném modulu. Pokud má čekající zarážka nulovou hodnotu ID modulu, pak je tato zarážka určena modulům, které ještě nebyly načteny.<br /><br /> K odebrání nevyřízených zarážek ze seznamu použijte možnost **-clear** nebo **-ClearAll** .|
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|Poskytne trasování zásobníku pouze pro spravovaný kód.<br /><br /> Možnost **-p** zobrazuje argumenty spravované funkce.<br /><br /> Možnost **-l** zobrazuje informace o místních proměnných v rámci rámečku. Rozšíření SOS Debugging nemůže načíst místní názvy, takže výstup pro místní názvy je ve formátu \<*local address*> **=** \<*value*> .<br /><br /> Možnost **-a**(vše) je zástupce pro kombinaci **-l** a **-p** .<br /><br /> Možnost **-n** zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. Pro zakázání tohoto chování lze zadat parametr **-n** (bez čísel řádků).<br /><br /> Nástroj SOS Debugging Extension nezobrazuje přechodné rámce pro platformy založené na architekturách x64 a IA-64.|
|**COMState**|Vypíše model Apartment modelu COM pro každé vlákno a `Context` ukazatel, pokud je k dispozici.|
|**DumpArray** [**-Start** \<*startIndex*> ] [**-Length** \<*length*> ] [**-Details**] [**--Fields**]\<*array object address*><br /><br /> -nebo-<br /><br /> **Da** [**-Start** \<*startIndex*> ] [**-Length** \<*length*> ] [**-Detail**] [**-nepole**] *Adresa objektu pole*>|Prozkoumá prvky objektu pole (typ array).<br /><br /> Možnost **-Start** Určuje počáteční index, pro který mají být zobrazeny prvky.<br /><br /> Možnost **-Length** určuje, kolik prvků se má zobrazit.<br /><br /> Možnost **-Details** zobrazí podrobnosti elementu pomocí formátů **DumpObj** a **DumpVC** .<br /><br /> Možnost **---Field** zabraňuje zobrazení polí. Tato možnost je k dispozici pouze v případě, že je zadána možnost **-Detail** .|
|**DumpAssembly**\<*assembly address*>|Zobrazí informace o sestavení.<br /><br /> Příkaz **DumpAssembly** vypíše více modulů, pokud existují.<br /><br /> Adresu sestavení můžete získat pomocí příkazu **DumpDomain** .|
|**DumpClass**\<*EEClass address*>|Zobrazí informace o `EEClass` struktuře přidružené k typu.<br /><br /> Příkaz **DumpClass** zobrazí statické hodnoty polí, ale nezobrazuje hodnoty nestatických polí.<br /><br /> K získání adresy struktury použijte příkaz **DumpMT**, **DumpObj**, **Name2EE**nebo **Token2EE** `EEClass` .|
|**DumpDomain** [ \<*domain address*> ]|Vytvoří výčet všech <xref:System.Reflection.Assembly> objektů, které jsou načteny v rámci zadané <xref:System.AppDomain> adresy objektu.  Při volání bez parametrů příkaz **DumpDomain** vypíše všechny <xref:System.AppDomain> objekty v procesu.|
|**Dumpheap** [**-stat**] [**-strings**] [**-short**] [**-min** \<*size*> ] [**-Max** \<*size*> ] [**-thinlock**] [**-startAtLowerBound**] [-**Mt** \<*MethodTable address*> ] [**-Type** \<*partial type name*> ] [*Start* [*End*]]|Zobrazí informace o haldě uvolnění paměti a statistiky uvolňování objektů.<br /><br /> Příkaz **dumpheap** zobrazí upozornění, pokud detekuje nadměrné fragmentace v haldě uvolňování paměti.<br /><br /> Možnost **-stat** omezuje výstup na souhrn statistických typů.<br /><br /> Možnost **-strings** omezí výstup na souhrn hodnot statistických řetězců.<br /><br /> Možnost **-short** omezí výstup na pouze adresu každého objektu. To umožňuje automatizovat snadným vytvořením kanálu pro výstup z příkazu do dalšího příkazu ladicího programu.<br /><br /> Možnost **-min** ignoruje objekty, které jsou menší než `size` parametr, zadaný v bajtech.<br /><br /> Možnost **-Max** ignoruje objekty, které jsou větší než `size` parametr, zadaný v bajtech.<br /><br /> Možnost **-thinlock** hlásí ThinLocks.  Další informace najdete v příkazu **SyncBlk** .<br /><br /> `-startAtLowerBound`Možnost vynutí, aby bylo procházení haldy zahájeno s dolní mezí zadaného rozsahu adres. Během fáze plánování často nelze haldu projít, jelikož je s objekty pohybováno. Tato možnost vynutí, aby **dumpheap** začínat svůj názor na určené dolní hranici. Aby tato možnost fungovala, je třeba zadat adresu platného objektu jako dolní mez. Na adrese chybného objektu lze zobrazit paměť a vyhledat další tabulky metody ručně. Pokud je uvolňování paměti momentálně v rámci volání `memcopy` , může být také možné najít adresu dalšího objektu přidáním velikosti ke spouštěcí adrese, která je zadána jako parametr.<br /><br /> Možnost **-Mt** vypíše pouze ty objekty, které odpovídají zadané `MethodTable` struktuře.<br /><br /> Možnost **-Type** vypíše pouze objekty, jejichž název typu je shoda podřetězce zadaného řetězce.<br /><br /> `start`Parametr zahájí výpis ze zadané adresy.<br /><br /> `end`Parametr zastaví výpis na zadané adrese.|
|**DumpIL** \<*Managed DynamicMethod object*> &#124; \<*DynamicMethodDesc pointer*> &#124;\<*MethodDesc pointer*>|Zobrazí kód v jazyce MSIL (Microsoft Intermediate Language) přidružený ke spravované metodě.<br /><br /> Dynamický kód jazyka MSIL je vysílán jinak, než kód jazyka MSIL, který je načten ze sestavení. Dynamický kód jazyka MSIL odkazuje spíše na objekty v poli spravovaných objektů, než na tokeny metadat.|
|**DumpLog** [**-addr** \<*addressOfStressLog*> ] [<*FILENAM* `e`>]|Zapíše obsah zátěžového protokolu uloženého v paměti do zadaného souboru. Pokud nebude název zadán, vytvoří příkaz v aktuálním adresáři soubor s názvem StressLog.txt.<br /><br /> Zátěžový protokol uložený v paměti pomáhá diagnostikovat zátěžová selhání bez pomoci zámků nebo vstupů a výstupů. Pokud chcete protokol zátěže povolit, nastavte v části HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft následující klíče registru \\ . NETFramework<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> Volitelná `-addr` možnost umožňuje zadat protokol zátěže jiný než výchozí protokol.|
|**DumpMD**\<*MethodDesc address*>|Zobrazí informace o `MethodDesc` struktuře na zadané adrese.<br /><br /> Pomocí příkazu **IP2MD** můžete získat `MethodDesc` adresu struktury ze spravované funkce.|
|**DumpMT** [**-MD**]\<*MethodTable address*>|Zobrazí informace o tabulce metod na zadané adrese. Zadáním možnosti **-MD** zobrazíte seznam všech metod definovaných s objektem.<br /><br /> Každý spravovaný objekt obsahuje ukazatel tabulky metod.|
|**DumpMethodSig** \<*sigaddr*> DumpMethodSig  < *moduleadd*`r`>|Zobrazí informace o `MethodSig` struktuře na zadané adrese.|
|**DumpModule** [**-Mt**]\<*Module address*>|Zobrazí informace o modulu na zadané adrese. Možnost **-Mt** zobrazí typy definované v modulu a typy, na které se odkazuje modul.<br /><br /> K načtení adresy modulu můžete použít příkaz **DumpDomain** nebo **DumpAssembly** .|
|**DumpObj** [**-žádná pole**]\<*object address*><br /><br /> -nebo-<br /><br /> **Do**\<*object address*>|Zobrazí informace o objektu na zadané adrese. Příkaz **DumpObj** zobrazí pole, `EEClass` informace o struktuře, tabulku metody a velikost objektu.<br /><br /> K načtení adresy objektu lze použít příkaz **DumpStackObjects** .<br /><br /> Všimněte si, že příkaz **DumpObj** lze spustit pro pole typu, `CLASS` protože jsou také objekty.<br /><br /> `-` **nofields** Možnost-Fields zabraňuje polím objektu, který je zobrazen, je užitečná pro objekty jako řetězec.|
|**DumpRuntimeTypes**|Zobrazí objekty typu runtime z haldy systému uvolňování paměti a vypíše názvy s nimi asociovaných typů a tabulky metod.|
|**Dumpstack** [**-EE**] [**-n**] [ `top` *Stack* [ `bottom` *zásobní* `k` ]]|Zobrazí trasování zásobníku.<br /><br /> Možnost **-EE** způsobí, že příkaz **dumpstack** zobrazí pouze spravované funkce. Pomocí `top` parametrů a `bottom` můžete omezit rámce zásobníku zobrazené na platformách x86.<br /><br /> Možnost **-n** zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. Pro zakázání tohoto chování lze zadat parametr **-n** (bez čísel řádků).<br /><br /> Na platformách x86 a x64 vytvoří příkaz **dumpstack** podrobné trasování zásobníku.<br /><br /> Na platformách založených na platformě IA-64 napodobuje příkaz **dumpstack** příkaz **k** ladicímu programu. `top`Parametry a `bottom` jsou ignorovány na platformách založených na platformě IA-64.|
|**DumpSig** \<*sigaddr*>\<*moduleaddr*>|Zobrazí informace o `Sig` struktuře na zadané adrese.|
|**DumpSigElem** \<*sigaddr*>\<*moduleaddr*>|Zobrazí jediný prvek objektu podpisu. Ve většině případů byste měli použít **DumpSig** k zobrazení jednotlivých objektů podpisu. Pokud je však podpis nějakým způsobem poškozen, můžete použít **DumpSigElem** ke čtení platných částí.|
|**DumpStackObjects** [**-verify**] [ `top` *zásobník* [ `bottom` *Stack*]]<br /><br /> -nebo-<br /><br /> **DSO** [**-verify**] [ `top` *zásobník* [ `bottom` *Stack*]]|Zobrazí všechny spravované objekty nalezené v rámci aktuálního zásobníku.<br /><br /> Možnost **-verify** ověří každé nestatické `CLASS` pole pole objektu.<br /><br /> Použijte příkaz **DumpStackObject** s příkazy pro trasování zásobníku, jako je například **k** a příkaz **CLRStack** , a určete tak hodnoty místních proměnných a parametrů.|
|**DumpVC** \<*MethodTable address*>\<*Address*>|Zobrazí informace o polích třídy hodnot na konkrétní adrese.<br /><br /> Parametr **metody** umožňuje příkazu **DumpVC** správně interpretovat pole. Třídy hodnot nemají jako první pole tabulku metod.|
|**EEHeap** [**-GC**] [**-Loader**]|Zobrazí informace o paměti procesu spotřebované interními datovými strukturami CLR.<br /><br /> Možnosti **-GC** a **-Loader** omezují výstup tohoto příkazu na datové struktury systému uvolňování paměti nebo zavaděče.<br /><br /> Informace pro systém uvolňování paměti obsahují rozsahy každého segmentu ve spravované haldě.  Pokud ukazatel spadá do rozsahu segmentu zadaného **-GC**, ukazatel je ukazatel na objekt.|
|**EEStack** [**-short**] [**-EE**]|Spustí příkaz **dumpstack** ve všech vláknech v procesu.<br /><br /> Možnost **-EE** je předána přímo příkazu **dumpstack** . Parametr **-short** omezuje výstup na následující typy vláken:<br /><br /> Vlákna, která byla uzamknuta.<br /><br /> Vlákna, která byla kvůli uvolňování paměti pozastavena.<br /><br /> Vlákna, která jsou aktuálně ve spravovaném kódu.|
|**EEVersion**|Zobrazí verzi modulu CLR.|
|**EHInfo** [ \<*MethodDesc address*> ] [ \<*Code address*> ]|Zobrazí bloky zpracování výjimek v zadané metodě.  Tento příkaz zobrazí adresy a posuny kódu pro blok klauzule ( `try` blok) a blok obslužné rutiny ( `catch` blok).|
|**Nejčastější dotazy**|Zobrazí nejčastější dotazy.|
|**FinalizeQueue** [**-Detail**] &#124; [**-allready**] [**-short**]|Zobrazí všechny objekty, které jsou registrovány pro dokončení.<br /><br /> Možnost **-Detail** zobrazí další informace `SyncBlocks` , které je třeba vyčistit, a všechny `RuntimeCallableWrappers` (RCW), které čekají na vyčištění. Obě tyto datové struktury jsou uloženy do mezipaměti a vyčištěny finalizačním vláknem při spuštění.<br /><br /> `-allReady`Možnost zobrazí všechny objekty, které jsou připraveny k dokončení, bez ohledu na to, zda jsou již uvolňováním paměti označeny jako takové, nebo bude označena dalším uvolňováním paměti. Objekty, které jsou na seznamu objektů připravených k dokončení, jsou dokončitelné objekty, které již nezačínají kořenem. Tato možnost může být velice nákladná, jelikož ověřuje, zda všechny objekty ve frontě dokončitelných objektů stále začínají kořenem.<br /><br /> `-short`Možnost omezí výstup na adresu každého objektu. Pokud se používá ve spojení s **-allready**, vytvoří výčet všech objektů, které mají finalizační metodu, která již není rootem. Pokud je použita nezávisle, vypíše všechny objekty ve frontách s dokončitelnými objekty a objekty připravenými k dokončení.|
|**FindAppDomain**\<*Object address*>|Určuje doménu aplikace objektu na zadané adrese.|
|**FindRoots** **-fin** \<*N*> &#124; **– fin any** &#124;\<*object address*>|Způsobí přerušení ladicího programu během ladění při dalším shromáždění zadané generace. Efekt se obnoví, jakmile dojde k přerušení. Pro přerušení dalšího shromažďování je třeba znovu zadat tento příkaz. *\<object address>* Tvar tohoto příkazu se používá po přerušení způsobené **-gen** nebo **-gen any** . V tomto okamžiku je laděného procesu ve správném stavu, aby **FindRoots** identifikoval kořeny pro objekty z aktuálních generací Condemned.|
|**GCHandles** [**-perdomain**]|Zobrazí statistické údaje o popisovačích systému uvolňování paměti v procesu.<br /><br /> Možnost **-perdomain** uspořádá statistiku podle aplikační domény.<br /><br /> Použijte příkaz **GCHandles** k vyhledání nevrácené paměti způsobené nevracením popisovačů uvolňování paměti. Neuvolnění paměti například nastane, když kód zachová velké pole, protože silný popisovač systému uvolňování paměti na něj stále ukazuje, zatímco je zrušen, aniž by bylo uvolněno pole.|
|**GCHandleLeaks**|Vyhledá v paměti jakékoli odkazy na silné a připojené popisovače systému uvolňování paměti v procesu a zobrazí výsledky. Pokud je nalezen popisovač, příkaz **GCHandleLeaks** zobrazí adresu odkazu. Pokud není popisovač v paměti nalezen, zobrazí tento příkaz upozornění.|
|**GCInfo**\<*MethodDesc address*>\<*Code address*>|Zobrazí data, která označují, kdy registry nebo umístění zásobníku obsahují spravované objekty. Pokud dojde k uvolnění paměti, musí uvolňovač vědět o umístění odkazů na objekty, aby je bylo možné aktualizovat novou hodnotou ukazatele na objekt.|
|**Gcroot** [**-instacks**]\<*Object address*>|Zobrazí informace o odkazech (nebo kořenech) na objekt na zadané adrese.<br /><br /> Příkaz **gcroot** prověřuje celou spravovanou haldu a tabulku popisovačů pro obslužné rutiny v rámci jiných objektů a popisovačů v zásobníku. Každý zásobník následně vyhledá ukazatele na objekty a rovněž je prohledána fronta finalizační metody.<br /><br /> Tento příkaz neurčuje, zda je kořen zásobníku platný nebo zrušený. Použijte příkazy **CLRStack** a **U** pro zpětný překlad rámce, ke kterému místní hodnota nebo hodnota argumentu patří, aby bylo možné zjistit, zda se kořen zásobníku stále používá.<br /><br /> Možnost **-instacks** omezuje hledání na popisovače systému uvolňování paměti a dosažitelné objekty.|
|**GCWhere**  *\<object address>*|Zobrazí umístění a velikost předaného argumentu v haldě uvolňování paměti. Pokud argument leží ve spravované haldě, ale není platnou adresou objektu, je zobrazena velikost 0 (nula).|
|**help** [ \<*command*> ] [ `faq` ]|Zobrazí všechny dostupné příkazy, pokud není zadán žádný parametr, nebo zobrazí detailní informace nápovědy o zadaném příkazu.<br /><br /> `faq`Parametr zobrazuje odpovědi na nejčastější dotazy.|
|**HeapStat** [**-inclUnrooted** &#124; **-IU**]|Zobrazí velikosti generací pro každou haldu a celkové volné místo v každé generaci v každé haldě. Pokud je zadána možnost-**inclUnrooted** , sestava obsahuje informace o spravovaných objektech z haldy uvolňování paměti, která již není rootem.|
|**HistClear**|Uvolňuje všechny prostředky, které používá rodina `Hist` příkazů.<br /><br /> Obecně není nutné explicitně volat `HistClear` , protože každá `HistInit` vyčistí předchozí prostředky.|
|**HistInit**|Inicializuje struktury SOS ze zátěžového protokolu uloženého v laděné položce.|
|**HistObj***\<obj_address>*|Zkontroluje všechny záznamy přemístění zátěžového protokolu a zobrazí řetězec přemísťování uvolňování paměti, který může vést na adresu předanou jako argument.|
|**HistObjFind**  *\<obj_address>*|Zobrazí všechny položky protokolu, které odkazují na objekt na zadané adrese.|
|**HistRoot***\<root>*|Zobrazí informace týkající se propagace a přemístění zadaného kořenu.<br /><br /> Hodnotu kořenu lze použít ke sledování pohybu objektu skrz uvolňování paměti.|
|**IP2MD**\<*Code address*>|Zobrazuje `MethodDesc` strukturu na zadané adrese v kódu, který byl ZKOMPILOVÁN JIT.|
|`ListNearObj` (`lno`) *\<obj_address>*|Zobrazí objekty před a za zadanou adresou. Tento příkaz vyhledá adresu v haldě uvolňování paměti vypadající jako platný začátek spravovaného objektu (podle platné tabulky metod) a objekt následující za adresou argumentu.|
|**MinidumpMode** [**0**] [**1**]|Zabrání ve spuštění nebezpečných příkazů pomocí minimálního výpisu.<br /><br /> Předejte **0** pro vypnutí této funkce nebo **1** pro povolení této funkce. Ve výchozím nastavení je hodnota **MinidumpMode** nastavena na **0**.<br /><br /> Mini výpisy vytvořené pomocí příkazu **. dump/m** nebo **výpisu. dump** mají omezená data specifická pro CLR a umožňují, aby se správně spouštěla pouze podmnožina příkazů SOS. Některé příkazy mohou selhat s neočekávanými chybami, jelikož požadované oblasti paměti nejsou zmapovány nebo jsou zmapovány pouze částečně. Tato možnost zabraňuje ve spuštění nebezpečných příkazů s minimálním výpisem.|
|**Name2EE** \<*module name*>\<*type or method name*><br /><br /> -nebo-<br /><br /> **Name2EE** \<*module name*> **!**\<*type or method name*>|Zobrazuje `MethodTable` strukturu a `EEClass` strukturu zadaného typu nebo metody v zadaném modulu.<br /><br /> Zadaný modul musí být načten v procesu.<br /><br /> Chcete-li získat správný název typu, procházejte modul pomocí [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md). Můžete také předat `*` jako parametr název modulu a vyhledat všechny načtené spravované moduly. Parametr *názvu modulu* může být také název ladicího programu pro modul, jako je například `mscorlib` nebo `image00400000` .<br /><br /> Tento příkaz podporuje syntaxi ladicího programu Windows <`module` > `!` < `type`>. Typ musí být plně kvalifikovaný.|
|**ObjSize** [ \<*Object address*> ] &#124; [**-Aggregate**] [**-stat**]|Zobrazí velikost zadaného objektu. Pokud nezadáte žádné parametry, příkaz **ObjSize** zobrazí velikost všech objektů nalezených ve spravovaných vláknech, zobrazí všechny popisovače systému uvolňování paměti v procesu a celková velikost všech objektů, na které odkazují tyto popisovače. Příkaz **ObjSize** zahrnuje velikost všech podřízených objektů kromě nadřazeného objektu.<br /><br /> Možnost **-Aggregate** lze použít společně s argumentem **-stat** pro získání podrobného zobrazení typů, které jsou stále rootované. Pomocí **! dumpheap-stat** a **! ObjSize-Aggregate-stat**můžete určit, které objekty již nejsou root a diagnostikovat různé problémy s pamětí.|
|**PrintException** [**-Nested**] [**-Lines**] [ \<*Exception object address*> ]<br /><br /> -nebo-<br /><br /> **PE** [**-Nested**] [ \<*Exception object address*> ]|Zobrazí a formátuje pole libovolného objektu odvozeného ze <xref:System.Exception> třídy na zadané adrese. Pokud nezadáte adresu, příkaz **PrintException** zobrazí poslední výjimku vyvolanou v aktuálním vlákně.<br /><br /> Možnost **-Nested** zobrazí podrobnosti o vnořených objektech výjimek.<br /><br /> Možnost **-Lines** zobrazí informace o zdroji, pokud je k dispozici.<br /><br /> Tento příkaz můžete použít k formátování a zobrazení `_stackTrace` pole, což je binární pole.|
|**ProcInfo** [**-ENV**] [**-Time**] [**-mem**]|Zobrazí proměnné prostředí pro proces, čas jádra CPU a statistiky využití paměti.|
|**RCWCleanupList**\<*RCWCleanupList address*>|Zobrazí seznam obálek volatelných za běhu (RCW), které čekají na vyčištění, na zadané adrese.|
|**SaveModule** \<*Base address*>\<*Filename*>|Zapíše bitovou kopii, která je načtena do paměti na zadané adrese, do zadaného souboru.|
|**SOSFlush**|Vyprázdní interní mezipaměť SOS.|
|**StopOnException** [**-Derived**] [**-Create** &#124; **-create2**] \<*Exception*>\<*Pseudo-register number*>|Způsobí, že se ladicí program zastaví, pokud je vyvolána zadaná výjimka, ale bude pokračovat, pokud je vyvolána jiná výjimka.<br /><br /> Možnost **-Derived** zachytí zadanou výjimku a všechny výjimky, které jsou odvozeny ze zadané výjimky.|
|**SyncBlk** [**-All** &#124; \<*syncblk number*> ]|Zobrazí zadanou `SyncBlock` strukturu nebo všechny `SyncBlock` struktury.  Pokud nepředáte žádné argumenty, příkaz **SyncBlk** zobrazí `SyncBlock` strukturu odpovídající objektům, které jsou vlastněny vláknem.<br /><br /> `SyncBlock`Struktura je kontejnerem pro další informace, které není nutné vytvořit pro každý objekt. Může obsahovat data zprostředkovatele komunikace s objekty COM, hodnoty hash a informace o zamykání pro operace bezpečné pro přístup z více vláken.|
|**ThreadPool**|Zobrazí informace o spravovaném fondu vláken, včetně počtu pracovních požadavků ve frontě, počtu vláken portů dokončení a počtu časovačů.|
|**Token2EE** \<*module name*>\<*token*>|Zapne zadaný token metadat v zadaném modulu do `MethodTable` struktury nebo `MethodDesc` struktury.<br /><br /> Můžete předat `*` za parametr název modulu, abyste zjistili, k čemu se token mapuje v každém načteném spravovaném modulu. Můžete také předat název ladicího programu pro modul, například `mscorlib` nebo `image00400000` .|
|**Vlákna** [**-Live**] [**-Special**]|Zobrazí všechna spravovaná vlákna v procesu.<br /><br /> Příkaz **Threads** zobrazí zkrácený identifikátor ladicího programu, ID vlákna CLR a ID vlákna operačního systému.  Kromě toho příkaz **Threads** zobrazí sloupec doména, který označuje doménu aplikace, ve které je vlákno spuštěno, sloupec apt, který zobrazuje režim Apartment modelu COM, a sloupec výjimky, který zobrazuje poslední vyvolanou výjimku ve vlákně.<br /><br /> Možnost **-Live** zobrazí vlákna přidružená k živému vláknu.<br /><br /> Možnost **-Special** zobrazí všechna speciální vlákna VYTVOŘENá modulem CLR. Speciální vlákna zahrnují vlákna uvolňování paměti (v souběžném a uvolňování paměti serveru), pomocná vlákna ladicího programu, vlákna finalizační metody, <xref:System.AppDomain> uvolnění vláken a vlákna časovače fondu vláken.|
|**ThreadState\<** *State value field* **>**|Zobrazí stav vlákna. `value`Parametr je hodnota `State` pole ve výstupu sestavy **vláken** .<br /><br /> Příklad:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [**-XML**]\<*filename*>|Zapíše informace o haldě do zadaného souboru ve formátu srozumitelném pro profiler modulu CLR. Možnost **-XML** způsobí, že příkaz **TraverseHeap** naformátuje soubor jako XML.<br /><br /> Profiler CLR si můžete stáhnout z webu [služby Stažení softwaru](https://go.microsoft.com/fwlink/?LinkID=67325).|
|**U** [**-GCInfo**] [**-EHInfo**] [**-n**] \<*MethodDesc address*> &#124;\<*Code address*>|Zobrazuje komentovaný zpětný překlad spravované metody zadané buď pomocí `MethodDesc` ukazatele struktury pro metodu, nebo pomocí adresy kódu v těle metody. Příkaz **U** zobrazí celou metodu od začátku do konce s poznámkami, které převádějí tokeny metadat na názvy.<br /><br /> Možnost **-GCInfo** způsobí, že příkaz **u** zobrazí `GCInfo` strukturu pro metodu.<br /><br /> Možnost **-EHInfo** zobrazí informace o výjimce pro metodu. Tyto informace můžete získat také pomocí příkazu **EHInfo** .<br /><br /> Možnost **-n** zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud má ladicí program zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. Pokud chcete toto chování zakázat, můžete zadat možnost **-n** .|
|**VerifyHeap**|Zkontroluje, zda halda systému uvolňování paměti vykazuje známky poškození a zobrazí všechny nalezené chyby.<br /><br /> Poškození haldy může být způsobeno voláními vyvolání platformy, která nejsou správně vytvořena.|
|**VerifyObj**\<*object address*>|Zkontroluje, zda objekt, který je předán jako argument, jeví známky poškození.|
|**VMMap**|Projde prostor virtuálních adres a zobrazí typy ochran aplikované na jednotlivé oblasti.|
|**VMStat**|Poskytuje souhrnné zobrazení prostoru virtuálních adres, seřazených podle typů ochran aplikovaných na danou paměť (volná, rezervovaná, potvrzená, soukromá, mapovaná, bitová kopie). Sloupec TOTAL obsahuje hodnotu ze sloupce AVERAGE vynásobenou hodnotou ze sloupce BLK COUNT.|

## <a name="remarks"></a>Poznámky

Rozšíření SOS Debugging umožňuje zobrazit informace o kódu, který je spuštěn v rámci CLR. Nástroj SOS Debugging Extension lze například použít k zobrazení informací o spravované haldě, vyhledání poškození haldy, zobrazení vnitřních datových typů používaných modulem runtime a zobrazení informací o spravovaném kódu běžícím uvnitř modulu runtime.

Chcete-li použít rozšíření ladění SOS v sadě Visual Studio, nainstalujte [sadu Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk). Informace o integrovaném ladicím prostředí v aplikaci Visual Studio naleznete v tématu [ladění prostředí](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package).

Můžete také použít rozšíření ladění SOS, a to tak, že ho načtete do [ladicího programuWinDbg.exe](/windows-hardware/drivers/debugger/debugger-download-tools) a spouštíte příkazy v rámci WinDbg.exe.

K načtení nástroje SOS Debugging Extension do ladicího programu WinDbg.exe je třeba v tomto nástroji zadat následující příkaz:

```console
.loadby sos clr
```

Nástroj WinDbg.exe i sada Visual Studio používají verzi knihovny SOS.dll odpovídající aktuálně používané verzi knihovny Mscorwks.dll. Ve výchozím nastavení by měla být použita verze knihovny SOS.dll, která odpovídá aktuální verzi knihovny Mscorwks.dll.

Pro zpracování souboru výpisu paměti vytvořeného na jiném počítači je třeba se ujistit, že soubor Mscorwks.dll, který byl distribuován s instalací, je v cestě k symbolům, a že je načtena odpovídající verze knihovny SOS.dll.

Pro načtení konkrétní verze knihovny SOS.dll je třeba do ladicího programu systému Windows zadat následující příkaz:

```console
.load <full path to sos.dll>
```

## <a name="examples"></a>Příklady

Následující příkaz zobrazí obsah pole na adrese `00ad28d0` .  Zobrazí se druhý prvek a pět následujících.

```console
!dumparray -start 2 -length 5 -detail 00ad28d0
```

Následující příkaz zobrazí obsah sestavení na adrese `1ca248` .

```console
!dumpassembly 1ca248
```

Následující příkaz zobrazí informace o haldě systému uvolňování paměti.

```console
!dumpheap
```

Následující příkaz zapíše obsah zátěžového protokolu z paměti do (výchozího) souboru s názvem StressLog.txt v aktuálním adresáři.

```console
!DumpLog
```

Následující příkaz zobrazí `MethodDesc` strukturu na adrese `902f40` .

```console
!dumpmd 902f40
```

Následující příkaz zobrazí informace o modulu na adrese `1caa50` .

```console
!dumpmodule 1caa50
```

Následující příkaz zobrazí informace o objektu na adrese `a79d40` .

```console
!DumpObj a79d40
```

Následující příkaz zobrazí pole hodnotové třídy na adrese `00a79d9c` pomocí tabulky metod na adrese `0090320c` .

```console
!DumpVC 0090320c 00a79d9c
```

Následující příkaz zobrazí paměť procesu využitou systémem uvolňování paměti.

```console
!eeheap -gc
```

Následující příkaz zobrazí všechny objekty, které jsou naplánovány k dokončení.

```console
!finalizequeue
```

Následující příkaz určuje doménu aplikace objektu na adrese `00a79d98` .

```console
!findappdomain 00a79d98
```

Následující příkaz zobrazí všechny popisovače systému uvolňování paměti v aktuálním procesu.

```console
!gcinfo 5b68dbb8
```

Následující příkaz zobrazí `MethodTable` `EEClass` struktury a pro `Main` metodu ve třídě `MainClass` v modulu `unittest.exe` .

```console
!name2ee unittest.exe MainClass.Main
```

Následující příkaz zobrazí informace o tokenu metadat na adrese `02000003` v modulu `unittest.exe` .

```console
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)
