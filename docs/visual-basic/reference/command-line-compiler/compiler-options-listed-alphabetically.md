---
title: Možnosti kompilátoru jazyka Visual Basic v abecedním pořadí
ms.date: 03/09/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c78246a1e9fe14b0ba64ac447293d02e8416079
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Možnosti kompilátoru jazyka Visual Basic abecední
Visual Basic – kompilátor příkazového řádku je k dispozici jako alternativu k kompilace programů z [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Následuje seznam řadí abecedně možnosti příkazového řádku kompilátoru jazyka Visual Basic.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Možnost|Účel|  
|------------|-------------|  
|[@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Určuje soubor odezvy.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-help` možnost. Dojde k žádné kompilace.|  
|`-additionalfile`|Názvy další soubory, které neovlivňují přímo generování kódu, ale může být používán analyzátory pro vytvoření chyby nebo upozornění.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Způsobí, že kompilátor zkontrolujte všechny informace ze zadané soubory, které jsou k dispozici do projektu, které jsou aktuálně kompilování typu.|  
|`-analyzer`|Spusťte analyzátory z tohoto sestavení (krátký tvar: - a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Určuje základní adresy knihovny DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Vytvoří soubor, který obsahuje informace, které usnadňuje ohlásit chybu.|  
|`-checksumalgorithm:<alg>`|Zadejte algoritmus pro výpočet kontrolní součet souboru zdroje uložené v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Určuje znakovou stránku pro všechny soubory zdrojového kódu v kompilace.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Vytváří ladicí informace.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definuje symboly pro Podmíněná kompilace.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Určuje, zda bude sestavení zcela nebo částečně podepsáno.|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Zpracuje dokumentační komentáře do souboru XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Určuje, jak by měla Visual Basic – kompilátor zprávy o chybách interní kompilátoru.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Určuje, kde chcete-li zarovnat na části výstupní soubor.|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|Zobrazí možnosti kompilátoru. Tento příkaz je stejné jako zadání `-?` možnost. Dojde k žádné kompilace.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Určuje, jestli konkrétní spustitelný soubor podporuje vysokou entropie místo rozložení náhodného přeskupování (technologie ASLR) adres.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje oboru názvů ze zadaného sestavení.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Určuje název kontejneru klíčů pro pár klíčů umožnit sestavení silným názvem.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Určuje soubor, který obsahuje klíč nebo pár klíčů umožnit sestavení silným názvem.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Zadejte jazyková verze: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Určuje umístění sestavení odkazuje [– referenční dokumentace](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Vytvoří odkaz na spravovaných prostředků.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Určuje třídu, která obsahuje `Sub Main` postupu se má provést při spuštění.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Určuje název sestavení, které modul bude součástí.|  
|`-modulename:<string>`|Zadejte název zdrojového modulu|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nejde kompilovat s Vbc.rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Potlačí informace kompilátoru.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Způsobí, že kompilátor není tak, aby odkazovaly na standardní knihovny.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Potlačí schopnost kompilátoru generovat upozornění.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Dá pokyn kompilátoru není pro vložení jakýkoli manifest aplikace do spustitelného souboru.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Povolí nebo zakáže kódu optimalizace.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Určuje, zda porovnání řetězců by měla být binární nebo používají sémantiku text specifická pro národní prostředí.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Vynucuje explicitní deklarace proměnné.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umožňuje použití odvození místního typu v deklarace proměnných.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Vynutí striktní sémantiku jazyka.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Určuje výstupní soubor.|  
|`-parallel[+&#124;-]`|Určuje, jestli se má používat souběžných sestavení (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Určuje procesor platformy kompilátoru cíle pro výstupní soubor.|  
|`-preferreduilang`|Zadejte název jazyka upřednostňované výstup.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zabrání zobrazení kódu syntaxe související chyby a upozornění kompilátoru.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Vyhledá podadresáře pro zdrojové soubory pro kompilaci.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Naimportuje metadata ze sestavení.|  
|[-refonly](refonly-compiler-option.md)|Výstupy referenční sestavení.|
|[-refout](refout-compiler-option.md)|Určuje cestu výstupního referenční sestavení.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Zakáže kontrola přetečení celé číslo.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Vloží spravovaných prostředků v sestavení.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Určuje obor názvů pro všechny deklarace typu.|  
|`-ruleset:<file>`|Zadejte soubor ruleset zakazující diagnostiky specifické.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Určuje umístění Mscorlib.dll a souboru Microsoft.VisualBasic.dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Určuje minimální verze subsystému, můžete použít vygenerovaný spustitelný soubor.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Určuje formát výstupního souboru.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Určuje, že by měl kompilátor kompilovat bez odkaz na Visual Basic Runtime Library nebo s odkazem na knihovnu konkrétní runtime.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Výstupy doplňující informace během kompilace.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Zvýší úroveň upozornění na chyby.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Soubor .ico, který se vloží do výstupního souboru.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifikuje uživatelem definované souboru manifestu aplikace Win32, který má být vložen do souboru projektu přenosné spustitelný soubor (PE).|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Vloží prostředek systému Win32 do výstupní soubor.|  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – možnosti kompilátoru uvedené podle kategorie](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)  
 [Úvod do Návrhář projektu](http://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)  
 [Možnosti kompilátoru jazyka C# (abecední pořadí)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Možnosti kompilátoru jazyka C# uvedené podle kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)
