---
title: Možnosti kompilátoru C# uvedené podle kategorie
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 891e5eac249f4bd22b6eadde7509de2d07cd1576
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527184"
---
# <a name="c-compiler-options-listed-by-category"></a>Možnosti kompilátoru C# uvedené podle kategorie

Jsou následující možnosti kompilátoru seřazené podle kategorie. Abecední seznam naleznete v tématu [možnosti jazyka C# kompilátoru uvedené abecedně](listed-alphabetically.md).

## <a name="optimization"></a>Optimalizace

|Možnost|Účel|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Určuje velikost oddíly výstupního souboru.|
|[-optimize](optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|

## <a name="output-files"></a>Výstupní soubory

|Možnost|Účel|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Způsobí, že kompilátor do výstupního sestavení, jejichž binární obsah je identické napříč kompilace Pokud vstupů jsou stejné.|
|[-doc](doc-compiler-option.md)|Určuje soubor XML, ve kterém mají být zapsány komentáře k dokumentaci zpracované.|
|[-out](out-compiler-option.md)|Určuje výstupní soubor.|
|[-pathmap](pathmap-compiler-option.md)|Zadat mapování pro zdrojové cesty názvy výstup kompilátorem|
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru pdb.|
|[-platform](platform-compiler-option.md)|Určení výstupní platformy.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
|[-refout](refout-compiler-option.md)|Generovat referenční sestavení kromě primárního sestavení.|
|[-refonly](refonly-compiler-option.md)|Generovat referenční sestavení místo primárního sestavení.|
|[-target](target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné z pěti možnosti: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-target: module ](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), nebo [-target: winmdobj](target-winmdobj-compiler-option.md).|
|-modulename:\<řetězec >|Zadejte název zdrojového modulu|

## <a name="net-framework-assemblies"></a>Sestavení rozhraní .NET framework

|Možnost|Účel|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Určuje jeden nebo více modulů jako součást tohoto sestavení.|
|[-delaysign](delaysign-compiler-option.md)|Instruuje kompilátor, přidejte veřejný klíč, ale ponechá sestavení bez znaménka.|
|[-keycontainer](keycontainer-compiler-option.md)|Určuje název kontejneru kryptografických klíčů.|
|[-keyfile](keyfile-compiler-option.md)|Určuje název souboru obsahujícího kryptografický klíč.|
|[-lib](lib-compiler-option.md)|Určuje umístění sestavení odkazováno prostřednictvím [– referenční dokumentace](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Dává pokyn kompilátoru Neimportovat standardní knihovnu (mscorlib.dll).|
|[-publicsign](publicsign-compiler-option.md)|Použít veřejný klíč bez podepisování sestavení, ale nastaví bit v sestavení, která udává, že je sestavení podepsáno.|
|[-reference](reference-compiler-option.md)|Importuje metadata ze souboru, který obsahuje sestavení.|
|-analyzátoru|Spustit analyzátory z tohoto sestavení (krátký tvar: /)|
|-additionalfile|Názvy další soubory, které nemají přímý vliv na generování kódu, ale může používat analyzátory pro vytvoření chyby nebo varování.|

## <a name="debuggingerror-checking"></a>Ladění a kontrola chyb

|Možnost|Účel|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Vytvoří soubor, který obsahuje informace, které usnadňuje hlášení chyby.|
|[-checked](checked-compiler-option.md)|Určuje, zda aritmetika, která přesahuje hranice datový typ celé číslo způsobí výjimku za běhu.|
|[-debug](debug-compiler-option.md)|Instruovali kompilátor k Generovat ladicí informace.|
|[-errorreport](errorreport-compiler-option.md)|Nastaví chování zpráv o chybách.|
|[-fullpaths](fullpaths-compiler-option.md)|Určuje absolutní cestu k souboru ve výstupu kompilátoru.|
|[-nowarn](nowarn-compiler-option.md)|Potlačí generování kompilátoru určených upozornění.|
|[-warn](warn-compiler-option.md)|Nastaví úroveň upozornění.|
|[-warnaserror](warnaserror-compiler-option.md)|Zvýší úroveň upozornění na chyby.|
|-sady pravidel:\<souboru >|Zadejte soubor sady pravidel, která zakáže konkrétní diagnostiky.|

## <a name="preprocessor"></a>Preprocesor

|Možnost|Účel|
|------------|-------------|
|[-define](define-compiler-option.md)|Definuje symboly preprocesoru.|

## <a name="resources"></a>Prostředky

|Možnost|Účel|
|------------|-------------|
|[-link](link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaném sestavení do projektu.|
|[-linkresource](linkresource-compiler-option.md)|Vytvoří odkaz na spravovaný prostředek.|
|[-resource](resource-compiler-option.md)|Vloží prostředek rozhraní .NET Framework do výstupního souboru.|
|[-win32icon](win32icon-compiler-option.md)|Určuje soubor .ico, který se má vložit do výstupního souboru.|
|[-win32res](win32res-compiler-option.md)|Určuje prostředek systému Win32 k vložení do výstupního souboru.|

## <a name="miscellaneous"></a>Různé

|Možnost|Účel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Určuje soubor odpovědí.|
|[-?](help-compiler-option.md)|Zobrazí seznam možností kompilátoru do stdout.|
|[-baseaddress](baseaddress-compiler-option.md)|Určuje upřednostňovaná základní adresa, ve kterém se má načíst knihovnu DLL.|
|[-codepage](codepage-compiler-option.md)|Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace.|
|[– Nápověda](help-compiler-option.md)|Zobrazí seznam možností kompilátoru do stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Určuje, že spustitelného souboru, který podporuje náhodného generování rozložení prostoru adres (ASLR).|
|[-langversion](langversion-compiler-option.md)|Určení jazykové verze: výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 nebo nejnovější |
|[-main](main-compiler-option.md)|Určuje umístění **hlavní** metody.|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilátor, ne pro kompilaci pomocí csc.rsp.|
|[-nologo](nologo-compiler-option.md)|Potlačí informace kompilátoru.|
|[-recurse](recurse-compiler-option.md)|Prohledává podadresáře pro zdrojové soubory pro kompilaci.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Určuje minimální verzi podsystému, který můžete použít spustitelný soubor.|
|[-unsafe](unsafe-compiler-option.md)|Zapne kompilaci kódu, který používá [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo.|
|[-utf8output](utf8output-compiler-option.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|
|-paralelní [+&#124;-]|Určuje, jestli se má použít souběžné sestavení (+).|
|-checksumalgorithm:\<alg >|Zadejte algoritmus pro výpočet kontrolního součtu souboru zdroje uloženo v PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|

## <a name="obsolete-options"></a>Zastaralé možnosti

|Možnost|Účel|
|---|---|
|-přírůstkové|Umožňuje přírůstkové kompilace.|

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](index.md)  
- [Možnosti kompilátoru jazyka C# (abecední pořadí)](listed-alphabetically.md)  
- [Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
