---
title: Možnosti kompilátoru C# (abecední pořadí)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: deffa6556d02cd5449d4bc91cf051a591b1c333e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="c-compiler-options-listed-alphabetically"></a>Možnosti kompilátoru C# (abecední pořadí)
Následující možnosti kompilátoru jsou seřazeny podle abecedy. Seznam kategorií, najdete v části [C# kompilátoru možnosti uvedené podle kategorie](listed-by-category.md).  
  
|Možnost|Účel|  
|------------|-------------|  
|[@](response-file-compiler-option.md)|Přečte soubor odpovědí pro další možnosti.|  
|[-?](help-compiler-option.md)|Zobrazí zprávu využití pro stdout.|  
|-additionalfile|Názvy další soubory, které neovlivňují přímo generování kódu, ale může být používán analyzátory pro vytvoření chyby nebo upozornění.|  
|[-addmodule](addmodule-compiler-option.md)|Odkazy zadané moduly do tohoto sestavení|  
|-Analyzátor|Spusťte analyzátory z tohoto sestavení (krátký tvar: - a)|  
|[-appconfig](appconfig-compiler-option.md)|Určuje umístění souboru app.config v době vazby sestavení.|  
|[-baseaddress](baseaddress-compiler-option.md)|Určuje základní adresu pro knihovnu, která má být sestaven.|  
|[-bugreport](bugreport-compiler-option.md)|Vytvoří soubor "Hlášení chyb". Tento soubor bude odeslán spolu se všemi informacemi, pokud se používá s - errorreport: řádku nebo - errorreport: Odeslat.|  
|[-checked](checked-compiler-option.md)|Způsobí, že kompilátor generování kontroly přetečení.|  
|-checksumalgorithm:\<alg >|Zadejte algoritmus pro výpočet kontrolní součet souboru zdroje uložené v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|  
|[-codepage](codepage-compiler-option.md)|Určuje znakovou stránku pro použití při otevírání zdrojové soubory.|  
|[-debug](debug-compiler-option.md)|Posílá informace pro ladění.|  
|[-define](define-compiler-option.md)|Definuje symboly podmíněné kompilace.|  
|[-delaysign](delaysign-compiler-option.md)|Podepíše sestavení pomocí pouze veřejné část složitý název klíče.|  
|[-deterministickou](deterministic-compiler-option.md)|Způsobí, že kompilátor výstup sestavení jejichž binární obsah je stejný jako napříč kompilace Pokud vstupní hodnoty jsou identické.|
|[-doc](doc-compiler-option.md)|Určuje soubor dokumentace XML pro generování.|  
|[-errorreport](errorreport-compiler-option.md)|Určuje, jak se budou zpracovávat chyby kompilátoru interní: řádku odeslání nebo žádný. Výchozí hodnota je none.|  
|[-filealign](filealign-compiler-option.md)|Určuje zarovnání použité pro oddíly výstupního souboru.|  
|[-fullpaths](fullpaths-compiler-option.md)|Způsobí, že kompilátor generuje úplné cesty.|  
|[– Nápověda](help-compiler-option.md)|Zobrazí zprávu využití pro stdout.|  
|[-highentropyva](highentropyva-compiler-option.md)|Určuje, že vysoké entropie technologie ASLR je podporována.|  
|-přírůstkové|Umožňuje přírůstkovou kompilaci [zastaralé].|  
|[-keycontainer](keycontainer-compiler-option.md)|Určuje kontejner klíče se silným názvem.|  
|[-keyfile](keyfile-compiler-option.md)|Určuje soubor klíče se silným názvem.|  
|[-langversion:\<řetězec >](langversion-compiler-option.md)|Zadejte režim jazykové verze: výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 nebo nejnovější |  
|[-lib](lib-compiler-option.md)|Určuje další adresáře, ve kterém se bude vyhledávat pro odkazy.|  
|[-link](link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaném sestavení do projektu.|  
|[-linkresource](linkresource-compiler-option.md)|Zadaný zdroj odkazuje na toto sestavení.|  
|[-main](main-compiler-option.md)|Určuje typ, který obsahuje vstupní bod (ignorovat všechny ostatní vstupní body).|  
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Určuje sestavení, jehož neveřejným typům .netmodule přístup.|  
|-modulename:\<řetězec >|Zadejte název zdrojového modulu|  
|[-noconfig](noconfig-compiler-option.md)|Dá pokyn kompilátoru, aby automaticky zahrnout CSC. Soubor konfigurace.|  
|[-nologo](nologo-compiler-option.md)|Potlačí zpráva o autorských právech kompilátoru.|  
|[-nostdlib](nostdlib-compiler-option.md)|Dá pokyn kompilátoru, aby standardní knihovně odkazů (mscorlib.dll).|  
|[-nowarn](nowarn-compiler-option.md)|Zakáže konkrétní zprávy upozornění|  
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Dá pokyn kompilátoru není pro vložení manifestu aplikace ve spustitelném souboru.|  
|[-optimize](optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|  
|[-out](out-compiler-option.md)|Určuje název výstupního souboru (výchozí: základní název souboru s hlavní třídy nebo první).|  
|-paralelní [+&#124;-]|Určuje, jestli se má používat souběžných sestavení (+).|  
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru pdb.|  
|[-platform](platform-compiler-option.md)|Omezení platformy, na kterých tento kód můžete spustit na: x86, Itanium, x 64, anycpu, nebo anycpu32bitpreferred. Výchozí hodnota je anycpu.|  
|[-preferreduilang](preferreduilang-compiler-option.md)|Určuje jazyk, který se má použít pro výstup kompilátoru.|  
|[-recurse](recurse-compiler-option.md)|Zahrne všechny soubory v aktuálním adresáři a podadresářích podle specifikace zástupného znaku.|  
|[-reference](reference-compiler-option.md)|Odkazy na metadata ze zadaných souborů sestavení.|  
|[-refout](refout-compiler-option.md)|Generovat odkaz na sestavení kromě primární sestavení.|  
|[-refonly](refonly-compiler-option.md)|Generovat odkaz na sestavení namísto primární sestavení.|  
|[-resource](resource-compiler-option.md)|Vloží zadaný prostředek.|  
|-ruleset:\<souboru >|Zadejte soubor ruleset zakazující diagnostiky specifické.|  
|[-subsystemversion](subsystemversion-compiler-option.md)|Určuje minimální verze subsystému, můžete použít na spustitelný soubor.|  
|[-target](target-compiler-option.md)|Určuje formát výstupního souboru, a to pomocí jedné ze čtyř možností: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-cíl: modul](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|  
|[-unsafe](unsafe-compiler-option.md)|Umožňuje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kódu.|  
|[-utf8output](utf8output-compiler-option.md)|Výstupy zpráv kompilátoru s kódováním UTF-8.|  
|[-warn](warn-compiler-option.md)|Nastaví úroveň pro upozornění (0-4).|  
|[-warnaserror](warnaserror-compiler-option.md)|Sestavy konkrétní upozornění jako chyby.|  
|[-win32icon](win32icon-compiler-option.md)|Tato ikona se používá pro výstup.|  
|[-win32manifest](win32manifest-compiler-option.md)|Určuje soubor manifestu win32 vlastní.|  
|[-win32res](win32res-compiler-option.md)|Určuje zdrojového souboru win32 (.res).|  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](index.md)  
 [Možnosti kompilátoru jazyka C# uvedené podle kategorie](listed-by-category.md)  
 [Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [\<kompilátoru > elementu](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
