---
title: Možnosti kompilátoru
description: Použijte F# možnosti příkazového řádku kompilátoru pro řízení kompilace vašich F# aplikací a knihoven.
ms.date: 12/10/2018
ms.openlocfilehash: d0f4d1ca5ae45af25d6c304a2920d5c457700b1a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424757"
---
# <a name="compiler-options"></a>Možnosti kompilátoru

Toto téma popisuje možnosti příkazového řádku kompilátoru pro F# kompilátor, FSC. exe. Prostředí kompilace lze také ovládat nastavením vlastností projektu.

## <a name="compiler-options-listed-alphabetically"></a>Možnosti kompilátoru (abecední pořadí)

V následující tabulce jsou uvedeny možnosti kompilátoru seřazené podle abecedy. Některé z možností F# kompilátoru jsou podobné možnostem C# kompilátoru. V takovém případě je k dispozici odkaz na C# téma možnosti kompilátoru.

|Možnost kompilátoru|Popis|
|---------------|-----------|
|`-a filename.fs`|Vygeneruje knihovnu ze zadaného souboru. Tato možnost je krátká forma `--target:library filename.fs`.|
|`--baseaddress:address`|Určuje upřednostňovanou základní adresu, na které se má načíst knihovna DLL.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; BaseAddress jazyka C](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|`--codepage:id`|Určuje znakovou stránku, která se má použít při kompilaci, pokud požadovaná stránka není aktuální výchozí znakovou stránkou pro systém.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;znakové stránky &#40;C&#35; – možnosti&#41;kompilátoru](../../csharp/language-reference/compiler-options/codepage-compiler-option.md).|
|`--consolecolors`|Určuje, že chyby a upozornění používají v konzole barevně kódovaný text.|
|`--crossoptimize[+|-]`|Povolí nebo zakáže optimalizace mezi moduly.|
|<code>--delaysign[+&#124;-]</code>|Odhlásí sestavení pouze pomocí veřejné části klíče silného názvu.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; delaysign C](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|<code>--checked[+&#124;-]</code>|Povolí nebo zakáže generování kontrol přetečení.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;kontrolované &#40;možnosti&#35; &#41;kompilátoru jazyka C](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|Povoluje nebo zakazuje generování ladicích informací nebo určuje typ informací o ladění, které mají být vygenerovány. Výchozí hodnota je plná, což umožňuje připojení ke spuštěnému programu. Zvolením možnosti **pdbonly** získáte omezené informace o ladění uložené v souboru PDB (program databáze).<br /><br />Odpovídá možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu<br /><br />[ladění možností kompilátoru jazyka C&#35; &#40; &#47;&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx)|
|`--define:symbol`<br /><br />`-d:symbol`|Definuje symbol pro použití v podmíněné kompilaci.|
|<code>--deterministic[+&#124;-]</code>|Vytvoří deterministické sestavení (včetně GUID verze modulu a časového razítka). Tato možnost se nedá použít s čísly verze zástupných znaků a podporuje jenom vložené a přenosné typy ladění.|
|`--doc:xmldoc-filename`|Instruuje kompilátor, aby vygeneroval dokumentační komentáře XML do zadaného souboru. Další informace najdete v [dokumentaci XML](xml-documentation.md).<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; doc C](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|`--fullpaths`|Instruuje kompilátor, aby vygeneroval plně kvalifikované cesty.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; fullpaths – C](https://msdn.microsoft.com/library/d315xc66.aspx).|
|`--help`<br /><br />`-?`|Zobrazí informace o použití, včetně stručného popisu všech možností kompilátoru.|
|<code>--highentropyva[+&#124;-]</code>|Povolte nebo zakažte funkci ASLR (High-entropiing layouting Layout), což je Vylepšená funkce zabezpečení. Operační systém náhodně rozbalí umístění v paměti, kde se načtou infrastruktura pro aplikace (například zásobník a halda). Pokud povolíte tuto možnost, operační systémy mohou tuto náhodnost použít k použití úplného 64ho adresního prostoru na 64 počítači.|
|`--keycontainer:key-container-name`|Určuje kontejner klíče se silným názvem.|
|`--keyfile:filename`|Určuje název souboru veřejného klíče pro podepsání vygenerovaného sestavení.|
|`--lib:folder-name`<br /><br />`-I:folder-name`|Určuje adresář, ve kterém budou prohledána odkazovaná sestavení.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;věnovaném&#35; možnostem&#41;kompilátoru lib &#40;C](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|`--linkresource:resource-info`|Propojí zadaný prostředek se sestavením. Formát informací o prostředku je <code>filename[name[public&#124;private]]</code><br /><br />Propojení jednoho prostředku s touto možností je alternativou k vložení celého souboru prostředků s možností `--resource`.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; linkresource – C](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|`--mlcompatibility`|Ignoruje varování, která se zobrazí při použití funkcí, které jsou navržené pro kompatibilitu s jinými verzemi ML.|
|`--noframework`|Zakáže výchozí odkaz na .NET Framework sestavení.|
|`--nointerfacedata`|Instruuje kompilátor, aby vynechal prostředek, který obvykle přidává do sestavení, F#které obsahuje metadata specifická pro.|
|`--nologo`|Při spuštění kompilátoru nezobrazuje text banneru.|
|`--nooptimizationdata`|Instruuje kompilátor, aby zahrnoval jenom optimalizaci, který je nezbytný pro implementaci vložených konstrukcí. Znemožňuje vkládání mezi moduly, ale vylepšuje binární kompatibilitu.|
|`--nowin32manifest`|Instruuje kompilátor, aby vynechal výchozí manifest Win32.|
|`--nowarn:warning-number-list`|Zakáže specifická upozornění uvedená v čísle. Každé číslo upozornění oddělte čárkou. Můžete zjistit číslo upozornění pro jakékoli upozornění z výstupu kompilace.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;možnosti&#41;kompilátoru &#40;bez&#35; upozornění jazyka C](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|Povolí nebo zakáže optimalizace. Některé možnosti optimalizace lze selektivně zakázat nebo povolit jejich výpisem. Jsou to tyto: `nojitoptimize`, `nojittracking`, `nolocaloptimize`, `nocrossoptimize``notailcalls`.|
|`--out:output-filename`<br /><br />`-o:output-filename`|Určuje název zkompilovaného sestavení nebo modulu.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; jazyka C](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|`--pdb:pdb-filename`|Pojmenuje výstupní soubor Debug PDB (program Database). Tato možnost platí pouze v případě, že je povolena i `--debug`.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; PDB C](https://msdn.microsoft.com/library/ms228625.aspx).|
|`--platform:platform-name`|Určuje, že generovaný kód bude spuštěn pouze na zadané platformě (`x86`, `Itanium`nebo `x64`), nebo pokud je zvolena `anycpu` název platformy, určuje, že generovaný kód může běžet na libovolné platformě.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; platformy C](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|`--preferreduilang:lang`| Určuje preferovaný název jazykové verze jazyka (například `es-ES``ja-JP`). |
|`--quotations-debug`|Určuje, že se mají vygenerovat dodatečné informace o ladění pro výrazy, které F# jsou odvozeny z literálů citace a reflektované definice. Informace o ladění jsou přidány do vlastních atributů uzlu stromu F# výrazu. Viz [citace kódu](code-quotations.md) a [expr. CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|Zpřístupňuje kód z F# sestavení nebo .NET Framework k kompilovanému kódu.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;reference &#40;k&#35; možnostem&#41;kompilátoru jazyka C](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|`--resource:resource-filename`|Vloží spravovaný soubor prostředků do generovaného sestavení.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; Resource C](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|`--sig:signature-filename`|Vygeneruje soubor signatury založený na generovaném sestavení. Další informace o souborech signatur najdete v tématu [signatury](signature-files.md).|
|`--simpleresolution`|Určuje, že odkazy na sestavení by měly být vyřešeny pomocí pravidel mono založených na adresáři namísto řešení MSBuild. Výchozím nastavením je použití řešení MSBuild s výjimkou případů, kdy běží v mono.|
|`--standalone`|Určuje, že se má vydávat sestavení, které obsahuje všechny jeho závislosti, aby běželo sama o sobě bez nutnosti dalších sestavení, jako F# je například knihovna.|
|`--staticlink:assembly-name`|Staticky propojí dané sestavení a všechny odkazované knihovny DLL, které jsou závislé na tomto sestavení. Použijte název sestavení, nikoli název knihovny DLL.|
|`--subsystemversion`|Určuje verzi subsystému OS, která se má použít pro vygenerovaný spustitelný soubor. Použijte 6,02 pro Windows 8.1 6,01 pro Windows 7, 6,00 pro Windows Vista. Tato možnost se týká pouze spustitelných souborů, nikoli knihoven DLL a potřebujete použít pouze v případě, že vaše aplikace závisí na konkrétních funkcích zabezpečení dostupných pouze v určitých verzích operačního systému. Pokud je tato možnost použita a uživatel se pokusí spustit vaši aplikaci v nižší verzi operačního systému, selže s chybovou zprávou.|
|<code>--tailcalls[+&#124;-]</code>|Povolí nebo zakáže použití instrukcí Tail IL, což způsobí, že se rámec zásobníku znovu použije pro rekurzivní funkce tail. Tato možnost je ve výchozím nastavení povolená.|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|Určuje typ a název souboru generovaného zkompilovaného kódu.<ul><li>`exe` znamená konzolovou aplikaci.<br /></li><li>`winexe` znamená aplikaci systému Windows, která se liší od konzolové aplikace v tom, že nemá definovány standardní vstupní/výstupní datové proudy (stdin, stdout a stderr).<br /></li><li>`library` je sestavení bez vstupního bodu.<br /></li><li>`module` je modul .NET Framework (. netmodule), který se dá později zkombinovat s jinými moduly do sestavení.<br /></li><ul/>Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;cílové &#40;možnosti&#35; &#41;kompilátoru jazyka C](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|`--times`|Zobrazí informace o časování pro kompilaci.|
|`--utf8output`|Povoluje výstup kompilátoru tisku v kódování UTF-8.|
|`--warn:warning-level`|Nastaví úroveň upozornění (0 až 5). Výchozí úroveň je 3. Každé upozornění má na základě jeho závažnosti úroveň. Úroveň 5 poskytuje více, ale méně závažných varování než úroveň 1.<br /><br />Upozornění úrovně 5:21 (rekurzivní použití zaškrtnuté při běhu), 22 (`let rec` vyhodnoceno mimo pořadí), 45 (úplná abstrakce) a 52 (kopie obrannou linií). Všechna ostatní upozornění jsou úrovně 2.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47; &#40;upozorňující&#35; na možnosti&#41;kompilátoru C](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|`--warnon:warning-number-list`|Povolí specifická upozornění, která můžou být ve výchozím nastavení vypnutá, nebo zakázaná jinou možností příkazového řádku. V F# 3,0 je ve výchozím nastavení vypnuto pouze upozornění 1182 (nepoužité proměnné).|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|Povolí nebo zakáže možnost hlásit upozornění jako chyby. Můžete zadat konkrétní čísla upozornění, která mají být zakázána nebo povolena. Možnosti později v možnostech přepsání příkazového řádku výše v příkazovém řádku. Pokud například chcete zadat upozornění, která nechcete ohlásit jako chyby, zadejte `--warnaserror+` `--warnaserror-:warning-number-list`.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; warnaserror – C](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|`--win32manifest:manifest-filename`|Přidá soubor manifestu Win32 do kompilace. Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace najdete v tématu [ &#47;možnosti &#40;&#41;kompilátoru&#35; win32manifest C](https://msdn.microsoft.com/library/bb545961.aspx).|
|`--win32res:resource-filename`|Přidá soubor prostředků Win32 do kompilace.<br /><br />Tato možnost kompilátoru je ekvivalentní možnosti C# kompilátoru se stejným názvem. Další informace naleznete v tématu [ &#47;možnosti&#41;kompilátoru&#40;win32res&#35;(C)](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----|-----------|
|[Možnosti F# Interactive](fsharp-interactive-options.md)|Popisuje možnosti příkazového řádku podporované F# překladačem, FSI. exe.|
|[Referenční dokumentace k vlastnostem projektu](/visualstudio/ide/reference/project-properties-reference)|Popisuje uživatelské rozhraní pro projekty, včetně stránek vlastností projektu, které poskytují možnosti sestavení.|
