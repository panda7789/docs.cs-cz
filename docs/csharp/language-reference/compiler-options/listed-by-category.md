---
title: Možnosti kompilátoru C# uvedené podle kategorie
ms.date: 06/04/2020
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: ffa5372678362e47eb59d8b041da55c79bf8475d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447040"
---
# <a name="c-compiler-options-listed-by-category"></a>Možnosti kompilátoru C# uvedené podle kategorie

Následující možnosti kompilátoru jsou seřazené podle kategorie. Abecední seznam naleznete v tématu [Možnosti kompilátoru C#, které jsou uvedeny abecedně](listed-alphabetically.md).

## <a name="optimization"></a>Optimalizace

|Možnost|Účel|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Určuje velikost oddílů ve výstupním souboru.|
|[– optimalizovat](optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|

## <a name="output-files"></a>Výstupní soubory

|Možnost|Účel|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Způsobí, že kompilátor výstupuje sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.|
|[-doc](doc-compiler-option.md)|Určuje soubor XML, ve kterém mají být zpracovány dokumentační komentáře.|
|[-out](out-compiler-option.md)|Určuje výstupní soubor.|
|[-pathmap](pathmap-compiler-option.md)|Zadejte mapování pro výstup názvů zdrojových cest kompilátorem|
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru. pdb.|
|[– platforma](platform-compiler-option.md)|Zadejte výstupní platformu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
|[-refout](refout-compiler-option.md)|Kromě primárního sestavení vygenerujte referenční sestavení.|
|[-refonly](refonly-compiler-option.md)|Vygenerujte referenční sestavení namísto primárního sestavení.|
|[-target](target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné z pěti možností: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: Library](target-library-compiler-option.md), [-target: Module](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md)nebo [-target: winmdobj](target-winmdobj-compiler-option.md).|
|ModuleName\<string>|Zadejte název zdrojového modulu.|

## <a name="net-framework-assemblies"></a>.NET Framework sestavení

|Možnost|Účel|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Určuje jeden nebo více modulů, které mají být součástí tohoto sestavení.|
|[-delaysign](delaysign-compiler-option.md)|Instruuje kompilátor, aby přidal veřejný klíč, ale pro sestavení bez znaménka.|
|[-keycontainer](keycontainer-compiler-option.md)|Určuje název kontejneru kryptografických klíčů.|
|[-keyfile](keyfile-compiler-option.md)|Určuje název souboru, který obsahuje kryptografický klíč.|
|[-lib](lib-compiler-option.md)|Určuje umístění sestavení, na které odkazuje [odkaz](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilátor, aby neimportoval standardní knihovnu (mscorlib. dll).|
|[-publicsign](publicsign-compiler-option.md)|Použijte veřejný klíč bez podepsání sestavení, ale nastavte bitovou kopii v sestavení, která značí, že je sestavení podepsáno.|
|[– Referenční informace](reference-compiler-option.md)|Importuje metadata ze souboru, který obsahuje sestavení.|
|– Analyzátor|Spustit analyzátory z tohoto sestavení (krátký tvar:/a)|
|-additionalfile|Názvy dalších souborů, které přímo neovlivňují generování kódu, ale mohou být využívány analyzátory pro vytváření chyb nebo upozornění.|
|– Vložit|Vložte všechny zdrojové soubory do souboru PDB.|
|Uložit\<file list>|Vloží konkrétní soubory do souboru PDB.|

## <a name="debuggingerror-checking"></a>Ladění/kontrola chyb

|Možnost|Účel|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Vytvoří soubor, který obsahuje informace, které usnadňují hlášení chyby.|
|[-checked](checked-compiler-option.md)|Určuje, zda aritmetické aritmetické operace přetéká hranice datového typu způsobí výjimku v době běhu.|
|[– ladění](debug-compiler-option.md)|Instruuje kompilátor, aby vygeneroval ladicí informace.|
|[-errorreport](errorreport-compiler-option.md)|Nastaví chování zasílání zpráv o chybách.|
|[-fullpaths](fullpaths-compiler-option.md)|Určuje absolutní cestu k souboru ve výstupu kompilátoru.|
|[-nowarn](nowarn-compiler-option.md)|Potlačí generování zadaných upozornění kompilátorem.|
|[-Nullable](nullable-compiler-option.md)|Určuje možnost kontextu s možnou hodnotou null.|
|[-warn](warn-compiler-option.md)|Nastaví úroveň upozornění.|
|[-warnaserror](warnaserror-compiler-option.md)|Propaguje upozornění na chyby.|
|RuleSet\<file>|Zadejte soubor RuleSet, který zakáže konkrétní diagnostiku.|

## <a name="preprocessor"></a>Preprocesor

|Možnost|Účel|
|------------|-------------|
|[-define](define-compiler-option.md)|Definuje symboly preprocesoru.|

## <a name="resources"></a>Zdroje a prostředky

|Možnost|Účel|
|------------|-------------|
|[-Link](link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaných sestaveních pro projekt.|
|[-linkresource](linkresource-compiler-option.md)|Vytvoří odkaz na spravovaný prostředek.|
|[– prostředek](resource-compiler-option.md)|Vloží prostředek .NET Framework do výstupního souboru.|
|[-win32icon](win32icon-compiler-option.md)|Určuje soubor. ico, který se má vložit do výstupního souboru.|
|[-win32res](win32res-compiler-option.md)|Určuje prostředek Win32, který se má vložit do výstupního souboru.|

## <a name="miscellaneous"></a>Různé

|Možnost|Účel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Určuje soubor odpovědí.|
|[-?](help-compiler-option.md)|Zobrazí seznam možností kompilátoru pro STDOUT.|
|[-baseaddress](baseaddress-compiler-option.md)|Určuje upřednostňovanou základní adresu, na které se má načíst knihovna DLL.|
|[-codepage](codepage-compiler-option.md)|Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.|
|[-Help](help-compiler-option.md)|Zobrazí seznam možností kompilátoru pro STDOUT.|
|[-highentropyva](highentropyva-compiler-option.md)|Určuje, že spustitelný soubor podporuje náhodnost rozložení adresního prostoru (ASLR).|
|[-langversion](langversion-compiler-option.md)|Zadejte jazykovou verzi: výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7,1, 7,2, 7,3 nebo nejnovější. |
|[-main](main-compiler-option.md)|Určuje umístění metody **Main** .|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilátor, aby nekompiluje pomocí CSc. rsp.|
|[-nologo](nologo-compiler-option.md)|Potlačí informace banneru kompilátoru.|
|[-recurse](recurse-compiler-option.md)|Vyhledá v podadresářích zdrojové soubory, které se mají kompilovat.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Určuje minimální verzi subsystému, který může spustitelný soubor použít.|
|[-unsafe](unsafe-compiler-option.md)|Povolí kompilaci kódu, který používá klíčové slovo [unsafe](../keywords/unsafe.md) .|
|[-utf8output](utf8output-compiler-option.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|
|– paralelní [+&#124;-]|Určuje, jestli se má použít souběžné sestavení (+).|
|-checksumalgorithm:\<alg>|Zadejte algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v souboru PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|

## <a name="obsolete-options"></a>Zastaralé možnosti

|Možnost|Účel|
|---|---|
|– přírůstkové|Povolí přírůstkovou kompilaci.|

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](index.md)
- [Možnosti kompilátoru C# (abecední pořadí)](listed-alphabetically.md)
- [Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
