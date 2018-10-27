---
title: MDbg.exe (ladicí program z příkazového řádku .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2861d2364d2c29d15b25911524ef28aa78130913
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034491"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (ladicí program z příkazového řádku .NET Framework)
Aplikace .NET Framework Command-Line Debugger pomáhá výrobcům nástrojů a vývojářům aplikací najít a opravit chyby v programech, které využívají .NET Framework Common Language Runtime. Tento nástroj používá API ladění za běhu k poskytování služeb ladění. Pomocí MDbg.exe můžete ladit pouze spravovaný kód; ladění nespravovaného kódu není podporováno.  
  
Tento nástroj je k dispozici prostřednictvím balíčku NuGet. Informace o instalaci, naleznete v tématu [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Ke spuštění nástroje, pomocí konzoly Správce balíčků. Další informace o tom, jak použít konzolu Správce balíčků, najdete v článku [Konzola správce balíčků](/nuget/tools/package-manager-console) článku.
  
Do příkazového řádku Správce balíčků zadejte následující příkaz:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Příkazy  
 Až budete v ladicím programu (jak je uvedeno ve **mdbg >** řádek), zadejte jeden z příkazů popsaných v následující části:  
  
 **příkaz** [*argumenty*]  
  
 Příkazy MDbg.exe rozlišují velká a malá písmena.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|**Asie a Tichomoří**[**rocess**] [*číslo*]|Přepne na jiný laděný proces nebo vypíše dostupné procesy. Čísla nejsou skutečnými ID procesů (PID), ale seznam indexovaný od 0.|  
|**a**[**připojit**] [*pid*]|Připojí se k procesu nebo vytiskne dostupné procesy.|  
|**b**[**binárními**] [*ClassName.Method* &#124; *Číslořádku*]|Nastaví zarážku v zadané metodě. Moduly jsou prohledávány postupně.<br /><br /> -   **Konec** *Číslořádku* Nastaví zarážku v umístění ve zdroji.<br />-   **Konec** *~ číslo* Nastaví zarážku nedávno zobrazený symbol s **x** příkazu.<br />-   **Konec** *modulu! ClassName.Method+IlOffset* Nastaví zarážku na plně kvalifikované umístění.|  
|**blok**[**ingObjects**]|Zobrazí zámky monitoru, které blokují vlákna.|  
|**certifikační autorita**[**tch**] [*exceptionType*]|Způsobí, že se ladicí program přeruší na všech výjimkách a nejen na neošetřených výjimkách.|  
|**cl**[**earException**]|Označí aktuální výjimku jako ošetřenou, takže provádění může pokračovat. Pokud příčina chyby nebyla odstraněna, výjimka se může rychle objevit znovu.|  
|**conf**[**ig**] [*hodnota možnosti*]|Zobrazí všechny konfigurovatelné parametry a ukazuje, jak jsou parametry vyvolány bez jakékoli volitelné hodnoty. Pokud je parametr zadán, nastaví `value` jako aktuální možnost. V současné době jsou k dispozici následující možnosti:<br /><br /> -   `extpath` Nastaví cestu k vyhledání rozšíření při `load` příkaz se používá.<br />-   `extpath+` přidá cestu pro načtení rozšíření.|  
|**del**[**ete**]|Odstraní zarážku.|  
|**de**[**odpojit**]|Odpojí se od laděného procesu.|  
|**d**[**vlastní**] [*snímků*]|Přesune aktivní blok zásobníku směrem dolů.|  
|**echo**|Vrátí zprávu do konzoly.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Povolí (1) nebo zakáže (0) vlastní oznámení pro zadaný typ.|  
|**ex**[**ho**] [*exitcode*]|Ukončí prostředí MDbg.exe a volitelně určí ukončovací kód procesu.|  
|**Fo**[**oslovit**] [*Dalšípříkaz*]|Provede příkaz na všech vláknech. *Dalšípříkaz* je platný příkaz, který na jednom vláknu; **foreach** *Dalšípříkaz* vykoná tentýž příkaz na všech vláknech.|  
|**f**[**unceval**] [`-ad` *Num*] *functionName* [*argumenty...*  ]|Provádí vyhodnocení funkce na aktuálně aktivním vláknu, ve kterém je daná funkce k vyhodnocení *functionName*. Název funkce musí být plně kvalifikovaný, včetně oborů názvů.<br /><br /> `-ad` Určuje doménu aplikace použít pro vyřešení funkce. Pokud `-ad` možnost nezadá, výchozí doménu aplikace pro řešení aplikační doménu, kde se nachází vlákno sloužící k vyhodnocení funkce.<br /><br /> Pokud vyhodnocovaná funkce není statická, prvním předaným parametrem by měl být `this` ukazatele. Argumenty pro vyhodnocení funkce se vyhledávají ve všech aplikačních doménách.<br /><br /> Chcete-li vyžádat hodnotu z domény aplikace, před proměnnou Název modulu a aplikační domény; například `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Tento příkaz vyhodnocuje funkci `System.Object.ToString` v aplikační doméně `0`. Protože `ToString` metoda je instance funkce, musí být první parametr `this` ukazatel.|  
|**g**[**o**]|Způsobí, že program bude pokračovat, dokud nenarazí na zarážku, neukončí se nebo událost (například neošetřená výjimka) nezpůsobí zastavení programu.|  
|**h**[**elp**] [*příkaz*]<br /><br /> -nebo-<br /><br /> **?** [*příkaz*]|Zobrazí popis všech příkazů nebo podrobný popis zadaného příkazu.|  
|**IG**[**norovat**] [*události*]|Způsobí, že se ladicí program zastaví pouze v případě neošetřené výjimky.|  
|**int**[**ercept**] *Číslorámce*|Vrátí ladicí program na zadané číslo rámce.<br /><br /> Jestliže ladicí program narazí na výjimku, použijte tento příkaz k navrácení ladicího programu na zadané číslo rámce. Stav programu můžete změnit pomocí **nastavit** příkazů a pokračovat a používat **Přejít** příkazu.|  
|**k**[**výplně**]|Zastaví aktivní proces.|  
|**l**[**TIS**] [*moduly* &#124; *objektů třídy appdomains* &#124; *sestavení*]|Zobrazí načtené moduly, aplikační domény a sestavení.|  
|**Lo**[**ad**] *assemblyName*|Načte příponu následujícím způsobem: zadané sestavení a pak je proveden pokus o spuštění statické metody `LoadExtension` z `Microsoft.Tools.Mdbg.Extension.Extension` typu.|  
|**protokol** [*eventType*]|Nastavit nebo zobrazit události, které mají být protokolovány.|  
|**MO**[**de**] [*možnost Zapnuto/vypnuto*]|Nastaví různé parametry ladicího programu. Použití `mode` s bez parametrů vypíše seznam režimů ladění a jejich aktuální nastavení.|  
|**MON**[**itorInfo**] *Odkazmonitoru*|Zobrazí informace o uzamčení monitoru objektu.|  
|**newo**[**bj**] *typeName* [*argumenty...* ]|Vytvoří nový objekt typu *typeName*.|  
|**n**[**ext**]|Spustí kód a přesune se na další řádek (i v případě, že další řádek obsahuje mnoho volání funkce).|  
|**Opendump** *pathToDumpFile*|Otevře zadaný soubor s výpisem paměti pro ladění.|  
|**o**[**ut**]|Přejde na konec aktuální funkce.|  
|**Pa**[**th**] [*cesta*]|Pokud není umístění v binárních souborech dostupné, vyhledá zdrojové soubory v zadaném umístění.|  
|**p**[**isknout**] [*var*] &#124; [`-d`]|Vytiskne všechny proměnné v rozsahu (**tisk**), vytiskne zadanou proměnnou (**tisk** *var*), nebo vytiskne proměnné ladicího programu (**tisk** `-d`).|  
|**printe**[**yvolat výjimku jinou**] [*- r*]|Vypíše poslední výjimku pro aktuální vlákno. Použití `–r` (rekurzivní) možnost Procházet `InnerException` vlastnost v objektu výjimky a získat informace o celém řetězci výjimek.|  
|**pro**[**cessenum**]|Zobrazí aktivní procesy.|  
|**q**[**uit**] [*exitcode*]|Ukončí prostředí MDbg.exe, volitelně vypíše ukončovací kód procesu.|  
|**RE**[**sume**] [`*` &#124; [`~`]*Číslovlákna*]|Obnoví aktuální vlákno nebo vlákno určené parametrem *Číslovlákna* parametru.<br /><br /> Pokud *Číslovlákna* parametru je zadán jako `*` nebo pokud číslo vlákna začíná znakem `~`, příkaz se vztahuje na všechna vlákna kromě vlákna zadaného parametrem *Číslovlákna*.<br /><br /> Obnovení nepozastaveného vlákna nebude mít žádný vliv.|  
|**r**[**zrušení**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124; `-enc`] [[*path_to_exe*] [*argumentů _to_exe*]]|Zastaví aktuální proces (pokud existuje) a spustí nový. Pokud není předán žádný argument spustitelného souboru, tento příkaz spustí program, který byl dříve spuštěn pomocí `run` příkazu. Pokud je zadán argument spustitelného souboru, zadaný program se spustí pomocí volitelně zadaných argumentů.<br /><br /> Pokud jsou události načtení třídy, načtení modulu a spuštění vlákna ignorovány (což ve výchozím nastavení jsou), program se zastaví na prvním spustitelném příkazu hlavního vlákna.<br /><br /> Pomocí některého z následujících příznaků můžete přinutit ladicí program, aby prováděl kompilaci kódu just-in-time (JIT):<br /><br /> -   `-d` *(* `ebug` *)* zakáže optimalizace. Toto je výchozí nastavení pro MDbg.exe.<br />-   `-o` *(* `ptimize` *)* přinutí kód spuštění mimo ladicí program, ale také díky možnosti ladění obtížnější. Toto je výchozí nastavení pro použití mimo ladicí program.<br />-   `-enc` Povolí funkci upravit a pokračovat, ale sníží výkon.|  
|**Nastavte** *proměnnou*=*hodnota*|Změní hodnotu kterékoli proměnné v rozsahu.<br /><br /> Můžete také vytvořit vlastní proměnné ladicího programu a přiřadit k nim referenční hodnoty z vaší aplikace. Tyto hodnoty se chovají jako popisovače původní hodnoty i tehdy, když je původní proměnná mimo rozsah. Všechny proměnné pro ladicí program musí začínat řetězcem `$` (například `$var`). Tyto popisovače můžete vymazat jejich nastavením na prázdnou hodnotu pomocí tohoto příkazu:<br /><br /> `set $var=`|  
|**Operace Setip** [`-il`] *číslo*|Nastaví aktuální ukazatel příkazu (IP) v souboru na určenou pozici. Pokud zadáte `-il` možnost, představuje číslo jazyk Microsoft intermediate language (MSIL) posun v metodě. Jinak číslo představuje číslo řádku ve zdroji.|  
|**TV**[**ak**] [*řádky*]|Určuje počet řádků, které chcete zobrazit.|  
|**s**[**rok**]|Přesune spuštění do další funkce na aktuálním řádku, nebo přejde na další řádek, pokud neexistuje žádná funkce, do které by se dalo přejít.|  
|**su**[**věnovat**] [\* &#124; [~]*Číslovlákna*]|Pozastaví aktuální vlákno nebo vlákno určené parametrem *Číslovlákna* parametru.  Pokud *Číslovlákna* je zadán jako `*`, příkaz se vztahuje na všechna vlákna. Pokud číslo vlákna začíná znakem `~`, příkaz se vztahuje na všechna vlákna kromě vlákna zadaného parametrem *Číslovlákna*. Pozastavená vlákna jsou vypuštěna ze spuštění, jestliže je proces spuštěn buď **Přejít** nebo **krok** příkazu. Pokud neexistují žádná pozastavená vlákna v procesu a vydat **Přejít** příkazu, proces nebude pokračovat. V takovém případě se stiskem kláves CTRL-C vrátíte zpět do procesu.|  
|**sy**[**mbol**] *commandName* [*Hodnotapříkazu*]|Určuje jeden z následujících příkazů:<br /><br /> -   `symbol path` [`"``value``"`] – Zobrazí nebo nastaví cestu k aktuálnímu symbolu.<br />-   `symbol addpath` `"` `value` `"` – Přidá do vaší cesty k symbolu.<br />-   `symbol reload` [`"``module``"`] – Znovu načte všechny symboly nebo symboly pro zadaný modul.<br />-   `symbol list` [`module`] – Zobrazí aktuálně načtené symboly pro všechny moduly nebo zadaný modul.|  
|**t**[**hread**] [*Novévlákno*] [-*nick pojmenování*`]`|Příkaz vlákna bez parametrů zobrazí všechna spravovaná vlákna v aktuálním procesu. Vlákna jsou zpravidla identifikována číslem vlákna; pokud je však vlákno pojmenováno, zobrazí se místo čísla toto pojmenování. Můžete použít `-nick` parametr pojmenovat vlákno.<br /><br /> -   **vlákno** `-nick` *threadName* přiřadí pojmenování aktuálně běžícímu vláknu.<br /><br /> Pojmenování nesmí být číselné hodnoty. Pokud aktuální vlákno má již přiděleno pojmenování, staré pojmenování se nahradí novým. Pokud je nové pojmenování prázdný řetězec (""), pojmenování pro aktuální vlákno se odstraní a vláknu se nepřidělí další pojmenování.|  
|**u**[**p**]|Přesune aktivní rámec zásobníku směrem nahoru.|  
|**uwgc**[**zpracování**] [*var*] &#124; [*adresu*]|Vytiskne proměnnou sledovanou popisovačem. Popisovač lze zadat pomocí názvu nebo adresy.|  
|**Kdy**|Zobrazí aktuálně aktivní `when` příkazy.<br /><br /> **Když** **odstranit všechny** &#124; `num` [`num` [`num` ...]] – Odstraní `when` příkaz určený argumentem číslo nebo všechny `when` příkazy Pokud `all` je zadán.<br /><br /> **Když** `stopReason` [`specific_condition`] **proveďte** `cmd` [`cmd` [`cmd` ...]] – *Důvoduzastavení* parametr může být jedna z následujících akcí:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* může být jedna z následujících akcí:<br /><br /> -   *číslo* – `ThreadCreated` a `BreakpointHit`, aktivuje akci pouze při zastavení vláknem ID/čísla zarážky se stejnou hodnotou.<br />-[`!`]*název* – `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ExceptionThrown`, a `UnhandledExceptionThrown`, aktivuje akci pouze v případě, že název odpovídá názvu  *Důvoduzastavení*.<br /><br /> *specific_condition* musí být prázdná pro ostatní hodnoty *Důvoduzastavení*.|  
|**w**[**tady**] [`-v`] [`-c` *hloubky*] [*Idvlákna*]|Zobrazí informace o ladění týkající se rámců zásobníku.<br /><br /> – `-v` Poskytuje podrobné informace o každém zobrazeném rámci zásobníku.<br />-Zadáním čísla pro `depth` omezuje počet rámců. Použití **všechny** příkazu zobrazíte všechny rámce. Výchozí hodnota je 100.<br />– Pokud je zadat *Idvlákna* parametr, můžete řídit, které vlákno je asociováno se zásobníkem. Ve výchozím stavu se jedná pouze o aktuální vlákno. Použití **všechny** příkazu zobrazíte všechna vlákna.|  
|**x** [`-c`*Číselnésymboly*] [*modulu*[`!`*vzor*]]|Zobrazí funkce, které odpovídají `pattern` pro modul.<br /><br /> Pokud *Číselnésymboly* není zadána, výstup se omezí na zadané číslo. Pokud `!` (značící regulární výraz) není pro zadaný *vzor*, zobrazí se všechny funkce. Pokud *modulu* není zadán, jsou zobrazeny všechny nahrané moduly. Symboly (*~#*) slouží k nastavení zarážek pomocí **přerušení** příkazu.|  
  
## <a name="remarks"></a>Poznámky  
 Zkompilujte aplikaci do ladicího programu pomocí příznaků specifických pro kompilátor, které zajistí, že kompilátor vygeneruje symboly ladění. Další informace o těchto příznacích najdete v dokumentaci ke kompilátoru. Můžete ladit optimalizované aplikace, ale některé informace o ladění budou chybět. Například mnoho lokálních proměnných nebude vidět a řádky zdroje budou nepřesné.  
  
 Po zkompilování aplikace zadejte **mdbg** na příkazovém řádku spustíte relaci ladění, jak je znázorněno v následujícím příkladu.  
  
```  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>` Značí, že jste v ladicím programu.  
  
 Jakmile budete v ladicím programu, použijte příkazy a argumenty popsané v předchozí části.  
  
## <a name="examples"></a>Příklady  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
