---
title: Možnosti kompilátoru jazyka Visual Basic uvedené podle kategorie
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 8f09566585c06531a346b0143a6002c2854a0b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182563"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Visual Basic možnosti kompilátoru uvedené podle kategorie
Kompilátor příkazového řádku Visual Basic je k dispozici jako alternativa k kompilování programů z integrovaného vývojového prostředí (IDE) sady Visual Studio. Následuje seznam možností kompilátoru příkazového řádku Visual Basic seřazených podle funkční kategorie.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Výstup kompilátoru  
  
|Možnost|Účel|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Potlačí informace banneru kompilátoru.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Vytvoří výstup dalších informací během kompilace.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu.|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
  
## <a name="optimization"></a>Optimalizace  
  
|Možnost|Účel|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Určuje, kam se mají zarovnat oddíly výstupního souboru.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Povolí nebo zakáže optimalizace.|  
  
## <a name="output-files"></a>Výstupní soubory  
  
|Možnost|Účel|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Zpracuje komentáře dokumentace do souboru XML.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Způsobí, že kompilátor výstupuje sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Nastaví kompilátor pro cílení na prostředí .NET Compact Framework.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Určuje výstupní soubor.|  
|[-refonly](refonly-compiler-option.md)|Výstupuje pouze referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje výstupní cestu pro referenční sestavení.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Určuje formát výstupu.|  
  
## <a name="net-assemblies"></a>Sestavení .NET  
  
|Možnost|Účel|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje obor názvů ze zadaného sestavení.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Určuje název kontejneru klíče pro dvojici klíčů, který poskytne sestavení silného názvu.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Určuje soubor obsahující klíč nebo dvojici klíčů, které sestavení poskytují silný název.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Určuje umístění sestavení, na která odkazuje možnost [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) .|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadata ze sestavení.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Určuje název sestavení, jehož součástí bude modul.|  
|`-analyzer`|Spustit analyzátory z tohoto sestavení (krátký tvar:-a)|  
|`-additionalfile`|Názvy dalších souborů, které přímo neovlivňují generování kódu, ale mohou být využívány analyzátory pro vytváření chyb nebo upozornění.|  
  
## <a name="debuggingerror-checking"></a>Ladění/kontrola chyb  
  
|Možnost|Účel|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňují hlášení chyby.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Vytvoří ladicí informace.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Potlačí schopnost kompilátoru generovat upozornění.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Zakáže kontrolu přetečení celých čísel.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Propaguje upozornění na chyby.|  
|`-ruleset:<file>`|Zadejte soubor RuleSet, který zakáže konkrétní diagnostiku.|  
  
## <a name="help"></a>Nápověda  
  
|Možnost|Účel|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako při zadávání `-help` možnosti. Nedochází k žádné kompilaci.|  
|[-Help](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako při zadávání `-?` možnosti. Nedochází k žádné kompilaci.|  
  
## <a name="language"></a>Jazyk  
  
|Možnost|Účel|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Určete jazykovou verzi: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Vynutil explicitní deklaraci proměnných.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Vynutil sémantiku striktního typu.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Určuje, zda mají být porovnávání řetězců binární, nebo použijte sémantiku textu specifickou pro národní prostředí.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Povoluje použití odvození místního typu v deklaracích proměnných.|  
  
## <a name="preprocessor"></a>Preprocesor  
  
|Možnost|Účel|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definuje symboly pro podmíněnou kompilaci.|  
  
## <a name="resources"></a>Prostředky  
  
|Možnost|Účel|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Vytvoří odkaz na spravovaný prostředek.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Vloží spravovaný prostředek do sestavení.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Vloží soubor. ico do výstupního souboru.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Vloží prostředek Win32 do výstupního souboru.|  
  
## <a name="miscellaneous"></a>Různé  
  
|Možnost|Účel|  
|---|---|  
|[@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Určuje soubor odpovědí.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Určuje základní adresu knihovny DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Určuje, jak by měl kompilátor Visual Basic hlásit vnitřní chyby kompilátoru.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Oznamuje jádru systému Windows, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru entropie (ASLR).|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Určuje třídu, která obsahuje `Sub Main` proceduru, která se má použít při spuštění.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nekompilovat pomocí vbc. rsp|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Způsobí, že kompilátor neodkazuje na standardní knihovny.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instruuje kompilátor, aby nevložil žádný manifest aplikace do spustitelného souboru.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Určuje platformu procesoru, kterou kompilátor cílí na výstupní soubor.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Vyhledá v podadresářích zdrojové soubory, které se mají kompilovat.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Určuje obor názvů pro všechny deklarace typů.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Určuje umístění knihovny mscorlib. dll a Microsoft. VisualBasic. dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Určuje, že má kompilátor kompilovat bez odkazu na knihovnu modulu runtime Visual Basic, nebo s odkazem na konkrétní běhovou knihovnu.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifikuje uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.|  
|`-parallel[+&#124;-]`|Určuje, jestli se má použít souběžné sestavení (+).|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256. <br>Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.|  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic možnosti kompilátoru seřazené abecedně](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Správa vlastností projektu a řešení](/visualstudio/ide/managing-project-and-solution-properties)
