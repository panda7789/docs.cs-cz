---
title: MDbg.exe (ladicí program z příkazového řádku .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2b8f96e9a042681642225ad4e644c6fd1f001cb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044434"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (ladicí program z příkazového řádku .NET Framework)
Aplikace .NET Framework Command-Line Debugger pomáhá výrobcům nástrojů a vývojářům aplikací najít a opravit chyby v programech, které využívají .NET Framework Common Language Runtime. Tento nástroj používá API ladění za běhu k poskytování služeb ladění. Pomocí MDbg.exe můžete ladit pouze spravovaný kód; ladění nespravovaného kódu není podporováno.  
  
Tento nástroj je k dispozici prostřednictvím NuGet. Informace o instalaci najdete v tématu [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Chcete-li spustit nástroj, použijte konzolu Správce balíčků. Další informace o tom, jak používat konzolu Správce balíčků, najdete v článku [Konzola správce balíčků](/nuget/tools/package-manager-console) .
  
Na příkazovém řádku správce balíčků zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Příkazy  
 Když jste v ladicím programu (jak je uvedeno na příkazovém řádku **mdbg >** ), zadejte jeden z příkazů popsaných v následující části:  
  
 **příkaz** [*argumenty*]  
  
 Příkazy MDbg.exe rozlišují velká a malá písmena.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|**přístupový bod** [**rávce**] [*číslo*]|Přepne na jiný laděný proces nebo vypíše dostupné procesy. Čísla nejsou skutečnými ID procesů (PID), ale seznam indexovaný od 0.|  
|**a**[**připojit**] [*pid*]|Připojí se k procesu nebo vytiskne dostupné procesy.|  
|**b** [**reak**] [*ClassName. Method* &#124; *název_souboru: ČísloŘádku*]|Nastaví zarážku v zadané metodě. Moduly jsou prohledávány postupně.<br /><br /> -   **přerušení** *Filename: ČísloŘádku* nastaví zarážku na umístění ve zdroji.<br />-   **přerušení** *~ Number* nastaví zarážku na symbol naposledy zobrazený pomocí příkazu **x** .<br />-   **přerušení** *modul! ClassName. Method + IlOffset* nastaví zarážku na plně kvalifikované umístění.|  
|**blok** [**ingObjects**]|Zobrazí zámky monitoru, které blokují vlákna.|  
|**ca**[**tch**] [*exceptionType*]|Způsobí, že se ladicí program přeruší na všech výjimkách a nejen na neošetřených výjimkách.|  
|**cl**[**earException**]|Označí aktuální výjimku jako ošetřenou, takže provádění může pokračovat. Pokud příčina chyby nebyla odstraněna, výjimka se může rychle objevit znovu.|  
|**conf** [**IG**] [*hodnota možnosti*]|Zobrazí všechny konfigurovatelné parametry a ukazuje, jak jsou parametry vyvolány bez jakékoli volitelné hodnoty. Pokud je zadána možnost, nastaví `value` se jako aktuální možnost. V současné době jsou k dispozici následující možnosti:<br /><br /> -   `extpath`nastaví cestu pro vyhledávání rozšíření při `load` použití příkazu.<br />-   `extpath+`Přidá cestu pro načtení rozšíření.|  
|**del**[**ete**]|Odstraní zarážku.|  
|**de**[**tach**]|Odpojí se od laděného procesu.|  
|**d** [**vlastní**] [*snímky*]|Přesune aktivní blok zásobníku směrem dolů.|  
|**echo**|Vrátí zprávu do konzoly.|  
|**enableNotif** [**kace**] *TypeName* 0&#124;1|Povolí (1) nebo zakáže (0) vlastní oznámení pro zadaný typ.|  
|**ex** [**IT**] [*ExitCode*]|Ukončí prostředí MDbg.exe a volitelně určí ukončovací kód procesu.|  
|v **FO** [**dosah**] [*DalšíPříkaz*]|Provede příkaz na všech vláknech. *DalšíPříkaz* je platný příkaz, který pracuje na jednom vlákně. **foreach** *DalšíPříkaz* provádí stejný příkaz na všech vláknech.|  
|**f** [**unceval**] [`-ad` *NUM*] *funkce Function* [*args...* ]|Provede vyhodnocení funkce v aktuálním aktivním vlákně, kde funkce k vyhodnocení má hodnotu *Function*. Název funkce musí být plně kvalifikovaný, včetně oborů názvů.<br /><br /> `-ad` Možnost určuje aplikační doménu, která se má použít k vyřešení funkce. Není-li parametr zadán, je doména aplikace pro rozlišení výchozí pro doménu aplikace, kde je umístěn podproces, který je použit pro vyhodnocení funkce. `-ad`<br /><br /> Pokud funkce, která je vyhodnocována, není statická, první předaný parametr by měl být `this` ukazatel. Argumenty pro vyhodnocení funkce se vyhledávají ve všech aplikačních doménách.<br /><br /> Chcete-li požádat o hodnotu z domény aplikace, předponu proměnné s názvem domény modulu a aplikace; například `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Tento příkaz vyhodnocuje funkci `System.Object.ToString` v doméně `0`aplikace. Vzhledem k tomu, že `this` Metodajefunkceinstance,prvníparametrmusíbýtukazatel.`ToString`|  
|**g**[**o**]|Způsobí, že program bude pokračovat, dokud nenarazí na zarážku, neukončí se nebo událost (například neošetřená výjimka) nezpůsobí zastavení programu.|  
|**h** [**ELP**] [*příkaz*]<br /><br /> -nebo-<br /><br /> **?** [*příkaz*]|Zobrazí popis všech příkazů nebo podrobný popis zadaného příkazu.|  
|**IG** [**norovat**] [*událost*]|Způsobí, že se ladicí program zastaví pouze v případě neošetřené výjimky.|  
|**int** [**ercept**] *Číslorámce*|Vrátí ladicí program na zadané číslo rámce.<br /><br /> Jestliže ladicí program narazí na výjimku, použijte tento příkaz k navrácení ladicího programu na zadané číslo rámce. Stav programu můžete změnit pomocí příkazu **set** a pokračovat pomocí příkazu **Přejít** .|  
|**k**[**ill**]|Zastaví aktivní proces.|  
|**l** [**tis**] [*moduly* &#124; *AppDomains* &#124; – *sestavení*]|Zobrazí načtené moduly, aplikační domény a sestavení.|  
|**lo**[**ad**] *assemblyName*|Načte rozšíření následujícím způsobem: Zadané sestavení je načteno a potom je proveden pokus o spuštění statické metody `LoadExtension` `Microsoft.Tools.Mdbg.Extension.Extension` z typu.|  
|**protokol** [*Typ události*]|Nastavit nebo zobrazit události, které mají být protokolovány.|  
|**mo** [**de**] [*parametr zapnuto/vypnuto*]|Nastaví různé parametry ladicího programu. Pomocí `mode` možnosti bez možností získáte seznam režimů ladění a jejich aktuální nastavení.|  
|**Mon** [**itorInfo**] *odkazmonitoru*|Zobrazí informace o uzamčení monitoru objektu.|  
|**newo** [**BJ**] *TypeName* [*argumenty...* ]|Vytvoří nový objekt typu *TypeName*.|  
|**n**[**ext**]|Spustí kód a přesune se na další řádek (i v případě, že další řádek obsahuje mnoho volání funkce).|  
|**Opendump** *pathToDumpFile*|Otevře zadaný soubor s výpisem paměti pro ladění.|  
|**o**[**ut**]|Přejde na konec aktuální funkce.|  
|**PA** [**th**] [*cesta*]|Pokud není umístění v binárních souborech dostupné, vyhledá zdrojové soubory v zadaném umístění.|  
|**p** [**isknout**] [*var*] &#124; [`-d`]|Vytiskne všechny proměnné v oboru (**Tisk**), vytiskne zadanou proměnnou (**Print** *var*) nebo vytiskne proměnné ladicího programu (**Print**`-d`).|  
|**Tisk** [**zapnout**] [ *-r*]|Vypíše poslední výjimku pro aktuální vlákno. Použijte možnost `InnerException` (rekurzivní), chcete-li procházet vlastnost objektu výjimky a získat informace o celém řetězci výjimek. `–r`|  
|**pro**[**cessenum**]|Zobrazí aktivní procesy.|  
|**otázka** [**uit**] [*ExitCode*]|Ukončí prostředí MDbg.exe, volitelně vypíše ukončovací kód procesu.|  
|**znovu** [**Sume**] [`*` &#124; []`~`*čísloVlákna*]|Obnoví aktuální vlákno nebo vlákno určené parametrem *čísloVlákna* .<br /><br /> Pokud je parametr *čísloVlákna* zadán jako `*` nebo pokud číslo `~`vlákna začíná na, příkaz se vztahuje na všechna vlákna s výjimkou toho, který je určen parametrem *čísloVlákna*.<br /><br /> Obnovení nepozastaveného vlákna nebude mít žádný vliv.|  
|**r** [**un**] [`-d` &#124; &#124;( )-`-enc`()] [[*path_to_exe*] [args_to_exe]]`ptimize``o``ebug`|Zastaví aktuální proces (pokud existuje) a spustí nový. Pokud není předán žádný argument spustitelného souboru, spustí tento příkaz program, který byl dříve proveden `run` pomocí příkazu. Pokud je zadán argument spustitelného souboru, zadaný program se spustí pomocí volitelně zadaných argumentů.<br /><br /> Pokud jsou události načtení třídy, načtení modulu a spuštění vlákna ignorovány (což ve výchozím nastavení jsou), program se zastaví na prvním spustitelném příkazu hlavního vlákna.<br /><br /> Pomocí některého z následujících příznaků můžete přinutit ladicí program, aby prováděl kompilaci kódu just-in-time (JIT):<br /><br /> -   `-d` (`ebug` *)* zakáže optimalizace. Toto je výchozí nastavení pro MDbg.exe.<br />-   `-o` (`ptimize` *)* vynutí, aby kód běžel více, jako by byl mimo ladicí program, ale také je obtížné ladit. Toto je výchozí nastavení pro použití mimo ladicí program.<br />-   `-enc`povolí funkci upravit a pokračovat, ale dojde k dosažení výkonu.|  
|**Nastavit** *Proměnná* = *hodnota*|Změní hodnotu kterékoli proměnné v rozsahu.<br /><br /> Můžete také vytvořit vlastní proměnné ladicího programu a přiřadit k nim referenční hodnoty z vaší aplikace. Tyto hodnoty se chovají jako popisovače původní hodnoty i tehdy, když je původní proměnná mimo rozsah. Všechny proměnné ladicího programu musí `$` začínat ( `$var`například). Tyto popisovače můžete vymazat jejich nastavením na prázdnou hodnotu pomocí tohoto příkazu:<br /><br /> `set $var=`|  
|**SetIP** [`-il`] *číslo*|Nastaví aktuální ukazatel příkazu (IP) v souboru na určenou pozici. Pokud zadáte `-il` možnost, číslo představuje posun jazyka MSIL (Microsoft Intermediate Language) v metodě. Jinak číslo představuje číslo řádku ve zdroji.|  
|**SH** [**k**] [*řádky*]|Určuje počet řádků, které chcete zobrazit.|  
|**s** [**k rok**]|Přesune spuštění do další funkce na aktuálním řádku, nebo přejde na další řádek, pokud neexistuje žádná funkce, do které by se dalo přejít.|  
|**Su** [**výdaje**] [\* &#124; [~]*čísloVlákna*]|Pozastaví aktuální vlákno nebo vlákno určené parametrem *čísloVlákna* .  Pokud je zadán *čísloVlákna* jako `*`, příkaz se vztahuje na všechna vlákna. Pokud číslo vlákna začíná `~`na, příkaz se vztahuje na všechna vlákna s výjimkou toho, který je určen parametrem *čísloVlákna*. Pozastavená vlákna jsou vyloučena ze spouštění, pokud je proces spuštěn pomocí příkazu **Přejít** nebo **Krok** . Pokud v procesu neexistují žádná pozastavená vlákna a vydáváte příkaz **Přejít** , proces nebude pokračovat. V takovém případě se stiskem kláves CTRL-C vrátíte zpět do procesu.|  
|**sy** [**mbol**] *příkazový* [*hodnotapříkazu*]|Určuje jeden z následujících příkazů:<br /><br /> -   `symbol path`[`"value"`] – Zobrazí nebo nastaví aktuální cestu k symbolu.<br />-   `symbol addpath``"value"` – Přidá k aktuální cestě k symbolu.<br />-   `symbol reload`[`"module"`] – Znovu načte všechny symboly nebo symboly pro zadaný modul.<br />-   `symbol list`[`module`] – Zobrazí aktuálně načtené symboly pro všechny moduly nebo určený modul.|  
|**t** [**hread**] [*novéVlákno*] [-*Přezdívka Přezdívka*`]`|Příkaz vlákna bez parametrů zobrazí všechna spravovaná vlákna v aktuálním procesu. Vlákna jsou zpravidla identifikována číslem vlákna; pokud je však vlákno pojmenováno, zobrazí se místo čísla toto pojmenování. Můžete použít `-nick` parametr k přiřazení přezdívky do vlákna.<br /><br /> -   **podproces** Thread přiřadí přezdívku aktuálně běžícímu vláknu. `-nick`<br /><br /> Pojmenování nesmí být číselné hodnoty. Pokud aktuální vlákno má již přiděleno pojmenování, staré pojmenování se nahradí novým. Pokud je nové pojmenování prázdný řetězec (""), pojmenování pro aktuální vlákno se odstraní a vláknu se nepřidělí další pojmenování.|  
|**u**[**p**]|Přesune aktivní rámec zásobníku směrem nahoru.|  
|**uwgc** [**popisovač**] [*var*] &#124; [*adresa*]|Vytiskne proměnnou sledovanou popisovačem. Popisovač lze zadat pomocí názvu nebo adresy.|  
|**Kdy**|Zobrazí aktuálně aktivní `when` příkazy.<br /><br /> **kdy** **Odstranit vše** &#124; `when` `all` [[...]] – Odstraní `when` příkaz určený číslem nebo všemi příkazy, pokud je zadaný.`num` `num` `num`<br /><br /> **kdy** `stopReason` []do`cmd` [[.`cmd` ..]]-parametr *důvoduZastavení* může být jedna z následujících:`cmd` `specific_condition`<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* může být jedna z následujících:<br /><br /> -   *číslo* – pro `ThreadCreated` a `BreakpointHit`aktivuje akci pouze v případě, že je zastaveno identifikátorem vlákna nebo číslem zarážky se stejnou hodnotou.<br />-[`!`]*Name* `ModuleLoaded`- `ClassLoaded` `AssemblyLoaded` for,,`ExceptionThrown`,, a`UnhandledExceptionThrown`spustí akci pouze v případě, že se název shoduje s názvem *důvoduZastavení.* `AssemblyUnloaded`<br /><br /> *specific_condition* musí být prázdné pro jiné hodnoty *důvoduZastavení*.|  
|**w** [**sem**] [`-v`] [`-c` *Hloubka*] [*IDvlákna*]|Zobrazí informace o ladění týkající se rámců zásobníku.<br /><br /> `-v` -Možnost poskytuje podrobné informace o každém zobrazeném snímku zásobníku.<br />– Určuje číslo pro `depth` omezení počtu zobrazených snímků. Pomocí příkazu **All** zobrazíte všechny snímky. Výchozí hodnota je 100.<br />– Pokud zadáte parametr *IDvlákna* , můžete řídit, které vlákno je přidruženo k zásobníku. Ve výchozím stavu se jedná pouze o aktuální vlákno. K získání všech vláken použijte příkaz **All** .|  
|**x** [`-c`*numSymbols*] [*module*[`!`*pattern*]]|Zobrazí funkce, které se `pattern` shodují s modulem.<br /><br /> Je-li zadán parametr *číselnéSymboly* , je výstup omezen na zadané číslo. Pokud `!` (označuje regulární výraz) není pro *vzor*zadán, zobrazí se všechny funkce. Pokud není zadán *modul* , zobrazí se všechny načtené moduly. Symboly ( *~#* ) lze použít k nastavení zarážek pomocí příkazu **Break** .|  
  
## <a name="remarks"></a>Poznámky  
 Zkompilujte aplikaci do ladicího programu pomocí příznaků specifických pro kompilátor, které zajistí, že kompilátor vygeneruje symboly ladění. Další informace o těchto příznacích najdete v dokumentaci ke kompilátoru. Můžete ladit optimalizované aplikace, ale některé informace o ladění budou chybět. Například mnoho lokálních proměnných nebude vidět a řádky zdroje budou nepřesné.  
  
 Po zkompilování aplikace zadejte do příkazového řádku **MDbg** a spusťte tak relaci ladění, jak je znázorněno v následujícím příkladu.  
  
```console  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>` Výzva indikuje, že jste v ladicím programu.  
  
 Jakmile budete v ladicím programu, použijte příkazy a argumenty popsané v předchozí části.  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
