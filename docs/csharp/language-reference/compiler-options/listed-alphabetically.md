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
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972745"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Možnosti kompilátoru C# (abecední pořadí)

Následující možnosti kompilátoru jsou seřazené abecedně. Seznam kategorií naleznete v tématu [ C# možnosti kompilátoru uvedené podle kategorie](listed-by-category.md).

|Možnost|Účel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Přečte soubor odpovědí pro další možnosti.|
|[-?](help-compiler-option.md)|Zobrazí zprávu o použití pro STDOUT.|
|-additionalfile|Názvy dalších souborů, které přímo neovlivňují generování kódu, ale mohou být využívány analyzátory pro vytváření chyb nebo upozornění.|
|[-addmodule](addmodule-compiler-option.md)|Propojí zadané moduly s tímto sestavením.|
|– Analyzátor|Spustit analyzátory z tohoto sestavení (krátký tvar:-a)|
|[-appconfig](appconfig-compiler-option.md)|Určuje umístění souboru App. config v době vytváření vazby sestavení.|
|[-baseaddress](baseaddress-compiler-option.md)|Určuje základní adresu pro knihovnu, která má být sestavena.|
|[-bugreport](bugreport-compiler-option.md)|Vytvoří soubor hlášení o chybě. Tento soubor se pošle spolu s případnými informacemi o chybách, pokud se použije s-errorreport: prompt nebo-errorreport: Send.|
|[-checked](checked-compiler-option.md)|Způsobí, že kompilátor generuje kontroly přetečení.|
|-checksumalgorithm:\<ALG >|Určuje algoritmus pro výpočet kontrolního součtu zdrojového souboru uloženého v souboru PDB.  Podporované hodnoty jsou: SHA256 (default) nebo SHA1.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1. |
|[-codepage](codepage-compiler-option.md)|Určuje znakovou stránku, která má být použita při otevírání zdrojových souborů.|
|[-debug](debug-compiler-option.md)|Vygeneruje ladicí informace.|
|[-define](define-compiler-option.md)|Definuje symboly podmíněné kompilace.|
|[-delaysign](delaysign-compiler-option.md)|Odloží sestavení pouze pomocí veřejné části klíče silného názvu.|
|[-deterministic](deterministic-compiler-option.md)|Způsobí, že kompilátor výstupuje sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.|
|[-doc](doc-compiler-option.md)|Určuje soubor dokumentace XML, který má být vygenerován.|
|– Vložit|Vložte všechny zdrojové soubory do souboru PDB.|
|-embed:\<seznam souborů >|Vloží konkrétní soubory do souboru PDB.|
|-errorendlocation|Výstupní řádek a sloupec koncového umístění jednotlivých chyb|
|-protokolu chyb:\<soubor >|Zadejte soubor pro protokolování všech diagnostik kompilátorů a analyzátorů.|
|[-errorreport](errorreport-compiler-option.md)|Určuje, jak zpracovat vnitřní chyby kompilátoru: prompt, Send nebo None (žádný). Výchozí hodnota je None.|
|[-filealign](filealign-compiler-option.md)|Určuje zarovnání použité pro oddíly výstupního souboru.|
|[-fullpaths](fullpaths-compiler-option.md)|Způsobí, že kompilátor vygeneruje plně kvalifikované cesty.|
|[-Help](help-compiler-option.md)|Zobrazí zprávu o použití pro STDOUT.|
|[-highentropyva](highentropyva-compiler-option.md)|Určuje, že je podporována vysoká entropie ASLR.|
|– přírůstkové|Povolí přírůstkovou kompilaci [zastaralé].|
|[-keycontainer](keycontainer-compiler-option.md)|Určuje kontejner klíče se silným názvem.|
|[-keyfile](keyfile-compiler-option.md)|Určuje soubor klíče se silným názvem.|
|[-langversion –:\<> řetězců](langversion-compiler-option.md)|Zadejte jazykovou verzi: výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7,1, 7,2, 7,3 nebo nejnovější. |
|[-lib](lib-compiler-option.md)|Určuje další adresáře, ve kterých budou hledány odkazy.|
|[-link](link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaných sestaveních pro projekt.|
|[-linkresource](linkresource-compiler-option.md)|Propojí zadaný prostředek s tímto sestavením.|
|[-main](main-compiler-option.md)|Určuje typ, který obsahuje vstupní bod (ignoruje všechny ostatní možné vstupní body).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Určuje sestavení, jehož neveřejné typy a. netmodule mají přístup.|
|-Module:\<> řetězců|Zadejte název zdrojového modulu.|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilátor, že nemá automaticky zahrnovat CSC. Soubor RSP.|
|[-nologo](nologo-compiler-option.md)|Potlačí zprávu o autorských právech kompilátoru.|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilátor, aby odkazoval na standardní knihovnu (mscorlib. dll).|
|[-nowarn](nowarn-compiler-option.md)|Zakáže konkrétní zprávy upozornění.|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Instruuje kompilátor, aby nevložil manifest aplikace do spustitelného souboru.|
|[-optimize](optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|
|[-out](out-compiler-option.md)|Určuje název výstupního souboru (výchozí: základní název souboru s hlavní třídou nebo prvním souborem).|
|– paralelní [+&#124;-]|Určuje, jestli se má použít souběžné sestavení (+).|
|[-pathmap](pathmap-compiler-option.md)|Určuje mapování pro výstup názvů zdrojových cest kompilátorem.|
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru. pdb.|
|[-platform](platform-compiler-option.md)|Omezuje platformy, na kterých lze tento kód spustit: x86, Itanium, x64, anycpu nebo anycpu32bitpreferred. Výchozí hodnota je anycpu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Určuje jazyk, který má být použit pro výstup kompilátoru.|
|[-publicsign](publicsign-compiler-option.md)|Použijte veřejný klíč bez podepsání sestavení, ale nastavte bitovou kopii v sestavení, která značí, že je sestavení podepsáno.|
|[-recurse](recurse-compiler-option.md)|Zahrne všechny soubory v aktuálním adresáři a podadresářích podle specifikací zástupného znaku.|
|[-reference](reference-compiler-option.md)|Odkazuje na metadata ze zadaných souborů sestavení.|
|[-refout](refout-compiler-option.md)|Kromě primárního sestavení vygenerujte referenční sestavení.|
|[-refonly](refonly-compiler-option.md)|Vygenerujte referenční sestavení namísto primárního sestavení.|
|-reportanalyzer|Nahlásit Další informace analyzátoru, například čas spuštění.|
|[-resource](resource-compiler-option.md)|Vloží zadaný prostředek.|
|-RuleSet: soubor\<|Zadejte soubor RuleSet, který zakáže konkrétní diagnostiku.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Určuje minimální verzi subsystému, který může spustitelný soubor použít.|
|[-target](target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné ze čtyř možností: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: Library](target-library-compiler-option.md), [-target: Module](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|Umožňuje [nezabezpečený](../keywords/unsafe.md) kód.|
|[-utf8output](utf8output-compiler-option.md)|Vytvoří výstup zpráv kompilátoru v kódování UTF-8.|
|– verze|Zobrazte číslo verze kompilátoru a ukončete.|
|[-warn](warn-compiler-option.md)|Nastaví úroveň upozornění (0-4).|
|[-warnaserror](warnaserror-compiler-option.md)|Oznamuje specifická upozornění jako chyby.|
|[-win32icon](win32icon-compiler-option.md)|Použije tuto ikonu pro výstup.|
|[-win32manifest](win32manifest-compiler-option.md)|Určuje vlastní soubor manifestu Win32.|
|[-win32res](win32res-compiler-option.md)|Určuje soubor prostředků Win32 (. res).|

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](index.md)
- [Možnosti kompilátoru jazyka C# uvedené podle kategorie](listed-by-category.md)
- [Postup nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<element > kompilátoru](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
