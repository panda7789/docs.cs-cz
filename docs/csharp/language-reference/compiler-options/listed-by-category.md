---
title: Možnosti kompilátoru C# uvedené podle kategorie
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 5cd5607c25dabd8f56ebb58366116666e8e649ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972706"
---
# <a name="c-compiler-options-listed-by-category"></a>Možnosti kompilátoru C# uvedené podle kategorie

Následující možnosti kompilátoru jsou seřazeny podle kategorie. Abecední seznam naleznete v tématu [C# Compiler Options Listed Alphabetically](listed-alphabetically.md).

## <a name="optimization"></a>Optimalizace

|Možnost|Účel|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Určuje velikost oddílů ve výstupním souboru.|
|[-optimalizovat](optimize-compiler-option.md)|Povolí/zakáže optimalizace.|

## <a name="output-files"></a>Výstupní soubory

|Možnost|Účel|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Způsobí, že kompilátor výstup sestavení, jehož binární obsah je shodný napříč kompilacemi, pokud vstupy jsou identické.|
|[-doc](doc-compiler-option.md)|Určuje soubor XML, ve kterém mají být zapsány poznámky zzpracované dokumentace.|
|[-ven](out-compiler-option.md)|Určuje výstupní soubor.|
|[-pathmap](pathmap-compiler-option.md)|Určení mapování pro výstup názvů zdrojových cest kompilátorem|
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru PDB.|
|[-platforma](platform-compiler-option.md)|Zadejte výstupní platformu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Zadejte jazyk pro výstup kompilátoru.|
|[-refout](refout-compiler-option.md)|Vygenerujte referenční sestavení kromě primární sestavy.|
|[-refonly](refonly-compiler-option.md)|Vygenerujte referenční sestavení namísto primárního sestavení.|
|[-cíl](target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné z pěti možností: [-target:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md)nebo [-target:winmdobj](target-winmdobj-compiler-option.md).|
|-název modulu:\<řetězec>|Zadejte název zdrojového modulu.|

## <a name="net-framework-assemblies"></a>Sestavení rozhraní .NET Framework

|Možnost|Účel|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Určuje jeden nebo více modulů, které mají být součástí tohoto sestavení.|
|[-delaysign](delaysign-compiler-option.md)|Dá pokyn kompilátoru přidat veřejný klíč, ale ponechat sestavení nepodepsané.|
|[-keycontainer](keycontainer-compiler-option.md)|Určuje název kontejneru kryptografického klíče.|
|[-keyfile](keyfile-compiler-option.md)|Určuje název souboru obsahující kryptografický klíč.|
|[-lib](lib-compiler-option.md)|Určuje umístění sestav odkazovaných pomocí [-reference](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilátor, aby neimportoval standardní knihovnu (mscorlib.dll).|
|[-publicsign](publicsign-compiler-option.md)|Použijte veřejný klíč bez podepisování sestavení, ale nastavte bit v sestavení označující, že sestavení je podepsáno.|
|[-odkaz](reference-compiler-option.md)|Importuje metadata ze souboru, který obsahuje sestavení.|
|-analyzátor|Spuštění analyzátorů z tohoto sestavení (Krátký formulář: /a)|
|-additionalfile|Pojmenuje další soubory, které nemají přímý vliv na generování kódu, ale mohou být použity analyzátory pro vytváření chyb nebo upozornění.|
|-vložit|Vložit všechny zdrojové soubory do PDB.|
|-embed:\<> seznamu souborů|Vložit konkrétní soubory do PDB.|
## <a name="debuggingerror-checking"></a>Ladění/kontrola chyb

|Možnost|Účel|
|------------|-------------|
|[-hlášení o chybách](bugreport-compiler-option.md)|Vytvoří soubor, který obsahuje informace, které usnadňují nahlášení chyby.|
|[-zkontrolovat](checked-compiler-option.md)|Určuje, zda celá aritmetika, která přeteče hranice datového typu, způsobí výjimku za běhu.|
|[-ladění](debug-compiler-option.md)|Dejte kompilátoru pokyn k vyzařování ladicích informací.|
|[-hlášení o chybách](errorreport-compiler-option.md)|Nastaví chování hlášení chyb.|
|[-fullpaths](fullpaths-compiler-option.md)|Určuje absolutní cestu k souboru ve výstupu kompilátoru.|
|[-nowarn](nowarn-compiler-option.md)|Potlačí generování zadaného upozornění kompilátoru.|
|[-warn](warn-compiler-option.md)|Nastaví úroveň upozornění.|
|[-warnaserror](warnaserror-compiler-option.md)|Převyšuje upozornění na chyby.|
|-ruleset:\<> souborů|Zadejte soubor sady pravidel, který zakáže konkrétní diagnostiku.|

## <a name="preprocessor"></a>Preprocesor

|Možnost|Účel|
|------------|-------------|
|[-define](define-compiler-option.md)|Definuje symboly preprocesoru.|

## <a name="resources"></a>Zdroje informací

|Možnost|Účel|
|------------|-------------|
|[-odkaz](link-compiler-option.md)|Zpřístupní projektu informace o typu COM v určených sestaveních.|
|[-linkresource](linkresource-compiler-option.md)|Vytvoří odkaz na spravovaný prostředek.|
|[-zdroj](resource-compiler-option.md)|Vloží do výstupního souboru prostředek rozhraní .NET Framework.|
|[-win32icon](win32icon-compiler-option.md)|Určuje soubor .ico, který má být vložen do výstupního souboru.|
|[-win32res](win32res-compiler-option.md)|Určuje prostředek win32, který má být vložen do výstupního souboru.|

## <a name="miscellaneous"></a>Různé

|Možnost|Účel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Určuje soubor odpovědí.|
|[-?](help-compiler-option.md)|Zobrazí seznam možností kompilátoru stdout.|
|[-baseaddress](baseaddress-compiler-option.md)|Určuje upřednostňovanou základní adresu, na kterou má být načíst dll.|
|[-kódová stránka](codepage-compiler-option.md)|Určuje znakovou stránku, která má být v kompilaci používána pro všechny soubory zdrojového kódu.|
|[-pomoc](help-compiler-option.md)|Zobrazí seznam možností kompilátoru stdout.|
|[-highentropieva](highentropyva-compiler-option.md)|Určuje, že spustitelný soubor podporuje randomizaci rozložení adresního prostoru (ASLR).|
|[-langversion](langversion-compiler-option.md)|Zadejte jazykovou verzi: Výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 nebo Nejnovější |
|[-main](main-compiler-option.md)|Určuje umístění Metody **Main.**|
|[-noconfigová (noconfigová)](noconfig-compiler-option.md)|Dává kompilátoru pokyn, aby nekompiloval pomocí souboru csc.rsp.|
|[-nologo](nologo-compiler-option.md)|Potlačí informace o banneru kompilátoru.|
|[-recurse](recurse-compiler-option.md)|Vyhledá podadresáře pro kompilované zdrojové soubory.|
|[-subsystémverze](subsystemversion-compiler-option.md)|Určuje minimální verzi podsystému, kterou může spustitelný soubor použít.|
|[-nebezpečné](unsafe-compiler-option.md)|Povolí kompilaci kódu, který používá [nebezpečné](../keywords/unsafe.md) klíčové slovo.|
|[-utf8output](utf8output-compiler-option.md)|Zobrazí výstup kompilátoru pomocí kódování UTF-8.|
|-paralelní[+&#124;-]|Určuje, zda se má použít souběžné sestavení (+).|
|-checksumalgorithm:\<alg>|Zadejte algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v databázi PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.|

## <a name="obsolete-options"></a>Zastaralé možnosti

|Možnost|Účel|
|---|---|
|-přírůstkové|Povolí přírůstkovou kompilaci.|

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](index.md)
- [Možnosti kompilátoru C# (abecední pořadí)](listed-alphabetically.md)
- [Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
