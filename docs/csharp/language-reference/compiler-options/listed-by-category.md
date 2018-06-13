---
title: Možnosti kompilátoru C# uvedené podle kategorie
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 88ae18b11a48fd8b9610032e913c97d4c15d1c21
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472409"
---
# <a name="c-compiler-options-listed-by-category"></a>Možnosti kompilátoru C# uvedené podle kategorie

Následující možnosti kompilátoru jsou seřazeny podle kategorie. Abecední seznam najdete v tématu [Možnosti C# kompilátoru seřazeny abecedně](listed-alphabetically.md).

## <a name="optimization"></a>Optimalizace

|Možnost|Účel|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Určuje velikost oddílů ve výstupním souboru.|
|[-optimize](optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|

## <a name="output-files"></a>Výstupní soubory

|Možnost|Účel|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Způsobí, že kompilátor výstup sestavení jejichž binární obsah je stejný jako napříč kompilace Pokud vstupní hodnoty jsou identické.|
|[-doc](doc-compiler-option.md)|Určuje soubor XML, kde jsou zpracované dokumentační komentáře k zapsání.|
|[-out](out-compiler-option.md)|Určuje výstupní soubor.|
|[-pathmap](pathmap-compiler-option.md)|Zadat mapování pro zdrojové cesty názvy výstup kompilátorem|
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru pdb.|
|[-platform](platform-compiler-option.md)|Zadejte výstupní platformy.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
|[-refout](refout-compiler-option.md)|Generovat odkaz na sestavení kromě primární sestavení.|
|[-refonly](refonly-compiler-option.md)|Generovat odkaz na sestavení namísto primární sestavení.|
|[-target](target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné z pěti možností: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-target: module ](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), nebo [-target: winmdobj](target-winmdobj-compiler-option.md).|
|-modulename:\<řetězec >|Zadejte název zdrojového modulu|

## <a name="net-framework-assemblies"></a>Sestavení rozhraní .NET framework

|Možnost|Účel|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Určuje jeden nebo více modulů jako součást tohoto sestavení.|
|[-delaysign](delaysign-compiler-option.md)|Dá pokyn kompilátoru přidejte veřejný klíč, ale ponechte sestavení bez znaménka.|
|[-keycontainer](keycontainer-compiler-option.md)|Určuje název kontejneru kryptografických klíčů.|
|[-keyfile](keyfile-compiler-option.md)|Určuje název souboru obsahujícího kryptografický klíč.|
|[-lib](lib-compiler-option.md)|Určuje umístění sestavení odkazovaných pomocí možnosti [– referenční dokumentace](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Dá pokyn kompilátoru Neimportovat standardní knihovnu (mscorlib.dll).|
|[-publicsign](publicsign-compiler-option.md)|Veřejný klíč použít bez podepsání sestavení, ale nastavit bit v sestavení, což značí, že je podepsaná sestavení.|
|[-reference](reference-compiler-option.md)|Naimportuje metadata ze souboru, který obsahuje sestavení.|
|-Analyzátor|Spusťte analyzátory z tohoto sestavení (krátký tvar: / a)|
|-additionalfile|Názvy další soubory, které neovlivňují přímo generování kódu, ale může být používán analyzátory pro vytvoření chyby nebo upozornění.|

## <a name="debuggingerror-checking"></a>Ladění a kontrola chyb

|Možnost|Účel|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Vytvoří soubor, který obsahuje informace, které usnadňuje ohlásit chybu.|
|[-checked](checked-compiler-option.md)|Určuje, zda celé číslo aritmetické, která přesahuje hranice typu dat, způsobí výjimku za běhu.|
|[-debug](debug-compiler-option.md)|Pokyn kompilátoru k Generovat ladicí informace.|
|[-errorreport](errorreport-compiler-option.md)|Nastaví chování zpráv o chybách.|
|[-fullpaths](fullpaths-compiler-option.md)|Určuje absolutní cestu k souboru ve výstupu kompilátoru.|
|[-nowarn](nowarn-compiler-option.md)|Potlačí kompilátoru generování zadaných upozornění.|
|[-warn](warn-compiler-option.md)|Nastaví úroveň pro upozornění.|
|[-warnaserror](warnaserror-compiler-option.md)|Zvýší úroveň upozornění na chyby.|
|-ruleset:\<souboru >|Zadejte soubor ruleset zakazující diagnostiky specifické.|

## <a name="preprocessor"></a>Preprocesor

|Možnost|Účel|
|------------|-------------|
|[-define](define-compiler-option.md)|Definuje preprocesoru symboly.|

## <a name="resources"></a>Prostředky

|Možnost|Účel|
|------------|-------------|
|[-link](link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaném sestavení do projektu.|
|[-linkresource](linkresource-compiler-option.md)|Vytvoří odkaz na spravovaných prostředků.|
|[-resource](resource-compiler-option.md)|Vloží prostředek rozhraní .NET Framework do výstupního souboru.|
|[-win32icon](win32icon-compiler-option.md)|Určuje soubor .ico, který chcete vložit do výstupního souboru.|
|[-win32res](win32res-compiler-option.md)|Určuje prostředek systému Win32 vložení do výstupního souboru.|

## <a name="miscellaneous"></a>Různé

|Možnost|Účel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Určuje soubor odezvy.|
|[-?](help-compiler-option.md)|Zobrazí seznam možností kompilátoru do stdout.|
|[-baseaddress](baseaddress-compiler-option.md)|Určuje upřednostňovaná základní adresa, na které se mají načíst knihovnu DLL.|
|[-codepage](codepage-compiler-option.md)|Určuje znakovou stránku pro všechny soubory zdrojového kódu v kompilace.|
|[– Nápověda](help-compiler-option.md)|Zobrazí seznam možností kompilátoru do stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Určuje, že spustitelný soubor podporuje adresu místa rozložení náhodné (technologie ASLR).|
|[-langversion](langversion-compiler-option.md)|Zadejte jazyková verze: výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 nebo nejnovější |
|[-main](main-compiler-option.md)|Určuje umístění **hlavní** metoda.|
|[-noconfig](noconfig-compiler-option.md)|Dá pokyn kompilátoru, aby kompilovat s csc.rsp.|
|[-nologo](nologo-compiler-option.md)|Potlačí informace kompilátoru.|
|[-recurse](recurse-compiler-option.md)|Vyhledá podadresáře pro zdrojové soubory pro kompilaci.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Určuje minimální verze subsystému, můžete použít na spustitelný soubor.|
|[-unsafe](unsafe-compiler-option.md)|Umožňuje kompilace kódu, který používá [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo.|
|[-utf8output](utf8output-compiler-option.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|
|-paralelní [+&#124;-]|Určuje, jestli se má používat souběžných sestavení (+).|
|-checksumalgorithm:\<alg >|Zadejte algoritmus pro výpočet kontrolní součet souboru zdroje uložené v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|

## <a name="obsolete-options"></a>Zastaralé možnosti

|Možnost|Účel|
|---|---|
|-přírůstkové|Umožňuje přírůstkovou kompilaci.|

## <a name="see-also"></a>Viz také

 [Možnosti kompilátoru jazyka C#](index.md)  
 [Možnosti kompilátoru jazyka C# (abecední pořadí)](listed-alphabetically.md)  
 [Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
