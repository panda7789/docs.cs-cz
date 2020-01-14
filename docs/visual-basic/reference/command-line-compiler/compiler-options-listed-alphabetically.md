---
title: Možnosti kompilátoru (abecední pořadí)
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 85fb07f46c2d885491db7358f24b3b50836c2ca8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937762"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Visual Basic možnosti kompilátoru seřazené abecedně
Visual Basic Kompilátor příkazového řádku je k dispozici jako alternativa k kompilování programů z integrovaného vývojového prostředí (IDE) sady Visual Studio. Následující seznam uvádí možnosti kompilátoru Visual Basic příkazového řádku seřazené abecedně.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Možnost|Účel|  
|------------|-------------|  
|[@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Určuje soubor odpovědí.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako možnost zadání `-help`. Nedochází k žádné kompilaci.|  
|`-additionalfile`|Názvy dalších souborů, které přímo neovlivňují generování kódu, ale mohou být využívány analyzátory pro vytváření chyb nebo upozornění.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.|  
|`-analyzer`|Spustit analyzátory z tohoto sestavení (krátký tvar:-a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Určuje základní adresu knihovny DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňují hlášení chyby.|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256. <br>Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Vytvoří ladicí informace.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definuje symboly pro podmíněnou kompilaci.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Způsobí, že kompilátor výstupuje sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Zpracuje komentáře dokumentace do souboru XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Určuje, jak by měl kompilátor Visual Basic hlásit vnitřní chyby kompilátoru.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Určuje, kam se mají zarovnat oddíly výstupního souboru.|  
|[-Help](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako možnost zadání `-?`. Nedochází k žádné kompilaci.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Určuje, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru entropie (ASLR).|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje obor názvů ze zadaného sestavení.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Určuje název kontejneru klíče pro dvojici klíčů, který poskytne sestavení silného názvu.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Určuje soubor, který obsahuje klíč nebo dvojici klíčů, aby sestavení mělo silný název.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Zadejte jazykovou verzi:&#124;9&#124;9,0&#124;10&#124;10,0&#124;11 11,0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Určuje umístění sestavení, na která odkazuje možnost [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) .|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Vytvoří odkaz na spravovaný prostředek.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Určuje třídu, která obsahuje `Sub Main` postup, který se má použít při spuštění.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Určuje název sestavení, jehož součástí bude modul.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu.|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Nastaví kompilátor pro cílení na prostředí .NET Compact Framework.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nekompilovat pomocí vbc. rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Potlačí informace banneru kompilátoru.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Způsobí, že kompilátor neodkazuje na standardní knihovny.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Potlačí schopnost kompilátoru generovat upozornění.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instruuje kompilátor, aby nevložil žádný manifest aplikace do spustitelného souboru.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Povolí nebo zakáže optimalizaci kódu.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Určuje, zda mají být porovnávání řetězců binární, nebo použijte sémantiku textu specifickou pro národní prostředí.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Vynutil explicitní deklaraci proměnných.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Povoluje použití odvození místního typu v deklaracích proměnných.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Vynutil striktní sémantiku jazyka.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Určuje výstupní soubor.|  
|<code>-parallel[+&#124;-]</code>|Určuje, jestli se má použít souběžné sestavení (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Určuje platformu procesoru, kterou kompilátor cílí na výstupní soubor.|  
|`-preferreduilang`|Zadejte název upřednostňovaného výstupního jazyka.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Vyhledá v podadresářích zdrojové soubory, které se mají kompilovat.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadata ze sestavení.|  
|[-refonly](refonly-compiler-option.md)|Výstupuje pouze referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje výstupní cestu pro referenční sestavení.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Zakáže kontrolu přetečení celých čísel.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Vloží spravovaný prostředek do sestavení.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Určuje obor názvů pro všechny deklarace typů.|  
|`-ruleset:<file>`|Zadejte soubor RuleSet, který zakáže konkrétní diagnostiku.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Určuje umístění knihovny mscorlib. dll a Microsoft. VisualBasic. dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Určuje minimální verzi subsystému, kterou může vygenerovaný spustitelný soubor použít.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Určuje formát výstupního souboru.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Určuje, že má kompilátor kompilovat bez odkazu na knihovnu modulu runtime Visual Basic, nebo s odkazem na konkrétní běhovou knihovnu.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Vytvoří výstup dalších informací během kompilace.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Propaguje upozornění na chyby.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Vloží soubor. ico do výstupního souboru.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifikuje uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Vloží prostředek Win32 do výstupního souboru.|  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic možnosti kompilátoru uvedené podle kategorie](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)
- [Správa vlastností projektu a řešení](/visualstudio/ide/managing-project-and-solution-properties)
