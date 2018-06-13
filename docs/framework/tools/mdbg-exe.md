---
title: MDbg.exe (ladicí program z příkazového řádku .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be32659a270cd7c6b7e3551594934926eabf0d31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399766"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (ladicí program z příkazového řádku .NET Framework)
Aplikace .NET Framework Command-Line Debugger pomáhá výrobcům nástrojů a vývojářům aplikací najít a opravit chyby v programech, které využívají .NET Framework Common Language Runtime. Tento nástroj používá API ladění za běhu k poskytování služeb ladění. Pomocí MDbg.exe můžete ladit pouze spravovaný kód; ladění nespravovaného kódu není podporováno.  
  
 Tento nástroj je k dispozici prostřednictvím balíčku NuGet. Informace o instalaci, najdete v části [MDbg 0.1.0](http://www.nuget.org/packages/MDbg/0.1.0). Chcete-li spustit nástroj, pomocí konzoly Správce balíčků. Pro další informace o tom, jak použít konzolu Správce balíčků, najdete v části [pomocí konzoly Správce balíčků](http://docs.nuget.org/docs/start-here/Using-the-Package-Manager-Console).  
  
 Do příkazového řádku Správce balíčků zadejte následující příkaz:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Příkazy  
 Když jsou v ladicím programu (označené **mdbg >** řádku), zadejte jeden z příkazů popsané v následující části:  
  
 **příkaz** [*argumenty*]  
  
 Příkazy MDbg.exe rozlišují velká a malá písmena.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|**Asie a Tichomoří**[**zpracovat**] [*číslo*]|Přepne na jiný laděný proces nebo vypíše dostupné procesy. Čísla nejsou skutečnými ID procesů (PID), ale seznam indexovaný od 0.|  
|**a**[**připojit**] [*pid*]|Připojí se k procesu nebo vytiskne dostupné procesy.|  
|**b**[**binárními**] [*ClassName.Method* &#124; *FileName:LineNo*]|Nastaví zarážku v zadané metodě. Moduly jsou prohledávány postupně.<br /><br /> -   **rozdělení** *FileName:LineNo* nastaví zarážky v umístění ve zdroji.<br />-   **rozdělení** *~ číslo* Nastaví zarážku na symbol nedávno zobrazí **x** příkaz.<br />-   **rozdělení** *modulu! ClassName.Method+IlOffset* Nastaví zarážku na plně kvalifikovaný umístění.|  
|**blok**[**ingObjects**]|Zobrazí zámky monitoru, které blokují vlákna.|  
|**certifikační autority**[**t**] [*exceptionType*]|Způsobí, že se ladicí program přeruší na všech výjimkách a nejen na neošetřených výjimkách.|  
|**cl**[**earException**]|Označí aktuální výjimku jako ošetřenou, takže provádění může pokračovat. Pokud příčina chyby nebyla odstraněna, výjimka se může rychle objevit znovu.|  
|**conf**[**Ign**] [*hodnota možnosti*]|Zobrazí všechny konfigurovatelné parametry a ukazuje, jak jsou parametry vyvolány bez jakékoli volitelné hodnoty. Pokud je zadána možnost, nastaví `value` jako aktuální možnost. V současné době jsou k dispozici následující možnosti:<br /><br /> -   `extpath` Nastaví cestu k vyhledání pro rozšíření, když `load` pomocí příkazu.<br />-   `extpath+` přidá cestu pro načítání rozšíření.|  
|**del**[**ete**]|Odstraní zarážku.|  
|**de**[**tach**]|Odpojí se od laděného procesu.|  
|**d**[**vlastní**] [*rámce*]|Přesune aktivní blok zásobníku směrem dolů.|  
|**zobrazení výsledků**|Vrátí zprávu do konzoly.|  
|**enableNotif**[**ověření**] *typeName* 0&#124;1|Povolí (1) nebo zakáže (0) vlastní oznámení pro zadaný typ.|  
|**ex**[**ho**] [*exitcode*]|Ukončí prostředí MDbg.exe a volitelně určí ukončovací kód procesu.|  
|**Fo**[**dosáhnout**] [*OtherCommand*]|Provede příkaz na všech vláknech. *OtherCommand* je platný příkaz, který funguje na jedno vlákno; **foreach** *OtherCommand* provádí stejný příkaz na všechna vlákna.|  
|**f**[**unceval**] [`-ad` *Num*] *%{FunctionName/* [*argumentů...*  ]|Provádí funkce vyhodnocení na aktuální aktivní vlákno, kde je funkce, kterou chcete vyhodnotit *%{FunctionName/*. Název funkce musí být plně kvalifikovaný, včetně oborů názvů.<br /><br /> `-ad` Možnost určuje doménu aplikace sloužící k vyřešení funkce. Pokud `-ad` není určena možnost, doménu aplikace pro překlad výchozí doménu aplikace, kde se nachází vlákno, které se používá pro funkce vyhodnocování.<br /><br /> Pokud funkce, která se vyhodnocuje nejsou statické, musí být první parametr předána `this` ukazatel. Argumenty pro vyhodnocení funkce se vyhledávají ve všech aplikačních doménách.<br /><br /> Chcete-li požádat o hodnotu z domény aplikace, předpony proměnné s názvem domény modul a aplikace; například `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Tento příkaz vyhodnotí funkce `System.Object.ToString` v doméně aplikace `0`. Protože `ToString` metoda je instance funkce, musí být první parametr `this` ukazatel.|  
|**g**[**o**]|Způsobí, že program bude pokračovat, dokud nenarazí na zarážku, neukončí se nebo událost (například neošetřená výjimka) nezpůsobí zastavení programu.|  
|**h**[**nápovědu**] [*příkaz*]<br /><br /> -nebo-<br /><br /> **?** [*příkaz*]|Zobrazí popis všech příkazů nebo podrobný popis zadaného příkazu.|  
|**Ign**[**orovat**] [*událostí*]|Způsobí, že se ladicí program zastaví pouze v případě neošetřené výjimky.|  
|**int**[**ercept**] *FrameNumber*|Vrátí ladicí program na zadané číslo rámce.<br /><br /> Jestliže ladicí program narazí na výjimku, použijte tento příkaz k navrácení ladicího programu na zadané číslo rámce. Stav programu můžete změnit pomocí **nastavit** příkazů a pokračovat pomocí **přejděte** příkaz.|  
|**k**[**chybný**]|Zastaví aktivní proces.|  
|**l**[**ist**] [*moduly* &#124; *domén* &#124; *sestavení*]|Zobrazí načtené moduly, aplikační domény a sestavení.|  
|**u**[**ad**] *assemblyName*|Načte rozšíření následujícím způsobem: načtení zadaného sestavení a pak proveden pokus o spuštění statickou metodu `LoadExtension` z `Microsoft.Tools.Mdbg.Extension.Extension` typu.|  
|**protokol** [*eventType*]|Nastavit nebo zobrazit události, které mají být protokolovány.|  
|**Pře**[**de**] [*možnost zapnutí nebo vypnutí*]|Nastaví různé parametry ladicího programu. Použití `mode` bez použití možností získat seznam režimů ladění a jejich aktuální nastavení.|  
|**MON**[**itorInfo**] *monitorReference*|Zobrazí informace o uzamčení monitoru objektu.|  
|**newo**[**bj**] *typeName* [*argumenty...* ]|Vytvoří nový objekt typu *typeName*.|  
|**n**[**ext**]|Spustí kód a přesune se na další řádek (i v případě, že další řádek obsahuje mnoho volání funkce).|  
|**Opendump** *pathToDumpFile*|Otevře zadaný soubor s výpisem paměti pro ladění.|  
|**o**[**ut**]|Přejde na konec aktuální funkce.|  
|**Pa**[**tý**] [*pathName*]|Pokud není umístění v binárních souborech dostupné, vyhledá zdrojové soubory v zadaném umístění.|  
|**p**[**tisknout**] [*var*] &#124; [`-d`]|Zobrazí všechny proměnné v oboru (**tisku**), vytiskne zadanou proměnnou (**tisku** *var*), nebo vytiskne proměnné ladicí program (**tisku** `-d`).|  
|**printe**[**zapnout**] [*- r*]|Vypíše poslední výjimku pro aktuální vlákno. Použití `–r` (rekurzivní) možnost procházení `InnerException` vlastnost u objektu výjimka, a získat informace o celý řetěz výjimek.|  
|**pro**[**cessenum**]|Zobrazí aktivní procesy.|  
|**q**[**uit**] [*exitcode*]|Ukončí prostředí MDbg.exe, volitelně vypíše ukončovací kód procesu.|  
|**RE**[**obnovit**] [`*` &#124; [`~`]*threadNumber*]|Obnoví aktuální vlákno nebo vlákno určeného *threadNumber* parametr.<br /><br /> Pokud *threadNumber* parametr je zadán jako `*` nebo pokud počet vláken začíná `~`, příkaz platí pro všechna vlákna kromě určenému *threadNumber*.<br /><br /> Obnovení nepozastaveného vlákna nebude mít žádný vliv.|  
|**r**[**zrušení**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124; `-enc`] [[*path_to_exe*] [*argumentů _to_exe*]]|Zastaví aktuální proces (pokud existuje) a spustí nový. Pokud je předán žádný argument spustitelný soubor, tento příkaz spustí program, který byl dříve provést s `run` příkaz. Pokud je zadán argument spustitelného souboru, zadaný program se spustí pomocí volitelně zadaných argumentů.<br /><br /> Pokud jsou události načtení třídy, načtení modulu a spuštění vlákna ignorovány (což ve výchozím nastavení jsou), program se zastaví na prvním spustitelném příkazu hlavního vlákna.<br /><br /> Pomocí některého z následujících příznaků můžete přinutit ladicí program, aby prováděl kompilaci kódu just-in-time (JIT):<br /><br /> -   `-d` *(* `ebug` *)* zakáže optimalizace. Toto je výchozí nastavení pro MDbg.exe.<br />-   `-o` *(* `ptimize` *)* vynutí kód ke spuštění více jako nemá mimo ladicí program, ale také díky zkušenosti s laděním obtížnější. Toto je výchozí nastavení pro použití mimo ladicí program.<br />-   `-enc` Povolí funkci upravit a pokračovat, ale způsobuje podle výkonu.|  
|**Nastavit** *proměnná*=*hodnota*|Změní hodnotu kterékoli proměnné v rozsahu.<br /><br /> Můžete také vytvořit vlastní proměnné ladicího programu a přiřadit k nim referenční hodnoty z vaší aplikace. Tyto hodnoty se chovají jako popisovače původní hodnoty i tehdy, když je původní proměnná mimo rozsah. Všechny proměnné ladicí program musí začínat řetězcem `$` (například `$var`). Tyto popisovače můžete vymazat jejich nastavením na prázdnou hodnotu pomocí tohoto příkazu:<br /><br /> `set $var=`|  
|**Setip –** [`-il`] *číslo*|Nastaví aktuální ukazatel příkazu (IP) v souboru na určenou pozici. Pokud zadáte `-il` možnost toto číslo představuje Microsoft (MSIL intermediate language) posun v metodě. Jinak číslo představuje číslo řádku ve zdroji.|  
|**Zo**[**olit**] [*řádky*]|Určuje počet řádků, které chcete zobrazit.|  
|**s**[**rok**]|Přesune spuštění do další funkce na aktuálním řádku, nebo přejde na další řádek, pokud neexistuje žádná funkce, do které by se dalo přejít.|  
|**su**[**tráví**] [\* &#124; [~]*threadNumber*]|Pozastaví aktuální vlákno nebo vlákno určeného *threadNumber* parametr.  Pokud *threadNumber* je zadán jako `*`, příkaz platí pro všechna vlákna. Pokud počet vláken začíná `~`, příkaz platí pro všechna vlákna kromě určenému *threadNumber*. Pozastavená vláken jsou vyloučeny z spuštěna při spuštění procesu a to buď **přejděte** nebo **krok** příkaz. Pokud nejsou žádné jiné pozastaveno vláken v procesu a odešlete **přejděte** příkaz, proces nebude pokračovat. V takovém případě se stiskem kláves CTRL-C vrátíte zpět do procesu.|  
|**sy**[**menšený symbol**] *commandName* [*commandValue*]|Určuje jeden z následujících příkazů:<br /><br /> -   `symbol path` [`"``value``"`]-Zobrazí nebo nastaví aktuální symbol cestu.<br />-   `symbol addpath` `"` `value` `"` -Přidá do vašeho aktuální symbol cestě.<br />-   `symbol reload` [`"``module``"`]-Znovu načte všechny symboly nebo symboly pro zadaný modul.<br />-   `symbol list` [`module`]-Zobrazí aktuálně načtených symboly pro všechny moduly nebo zadaný modul.|  
|**t**[**odstranit vlákno**] [*newThread*] [-*nick Přezdívka*`]`|Příkaz vlákna bez parametrů zobrazí všechna spravovaná vlákna v aktuálním procesu. Vlákna jsou zpravidla identifikována číslem vlákna; pokud je však vlákno pojmenováno, zobrazí se místo čísla toto pojmenování. Můžete použít `-nick` parametr přiřadit přezdívku na vlákno.<br /><br /> -   **vlákno** `-nick` *threadName* přezdívku přiřadí aktuálně spuštěných vláken.<br /><br /> Pojmenování nesmí být číselné hodnoty. Pokud aktuální vlákno má již přiděleno pojmenování, staré pojmenování se nahradí novým. Pokud je nové pojmenování prázdný řetězec (""), pojmenování pro aktuální vlákno se odstraní a vláknu se nepřidělí další pojmenování.|  
|**u**[**p**]|Přesune aktivní rámec zásobníku směrem nahoru.|  
|**uwgc**[**zpracování**] [*var*] &#124; [*adresu*]|Vytiskne proměnnou sledovanou popisovačem. Popisovač lze zadat pomocí názvu nebo adresy.|  
|**Kdy**|Zobrazí aktuálně aktivní `when` příkazy.<br /><br /> **Když** **odstranit všechny** &#124; `num` [`num` [`num` ...]]-Odstraní `when` příkaz určený argumentem číslo nebo všechny `when` příkazy Pokud `all` je zadán.<br /><br /> **Když** `stopReason` [`specific_condition`] **provést** `cmd` [`cmd` [`cmd` ...]] – *stopReason* parametr může být jedna z následujících akcí:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* může být jedna z následujících akcí:<br /><br /> -   *číslo* – `ThreadCreated` a `BreakpointHit`, aktivuje akce jenom v případě, že zastavena vlákno ID nebo zarážek čísla stejnou hodnotu.<br />-[`!`]*název* – `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ExceptionThrown`, a `UnhandledExceptionThrown`, aktivuje akce jenom v případě, že název odpovídá názvu  *stopReason*.<br /><br /> *specific_condition* musí být prázdná pro jiné hodnoty *stopReason*.|  
|**w**[**sem**] [`-v`] [`-c` *hloubka*] [*ID podprocesu*]|Zobrazí informace o ladění týkající se rámců zásobníku.<br /><br /> -Na `-v` možnost poskytuje podrobné informace o jednotlivých zobrazených zásobníku.<br />-Zadat číslo pro `depth` omezení počtu snímků se zobrazí. Použití **všechny** příkazu se zobrazí všechny snímky. Výchozí hodnota je 100.<br />– Pokud zadáte *ID podprocesu* parametr, můžete řídit vlákna, které souvisí s zásobníku. Ve výchozím stavu se jedná pouze o aktuální vlákno. Použití **všechny** získat všechna vlákna.|  
|**x** [`-c`*numSymbols*] [*modulu*[`!`*vzor*]]|Zobrazí funkce, které odpovídají `pattern` pro modul.<br /><br /> Pokud *numSymbols* je zadána, je omezený na zadané číslo výstup. Pokud `!` (značí, že regulární výraz) nebyl zadán pro *vzor*, jsou zobrazeny všechny funkce. Pokud *modulu* není zadána, jsou zobrazeny všechny moduly načíst. Symboly (*~#*) umožňuje nastavit zarážky pomocí **zalomení** příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 Zkompilujte aplikaci do ladicího programu pomocí příznaků specifických pro kompilátor, které zajistí, že kompilátor vygeneruje symboly ladění. Další informace o těchto příznacích najdete v dokumentaci ke kompilátoru. Můžete ladit optimalizované aplikace, ale některé informace o ladění budou chybět. Například mnoho lokálních proměnných nebude vidět a řádky zdroje budou nepřesné.  
  
 Když zkompilujete vaší aplikace, zadejte **mdbg** na příkazovém řádku spusťte relaci ladění, jak je znázorněno v následujícím příkladu.  
  
```  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>` Řádku označuje, že jste v ladicím programu.  
  
 Jakmile budete v ladicím programu, použijte příkazy a argumenty popsané v předchozí části.  
  
## <a name="examples"></a>Příklady  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
