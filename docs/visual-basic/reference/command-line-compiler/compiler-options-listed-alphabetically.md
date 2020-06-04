---
title: Možnosti kompilátoru (abecední pořadí)
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 19e14953c08f90ea1ab245fa3124a462ccba162f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408735"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Visual Basic možnosti kompilátoru seřazené abecedně
Visual Basic Kompilátor příkazového řádku je k dispozici jako alternativa k kompilování programů z integrovaného vývojového prostředí (IDE) sady Visual Studio. Následující seznam uvádí možnosti kompilátoru Visual Basic příkazového řádku seřazené abecedně.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Možnost|Účel|  
|------------|-------------|  
|[@ (určení souboru odezvy)](specify-response-file.md)|Určuje soubor odpovědí.|  
|[-?](help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako při zadávání `-help` Možnosti. Nedochází k žádné kompilaci.|  
|`-additionalfile`|Názvy dalších souborů, které přímo neovlivňují generování kódu, ale mohou být využívány analyzátory pro vytváření chyb nebo upozornění.|  
|[-addmodule](addmodule.md)|Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.|  
|`-analyzer`|Spustit analyzátory z tohoto sestavení (krátký tvar:-a)|  
|[-baseaddress](baseaddress.md)|Určuje základní adresu knihovny DLL.|  
|[-bugreport](bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňují hlášení chyby.|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256. <br>Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.|  
|[-codepage](codepage.md)|Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.|  
|[– ladění](debug.md)|Vytvoří ladicí informace.|  
|[-define](define.md)|Definuje symboly pro podmíněnou kompilaci.|  
|[-delaysign](delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-deterministic](deterministic.md)|Způsobí, že kompilátor výstupuje sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.|
|[-doc](doc.md)|Zpracuje komentáře dokumentace do souboru XML.|  
|[-errorreport](errorreport.md)|Určuje, jak by měl kompilátor Visual Basic hlásit vnitřní chyby kompilátoru.|  
|[-filealign](filealign.md)|Určuje, kam se mají zarovnat oddíly výstupního souboru.|  
|[-Help](help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejný jako při zadávání `-?` Možnosti. Nedochází k žádné kompilaci.|  
|[-highentropyva](highentropyva.md)|Určuje, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru entropie (ASLR).|  
|[-imports](imports.md)|Importuje obor názvů ze zadaného sestavení.|  
|[-keycontainer](keycontainer.md)|Určuje název kontejneru klíče pro dvojici klíčů, který poskytne sestavení silného názvu.|  
|[-keyfile](keyfile.md)|Určuje soubor, který obsahuje klíč nebo dvojici klíčů, aby sestavení mělo silný název.|  
|[-langversion](langversion.md)|Zadejte jazykovou verzi: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-libpath](libpath.md)|Určuje umístění sestavení, na která odkazuje možnost [-reference](reference.md) .|  
|[-linkresource](linkresource.md)|Vytvoří odkaz na spravovaný prostředek.|  
|[-main](main.md)|Určuje třídu, která obsahuje `Sub Main` proceduru, která se má použít při spuštění.|  
|[-moduleassemblyname](moduleassemblyname.md)|Určuje název sestavení, jehož součástí bude modul.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu.|  
|[-netcf](netcf.md)|Nastaví kompilátor pro cílení na prostředí .NET Compact Framework.|  
|[-noconfig](noconfig.md)|Nekompilovat pomocí vbc. rsp.|  
|[-nologo](nologo.md)|Potlačí informace banneru kompilátoru.|  
|[-nostdlib](nostdlib.md)|Způsobí, že kompilátor neodkazuje na standardní knihovny.|  
|[-nowarn](nowarn.md)|Potlačí schopnost kompilátoru generovat upozornění.|  
|[-nowin32manifest](nowin32manifest.md)|Instruuje kompilátor, aby nevložil žádný manifest aplikace do spustitelného souboru.|  
|[– optimalizovat](optimize.md)|Povolí nebo zakáže optimalizaci kódu.|  
|[-optioncompare](optioncompare.md)|Určuje, zda mají být porovnávání řetězců binární, nebo použijte sémantiku textu specifickou pro národní prostředí.|  
|[-optionexplicit](optionexplicit.md)|Vynutil explicitní deklaraci proměnných.|  
|[-optioninfer](optioninfer.md)|Povoluje použití odvození místního typu v deklaracích proměnných.|  
|[-optionstrict](optionstrict.md)|Vynutil striktní sémantiku jazyka.|  
|[-out](out.md)|Určuje výstupní soubor.|  
|<code>-parallel[+&#124;-]</code>|Určuje, jestli se má použít souběžné sestavení (+).|  
|[– platforma](platform.md)|Určuje platformu procesoru, kterou kompilátor cílí na výstupní soubor.|  
|`-preferreduilang`|Zadejte název upřednostňovaného výstupního jazyka.|  
|[-quiet](quiet.md)|Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.|  
|[-recurse](recurse.md)|Vyhledá v podadresářích zdrojové soubory, které se mají kompilovat.|  
|[– Referenční informace](reference.md)|Importuje metadata ze sestavení.|  
|[-refonly](refonly-compiler-option.md)|Výstupuje pouze referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje výstupní cestu pro referenční sestavení.|
|[-removeintchecks](removeintchecks.md)|Zakáže kontrolu přetečení celých čísel.|  
|[– prostředek](resource.md)|Vloží spravovaný prostředek do sestavení.|  
|[-rootnamespace](rootnamespace.md)|Určuje obor názvů pro všechny deklarace typů.|  
|`-ruleset:<file>`|Zadejte soubor RuleSet, který zakáže konkrétní diagnostiku.|  
|[-sdkpath](sdkpath.md)|Určuje umístění knihovny mscorlib. dll a Microsoft. VisualBasic. dll.|  
|[-subsystemversion](subsystemversion.md)|Určuje minimální verzi subsystému, kterou může vygenerovaný spustitelný soubor použít.|  
|[-target](target.md)|Určuje formát výstupního souboru.|  
|[-utf8output](utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-vbruntime](vbruntime.md)|Určuje, že má kompilátor kompilovat bez odkazu na knihovnu modulu runtime Visual Basic, nebo s odkazem na konkrétní běhovou knihovnu.|  
|[-verbose](verbose.md)|Vytvoří výstup dalších informací během kompilace.|  
|[-warnaserror](warnaserror.md)|Propaguje upozornění na chyby.|  
|[-win32icon](win32icon.md)|Vloží soubor. ico do výstupního souboru.|  
|[-win32manifest](win32manifest.md)|Identifikuje uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.|  
|[-win32resource](win32resource.md)|Vloží prostředek Win32 do výstupního souboru.|  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka Visual Basic uvedené podle kategorie](compiler-options-listed-by-category.md)
- [Správa vlastností projektu a řešení](/visualstudio/ide/managing-project-and-solution-properties)
