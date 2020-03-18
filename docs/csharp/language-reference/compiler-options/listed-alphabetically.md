---
title: Možnosti kompilátoru C# (abecední pořadí)
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alphabetically
- C# language, compiler options listed alphabetically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: d6d471cd27f35de6325a130e6c909d13cb1dcc85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972745"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Možnosti kompilátoru C# (abecední pořadí)

Následující možnosti kompilátoru jsou seřazeny abecedně. Pro kategorický seznam naleznete v [tématu C# Možnosti kompilátoru jsou uvedeny podle kategorie](listed-by-category.md).

|Možnost|Účel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Přečte soubor odpovědí pro další možnosti.|
|[-?](help-compiler-option.md)|Zobrazí zprávu o použití stdout.|
|-additionalfile|Pojmenuje další soubory, které nemají přímý vliv na generování kódu, ale mohou být použity analyzátory pro vytváření chyb nebo upozornění.|
|[-addmodule](addmodule-compiler-option.md)|Propojuje zadané moduly s tímto sestavením.|
|-analyzátor|Spuštění analyzátorů z této sestavy (Krátký tvar: -a)|
|[-appconfig](appconfig-compiler-option.md)|Určuje umístění souboru app.config v době vazby sestavení.|
|[-baseaddress](baseaddress-compiler-option.md)|Určuje základní adresu pro knihovnu, která má být vytvořena.|
|[-hlášení o chybách](bugreport-compiler-option.md)|Vytvoří soubor Hlášení o chybě. Tento soubor bude odeslán spolu s informacemi o selhání, pokud je použit s -errorreport:prompt nebo -errorreport:send.|
|[-zkontrolovat](checked-compiler-option.md)|Způsobí, že kompilátor generovat kontroly přetečení.|
|-checksumalgorithm:\<alg>|Určuje algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v databázi PDB.  Podporované hodnoty jsou: SHA256 (výchozí) nebo SHA1.<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256. |
|[-kódová stránka](codepage-compiler-option.md)|Určuje znakovou stránku, která se má použít při otevírání zdrojových souborů.|
|[-ladění](debug-compiler-option.md)|Vyzařuje informace o ladění.|
|[-define](define-compiler-option.md)|Definuje symboly podmíněné kompilace.|
|[-delaysign](delaysign-compiler-option.md)|Zpoždění podepisuje sestavení pomocí pouze veřejné části klíče silného názvu.|
|[-deterministic](deterministic-compiler-option.md)|Způsobí, že kompilátor výstup sestavení, jehož binární obsah je shodný napříč kompilacemi, pokud vstupy jsou identické.|
|[-doc](doc-compiler-option.md)|Určuje soubor dokumentace XML, který má být generován.|
|-vložit|Vložit všechny zdrojové soubory do PDB.|
|-embed:\<> seznamu souborů|Vložit konkrétní soubory do PDB.|
|-errorendlocation -errorendlocation -errorendlocation -error|Výstupní řádek a sloupec koncového umístění každé chyby.|
|-errorlog:\<> souborů|Zadejte soubor pro protokolování všech diagnostik kompilátorů a analyzátorů.|
|[-hlášení o chybách](errorreport-compiler-option.md)|Určuje způsob zpracování interních chyb kompilátoru: výzva, odeslání nebo žádná. Výchozí hodnota je none.|
|[-filealign](filealign-compiler-option.md)|Určuje zarovnání použité pro řezy výstupního souboru.|
|[-fullpaths](fullpaths-compiler-option.md)|Způsobí, že kompilátor generovat plně kvalifikované cesty.|
|[-pomoc](help-compiler-option.md)|Zobrazí zprávu o použití stdout.|
|[-highentropieva](highentropyva-compiler-option.md)|Určuje, že je podporována vysoká entropie ASLR.|
|-přírůstkové|Povolí přírůstkovou kompilaci [zastaralé].|
|[-keycontainer](keycontainer-compiler-option.md)|Určuje kontejner klíčů silného názvu.|
|[-keyfile](keyfile-compiler-option.md)|Určuje soubor klíče silného názvu.|
|[-langversion:\<řetězec>](langversion-compiler-option.md)|Zadejte jazykovou verzi: Výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 nebo Nejnovější |
|[-lib](lib-compiler-option.md)|Určuje další adresáře, ve kterých mají být vyhledány odkazy.|
|[-odkaz](link-compiler-option.md)|Zpřístupní projektu informace o typu COM v určených sestaveních.|
|[-linkresource](linkresource-compiler-option.md)|Propojuje zadaný prostředek s tímto sestavením.|
|[-main](main-compiler-option.md)|Určuje typ, který obsahuje vstupní bod (ignorujte všechny ostatní možné vstupní body).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Určuje sestavení, jehož neveřejné typy .netmodule přístup.|
|-název modulu:\<řetězec>|Zadejte název zdrojového modulu.|
|[-noconfigová (noconfigová)](noconfig-compiler-option.md)|Instruuje kompilátor, aby automaticky nezahrnoval CSC. RSP.|
|[-nologo](nologo-compiler-option.md)|Potlačí zprávu o autorských právech kompilátoru.|
|[-nostdlib](nostdlib-compiler-option.md)|Dává kompilátoru pokyn, aby neodkazoval na standardní knihovnu (mscorlib.dll).|
|[-nowarn](nowarn-compiler-option.md)|Zakáže určité varovné zprávy.|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Dává kompilátoru pokyn, aby do spustitelného souboru nevkládal manifest aplikace.|
|[-optimalizovat](optimize-compiler-option.md)|Povolí/zakáže optimalizace.|
|[-ven](out-compiler-option.md)|Určuje název výstupního souboru (výchozí: základní název souboru s hlavní třídou nebo prvním souborem).|
|-paralelní[+&#124;-]|Určuje, zda se má použít souběžné sestavení (+).|
|[-pathmap](pathmap-compiler-option.md)|Určuje mapování pro názvy zdrojových cest, které kompilátor vypracovává.|
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru PDB.|
|[-platforma](platform-compiler-option.md)|Omezení, které platformy tento kód lze spustit na: x86, Itanium, x64, anycpu nebo anycpu32bitpreferred. Výchozí hodnota je anycpu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Určuje jazyk, který má být použit pro výstup kompilátoru.|
|[-publicsign](publicsign-compiler-option.md)|Použijte veřejný klíč bez podepisování sestavení, ale nastavte bit v sestavení označující, že sestavení je podepsáno.|
|[-recurse](recurse-compiler-option.md)|Zahrnuje všechny soubory v aktuálním adresáři a podadresářích podle specifikací zástupných symbolů.|
|[-odkaz](reference-compiler-option.md)|Odkazuje na metadata ze zadaných souborů sestavení.|
|[-refout](refout-compiler-option.md)|Vygenerujte referenční sestavení kromě primární sestavy.|
|[-refonly](refonly-compiler-option.md)|Vygenerujte referenční sestavení namísto primárního sestavení.|
|-reportanalyzer|Nahlásit další informace analyzátoru, například čas spuštění.|
|[-zdroj](resource-compiler-option.md)|Vloží zadaný prostředek.|
|-ruleset:\<> souborů|Zadejte soubor sady pravidel, který zakáže konkrétní diagnostiku.|
|[-subsystémverze](subsystemversion-compiler-option.md)|Určuje minimální verzi podsystému, kterou může spustitelný soubor použít.|
|[-cíl](target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné ze čtyř možností: [-target:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md), [-target:winmdobj](target-winmdobj-compiler-option.md).|
|[-nebezpečné](unsafe-compiler-option.md)|Umožňuje [nebezpečný](../keywords/unsafe.md) kód.|
|[-utf8output](utf8output-compiler-option.md)|Výstupy zpráv kompilátoru v kódování UTF-8.|
|-verze|Zobrazí číslo verze kompilátoru a ukončete.|
|[-warn](warn-compiler-option.md)|Nastaví úroveň varování (0-4).|
|[-warnaserror](warnaserror-compiler-option.md)|Hlásí konkrétní upozornění jako chyby.|
|[-win32icon](win32icon-compiler-option.md)|Používá tuto ikonu pro výstup.|
|[-win32manifest](win32manifest-compiler-option.md)|Určuje vlastní soubor manifestu win32.|
|[-win32res](win32res-compiler-option.md)|Určuje soubor prostředků win32 (.res).|

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](index.md)
- [Možnosti kompilátoru C# uvedené podle kategorie](listed-by-category.md)
- [Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<> element kompilátoru](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
