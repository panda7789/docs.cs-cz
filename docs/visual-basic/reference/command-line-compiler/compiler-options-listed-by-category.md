---
title: Možnosti kompilátoru jazyka Visual Basic uvedené podle kategorie
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: b945edca8bd739e6f122ed8b3e950508ecc28510
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268162"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Možnosti kompilátoru jazyka Visual Basic uvedené podle kategorie
Kompilátor příkazového řádku jazyka Visual Basic se poskytuje jako alternativu ke kompilaci programů z v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio. Následuje seznam možností příkazového řádku kompilátoru jazyka Visual Basic, seřazené podle kategorie funkcí.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Výstup kompilátoru  
  
|Možnost|Účel|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Potlačí informace kompilátoru.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Vypíše dodatečné informace během kompilace.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
  
## <a name="optimization"></a>Optimalizace  
  
|Možnost|Účel|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Určuje, kam chcete zarovnat oddíly výstupního souboru.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Povolí nebo zakáže optimalizace.|  
  
## <a name="output-files"></a>Výstupní soubory  
  
|Možnost|Účel|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Zpracuje komentáře dokumentace do souboru XML.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Způsobí, že kompilátor do výstupního sestavení, jejichž binární obsah je identické napříč kompilace Pokud vstupů jsou stejné.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Nastaví kompilátoru cílit na .NET Compact Framework.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Určuje výstupní soubor.|  
|[-refonly](refonly-compiler-option.md)|Vypíše referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje výstupní cestu k referenčnímu sestavení.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Určuje formát výstupu.|  
  
## <a name="net-assemblies"></a>Sestavení .NET  
  
|Možnost|Účel|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Způsobí, že kompilátor, aby všechny informace ze zadané soubory, které jsou k dispozici do projektu je aktuálně kompilován typu.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importy oboru názvů ze zadaného sestavení.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Určuje název kontejneru klíčů pro dvojice klíčů poskytnout sestavení silným názvem.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Určuje soubor, který obsahuje klíč nebo dvojici klíčů poskytnout sestavení silným názvem.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Určuje umístění sestavení odkazuje [– referenční dokumentace](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadata ze sestavení.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Určuje název sestavení, které modul bude součástí.|  
|`-analyzer`|Spustit analyzátory z tohoto sestavení (krátký tvar: - a)|  
|`-additionalfile`|Názvy další soubory, které nemají přímý vliv na generování kódu, ale může používat analyzátory pro vytvoření chyby nebo varování.|  
  
## <a name="debuggingerror-checking"></a>Ladění a kontrola chyb  
  
|Možnost|Účel|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňuje hlášení chyby.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Vytvoří ladicí informace.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Potlačí umožňuje kompilátoru generovat upozornění.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zabrání zobrazení kódu pro syntaxi související chyby a upozornění kompilátoru.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Zakáže kontrolu přetečení celého čísla.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Zvýší úroveň upozornění na chyby.|  
|`-ruleset:<file>`|Zadejte soubor sady pravidel, která zakáže konkrétní diagnostiky.|  
  
## <a name="help"></a>Help  
  
|Možnost|Účel|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-help` možnost. Vyvolá se v žádné kompilace.|  
|[– Nápověda](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-?` možnost. Vyvolá se v žádné kompilace.|  
  
## <a name="language"></a>Jazyk  
  
|Možnost|Účel|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Určení jazykové verze: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Vynucuje explicitní deklaraci proměnných.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Vynutí sémantiku přísného typu.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Určuje, zda by měly být binární nebo používají sémantiku specifických pro národní prostředí textové porovnávání řetězců.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umožňuje použití odvození místního typu v deklaraci proměnných.|  
  
## <a name="preprocessor"></a>Preprocesor  
  
|Možnost|Účel|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definuje symboly podmíněné kompilace.|  
  
## <a name="resources"></a>Prostředky  
  
|Možnost|Účel|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Vytvoří odkaz na spravovaný prostředek.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Vloží spravovaný prostředek sestavení.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Vloží soubor .ico do výstupního souboru.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Vloží prostředek systému Win32 do výstupní soubor.|  
  
## <a name="miscellaneous"></a>Různé  
  
|Možnost|Účel|  
|---|---|  
|[@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Určuje soubor odpovědí.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Určuje základní adresu knihovny DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Určuje, jak by měl kompilátor jazyka Visual Basic ohlásit interní chyby kompilátoru.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Určuje, zda konkrétní spustitelný soubor podporuje vysokou entropie místo rozložení náhodné (technologie ASLR) Adresa říká jádra Windows.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Určuje třídu, která obsahuje `Sub Main` postup máte použít při spuštění.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nejde zkompilovat Vbc.rsp|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Způsobí, že kompilátor nelze odkazovat na standardní knihovny.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Dá pokyn kompilátoru, aby jakýkoli manifest aplikace pro vložení do spustitelného souboru.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Určuje procesor platformy kompilátoru cíle pro výstupní soubor.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Prohledává podadresáře pro zdrojové soubory pro kompilaci.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Určuje obor názvů pro všechny deklarace typů.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Určuje umístění knihovny Mscorlib.dll a Microsoft.VisualBasic.dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Určuje, že kompilátor by měl kompilovat bez odkazu do knihovny prostředí Runtime jazyka Visual Basic nebo s odkazem na knihovně modulu runtime specifické.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Určuje uživatelský soubor manifestu aplikace Win32, který má být vložen do projektu soubor (PE portable executable).|  
|`-parallel[+&#124;-]`|Určuje, jestli se má použít souběžné sestavení (+).|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolního součtu souboru zdroje uloženo v PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|  
  
## <a name="see-also"></a>Viz také:

- [Abecedně seřazené možnosti kompilátoru jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Správa vlastností projektu a řešení](/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)
