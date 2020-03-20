---
title: MDbg.exe (ladicí program z příkazového řádku .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
ms.openlocfilehash: 58502626fed6c9cee52acb673ae34f6024f78b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715753"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (ladicí program z příkazového řádku .NET Framework)
Aplikace .NET Framework Command-Line Debugger pomáhá výrobcům nástrojů a vývojářům aplikací najít a opravit chyby v programech, které využívají .NET Framework Common Language Runtime. Tento nástroj používá API ladění za běhu k poskytování služeb ladění. Pomocí MDbg.exe můžete ladit pouze spravovaný kód; ladění nespravovaného kódu není podporováno.  
  
Tento nástroj je k dispozici prostřednictvím NuGet. Informace o instalaci naleznete v [tématu MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Chcete-li nástroj spustit, použijte konzolu Správce balíčků. Další informace o použití konzoly Správce balíčků naleznete v článku [Konzola správce balíčků.](/nuget/tools/package-manager-console)
  
Na výzvu Správce balíčků zadejte následující příkaz:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Příkazy  
 Pokud jste v ladicím programu (jak je uvedeno **v příkazu mdbg>** řádku), zadejte jeden z příkazů popsaných v další části:  
  
 **příkaz** [*argumenty*]  
  
 Příkazy MDbg.exe rozlišují velká a malá písmena.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|**ap**[**rocess**] [*číslo*]|Přepne na jiný laděný proces nebo vypíše dostupné procesy. Čísla nejsou skutečnými ID procesů (PID), ale seznam indexovaný od 0.|  
|**a**[**ttach**] [*pid*]|Připojí se k procesu nebo vytiskne dostupné procesy.|  
|**b**[**reak**] [*ClassName.Method* &#124; *FileName:LineNo*]|Nastaví zarážku v zadané metodě. Moduly jsou prohledávány postupně.<br /><br /> -   **break** *FileName:LineNo* nastaví zarážku v umístění ve zdroji.<br />-   **break** *~number* nastaví zarážku na symbolu, který byl nedávno zobrazen pomocí příkazu **x.**<br />-   **break** *modul! ClassName.Method+IlOffset* nastaví zarážku na plně kvalifikovaném umístění.|  
|**blok**[**ingObjects**]|Zobrazí zámky monitoru, které blokují vlákna.|  
|**ca**[**tch**] [*exceptionType*]|Způsobí, že se ladicí program přeruší na všech výjimkách a nejen na neošetřených výjimkách.|  
|**cl**[**earException**]|Označí aktuální výjimku jako ošetřenou, takže provádění může pokračovat. Pokud příčina chyby nebyla odstraněna, výjimka se může rychle objevit znovu.|  
|**conf**[**ig**] [*hodnota opce*]|Zobrazí všechny konfigurovatelné parametry a ukazuje, jak jsou parametry vyvolány bez jakékoli volitelné hodnoty. Pokud je tato možnost `value` zadána, nastaví se jako aktuální. V současné době jsou k dispozici následující možnosti:<br /><br /> -   `extpath`nastaví cestu k hledání rozšíření `load` při použití příkazu.<br />-   `extpath+`přidá cestu pro načítání rozšíření.|  
|**del**[**ete**]|Odstraní zarážku.|  
|**de**[**tach**]|Odpojí se od laděného procesu.|  
|**d**[**vlastní**] [*rámy*]|Přesune aktivní blok zásobníku směrem dolů.|  
|**echo**|Vrátí zprávu do konzoly.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Povolí (1) nebo zakáže (0) vlastní oznámení pro zadaný typ.|  
|**ex**[**to**] [*ukončovací kód*]|Ukončí prostředí MDbg.exe a volitelně určí ukončovací kód procesu.|  
|**fo**[**dosah**] [*OtherCommand*]|Provede příkaz na všech vláknech. *OtherCommand* je platný příkaz, který pracuje na jednom vlákně; **foreach** *OtherCommand* provede stejný příkaz ve všech podprocesech.|  
|**f**[**unceval**]`-ad` [ *Num*] *functionName* [*args ...* ]|Provede vyhodnocení funkce v aktuálním aktivním vlákně, kde je funkcí pro vyhodnocení *functionName*. Název funkce musí být plně kvalifikovaný, včetně oborů názvů.<br /><br /> Tato `-ad` možnost určuje doménu aplikace, která má být používána k vyřešení funkce. Pokud `-ad` tato možnost není zadána, doména aplikace pro rozlišení je výchozí pro doménu aplikace, kde je umístěno vlákno, které se používá pro vyhodnocení funkce.<br /><br /> Pokud funkce, která je vyhodnocována není `this` statické, první parametr předávaný by měl být ukazatel. Argumenty pro vyhodnocení funkce se vyhledávají ve všech aplikačních doménách.<br /><br /> Chcete-li požádat o hodnotu z domény aplikace, předponu proměnné s modulem a názvem domény aplikace; například `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Tento příkaz vyhodnotí funkci `System.Object.ToString` `0`v doméně aplikace . Vzhledem `ToString` k tomu, že metoda je `this` funkce instance, první parametr musí být ukazatel.|  
|**g**[**o**]|Způsobí, že program bude pokračovat, dokud nenarazí na zarážku, neukončí se nebo událost (například neošetřená výjimka) nezpůsobí zastavení programu.|  
|**h**[**elp**] [*příkaz*]<br /><br /> -nebo-<br /><br /> **?** [*příkaz*]|Zobrazí popis všech příkazů nebo podrobný popis zadaného příkazu.|  
|**ig**[**nore**] [*událost*]|Způsobí, že se ladicí program zastaví pouze v případě neošetřené výjimky.|  
|**int**[**ercept**] *FrameNumber*|Vrátí ladicí program na zadané číslo rámce.<br /><br /> Jestliže ladicí program narazí na výjimku, použijte tento příkaz k navrácení ladicího programu na zadané číslo rámce. Stav programu můžete změnit pomocí příkazu **set** a pokračovat pomocí příkazu **go.**|  
|**k**[**nemocný**]|Zastaví aktivní proces.|  
|**l**[**ist**] [*moduly* &#124; *appdomains* &#124; *sestavení*]|Zobrazí načtené moduly, aplikační domény a sestavení.|  
|**lo**[**ad**] *název_sestavení*|Načte rozšíření následujícím způsobem: Zadané sestavení je načteno a pak je `LoadExtension` proveden `Microsoft.Tools.Mdbg.Extension.Extension` pokus o spuštění statické metody z typu.|  
|**log** [*eventType*]|Nastavit nebo zobrazit události, které mají být protokolovány.|  
|**mo**[**de**] [*možnost zapnutí/vypnutí*]|Nastaví různé parametry ladicího programu. Pomocí `mode` bez možností získáte seznam režimů ladění a jejich aktuální nastavení.|  
|**mon**[**itorInfo**] *monitorReference*|Zobrazí informace o uzamčení monitoru objektu.|  
|**newo**[**bj**] *typeName* [*argumenty...*]|Vytvoří nový objekt typu *type type typeType*.|  
|**n**[**ext**]|Spustí kód a přesune se na další řádek (i v případě, že další řádek obsahuje mnoho volání funkce).|  
|**Opendump** *pathToDumpFile*|Otevře zadaný soubor s výpisem paměti pro ladění.|  
|**o**[**ut**]|Přejde na konec aktuální funkce.|  
|**pa**[**th**] [*název cesty*]|Pokud není umístění v binárních souborech dostupné, vyhledá zdrojové soubory v zadaném umístění.|  
|**p p**[**rint**]`-d`[*var*] &#124; [ ]|Vytiskne všechny proměnné v oboru (**tisk**), vytiskne zadanou proměnnou (**print** *var*) nebo vytiskne proměnné ladicího programu (**tisk**`-d`).|  
|**printe**[**xception**] [*-r*]|Vypíše poslední výjimku pro aktuální vlákno. Pomocí `–r` možnosti (rekurzivní) procházet `InnerException` vlastnost na objekt uvýjimky získat informace o celý řetězec výjimek.|  
|**pro**[**cessenum**]|Zobrazí aktivní procesy.|  
|**q**[**uit**] [*ukončovací kód*]|Ukončí prostředí MDbg.exe, volitelně vypíše ukončovací kód procesu.|  
|**re**[**sume**] [`*` &#124; [`~`]*threadNumber*]|Obnoví aktuální vlákno nebo vlákno určené parametrem *threadNumber.*<br /><br /> Pokud je parametr *threadNumber* zadán jako `*` nebo `~`pokud číslo vlákna začíná , příkaz se vztahuje na všechna vlákna kromě vlákna určeného *threadNumber*.<br /><br /> Obnovení nepozastaveného vlákna nebude mít žádný vliv.|  
|**r****un**[ un`-d``ebug`] [`o``ptimize`( `-enc`) &#124; - ( ) &#124;] [[*path_to_exe*] [*args_to_exe*]]|Zastaví aktuální proces (pokud existuje) a spustí nový. Pokud není předán žádný spustitelný argument, spustí tento příkaz `run` program, který byl dříve spuštěn s příkazem. Pokud je zadán argument spustitelného souboru, zadaný program se spustí pomocí volitelně zadaných argumentů.<br /><br /> Pokud jsou události načtení třídy, načtení modulu a spuštění vlákna ignorovány (což ve výchozím nastavení jsou), program se zastaví na prvním spustitelném příkazu hlavního vlákna.<br /><br /> Pomocí některého z následujících příznaků můžete přinutit ladicí program, aby prováděl kompilaci kódu just-in-time (JIT):<br /><br /> -   `-d`*(* `ebug` *)* zakáže optimalizace. Toto je výchozí nastavení pro MDbg.exe.<br />-   `-o`*(* `ptimize` *)* vynutí spuštění kódu více jako mimo ladicí program, ale také ztěžuje ladění. Toto je výchozí nastavení pro použití mimo ladicí program.<br />-   `-enc`povolí funkci Upravit a Pokračovat, ale vznikne zásah do výkonu.|  
|**Nastavit** *hodnotu* *proměnné*=|Změní hodnotu kterékoli proměnné v rozsahu.<br /><br /> Můžete také vytvořit vlastní proměnné ladicího programu a přiřadit k nim referenční hodnoty z vaší aplikace. Tyto hodnoty se chovají jako popisovače původní hodnoty i tehdy, když je původní proměnná mimo rozsah. Všechny proměnné ladicího programu `$` musí začínat `$var`(například). Tyto popisovače můžete vymazat jejich nastavením na prázdnou hodnotu pomocí tohoto příkazu:<br /><br /> `set $var=`|  
|**Číslo setip** [`-il`] *number*|Nastaví aktuální ukazatel příkazu (IP) v souboru na určenou pozici. Pokud zadáte `-il` možnost, číslo představuje posun zprostředkujícího jazyka Microsoft (MSIL) v metodě. Jinak číslo představuje číslo řádku ve zdroji.|  
|**sh**[**ow**] [*řádky*]|Určuje počet řádků, které chcete zobrazit.|  
|**s**[**tep**]|Přesune spuštění do další funkce na aktuálním řádku, nebo přejde na další řádek, pokud neexistuje žádná funkce, do které by se dalo přejít.|  
|**su****spend**[ strávit\* ] [ &#124; [~]*threadNumber*]|Pozastaví aktuální vlákno nebo vlákno určené parametrem *threadNumber.*  Pokud je příkaz `*` *threadNumber* zadán jako , příkaz se vztahuje na všechna vlákna. Pokud číslo vlákna `~`začíná , příkaz se vztahuje na všechna vlákna kromě jednoho zadaného *podprocesem ThreadNumber*. Pozastavená vlákna jsou vyloučena ze spuštění při spuštění procesu příkazem **go** nebo **step.** Pokud v procesu nejsou žádná nepozastavená vlákna a vydáte příkaz **go,** proces nebude pokračovat. V takovém případě se stiskem kláves CTRL-C vrátíte zpět do procesu.|  
|**sy**[**mbol**] *commandName* [*commandValue*]|Určuje jeden z následujících příkazů:<br /><br /> -   `symbol path`[`"value"`] - Zobrazí nebo nastaví aktuální cestu symbolu.<br />-   `symbol addpath``"value"` - Přidá k vaší aktuální cestě symbolu.<br />-   `symbol reload`[`"module"`] - Znovu načte všechny symboly nebo symboly pro zadaný modul.<br />-   `symbol list`[`module`] - Zobrazuje aktuálně načtené symboly pro všechny moduly nebo pro zadaný modul.|  
|**t**[**hread**] [*newThread*] [-*přezdívka*`]`|Příkaz vlákna bez parametrů zobrazí všechna spravovaná vlákna v aktuálním procesu. Vlákna jsou zpravidla identifikována číslem vlákna; pokud je však vlákno pojmenováno, zobrazí se místo čísla toto pojmenování. `-nick` Parametr můžete použít k přiřazení přezdívky vláknu.<br /><br /> -   **threadName** `-nick` *threadName* přiřadí přezdívku aktuálně spuštěnévlákno.<br /><br /> Pojmenování nesmí být číselné hodnoty. Pokud aktuální vlákno má již přiděleno pojmenování, staré pojmenování se nahradí novým. Pokud je nové pojmenování prázdný řetězec (""), pojmenování pro aktuální vlákno se odstraní a vláknu se nepřidělí další pojmenování.|  
|**u**[**p**]|Přesune aktivní rámec zásobníku směrem nahoru.|  
|**uwgc**[**rukojeť**] [*var*] &#124; [*adresa*]|Vytiskne proměnnou sledovanou popisovačem. Popisovač lze zadat pomocí názvu nebo adresy.|  
|**Kdy**|Zobrazí aktuálně aktivní `when` příkazy.<br /><br /> **při** **odstranění všech** &#124; `num` [`num` [`num` ...]] - Odstraní `when` příkaz `when` určený `all` číslem nebo všechny příkazy, pokud je zadán.<br /><br /> **když** `stopReason` `specific_condition`[ ]`cmd` `cmd` **do** `cmd` [ [ ...] ] - Parametr *stopReason* může být jeden z následujících:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* může být jedna z následujících možností:<br /><br /> -   *number* - `ThreadCreated` `BreakpointHit`For a , spustí akci pouze při zastavení id vlákna/čísla zarážky se stejnou hodnotou.<br />-`!`[ ]*name* `AssemblyLoaded`- `AssemblyUnloaded` `ExceptionThrown`For `ModuleLoaded` `UnhandledExceptionThrown`, `ClassLoaded`, , , , , , a , triggers action only when the name match the name of the *stopReason*.<br /><br /> *specific_condition* musí být prázdné pro jiné hodnoty *stopReason*.|  
|**w****here**[ zde`-v`]`-c` [ ] [ *hloubka*] [*threadID*]|Zobrazí informace o ladění týkající se rámců zásobníku.<br /><br /> - `-v` Možnost poskytuje podrobné informace o každém zobrazeném rámci zásobníku.<br />- Zadání čísla `depth` pro omezení počtu snímků, které jsou zobrazeny. K zobrazení všech snímků použijte příkaz **vše.** Výchozí hodnota je 100.<br />- Pokud zadáte parametr *threadID,* můžete určit, které vlákno je přidruženo k zásobníku. Ve výchozím stavu se jedná pouze o aktuální vlákno. Pomocí příkazu **all** získáte všechna vlákna.|  
|**x** `-c`[*numSymbols*]`!`[*modul*[*vzor*]]|Zobrazí funkce, `pattern` které odpovídají modulu.<br /><br /> Pokud *numSymbols* je zadán, výstup je omezen na zadané číslo. Pokud `!` (označující regulární výraz) není zadán pro *vzorek*, zobrazí se všechny funkce. Pokud *modul* není k dispozici, zobrazí se všechny načtené moduly. Symboly*~#*( ) lze použít k nastavení zarážek pomocí příkazu **break.**|  
  
## <a name="remarks"></a>Poznámky  
 Zkompilujte aplikaci do ladicího programu pomocí příznaků specifických pro kompilátor, které zajistí, že kompilátor vygeneruje symboly ladění. Další informace o těchto příznacích najdete v dokumentaci ke kompilátoru. Můžete ladit optimalizované aplikace, ale některé informace o ladění budou chybět. Například mnoho lokálních proměnných nebude vidět a řádky zdroje budou nepřesné.  
  
 Po kompilaci aplikace zadejte **mdbg** na příkazovém řádku a spusťte relaci ladění, jak je znázorněno v následujícím příkladu.  
  
```console  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 Výzva `mdbg>` označuje, že jste v ladicím programu.  
  
 Jakmile budete v ladicím programu, použijte příkazy a argumenty popsané v předchozí části.  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
