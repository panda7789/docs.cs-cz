---
title: "Možnosti kompilátoru C# (abecední pořadí)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f4d7f1b122d3481dc8c3c5256ee361965846a830
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2018
---
# <a name="c-compiler-options-listed-alphabetically"></a>Možnosti kompilátoru C# (abecední pořadí)
Následující možnosti kompilátoru jsou seřazeny podle abecedy. Seznam kategorií, najdete v části [C# kompilátoru možnosti uvedené podle kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md).  
  
|Možnost|Účel|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Přečte soubor odpovědí pro další možnosti.|  
|[-?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Zobrazí zprávu využití pro stdout.|  
|-additionalfile|Názvy další soubory, které neovlivňují přímo generování kódu, ale může být používán analyzátory pro vytvoření chyby nebo upozornění.|  
|[-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Odkazy zadané moduly do tohoto sestavení|  
|-Analyzátor|Spusťte analyzátory z tohoto sestavení (krátký tvar: - a)|  
|[-appconfig](../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)|Určuje umístění souboru app.config v době vazby sestavení.|  
|[-baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Určuje základní adresu pro knihovnu, která má být sestaven.|  
|[-bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Vytvoří soubor "Hlášení chyb". Tento soubor bude odeslán spolu se všemi informacemi, pokud se používá s - errorreport: řádku nebo - errorreport: Odeslat.|  
|[-checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Způsobí, že kompilátor generování kontroly přetečení.|  
|-checksumalgorithm:\<alg >|Zadejte algoritmus pro výpočet kontrolní součet souboru zdroje uložené v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|  
|[-codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Určuje znakovou stránku pro použití při otevírání zdrojové soubory.|  
|[-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Posílá informace pro ladění.|  
|[-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Definuje symboly podmíněné kompilace.|  
|[-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Podepíše sestavení pomocí pouze veřejné část složitý název klíče.|  
|[-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|Určuje soubor dokumentace XML pro generování.|  
|[-errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Určuje, jak se budou zpracovávat chyby kompilátoru interní: řádku odeslání nebo žádný. Výchozí hodnota je none.|  
|[-filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Určuje zarovnání použité pro oddíly výstupního souboru.|  
|[-fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Způsobí, že kompilátor generuje úplné cesty.|  
|[-help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Zobrazí zprávu využití pro stdout.|  
|[-highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Určuje, že vysoké entropie technologie ASLR je podporována.|  
|-přírůstkové|Umožňuje přírůstkovou kompilaci [zastaralé].|  
|[-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Určuje kontejner klíče se silným názvem.|  
|[-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Určuje soubor klíče se silným názvem.|  
|[-langversion:\<řetězec >](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Zadejte režim jazykové verze: výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 nebo nejnovější |  
|[-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Určuje další adresáře, ve kterém se bude vyhledávat pro odkazy.|  
|[-link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaném sestavení do projektu.|  
|[-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Zadaný zdroj odkazuje na toto sestavení.|  
|[-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Určuje typ, který obsahuje vstupní bod (ignorovat všechny ostatní vstupní body).|  
|[-moduleassemblyname](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)|Určuje sestavení, jehož neveřejným typům .netmodule přístup.|  
|-modulename:\<řetězec >|Zadejte název zdrojového modulu|  
|[-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Dá pokyn kompilátoru, aby automaticky zahrnout CSC. Soubor konfigurace.|  
|[-nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Potlačí zpráva o autorských právech kompilátoru.|  
|[-nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Dá pokyn kompilátoru, aby standardní knihovně odkazů (mscorlib.dll).|  
|[-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Zakáže konkrétní zprávy upozornění|  
|[-nowin32manifest](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)|Dá pokyn kompilátoru není pro vložení manifestu aplikace ve spustitelném souboru.|  
|[-optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|  
|[-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Určuje název výstupního souboru (výchozí: základní název souboru s hlavní třídy nebo první).|  
|-parallel[+&#124;-]|Určuje, jestli se má používat souběžných sestavení (+).|  
|[-pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|Určuje název souboru a umístění souboru pdb.|  
|[-platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Omezení platformy, na kterých tento kód můžete spustit na: x86, Itanium, x 64, anycpu, nebo anycpu32bitpreferred. Výchozí hodnota je anycpu.|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Určuje jazyk, který se má použít pro výstup kompilátoru.|  
|[-recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Zahrne všechny soubory v aktuálním adresáři a podadresářích podle specifikace zástupného znaku.|  
|[-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Odkazy na metadata ze zadaných souborů sestavení.|  
|[-refout](refout-compiler-option.md)|Generovat odkaz na sestavení kromě primární sestavení.|  
|[-refonly](refonly-compiler-option.md)|Generovat odkaz na sestavení namísto primární sestavení.|  
|[-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|Vloží zadaný prostředek.|  
|-ruleset:\<souboru >|Zadejte soubor ruleset zakazující diagnostiky specifické.|  
|[-subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|Určuje minimální verze subsystému, můžete použít na spustitelný soubor.|  
|[-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Určuje formát výstupního souboru, a to pomocí jedné ze čtyř možností: [-target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md), [-target: library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md), [-cíl: modul](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), [-target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|[-unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Umožňuje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kódu.|  
|[-utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|Výstupy zpráv kompilátoru s kódováním UTF-8.|  
|[-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Nastaví úroveň pro upozornění (0-4).|  
|[-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Sestavy konkrétní upozornění jako chyby.|  
|[-win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Tato ikona se používá pro výstup.|  
|[-win32manifest](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)|Určuje soubor manifestu win32 vlastní.|  
|[-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Určuje zdrojového souboru win32 (.res).|  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Možnosti kompilátoru jazyka C# uvedené podle kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
