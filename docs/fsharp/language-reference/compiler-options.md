---
title: Možnosti kompilátoru
description: Použití F# možnosti příkazového řádku kompilátoru pro řízení sestavování vašich F# aplikací a knihoven.
ms.date: 12/10/2018
ms.openlocfilehash: d8e4331bcacd7082d7560ddc6fcadb4ce2b61cf8
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614490"
---
# <a name="compiler-options"></a>Možnosti kompilátoru

Toto téma popisuje možnosti příkazového řádku kompilátoru pro F# kompilátor, fsc.exe. Prostředí kompilace je možné řídit také nastavením vlastností projektu.


## <a name="compiler-options-listed-alphabetically"></a>Možnosti kompilátoru (abecední pořadí)
V následující tabulce jsou uvedeny možnosti kompilátoru uvedené podle abecedy. Některé F# jsou podobné možnosti kompilátoru C# – možnosti kompilátoru. Pokud je to tento případ, odkaz C# téma možností kompilátoru je k dispozici.



|– Možnost kompilátoru|Popis|
|---------------|-----------|
|`-a filename.fs`|Vytvoří knihovnu ze zadaného souboru. Tato možnost je zkrácená podoba `--target:library filename.fs`.|
|`--baseaddress:address`|Určuje upřednostňovaná základní adresa, ve kterém se má načíst knihovnu DLL.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;baseaddress &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|`--codepage:id`|Určuje znakovou stránku, která má použít během kompilace, pokud požadovaná stránka není aktuální výchozí znaková stránka systému.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;znakové stránky &#40;C&#35; – možnosti kompilátoru&#41;](../../csharp/language-reference/compiler-options/codepage-compiler-option.md).|
|`--consolecolors`|Určuje, že chyby a upozornění používají barevně označený text v konzole.|
|`--crossoptimize[+|-]`|Povolí nebo zakáže optimalizace mezi moduly.|
|<code>--delaysign[+&#124;-]</code>|Vytvoří zpožděný podpis sestavení s využitím veřejné části klíče silného názvu.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;delaysign &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|<code>--checked[+&#124;-]</code>|Povolí nebo zakáže generování kontroly přetečení.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;zaškrtnutí &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|Povolí nebo zakáže generování ladicích informací nebo určuje typ ladicích informací ke generování. Výchozí hodnota je plná, což umožňuje připojení ke spuštěnému programu. Zvolte **pdbonly** pro získání omezených ladicích informací uložených v souboru pdb (program database).<br /><br />Ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace naleznete v tématu<br /><br />[&#47;ladění &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|`--define:symbol`<br /><br />`-d:symbol`|Definuje symbol pro používání podmíněné kompilace.|
|<code>--deterministic[+&#124;-]</code>|Vytvoří deterministické sestavení (včetně GUID verze modulu a časového razítka). Tuto možnost nelze použít s čísly verzí zástupný znak a podporuje pouze typy vložené a přenosné ladění|
|`--doc:xmldoc-filename`|Instruuje kompilátor, aby generoval dokumentační komentáře XML do zadaného souboru. Další informace najdete v tématu [dokumentace XML](xml-documentation.md).<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;doc &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|`--fullpaths`|Instruuje kompilátor, aby generoval úplné cesty.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;fullpaths &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/d315xc66.aspx).|
|`--help`<br /><br />`-?`|Zobrazí informace o využití, včetně stručného popisu všech možností kompilátoru.|
|<code>--highentropyva[+&#124;-]</code>|Povolí nebo zakáže vysokou mírou entropie náhodné rozložení adresního prostoru (aslr) s rozšířenou funkci zabezpečení. Operační systém náhodně určí umístění v paměti, kde jsou načtena infrastruktura pro aplikace (například zásobník a halda). Pokud povolíte tuto možnost, můžete operační systémy používat toto generování použít úplnou adresu 64-bit – místo na 64bitovém počítači.|
|`--keycontainer:key-container-name`|Určuje kontejner klíče se silným názvem.|
|`--keyfile:filename`|Určuje název souboru veřejného klíče k podpisu vygenerovaného sestavení.|
|`--lib:folder-name`<br /><br />`-I:folder-name`|Určuje adresář, který má být vyhledáno odkazované sestavení.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;lib &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|`--linkresource:resource-info`|Propojí zadaný prostředek sestavením. Formát informací o zdroji je <code>filename[name[public&#124;private]]</code><br /><br />Propojení jednoho zdroje s touto možností je alternativou k vložení celého souboru se zdrojem pomocí `--resource` možnost.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;linkresource &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|`--mlcompatibility`|Ignoruje varování, která se zobrazí při použití funkcí, které jsou navrženy pro kompatibilitu s jinými verzemi ML.|
|`--noframework`|Zakáže výchozí odkaz na sestavení rozhraní .NET Framework.|
|`--nointerfacedata`|Instruuje kompilátor, aby vynechat zdroj, který obvykle přidá do sestavení, která zahrnuje F#-konkrétní metadat.|
|`--nologo`|Nezobrazí text nápisu při spuštění kompilátoru.|
|`--nooptimizationdata`|Instruuje kompilátor, aby pouze obsahoval optimalizace, které jsou důležité pro provádění vložených konstrukcí. Znemožňuje vkládání napříč moduly, ale zlepšuje binární kompatibilitu.|
|`--nowin32manifest`|Instruuje kompilátor, aby vynechat výchozí manifest Win32.|
|`--nowarn:warning-number-list`|Zakáže konkrétní upozornění zobrazeného podle čísla. Každé číslo upozornění oddělte čárkou. Můžete zjistit číslo upozornění varování z výstupu kompilace.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;nowarn &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|Povolí nebo zakáže optimalizace. Některé možnosti optimalizace lze zakázat nebo povolit selektivně jejich uvedení v seznamu. Jedná se o: `nojitoptimize`, `nojittracking`, `nolocaloptimize`, `nocrossoptimize`, `notailcalls`.|
|`--out:output-filename`<br /><br />`-o:output-filename`|Určuje název kompilovaného sestavení nebo modulu.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;si &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|`--pdb:pdb-filename`|Názvy výstupního souboru ladění PDB (program database). Tato možnost platí, jen když `--debug` je také povolena.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;pdb &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/ms228625.aspx).|
|`--platform:platform-name`|Určuje, že generovaný kód bude spouštěn pouze na určené platformě (`x86`, `Itanium`, nebo `x64`), nebo pokud název platformy `anycpu` je vybrána, určuje, že generovaný kód lze spustit na libovolné platformě.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;platformy &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|`--preferreduilang:lang`| Určuje název upřednostňovaného výstupního jazyka jazykové verze (například `es-ES`, `ja-JP`). |
|`--quotations-debug`|Určuje, že by pro výrazy, které jsou odvozeny z vyzařovaného dodatečné informace o ladění F# literály citace nezahrnou a reflektovaných definic. Informace o ladění se přidá do vlastní atributy F# uzel stromu výrazu. Zobrazit [nabídky kódu](code-quotations.md) a [Expr.CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|Díky kódu z F# nebo sestavení rozhraní .NET Framework pro kompilovaný kód k dispozici.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;odkaz &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|`--resource:resource-filename`|Vloží spravovaný soubor prostředků do generovaného sestavení.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;prostředků &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|`--sig:signature-filename`|Generuje soubor s podpisem na základě na vygenerované sestavení. Další informace o souborech podpisu naleznete v tématu [podpisy](signatures.md).|
|`--simpleresolution`|Určuje, že odkazy na sestavení měla být vyřešena pomocí adresářového Mono pravidla spíše než pomocí rozlišení MSBuild. Výchozí hodnota je použito řešení MSBuild s výjimkou spuštění v Mono.|
|`--standalone`|Určuje vytvoření sestavení, která obsahuje všechny jeho závislosti tak, aby ho spustit samostatně bez nutnosti další sestavení, jako F# knihovny.|
|`--staticlink:assembly-name`|Staticky odkazuje na dané sestavení a všechny odkazované knihovny DLL, které jsou závislé na toto sestavení. Použijte název sestavení, nikoli název knihovny DLL.|
|`--subsystemversion`|Určuje verzi podsystému OS pro generované spustitelné soubory. Použijte 6.02 pro Windows 8.1, 6.01 pro Windows 7, 6.00 pro Windows Vista. Tato možnost pouze platí pro spustitelné soubory, nikoli pro knihovny DLL a potřebují použít pouze v případě aplikace závisí na konkrétních bezpečnostních prvcích, které jsou k dispozici pouze v některých verzích operačního systému. Pokud tato možnost se používá, a uživatel se pokusí spustit vaši aplikaci v nižší verzi operačního systému, dojde k selhání s chybovou zprávou.|
|<code>--tailcalls[+&#124;-]</code>|Povolí nebo zakáže použití instrukce IL chvostu, což způsobí opětovné použití pro rekurzivní funkce chvostu rámce zásobníku. Tato možnost je povolená ve výchozím nastavení.|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|Určuje typ a název generovaným zkompilovaným kódem.<ul><li>`exe` znamená Konzolová aplikace.<br /></li><li>`winexe` znamená, že aplikace Windows, který se liší od konzolové aplikace v tom, že nemá žádné standardní vstupně/výstupní proudy (stdin, stdout a stderr) definovaný.<br /></li><li>`library` je sestavení bez vstupního bodu.<br /></li><li>`module` je modul rozhraní .NET Framework (.netmodule), který lze později kombinovat společně s ostatními moduly v sestavení.<br /></li><ul/>Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;cílové &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|`--times`|Zobrazí informace o časování pro kompilaci.|
|`--utf8output`|Umožňuje tisk výstupu kompilátoru v kódování UTF-8.|
|`--warn:warning-level`|Nastaví úroveň upozornění (0 až 5). Výchozí hodnota je 3. Každému varování je přiřazena úroveň podle závažnosti. Úroveň 5 nabízí více, ale méně závažných upozornění, než úroveň 1.<br /><br />Upozornění 5. úrovně jsou: (rekurzivnosti v době běhu) 21, 22 (`let rec` vyhodnocen jako mimo provoz), 45 (úplná abstrakce) a 52 (obranná kopie). Všechna další varování jsou na úrovni 2.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;upozornit &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|`--warnon:warning-number-list`|Povolte určité varování, které může být vypnuto ve výchozím nastavení nebo zakázáno jinou možnost příkazového řádku. V F# 3.0 pouze upozornění 1182 (nepoužité proměnné) je vypnuto ve výchozím nastavení.|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|Povolí nebo zakáže možnost hlásit upozornění jako chyby. Můžete zadat konkrétní čísla upozornění mají být zakázána nebo povolena. Volby dále v příkazovém řádku přepisují možnosti dříve v příkazovém řádku. Například pokud chcete nastavit upozornění, která nechcete hlásit jako chyby, zadejte `--warnaserror+` `--warnaserror-:warning-number-list`.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;warnaserror &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|`--win32manifest:manifest-filename`|Přidá soubor manifestu Win32 do kompilace. Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;win32manifest &#40;C&#35; – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/bb545961.aspx).|
|`--win32res:resource-filename`|Přidá soubor prostředků Win32 do kompilace.<br /><br />Tato možnost kompilátoru je ekvivalentní C# – možnost kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;win32res (&#40;C&#35;) – možnosti kompilátoru&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----|-----------|
|[Možnosti F# Interactive](fsharp-interactive-options.md)|Popisuje možnosti příkazového řádku podporované F# interpret, fsi.exe.|
|[Referenční dokumentace k vlastnostem projektu](/visualstudio/ide/reference/project-properties-reference)|Popisuje uživatelské rozhraní pro projekty, včetně stránek vlastností, které poskytují možnosti sestavení.|