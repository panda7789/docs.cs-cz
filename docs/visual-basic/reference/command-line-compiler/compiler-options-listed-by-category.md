---
title: Možnosti kompilátoru jazyka Visual Basic uvedené podle kategorie
ms.date: 04/12/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90c54ae1bb4d89b2fbe0df62730bc55c0ceb64f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Visual Basic – možnosti kompilátoru uvedené podle kategorie
Visual Basic – kompilátor příkazového řádku je k dispozici jako alternativu k kompilace programů z v sadě Visual Studio integrované vývojové prostředí (IDE). Následuje seznam možností příkazového řádku kompilátoru jazyka Visual Basic, seřazené podle kategorie funkční.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Výstup kompilátoru  
  
|Možnost|Účel|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Potlačí informace kompilátoru.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Výstupy doplňující informace během kompilace.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
  
## <a name="optimization"></a>Optimalizace  
  
|Možnost|Účel|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Určuje, kde chcete-li zarovnat na části výstupní soubor.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Povolí nebo zakáže optimalizace.|  
  
## <a name="output-files"></a>Výstupní soubory  
  
|Možnost|Účel|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Proces dokumentační komentáře do souboru XML.|  
|[-deterministickou](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Způsobí, že kompilátor výstup sestavení jejichž binární obsah je stejný jako napříč kompilace Pokud vstupní hodnoty jsou identické.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Určuje výstupní soubor.|  
|[-refonly](refonly-compiler-option.md)|Výstupy referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje cestu výstupního referenční sestavení.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Určuje formát výstupu.|  
  
## <a name="net-assemblies"></a>Sestavení .NET  
  
|Možnost|Účel|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Způsobí, že kompilátor zkontrolujte všechny informace ze zadané soubory, které jsou k dispozici do projektu, které jsou aktuálně kompilování typu.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje oboru názvů ze zadaného sestavení.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Určuje název kontejneru klíčů pro pár klíčů umožnit sestavení silným názvem.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Určuje soubor, který obsahuje klíč nebo pár klíčů umožnit sestavení silným názvem.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Určuje umístění sestavení odkazuje [– referenční dokumentace](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Naimportuje metadata ze sestavení.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Určuje název sestavení, které modul bude součástí.|  
|`-analyzer`|Spusťte analyzátory z tohoto sestavení (krátký tvar: - a)|  
|`-additionalfile`|Názvy další soubory, které neovlivňují přímo generování kódu, ale může být používán analyzátory pro vytvoření chyby nebo upozornění.|  
  
## <a name="debuggingerror-checking"></a>Ladění a kontrola chyb  
  
|Možnost|Účel|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňuje ohlásit chybu.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Vytváří ladicí informace.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Potlačí schopnost kompilátoru generovat upozornění.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zabrání zobrazení kódu syntaxe související chyby a upozornění kompilátoru.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Zakáže kontrola přetečení celé číslo.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Zvýší úroveň upozornění na chyby.|  
|`-ruleset:<file>`|Zadejte soubor ruleset zakazující diagnostiky specifické.|  
  
## <a name="help"></a>Nápověda  
  
|Možnost|Účel|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-help` možnost. Dojde k žádné kompilace.|  
|[– Nápověda](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-?` možnost. Dojde k žádné kompilace.|  
  
## <a name="language"></a>Jazyk  
  
|Možnost|Účel|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Zadejte jazyková verze: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Vynucuje explicitní deklarace proměnné.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Vynucuje přísné typ sémantiku.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Určuje, zda porovnání řetězců by měla být binární nebo používají sémantiku text specifická pro národní prostředí.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umožňuje použití odvození místního typu v deklarace proměnných.|  
  
## <a name="preprocessor"></a>Preprocesor  
  
|Možnost|Účel|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definuje symboly pro Podmíněná kompilace.|  
  
## <a name="resources"></a>Prostředky  
  
|Možnost|Účel|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Vytvoří odkaz na spravovaných prostředků.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Vloží spravovaných prostředků v sestavení.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Soubor .ico, který se vloží do výstupního souboru.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Vloží prostředek systému Win32 do výstupní soubor.|  
  
## <a name="miscellaneous"></a>Různé  
  
|Možnost|Účel|  
|---|---|  
|[@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Určuje soubor odezvy.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Určuje základní adresy knihovny DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Určuje znakovou stránku pro všechny soubory zdrojového kódu v kompilace.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Určuje, jak by měla Visual Basic – kompilátor zprávy o chybách interní kompilátoru.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Informuje jádro systému Windows, jestli konkrétní spustitelný soubor podporuje vysokou entropie místo rozložení náhodného přeskupování (technologie ASLR) adres.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Určuje třídu, která obsahuje `Sub Main` postupu se má provést při spuštění.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nejde kompilovat s Vbc.rsp|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Způsobí, že kompilátor není tak, aby odkazovaly na standardní knihovny.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Dá pokyn kompilátoru není pro vložení jakýkoli manifest aplikace do spustitelného souboru.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Určuje procesor platformy kompilátoru cíle pro výstupní soubor.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Vyhledá podadresáře pro zdrojové soubory pro kompilaci.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Určuje obor názvů pro všechny deklarace typu.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Určuje umístění Mscorlib.dll a souboru Microsoft.VisualBasic.dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Určuje, že by měl kompilátor kompilovat bez odkaz na Visual Basic Runtime Library nebo s odkazem na knihovnu konkrétní runtime.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifikuje uživatelem definované souboru manifestu aplikace Win32, který má být vložen do souboru projektu přenosné spustitelný soubor (PE).|  
|`-parallel[+&#124;-]`|Určuje, jestli se má používat souběžných sestavení (+).|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolní součet souboru zdroje uložené v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka Visual Basic abecední](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)  
 [Úvod do Návrhář projektu](https://msdn.microsoft.com/en-us/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))  
 [Možnosti kompilátoru jazyka C# (abecední pořadí)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Možnosti kompilátoru jazyka C# uvedené podle kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)
