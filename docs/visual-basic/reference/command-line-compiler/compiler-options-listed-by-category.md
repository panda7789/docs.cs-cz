---
title: Možnosti kompilátoru uvedené podle kategorie
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 533d3da2f76854d311262ce97b43f240acab5f7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408748"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Visual Basic možnosti kompilátoru uvedené podle kategorie
Kompilátor příkazového řádku Visual Basic je k dispozici jako alternativa k kompilování programů z integrovaného vývojového prostředí (IDE) sady Visual Studio. Následuje seznam možností kompilátoru příkazového řádku Visual Basic seřazených podle funkční kategorie.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Výstup kompilátoru  
  
|Možnost|Účel|  
|---|---|  
|[-nologo](nologo.md)|Potlačí informace banneru kompilátoru.|  
|[-utf8output](utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-verbose](verbose.md)|Vytvoří výstup dalších informací během kompilace.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu.|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
  
## <a name="optimization"></a>Optimalizace  
  
|Možnost|Účel|  
|---|---|  
|[-filealign](filealign.md)|Určuje, kam se mají zarovnat oddíly výstupního souboru.|  
|[– optimalizovat](optimize.md)|Povolí nebo zakáže optimalizace.|  
  
## <a name="output-files"></a>Výstupní soubory  
  
|Možnost|Účel|  
|---|---|  
|[-doc](doc.md)|Zpracuje komentáře dokumentace do souboru XML.|  
|[-deterministic](deterministic.md)|Způsobí, že kompilátor výstupuje sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.|
|[-netcf](netcf.md)|Nastaví kompilátor pro cílení na prostředí .NET Compact Framework.|  
|[-out](out.md)|Určuje výstupní soubor.|  
|[-refonly](refonly-compiler-option.md)|Výstupuje pouze referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje výstupní cestu pro referenční sestavení.|
|[-target](target.md)|Určuje formát výstupu.|  
  
## <a name="net-assemblies"></a>Sestavení .NET  
  
|Možnost|Účel|  
|---|---|  
|[-addmodule](addmodule.md)|Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.|  
|[-delaysign](delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-imports](imports.md)|Importuje obor názvů ze zadaného sestavení.|  
|[-keycontainer](keycontainer.md)|Určuje název kontejneru klíče pro dvojici klíčů, který poskytne sestavení silného názvu.|  
|[-keyfile](keyfile.md)|Určuje soubor obsahující klíč nebo dvojici klíčů, které sestavení poskytují silný název.|  
|[-libpath](libpath.md)|Určuje umístění sestavení, na která odkazuje možnost [-reference](reference.md) .|  
|[– Referenční informace](reference.md)|Importuje metadata ze sestavení.|  
|[-moduleassemblyname](moduleassemblyname.md)|Určuje název sestavení, jehož součástí bude modul.|  
|`-analyzer`|Spustit analyzátory z tohoto sestavení (krátký tvar:-a)|  
|`-additionalfile`|Názvy dalších souborů, které přímo neovlivňují generování kódu, ale mohou být využívány analyzátory pro vytváření chyb nebo upozornění.|  
  
## <a name="debuggingerror-checking"></a>Ladění/kontrola chyb  
  
|Možnost|Účel|  
|---|---|  
|[-bugreport](bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňují hlášení chyby.|  
|[– ladění](debug.md)|Vytvoří ladicí informace.|  
|[-nowarn](nowarn.md)|Potlačí schopnost kompilátoru generovat upozornění.|  
|[-quiet](quiet.md)|Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.|  
|[-removeintchecks](removeintchecks.md)|Zakáže kontrolu přetečení celých čísel.|  
|[-warnaserror](warnaserror.md)|Propaguje upozornění na chyby.|  
|`-ruleset:<file>`|Zadejte soubor RuleSet, který zakáže konkrétní diagnostiku.|  
  
## <a name="help"></a>Nápověda  
  
|Možnost|Účel|  
|---|---|  
|[-?](help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako při zadávání `-help` Možnosti. Nedochází k žádné kompilaci.|  
|[-Help](help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako při zadávání `-?` Možnosti. Nedochází k žádné kompilaci.|  
  
## <a name="language"></a>Jazyk  
  
|Možnost|Účel|  
|---|---|  
|[-langversion](langversion.md)|Zadejte jazykovou verzi: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-optionexplicit](optionexplicit.md)|Vynutil explicitní deklaraci proměnných.|  
|[-optionstrict](optionstrict.md)|Vynutil sémantiku striktního typu.|  
|[-optioncompare](optioncompare.md)|Určuje, zda mají být porovnávání řetězců binární, nebo použijte sémantiku textu specifickou pro národní prostředí.|  
|[-optioninfer](optioninfer.md)|Povoluje použití odvození místního typu v deklaracích proměnných.|  
  
## <a name="preprocessor"></a>Preprocesor  
  
|Možnost|Účel|  
|---|---|  
|[-define](define.md)|Definuje symboly pro podmíněnou kompilaci.|  
  
## <a name="resources"></a>Zdroje a prostředky  
  
|Možnost|Účel|  
|---|---|  
|[-linkresource](linkresource.md)|Vytvoří odkaz na spravovaný prostředek.|  
|[– prostředek](resource.md)|Vloží spravovaný prostředek do sestavení.|  
|[-win32icon](win32icon.md)|Vloží soubor. ico do výstupního souboru.|  
|[-win32resource](win32resource.md)|Vloží prostředek Win32 do výstupního souboru.|  
  
## <a name="miscellaneous"></a>Různé  
  
|Možnost|Účel|  
|---|---|  
|[@ (určení souboru odezvy)](specify-response-file.md)|Určuje soubor odpovědí.|  
|[-baseaddress](baseaddress.md)|Určuje základní adresu knihovny DLL.|  
|[-codepage](codepage.md)|Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.|  
|[-errorreport](errorreport.md)|Určuje, jak by měl kompilátor Visual Basic hlásit vnitřní chyby kompilátoru.|  
|[-highentropyva](highentropyva.md)|Oznamuje jádru systému Windows, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru entropie (ASLR).|  
|[-main](main.md)|Určuje třídu, která obsahuje `Sub Main` proceduru, která se má použít při spuštění.|  
|[-noconfig](noconfig.md)|Nekompilovat pomocí vbc. rsp|  
|[-nostdlib](nostdlib.md)|Způsobí, že kompilátor neodkazuje na standardní knihovny.|  
|[-nowin32manifest](nowin32manifest.md)|Instruuje kompilátor, aby nevložil žádný manifest aplikace do spustitelného souboru.|  
|[– platforma](platform.md)|Určuje platformu procesoru, kterou kompilátor cílí na výstupní soubor.|  
|[-recurse](recurse.md)|Vyhledá v podadresářích zdrojové soubory, které se mají kompilovat.|  
|[-rootnamespace](rootnamespace.md)|Určuje obor názvů pro všechny deklarace typů.|  
|[-sdkpath](sdkpath.md)|Určuje umístění knihovny mscorlib. dll a Microsoft. VisualBasic. dll.|  
|[-vbruntime](vbruntime.md)|Určuje, že má kompilátor kompilovat bez odkazu na knihovnu modulu runtime Visual Basic, nebo s odkazem na konkrétní běhovou knihovnu.|  
|[-win32manifest](win32manifest.md)|Identifikuje uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.|  
|`-parallel[+&#124;-]`|Určuje, jestli se má použít souběžné sestavení (+).|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256. <br>Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.|  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka Visual Basic v abecedním pořadí](compiler-options-listed-alphabetically.md)
- [Správa vlastností projektu a řešení](/visualstudio/ide/managing-project-and-solution-properties)
