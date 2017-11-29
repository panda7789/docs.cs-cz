---
title: "Možnosti kompilátoru C# uvedené podle kategorie"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95c5c3d1c7ea2461e9bda9a1d58464e97ccc688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="c-compiler-options-listed-by-category"></a>Možnosti kompilátoru C# uvedené podle kategorie
Následující možnosti kompilátoru jsou seřazeny podle kategorie. Abecední seznam najdete v tématu [Možnosti C# kompilátoru seřazeny abecedně](../../../csharp/language-reference/compiler-options/listed-alphabetically.md).  
  
### <a name="optimization"></a>Optimalizace  
  
|Možnost|Účel|  
|------------|-------------|  
|[/ filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Určuje velikost oddílů ve výstupním souboru.|  
|[/ optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|  
  
### <a name="output-files"></a>Výstupní soubory  
  
|Možnost|Účel|  
|------------|-------------|  
|[/ DOC](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|Určuje soubor XML, kde jsou zpracované dokumentační komentáře k zapsání.|  
|[/ Out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Určuje výstupní soubor.|  
|[/ pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|Určuje název souboru a umístění souboru pdb.|  
|[/ Platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Zadejte výstupní platformy.|  
|[/ preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|  
|[/refout](refout-compiler-option.md)|Generovat odkaz na sestavení kromě primární sestavení.|  
|[/refonly](refonly-compiler-option.md)|Generovat odkaz na sestavení namísto primární sestavení.|  
|[/ target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné z pěti možností: [/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [/target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md), [/target: library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md),  [ /target: module ](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), nebo [/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|/MODULENAME:\<řetězec >|Zadejte název zdrojového modulu|  
  
### <a name="net-framework-assemblies"></a>Sestavení rozhraní .NET framework  
  
|Možnost|Účel|  
|------------|-------------|  
|[/ addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Určuje jeden nebo více modulů jako součást tohoto sestavení.|  
|[/ delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Dá pokyn kompilátoru přidejte veřejný klíč, ale ponechte sestavení bez znaménka.|  
|[/ keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Určuje název kontejneru kryptografických klíčů.|  
|[/ keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Určuje název souboru obsahujícího kryptografický klíč.|  
|[/ lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Určuje umístění sestavení odkazovaných pomocí možnosti [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).|  
|[/ nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Dá pokyn kompilátoru Neimportovat standardní knihovnu (mscorlib.dll).|  
|[/ Reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Naimportuje metadata ze souboru, který obsahuje sestavení.|  
|/Analyzer|Spusťte analyzátory z tohoto sestavení (krátký tvar: / a)|  
|/additionalfile|Názvy další soubory, které neovlivňují přímo generování kódu, ale může být používán analyzátory pro vytvoření chyby nebo upozornění.|  
  
### <a name="debuggingerror-checking"></a>Ladění a kontrola chyb  
  
|Možnost|Účel|  
|------------|-------------|  
|[/ bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Vytvoří soubor, který obsahuje informace, které usnadňuje ohlásit chybu.|  
|[/ checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Určuje, zda celé číslo aritmetické, která přesahuje hranice typu dat, způsobí výjimku za běhu.|  
|[/ Debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Pokyn kompilátoru k Generovat ladicí informace.|  
|[/ errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Nastaví chování zpráv o chybách.|  
|[/ fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Určuje absolutní cestu k souboru ve výstupu kompilátoru.|  
|[/ nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Potlačí kompilátoru generování zadaných upozornění.|  
|[/ warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Nastaví úroveň pro upozornění.|  
|[/ warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Zvýší úroveň upozornění na chyby.|  
|/RuleSet:\<souboru >|Zadejte soubor ruleset zakazující diagnostiky specifické.|  
  
### <a name="preprocessor"></a>Preprocesor  
  
|Možnost|Účel|  
|------------|-------------|  
|[/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Definuje preprocesoru symboly.|  
  
### <a name="resources"></a>Prostředky  
  
|Možnost|Účel|  
|------------|-------------|  
|[/ Link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaném sestavení do projektu.|  
|[/ linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Vytvoří odkaz na spravovaných prostředků.|  
|[/ Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|Vloží prostředek rozhraní .NET Framework do výstupního souboru.|  
|[/ win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Určuje soubor .ico, který chcete vložit do výstupního souboru.|  
|[/ win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Určuje prostředek systému Win32 vložení do výstupního souboru.|  
  
### <a name="miscellaneous"></a>Různé  
  
|Možnost|Účel|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Určuje soubor odezvy.|  
|[/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Zobrazí seznam možností kompilátoru do stdout.|  
|[/ BaseAddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Určuje upřednostňovaná základní adresa, na které se mají načíst knihovnu DLL.|  
|[/ codePage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Určuje znakovou stránku pro všechny soubory zdrojového kódu v kompilace.|  
|[/ Help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Zobrazí seznam možností kompilátoru do stdout.|  
|[/ highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Určuje, že spustitelný soubor podporuje adresu místa rozložení náhodné (technologie ASLR).|  
|[/ langversion](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Zadejte režim jazykové verze: výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 nebo nejnovější |  
|[/ main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Určuje umístění **hlavní** metoda.|  
|[/ noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Dá pokyn kompilátoru, aby kompilovat s csc.rsp.|  
|[/ nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Potlačí informace kompilátoru.|  
|[/ recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Vyhledá podadresáře pro zdrojové soubory pro kompilaci.|  
|[/ subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|Určuje minimální verze subsystému, můžete použít na spustitelný soubor.|  
|[/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Umožňuje kompilace kódu, který používá [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo.|  
|[/ utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|  
|/ paralelní [+ &#124;-]|Určuje, jestli se má používat souběžných sestavení (+).|  
|/checksumalgorithm:\<alg >|Zadejte algoritmus pro výpočet kontrolní součet souboru zdroje uložené v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|  
  
## <a name="obsolete-options"></a>Zastaralé možnosti  
  
|Možnost|Účel|  
|---|---|  
|/ incremental|Umožňuje přírůstkovou kompilaci.|  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Možnosti kompilátoru C# uvedené podle abecedy](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Postupy: nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
