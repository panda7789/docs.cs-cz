---
title: "SOS.dll (rozšíření ladění SOS)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
caps.latest.revision: "55"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: efdb4bec75d160acd212b763690bd7a473c35eed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (rozšíření ladění SOS)
Nástroj SOS Debugging Extension (SOS.dll) pomáhá při ladění spravovaných programů v sadě Visual Studio a v ladicím programu operačního systému Windows (WinDbg.exe) poskytováním informací o vnitřním prostředí modulu CLR (Common Language Runtime). Tento nástroj vyžaduje, aby měl projekt povoleno nespravované ladění. Knihovna SOS.dll je automaticky nainstalována společně s rozhraním .NET Framework. Chcete-li použít SOS.dll v sadě Visual Studio, nainstalujte [ovladač Kit WDK (Windows)](http://msdn.microsoft.com/windows/hardware/hh852362).  
  
> [!NOTE]
>  Pokud používáte [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], SOS.dll je podporována v ladicím programu systému Windows v sadě Visual Studio, ale ne v okně okamžitou v ladicím programu sady Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
![command] [options]   
```  
  
## <a name="commands"></a>Příkazy  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|**AnalyzeOOM** (**ao**)|Zobrazí informace o poslední chybě v důsledku vyčerpání paměti (OOM), k níž došlo během požadavku na přidělení na haldu uvolňování paměti. (Při uvolňování paměti serveru se případná chyba v důsledku vyčerpání paměti (OOM) zobrazí u každé haldy uvolňování paměti zvlášť.)|  
|**BPMD** [**- nofuturemodule**] [\<*název modulu*> \<*název metody*>] [**- MD** <`MethodDesc`>] **-seznamu** **-vymazat** \< *čekající na vyřízení zarážek číslo* >  **- clearall**|Vytvoří ve zvoleném modulu zarážku u určené metody.<br /><br /> Pokud nebyl načten zvolený modul ani metoda, počká tento příkaz na notifikaci, že byl modul načten a zkompilován za běhu (JIT) před vytvořením zarážky.<br /><br /> Seznam čekající na vyřízení zarážky můžete spravovat pomocí **-seznamu**, **-vymazat**, a **- clearall** možnosti:<br /><br /> **-Seznamu** možnost generuje seznam čekající zarážky. Pokud má čekající zarážka nenulovou hodnotu ID modulu, pak je tato zarážka určena pro konkrétní funkci v konkrétním načteném modulu. Pokud má čekající zarážka nulovou hodnotu ID modulu, pak je tato zarážka určena modulům, které ještě nebyly načteny.<br /><br /> Použití **-vymazat** nebo **- clearall** možnost odebrání čekající na vyřízení zarážky ze seznamu.|  
|**CLRStack** [**–**] [**-l**] [**-p**] [**-n**]|Poskytne trasování zásobníku pouze pro spravovaný kód.<br /><br /> **-P** možnost ukazuje argumenty, které mají spravované funkce.<br /><br /> **-L** možnost zobrazuje informace o místní proměnné v rámečku. Rozšíření ladění SOS nelze načíst názvy místní, tak, aby výstup pro místní názvy ve formátu \< *místní adresu* >   **=**  \< *hodnotu*>.<br /><br /> **–**Možnost (vše) je zkratkou pro **-l** a **-p**kombinaci.<br /><br /> **-n**  Možnost zakáže zobrazení názvy zdrojových souborů a čísla řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. **-n**  (Bez čísel řádků) může být zadán parametr chcete toto chování zakázat.<br /><br /> Nástroj SOS Debugging Extension nezobrazuje přechodné rámce pro platformy založené na architekturách x64 a IA-64.|  
|**COMState**|Uvádí modelu objektu apartment COM pro každé vlákno a `Context` ukazatele, pokud je k dispozici.|  
|**DumpArray** [**-start** \< *počáteční index*>] [**-délka** \< *délka*>] [**-podrobnosti**] [**- nofields**] \< *pole adresu objektu*><br /><br /> -nebo-<br /><br /> **DA** [**-start** \< *počáteční index*>] [**-délka** \< *délka*>] [**-podrobnosti**] [**- nofields**] *pole adresu objektu*>|Prozkoumá prvky objektu pole (typ array).<br /><br /> **-Start** možnost určuje počáteční index, kdy má být prvky zobrazení.<br /><br /> **-Délka** možnost určuje, kolik elementů k zobrazení.<br /><br /> **-Podrobnosti** možnost zobrazí podrobnosti o použití elementu **DumpObj** a **DumpVC** formáty.<br /><br /> **- Nofields** možnost zabrání zobrazení pole. Tato možnost je dostupná pouze tehdy, když **-podrobnosti** je zadána možnost.|  
|**DumpAssembly** \< *adresu sestavení*>|Zobrazí informace o sestavení.<br /><br /> **DumpAssembly** příkaz vypíše více modulů, pokud existují.<br /><br /> Můžete získat adresu sestavení pomocí **DumpDomain** příkaz.|  
|**DumpClass** \< *EEClass adresa*>|Zobrazí informace o `EEClass` struktura související s typem.<br /><br /> **DumpClass** příkaz zobrazí statické pole hodnot, ale nezobrazí nestatické pole hodnot.<br /><br /> Použití **DumpMT**, **DumpObj**, **Name2EE**, nebo **Token2EE** získat `EEClass` struktury adresu.|  
|**DumpDomain** [\<*adresu domény*>]|Vytvoří výčet každý <xref:System.Reflection.Assembly> objektu, který je načíst v rámci zadaného <xref:System.AppDomain> objektu adresu.  Při volání bez parametrů, **DumpDomain** příkaz vypíše všechny <xref:System.AppDomain> objekty v procesu.|  
|**DumpHeap** [**-stat**] [**-řetězce**] [**-krátký**] [**-min** \< *velikost*>] [**-max** \< *velikost*>] [**- thinlock**] [**- startAtLowerBound**] [**- mt** \< *MethodTable adresu*>] [**– typ** \< *název částečné typu*>] [*spustit* [*end*]]|Zobrazí informace o haldě uvolnění paměti a statistiky uvolňování objektů.<br /><br /> **DumpHeap** příkaz zobrazí upozornění, pokud zjistí nadměrné fragmentace v haldě uvolňování paměti.<br /><br /> **-Stat** možnost omezuje výstup souhrn statistické typu.<br /><br /> **-Řetězce** možnost omezuje výstup souhrnné statistické řetězcovou hodnotu.<br /><br /> **-Krátký** možnost omezuje výstup na adresu každého objektu. To umožňuje automatizovat snadným vytvořením kanálu pro výstup z příkazu do dalšího příkazu ladicího programu.<br /><br /> **-Min** možnost ignoruje objekty, které jsou menší než `size` parametr, zadaný v bajtech.<br /><br /> **-Max** možnost ignoruje objekty, které jsou větší než `size` parametr, zadaný v bajtech.<br /><br /> **- Thinlock** možnost sestavy ThinLocks.  Další informace najdete v tématu **SyncBlk** příkaz.<br /><br /> `-startAtLowerBound` Možnost způsobí, že procházení haldy má začít ve dolní mez rozsahu zadaná adresa. Během fáze plánování často nelze haldu projít, jelikož je s objekty pohybováno. Tato možnost způsobí **DumpHeap** zahájíte jeho procházení v zadané dolní mez. Aby tato možnost fungovala, je třeba zadat adresu platného objektu jako dolní mez. Na adrese chybného objektu lze zobrazit paměť a vyhledat další tabulky metody ručně. Pokud kolekce paměti aktuálně probíhá volání `memcopy`, je také možné najít adresu další objekt přidáním velikost na adresu spuštění, který je poskytnut jako parametr.<br /><br /> **- Mt** možnost zobrazí pouze ty objekty, které odpovídají zadané `MethodTable` struktura.<br /><br /> **– Typ** možnost zobrazí pouze ty objekty, jejichž název typu je nalezena shoda substring zadaného řetězce.<br /><br /> `start` Parametr začne výpis ze zadané adresy.<br /><br /> `end` Parametr zastaví výpis na zadané adrese.|  
|**DumpIL** \< *spravované DynamicMethod objekt*> &#124;       \< *DynamicMethodDesc ukazatel*> &#124;        \< *MethodDesc ukazatele*>|Zobrazí kód v jazyce MSIL (Microsoft Intermediate Language) přidružený ke spravované metodě.<br /><br /> Dynamický kód jazyka MSIL je vysílán jinak, než kód jazyka MSIL, který je načten ze sestavení. Dynamický kód jazyka MSIL odkazuje spíše na objekty v poli spravovaných objektů, než na tokeny metadat.|  
|**DumpLog** [**- addr** \< *addressOfStressLog*>] [<*Filenam*`e`>]|Zapíše obsah zátěžového protokolu uloženého v paměti do zadaného souboru. Pokud nebude název zadán, vytvoří příkaz v aktuálním adresáři soubor s názvem StressLog.txt.<br /><br /> Zátěžový protokol uložený v paměti pomáhá diagnostikovat zátěžová selhání bez pomoci zámků nebo vstupů a výstupů. Pokud chcete povolit protokol přízvuk, nastavte následující klíče registru pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> Volitelné `-addr` možnost umožňuje zadat přízvuk protokolu než výchozí protokolu.|  
|**DumpMD** \< *MethodDesc adresa*>|Zobrazí informace o `MethodDesc` struktura na zadané adrese.<br /><br /> Můžete použít **IP2MD** získat `MethodDesc` struktury adresu z spravované funkce.|  
|**DumpMT** [**-MD**] \< *MethodTable adresa*>|Zobrazí informace o tabulce metod na zadané adrese. Určení **-MD** možnost zobrazí seznam všech metod, které jsou definované pomocí objektu.<br /><br /> Každý spravovaný objekt obsahuje ukazatel tabulky metod.|  
|**DumpMethodSig** \< *sigaddr*><*moduleadd*`r`>|Zobrazí informace o `MethodSig` struktura na zadané adrese.|  
|**DumpModule** [**- mt**] \< *adresu modulu*>|Zobrazí informace o modulu na zadané adrese. **- Mt** možnost zobrazí typy definované v modulu a odkazovaných modulem typů<br /><br /> Můžete použít **DumpDomain** nebo **DumpAssembly** příkaz pro načtení modulu adresu.|  
|**DumpObj** [**- nofields**] \< *objektu adresa*><br /><br /> -nebo-<br /><br /> **PROVEĎTE** \< *objektu adresa*>|Zobrazí informace o objektu na zadané adrese. **DumpObj** příkaz zobrazí pole, `EEClass` struktury informace, v tabulce metoda a velikost objektu.<br /><br /> Můžete použít **DumpStackObjects** příkaz k načtení objektu adresu.<br /><br /> Všimněte si, že můžete spustit **DumpObj** na pole typu `CLASS` vzhledem k tomu, že jsou i objekty.<br /><br /> `-` **Nofields** možnost brání pole objektu se zobrazí, je vhodné pro objekty jako řetězec.|  
|**DumpRuntimeTypes**|Zobrazí objekty typu runtime z haldy systému uvolňování paměti a vypíše názvy s nimi asociovaných typů a tabulky metod.|  
|**DumpStack** [**- EE**] [**-n**] [`top` *zásobníku* [`bottom` *stac* `k`]]|Zobrazí trasování zásobníku.<br /><br /> **- EE** možnost příčiny **DumpStack** příkaz k zobrazení pouze spravované funkce. Použití `top` a `bottom` parametry omezit rámce zásobníku zobrazí na x86 platformy.<br /><br /> **-n**  Možnost zakáže zobrazení názvy zdrojových souborů a čísla řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. **-n**  (Bez čísel řádků) může být zadán parametr chcete toto chování zakázat.<br /><br /> Na platformách x86 a x64 **DumpStack** příkaz vytvoří trasování verbose zásobníku.<br /><br /> Na platformách platformu IA-64 **DumpStack** příkaz napodobuje ladicího programu **tisíc** příkaz. `top` a `bottom` parametry jsou ignorovány na platformách platformu IA-64.|  
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|Zobrazí informace o `Sig` struktura na zadané adrese.|  
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Zobrazí jediný prvek objektu podpisu. Ve většině případů byste měli použít **DumpSig** podívat se na podpis jednotlivých objektů. Ale pokud podpis je poškozeno nějakým způsobem, můžete použít **DumpSigElem** číst platný části ho.|  
|**DumpStackObjects** [**-ověřte**] [`top` *zásobníku* [`bottom` *zásobníku*]]<br /><br /> -nebo-<br /><br /> **DSO** [**-ověřte**] [`top` *zásobníku* [`bottom` *zásobníku*]]|Zobrazí všechny spravované objekty nalezené v rámci aktuálního zásobníku.<br /><br /> **-Ověřte** možnost ověří každý nestatické `CLASS` pole pole objektu.<br /><br /> Použití **DumpStackObject** příkaz pomocí příkazů trasování zásobníku, jako **tisíc** příkaz a **CLRStack** příkaz, abyste zjistili hodnoty místní proměnné a Parametry.|  
|**DumpVC** \< *MethodTable adresu*> \<*adresa*>|Zobrazí informace o polích třídy hodnot na konkrétní adrese.<br /><br /> **MethodTable** parametr umožňuje **DumpVC** příkaz správně interpretovat pole. Třídy hodnot nemají jako první pole tabulku metod.|  
|**EEHeap** [**-gc**] [**– loader**]|Zobrazí informace o paměti procesu spotřebované vnitřními datovými strukturami modulu CLR.<br /><br /> **-Gc** a **– loader** možnosti omezit výstup tohoto příkazu na systém uvolňování paměti nebo zavaděč datové struktury.<br /><br /> Informace pro systém uvolňování paměti obsahují rozsahy každého segmentu ve spravované haldě.  Pokud ukazatele spadá do rozsahu segment poskytují **-gc**, ukazatele je ukazatel objektu.|  
|**EEStack** [**-krátký**] [**- EE**]|Spustí **DumpStack** na všechna vlákna v procesu.<br /><br /> **- EE** možnost předaný přímo na **DumpStack** příkaz. **-Krátký** parametr omezuje výstup na následující typy vláken:<br /><br /> Vlákna, která byla uzamknuta.<br /><br /> Vlákna, která byla kvůli uvolňování paměti pozastavena.<br /><br /> Vlákna, která jsou aktuálně ve spravovaném kódu.|  
|**EEVersion**|Zobrazí verzi modulu CLR.|  
|**EHInfo** [\<*MethodDesc adresu*>] [\<*kód adresa*>]|Zobrazí bloky zpracování výjimek v zadané metodě.  Tento příkaz zobrazí kód adresy a posunutí pro klauzuli bloku ( `try` blok) a zároveň se zablokují obslužné rutiny ( `catch` bloku).|  
|**NEJČASTĚJŠÍ DOTAZY**|Zobrazí nejčastější dotazy.|  
|**FinalizeQueue** [**-podrobnosti**] &#124; [**- allReady**] [**-krátký**]|Zobrazí všechny objekty, které jsou registrovány pro dokončení.<br /><br /> **-Podrobnosti** možnost zobrazí další informace o všech `SyncBlocks` kterém musí být vyčištěna a všechny `RuntimeCallableWrappers` (RCWs), await čištění. Obě tyto datové struktury jsou uloženy do mezipaměti a vyčištěny finalizačním vláknem při spuštění.<br /><br /> `-allReady` Možnost zobrazí všechny objekty, které jsou připravené pro dokončení, bez ohledu na to, zda jsou již označeny jako nové kolekce paměti, nebo budou označeny další uvolnění paměti. Objekty, které jsou na seznamu objektů připravených k dokončení, jsou dokončitelné objekty, které již nezačínají kořenem. Tato možnost může být velice nákladná, jelikož ověřuje, zda všechny objekty ve frontě dokončitelných objektů stále začínají kořenem.<br /><br /> `-short` Možnost omezuje výstup na adresu každého objektu. Pokud se používá ve spojení s **- allReady**, se zobrazí všechny objekty s finalizační metody, které jsou již root. Pokud je použita nezávisle, vypíše všechny objekty ve frontách s dokončitelnými objekty a objekty připravenými k dokončení.|  
|**FindAppDomain** \< *objektu adresa*>|Určuje doménu aplikace objektu na zadané adrese.|  
|**FindRoots** **-gen** \< *N*> &#124; **-fin žádné** &#124;\< *objektu adresa*>|Způsobí přerušení ladicího programu během ladění při dalším shromáždění zadané generace. Efekt se obnoví, jakmile dojde k přerušení. Pro přerušení dalšího shromažďování je třeba znovu zadat tento příkaz. *\<Objektu adresa >* formu tento příkaz slouží po přerušení způsobené **-generace** nebo **-fin žádné** došlo k chybě. V té době ladění je v pravém stavu pro **FindRoots** k identifikaci kořeny pro objekty z aktuální odsoudila generace.|  
|**GCHandles** [**- perdomain**]|Zobrazí statistické údaje o popisovačích systému uvolňování paměti v procesu.<br /><br /> **- Perdomain** možnost uspořádá statistik pro doménu aplikace.<br /><br /> Použití **GCHandles** příkazu najděte nevracení paměti způsobené nevracení popisovač systém uvolňování paměti. Neuvolnění paměti například nastane, když kód zachová velké pole, protože silný popisovač systému uvolňování paměti na něj stále ukazuje, zatímco je zrušen, aniž by bylo uvolněno pole.|  
|**GCHandleLeaks**|Vyhledá v paměti jakékoli odkazy na silné a připojené popisovače systému uvolňování paměti v procesu a zobrazí výsledky. Pokud je nalezen popisovač, **GCHandleLeaks** příkaz zobrazí adresu odkazu. Pokud není popisovač v paměti nalezen, zobrazí tento příkaz upozornění.|  
|**GCInfo** \< *MethodDesc adresu*>\<*kód adresa*>|Zobrazí data, která označují, kdy registry nebo umístění zásobníku obsahují spravované objekty. Pokud dojde k uvolnění paměti, musí uvolňovač vědět o umístění odkazů na objekty, aby je bylo možné aktualizovat novou hodnotou ukazatele na objekt.|  
|**GCRoot** [**- nostacks**] \< *objektu adresa*>|Zobrazí informace o odkazech (nebo kořenech) na objekt na zadané adrese.<br /><br /> **GCRoot** příkaz prozkoumá celý spravovaná halda a v tabulce popisovač obslužné rutiny v rámci jiné objekty a zpracovává v zásobníku. Každý zásobník následně vyhledá ukazatele na objekty a rovněž je prohledána fronta finalizační metody.<br /><br /> Tento příkaz neurčuje, zda je kořen zásobníku platný nebo zrušený. Použít **CLRStack** a **U** příkazů pro převod ze strojového kódu rámce, který hodnotu místní nebo argument patří Chcete-li určit, zda kořenový zásobníku je stále používáno.<br /><br /> **- Nostacks** možnost omezí vyhledávání popisovače systém uvolňování paměti a freachable objekty.|  
|**GCWhere***\<objektu adresa >* |Zobrazí umístění a velikost předaného argumentu v haldě uvolňování paměti. Pokud argument leží ve spravované haldě, ale není platnou adresou objektu, je zobrazena velikost 0 (nula).|  
|**pomůže** [\<*příkaz*>] [`faq`]|Zobrazí všechny dostupné příkazy, pokud není zadán žádný parametr, nebo zobrazí detailní informace nápovědy o zadaném příkazu.<br /><br /> `faq` , Zobrazí se odpovědi na nejčastější dotazy.|  
|**HeapStat** [**- inclUnrooted** &#124; **-iu**]|Zobrazí velikosti generací pro každou haldu a celkové volné místo v každé generaci v každé haldě. Pokud-**inclUnrooted** je zadána možnost, sestava obsahuje informace o spravovaných objektech z paměti haldy kolekce, který je už root.|  
|**HistClear**|Uvolní všechny prostředky využívané třídou řadu `Hist` příkazy.<br /><br /> Obecně platí, není nutné explicitně volání `HistClear`, protože každý `HistInit` vyčistí předchozí prostředky.|  
|**HistInit**|Inicializuje struktury SOS ze zátěžového protokolu uloženého v laděné položce.|  
|**HistObj** *< obj_address >*|Zkontroluje všechny záznamy přemístění zátěžového protokolu a zobrazí řetězec přemísťování uvolňování paměti, který může vést na adresu předanou jako argument.|  
|**HistObjFind***< obj_address >* |Zobrazí všechny položky protokolu, které odkazují na objekt na zadané adrese.|  
|**HistRoot**  *\<kořenové >*|Zobrazí informace týkající se propagace a přemístění zadaného kořenu.<br /><br /> Hodnotu kořenu lze použít ke sledování pohybu objektu skrz uvolňování paměti.|  
|**IP2MD** \< *kód adresa*>|Zobrazí `MethodDesc` struktura na zadané adrese v kódu, které bylo kompilováno za běhu.|  
|`ListNearObj`(`lno`) *< obj_address >*|Zobrazí objekty před a za zadanou adresou. Tento příkaz vyhledá adresu v haldě uvolňování paměti vypadající jako platný začátek spravovaného objektu (podle platné tabulky metod) a objekt následující za adresou argumentu.|  
|**MinidumpMode** [**0**] [**1**]|Zabrání ve spuštění nebezpečných příkazů pomocí minimálního výpisu.<br /><br /> Předat **0** tuto funkci zakázat nebo **1** tuto funkci povolíte. Ve výchozím nastavení **MinidumpMode** nastavena na hodnotu **0**.<br /><br /> Minimálním výpisem vytvořené pomocí **.dump /m** příkaz nebo **.dump** příkaz mají omezenou CLR specifických dat a umožňuje spouštět pouze podmnožinu SOS příkazy správně. Některé příkazy mohou selhat s neočekávanými chybami, jelikož požadované oblasti paměti nejsou zmapovány nebo jsou zmapovány pouze částečně. Tato možnost zabraňuje ve spuštění nebezpečných příkazů s minimálním výpisem.|  
|**Name2EE** \< *název modulu*> \<*typ nebo metoda název*><br /><br /> -nebo-<br /><br /> **Name2EE** \< *název modulu*>**!** \< *typ nebo metoda název*>|Zobrazí `MethodTable` struktura a `EEClass` strukturu pro zadaný typ nebo metoda v zadaný modul.<br /><br /> Zadaný modul musí být načten v procesu.<br /><br /> Získat název správné typu, vyhledejte modul pomocí [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). Můžete také předat `*` jako modul načíst název parametru pro vyhledávání všech spravované moduly. *Název modulu* parametr může být také ladicí program na název modulu, například `mscorlib` nebo `image00400000`.<br /><br /> Tento příkaz podporuje syntaxi ladicí program Windows <`module`>`!`<`type`>. Typ musí být plně kvalifikovaný.|  
|**ObjSize** [\<*objektu adresu*>] &#124; [**-agregační**] [**-stat**]|Zobrazí velikost zadaného objektu. Pokud nezadáte žádné parametry, **ObjSize** příkaz zobrazí velikost všech objektů na spravovaná vlákna nalezena, zobrazí všechny popisovače systém uvolňování paměti v procesu a celkový počet zpracovaných položek velikost všechny objekty ukazující na těchto obslužných rutin. **ObjSize** příkaz obsahuje velikost všechny podřízené objekty kromě nadřazený.<br /><br /> **-Agregační** možnost lze použít ve spojení s **-stat** argument získat podrobné zobrazení typů, které jsou stále root. Pomocí **! dumpheap-stat** a **! objsize-agregovat - Statistika**, můžete určit, které objekty jsou už root a diagnostikovat problémy různé paměti.|  
|**PrintException** [**-vnořené**] [**-řádky**] [\<*adresa objekt výjimky*>]<br /><br /> -nebo-<br /><br /> **PE** [**-vnořené**] [\<*adresa objekt výjimky*>]|Zobrazí a formáty polí libovolného objektu odvozeného z <xref:System.Exception> třída na zadané adrese. Pokud nezadáte adresu, **PrintException** příkaz zobrazí poslední výjimky na aktuální vlákno.<br /><br /> **-Vnořené** možnost zobrazí podrobnosti o objektech vnořené výjimce.<br /><br /> **-Řádky** možnost zobrazí informace o zdroji, pokud je k dispozici.<br /><br /> Můžete použít tento příkaz pro formátování a zobrazení `_stackTrace` pole, což je binární pole.|  
|**ProcInfo** [**- env**] [**-čas**] [**-mem**]|Zobrazí proměnné prostředí pro proces, čas jádra CPU a statistiky využití paměti.|  
|**RCWCleanupList** \< *RCWCleanupList adresa*>|Zobrazí seznam obálek volatelných za běhu (RCW), které čekají na vyčištění, na zadané adrese.|  
|**SaveModule** \< *základní adresa*> \<*Filename*>|Zapíše bitovou kopii, která je načtena do paměti na zadané adrese, do zadaného souboru.|  
|**SOSFlush**|Vyprázdní interní mezipaměť SOS.|  
|**StopOnException** [**-odvozené**] [**-vytvořit** &#124; **-create2**] \< *výjimka*> \<*číslo pseudo registrace*>|Způsobí, že se ladicí program zastaví, pokud je vyvolána zadaná výjimka, ale bude pokračovat, pokud je vyvolána jiná výjimka.<br /><br /> **-Odvozené** možnost zachytí zadané výjimky a každý výjimka, která je odvozena z zadanou výjimkou.|  
|**SyncBlk** [**– všechny** &#124; \< *syncblk číslo*>]|Zobrazí zadané `SyncBlock` struktura nebo všechny `SyncBlock` struktury.  Pokud všechny argumenty nepředávejte **SyncBlk** příkaz zobrazí `SyncBlock` struktura odpovídající objekty, které jsou vlastněny vlákna.<br /><br /> A `SyncBlock` struktura je kontejner pro další informace, které není potřeba vytvářet pro každý objekt. Může obsahovat data zprostředkovatele komunikace s objekty COM, hodnoty hash a informace o zamykání pro operace bezpečné pro přístup z více vláken.|  
|**Fondu**|Zobrazí informace o spravovaném fondu vláken, včetně počtu pracovních požadavků ve frontě, počtu vláken portů dokončení a počtu časovačů.|  
|**Token2EE** \< *název modulu*> \<*tokenu*>|Zadaná metadata se změní v zadaný modul do tokenu `MethodTable` struktura nebo `MethodDesc` struktury.<br /><br /> Abyste mohli předávat `*` pro parametr název modulu najít, co tento token mapuje v každé načíst spravovaný modul. Můžete také předat název ladicího programu pro modul, jako například `mscorlib` nebo `image00400000`.|  
|**Vlákna** [**-live**] [**-speciální**]|Zobrazí všechna spravovaná vlákna v procesu.<br /><br /> **Vláken** příkaz zobrazí ladicího programu sdružená ID, běžné ID vlákna modulu runtime jazyka a ID vlákna operačního systému  Kromě toho **vláken** příkaz zobrazí sloupec domény, který určuje doménu aplikace, ve kterém je prováděna vlákno, VÝSTIŽNÝ sloupce, který zobrazí režim apartment COM a sloupec výjimka, který zobrazí poslední ve vláknu došlo k výjimce.<br /><br /> **-Live** možnost zobrazí vláken spojené s vláknem za provozu.<br /><br /> **-Speciální** možnost zobrazí všechny speciální vláken vytvořené modulu CLR. Speciální vláken obsahovat vláken kolekce paměti (v uvolňování paměti souběžných a server), pomocné rutiny vláken ladicí program, finalizační metodu vláken <xref:System.AppDomain> uvolnit a podprocesy z fondu podprocesů časovače vláken.|  
|**ThreadState \<**  *pole hodnota stavu***>**|Zobrazí stav vlákna. `value` Je hodnota parametru `State` pole **vláken** sestavy výstup.<br /><br /> Příklad:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|  
|**TraverseHeap** [**- xml**] \< *filename*>|Zapíše informace o haldě do zadaného souboru ve formátu srozumitelném pro profiler modulu CLR. **- Xml** možnost příčiny **TraverseHeap** příkaz k formátování souboru ve formátu XML.<br /><br /> Si můžete stáhnout z profileru CLR [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=67325).|  
|**U** [**- gcinfo**] [**- ehinfo**] [**-n**] \< *MethodDesc adresu*> & # 124; \< *Kód adresa*>|Zobrazí poznámkami zpětný překlad spravované metody zadaný buď `MethodDesc` struktura ukazatele pro metodu nebo adresu kódu v těle metoda. **U** příkaz zobrazí metodu celou od začátku do konce s poznámky, které převést tokenů metadat na názvy.<br /><br /> **- Gcinfo** možnost příčiny **U** příkazu pro zobrazení `GCInfo` strukturu pro metodu.<br /><br /> **- Ehinfo** možnost zobrazí informace o výjimce pro metodu. Můžete také získat tyto informace se **EHInfo** příkaz.<br /><br /> **-n**  Možnost zakáže zobrazení názvy zdrojových souborů a čísla řádků. Pokud má ladicí program zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. Můžete zadat  **-n**  možnost toto chování zakázat.|  
|**VerifyHeap**|Zkontroluje, zda halda systému uvolňování paměti vykazuje známky poškození a zobrazí všechny nalezené chyby.<br /><br /> Poškození haldy může být způsobeno voláními vyvolání platformy, která nejsou správně vytvořena.|  
|**VerifyObj** \< *objektu adresa*>|Zkontroluje, zda objekt, který je předán jako argument, jeví známky poškození.|  
|**VMMap**|Projde prostor virtuálních adres a zobrazí typy ochran aplikované na jednotlivé oblasti.|  
|**VMStat**|Poskytuje souhrnné zobrazení prostoru virtuálních adres, seřazených podle typů ochran aplikovaných na danou paměť (volná, rezervovaná, potvrzená, soukromá, mapovaná, bitová kopie). Sloupec TOTAL obsahuje hodnotu ze sloupce AVERAGE vynásobenou hodnotou ze sloupce BLK COUNT.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj SOS Debugging Extension umožňuje zobrazit informace o kódu, který je spuštěn uvnitř modulu CLR. Nástroj SOS Debugging Extension lze například použít k zobrazení informací o spravované haldě, vyhledání poškození haldy, zobrazení vnitřních datových typů používaných modulem runtime a zobrazení informací o spravovaném kódu běžícím uvnitř modulu runtime.  
  
 Pokud chcete používat rozšíření ladění SOS v sadě Visual Studio, nainstalujte [ovladač Kit WDK (Windows)](http://msdn.microsoft.com/windows/hardware/hh852362). Informace o ladění integrované prostředí v sadě Visual Studio najdete v tématu [ladění prostředí](http://msdn.microsoft.com/library/windows/hardware/hh406268.aspx) ve službě Windows Dev Center.  
  
 Můžete také použít rozšíření ladění SOS načtením ladicího WinDbg.exe, která je k dispozici z [webu WDK a nástroje pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=103787)a provádění příkazů v rámci WinDbg.exe.  
  
 K načtení nástroje SOS Debugging Extension do ladicího programu WinDbg.exe je třeba v tomto nástroji zadat následující příkaz:  
  
```  
.loadby sos clr  
```  
  
 Nástroj WinDbg.exe i sada Visual Studio používají verzi knihovny SOS.dll odpovídající aktuálně používané verzi knihovny Mscorwks.dll. U verzí rozhraní .NET Framework 1.1 a 2.0 je knihovna SOS.dll nainstalována do stejného adresáře jako knihovna Mscorwks.dll. Ve výchozím nastavení by měla být použita verze knihovny SOS.dll, která odpovídá aktuální verzi knihovny Mscorwks.dll.  
  
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
  
 Následující příkaz zobrazí `MethodDesc` struktura na adrese `902f40`.  
  
```  
!dumpmd 902f40  
```  
  
 Následující příkaz zobrazí informace o modulu na adrese `1caa50`.  
  
```  
!dumpmodule 1caa50  
```  
  
 Následující příkaz zobrazí informace o objekt na adrese `a79d40`.  
  
```  
!DumpObj a79d40  
```  
  
 Následující příkaz zobrazí pole – hodnotová třída na adrese `00a79d9c` pomocí tabulky metoda na adrese `0090320c`.  
  
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
  
 Následující příkaz určuje doménu aplikace, které objektu na adrese `00a79d98`.  
  
```  
!findappdomain 00a79d98  
```  
  
 Následující příkaz zobrazí všechny popisovače systému uvolňování paměti v aktuálním procesu.  
  
```  
!gcinfo 5b68dbb8   
```  
  
 Následující příkaz zobrazí `MethodTable` a `EEClass` struktury pro `Main` metodu v třídě `MainClass` v modulu `unittest.exe`.  
  
```  
!name2ee unittest.exe MainClass.Main  
```  
  
 Následující příkaz zobrazí informace o tokenu metadata na adrese `02000003` v modulu `unittest.exe`.  
  
```  
!token2ee unittest.exe 02000003  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
