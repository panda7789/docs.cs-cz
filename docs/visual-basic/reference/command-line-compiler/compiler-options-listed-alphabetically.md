---
title: Možnosti kompilátoru jazyka Visual Basic v abecedním pořadí
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f24759d68f007caf5f79096c6d4cebb7c050851
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262318"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Abecedně seřazené možnosti kompilátoru jazyka Visual Basic
Kompilátor příkazového řádku jazyka Visual Basic se poskytuje jako alternativu ke kompilaci programů z integrovaného vývojového prostředí (IDE) sady Visual Studio. Následuje seznam možností příkazového řádku kompilátoru jazyka Visual Basic, seřazená podle abecedy.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Možnost|Účel|  
|------------|-------------|  
|[@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Určuje soubor odpovědí.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-help` možnost. Vyvolá se v žádné kompilace.|  
|`-additionalfile`|Názvy další soubory, které nemají přímý vliv na generování kódu, ale může používat analyzátory pro vytvoření chyby nebo varování.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Způsobí, že kompilátor, aby všechny informace ze zadané soubory, které jsou k dispozici do projektu je aktuálně kompilován typu.|  
|`-analyzer`|Spustit analyzátory z tohoto sestavení (krátký tvar: - a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Určuje základní adresu knihovny DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňuje hlášení chyby.|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolního součtu souboru zdroje uloženo v PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Vytvoří ladicí informace.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definuje symboly podmíněné kompilace.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Způsobí, že kompilátor do výstupního sestavení, jejichž binární obsah je identické napříč kompilace Pokud vstupů jsou stejné.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Zpracuje komentáře dokumentace do souboru XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Určuje, jak by měl kompilátor jazyka Visual Basic ohlásit interní chyby kompilátoru.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Určuje, kam chcete zarovnat oddíly výstupního souboru.|  
|[– Nápověda](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-?` možnost. Vyvolá se v žádné kompilace.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Určuje, zda konkrétní spustitelný soubor podporuje vysokou entropie adresu místo rozložení náhodné (ASLR).|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importy oboru názvů ze zadaného sestavení.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Určuje název kontejneru klíčů pro dvojice klíčů poskytnout sestavení silným názvem.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Určuje soubor, který obsahuje klíč nebo dvojici klíčů poskytnout sestavení silným názvem.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Určení jazykové verze: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Určuje umístění sestavení odkazuje [– referenční dokumentace](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Vytvoří odkaz na spravovaný prostředek.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Určuje třídu, která obsahuje `Sub Main` postup máte použít při spuštění.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Určuje název sestavení, které modul bude součástí.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nejde zkompilovat Vbc.rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Potlačí informace kompilátoru.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Způsobí, že kompilátor nelze odkazovat na standardní knihovny.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Potlačí umožňuje kompilátoru generovat upozornění.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Dá pokyn kompilátoru, aby jakýkoli manifest aplikace pro vložení do spustitelného souboru.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Povolí nebo zakáže kódu optimalizace.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Určuje, zda by měly být binární nebo používají sémantiku specifických pro národní prostředí textové porovnávání řetězců.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Vynucuje explicitní deklaraci proměnných.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umožňuje použití odvození místního typu v deklaraci proměnných.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Vynutí striktní sémantiku jazyka.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Určuje výstupní soubor.|  
|`-parallel[+&#124;-]`|Určuje, jestli se má použít souběžné sestavení (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Určuje procesor platformy kompilátoru cíle pro výstupní soubor.|  
|`-preferreduilang`|Zadejte název upřednostňovaného výstupního jazyka.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zabrání zobrazení kódu pro syntaxi související chyby a upozornění kompilátoru.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Prohledává podadresáře pro zdrojové soubory pro kompilaci.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadata ze sestavení.|  
|[-refonly](refonly-compiler-option.md)|Vypíše referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje výstupní cestu k referenčnímu sestavení.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Zakáže kontrolu přetečení celého čísla.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Vloží spravovaný prostředek sestavení.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Určuje obor názvů pro všechny deklarace typů.|  
|`-ruleset:<file>`|Zadejte soubor sady pravidel, která zakáže konkrétní diagnostiky.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Určuje umístění knihovny Mscorlib.dll a Microsoft.VisualBasic.dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Určuje minimální verzi podsystému, který může používat vygenerovaný spustitelný soubor.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Určuje formát výstupního souboru.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Určuje, že kompilátor by měl kompilovat bez odkazu do knihovny prostředí Runtime jazyka Visual Basic nebo s odkazem na knihovně modulu runtime specifické.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Vypíše dodatečné informace během kompilace.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Zvýší úroveň upozornění na chyby.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Vloží soubor .ico do výstupního souboru.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Určuje uživatelský soubor manifestu aplikace Win32, který má být vložen do projektu soubor (PE portable executable).|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Vloží prostředek systému Win32 do výstupní soubor.|  
  
## <a name="see-also"></a>Viz také:  
 [Možnosti kompilátoru jazyka Visual Basic uvedené podle kategorie](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)  
 [Úvod do Návrháře projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)  
 [Možnosti kompilátoru jazyka C# (abecední pořadí)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Možnosti kompilátoru jazyka C# uvedené podle kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)
