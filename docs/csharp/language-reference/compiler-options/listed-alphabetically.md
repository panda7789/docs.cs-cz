---
title: Možnosti kompilátoru C# (abecední pořadí)
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: 439366791fcd8fa40bb3fe8fc2982272798120ef
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441603"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Možnosti kompilátoru C# (abecední pořadí)

Následující možnosti kompilátoru jsou seřazená podle abecedy. Seznam kategorií naleznete v tématu [jazyka C# možnosti kompilátoru seřazené podle kategorie](listed-by-category.md).

|Možnost|Účel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Přečte soubor odpovědí pro další možnosti.|
|[-?](help-compiler-option.md)|Zobrazí zprávu o použití do stdout.|
|-additionalfile|Názvy další soubory, které nemají přímý vliv na generování kódu, ale může používat analyzátory pro vytvoření chyby nebo varování.|
|[-addmodule](addmodule-compiler-option.md)|Odkazy zadané moduly k tomuto sestavení|
|-analyzátoru|Spustit analyzátory z tohoto sestavení (krátký tvar: - a)|
|[-appconfig](appconfig-compiler-option.md)|Určuje umístění souboru app.config v době vazby sestavení.|
|[-baseaddress](baseaddress-compiler-option.md)|Určuje základní adresu knihovny, který má být sestaven.|
|[-bugreport](bugreport-compiler-option.md)|Vytvoří soubor hlášení o chybě. Tento soubor se odesílá spolu s žádné informace o chybách, pokud se použije s parametrem-errorreport: řádek nebo - errorreport: Odeslat.|
|[-checked](checked-compiler-option.md)|Způsobí, že kompilátor generovat kontroly přetečení.|
|-checksumalgorithm:\<alg >|Určuje algoritmus pro výpočet kontrolního součtu souboru zdroje uloženo v PDB.  Podporované hodnoty jsou: SHA1 (výchozí) nebo SHA256.|
|[-codepage](codepage-compiler-option.md)|Určuje znakovou stránku, která má použít při otevírání zdrojových souborů.|
|[-debug](debug-compiler-option.md)|Generuje ladicí informace.|
|[-define](define-compiler-option.md)|Definuje symboly podmíněné kompilace.|
|[-delaysign](delaysign-compiler-option.md)|Vytvoří zpožděný podpis sestavení s použitím pouze veřejné části klíče silného názvu.|
|[-deterministic](deterministic-compiler-option.md)|Způsobí, že kompilátor do výstupního sestavení, jejichž binární obsah je identické napříč kompilace Pokud vstupů jsou stejné.|
|[-doc](doc-compiler-option.md)|Určuje soubor dokumentace XML, který se má vygenerovat.|
|-pro vložení|Vložte všechny zdrojové soubory v souborech PDB.|
|-vložení:\<seznam souborů >|Vložte konkrétní soubory PDB.|
|[-errorreport](errorreport-compiler-option.md)|Určuje, jak zpracovávat interní chyby kompilátoru: řádku, odesílání nebo žádný. Výchozí hodnota je none.|
|[-filealign](filealign-compiler-option.md)|Určuje zarovnání použité pro oddíly výstupního souboru.|
|[-fullpaths](fullpaths-compiler-option.md)|Způsobí, že kompilátor generoval úplné cesty.|
|[– Nápověda](help-compiler-option.md)|Zobrazí zprávu o použití do stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Určuje, že vysokou entropie podporována technologie ASLR.|
|-přírůstkové|Umožňuje přírůstkové kompilace [zastaralé].|
|[-keycontainer](keycontainer-compiler-option.md)|Určuje kontejner klíče se silným názvem.|
|[-keyfile](keyfile-compiler-option.md)|Určuje soubor klíče se silným názvem.|
|[-langversion:\<řetězec >](langversion-compiler-option.md)|Určení jazykové verze: Výchozí, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 nebo nejnovější verzi |
|[-lib](lib-compiler-option.md)|Určuje další adresáře, ve kterém chcete hledat odkazy.|
|[-link](link-compiler-option.md)|Zpřístupní informace o typu modelu COM v zadaném sestavení do projektu.|
|[-linkresource](linkresource-compiler-option.md)|Propojí zadaný prostředek s tímto sestavením.|
|[-main](main-compiler-option.md)|Určuje typ obsahující vstupní bod (ignoruje všechny ostatní vstupní body).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Určuje sestavení, jejichž typy neveřejným .netmodule můžete získat přístup.|
|-modulename:\<řetězec >|Zadejte název zdrojového modulu|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilátor, aby automaticky zahrnují CSC. RSP souboru.|
|[-nologo](nologo-compiler-option.md)|Potlačí zprávu o autorských právech kompilátoru.|
|[-nostdlib](nostdlib-compiler-option.md)|Dá pokyn kompilátoru, aby odkaz na standardní knihovnu (mscorlib.dll).|
|[-nowarn](nowarn-compiler-option.md)|Zakáže specifická upozornění|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Dává pokyn kompilátoru, aby Vložit manifest aplikace ve spustitelném souboru.|
|[-optimize](optimize-compiler-option.md)|Povolí nebo zakáže optimalizace.|
|[-out](out-compiler-option.md)|Určuje název výstupního souboru (výchozí: základní název souboru s hlavní třídou nebo prvního souboru).|
|-paralelní [+&#124;-]|Určuje, jestli se má použít souběžné sestavení (+).|
|[-pathmap](pathmap-compiler-option.md)|Určuje mapování pro zdrojové cesty názvy výstup kompilátorem.|
|[-pdb](pdb-compiler-option.md)|Určuje název souboru a umístění souboru pdb.|
|[-platform](platform-compiler-option.md)|Omezení platformy, na kterých tento kód lze spustit: x86, Itanium, x 64, anycpu, anycpu32bitpreferred nebo. Výchozí je anycpu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Určuje jazyk, který má být použit pro výstup kompilátoru.|
|[-publicsign](publicsign-compiler-option.md)|Použít veřejný klíč bez podepisování sestavení, ale nastaví bit v sestavení, která udává, že je sestavení podepsáno.|
|[-recurse](recurse-compiler-option.md)|Zahrne všechny soubory v aktuálním adresáři a jeho podadresářích v závislosti na určení zástupných znaků.|
|[-reference](reference-compiler-option.md)|Odkazuje na metadata ze zadaných souborů sestavení.|
|[-refout](refout-compiler-option.md)|Generovat referenční sestavení kromě primárního sestavení.|
|[-refonly](refonly-compiler-option.md)|Generovat referenční sestavení místo primárního sestavení.|
|[-resource](resource-compiler-option.md)|Vloží zadaný prostředek.|
|-sady pravidel:\<souboru >|Zadejte soubor sady pravidel, která zakáže konkrétní diagnostiky.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Určuje minimální verzi podsystému, který můžete použít spustitelný soubor.|
|[-target](target-compiler-option.md)|Určuje formát výstupního souboru pomocí jedné ze čtyř možností: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [– cíl: modul](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|Umožňuje [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) kódu.|
|[-utf8output](utf8output-compiler-option.md)|Výstup zpráv kompilátoru v kódování UTF-8.|
|[-warn](warn-compiler-option.md)|Nastaví úroveň upozornění (0-4).|
|[-warnaserror](warnaserror-compiler-option.md)|Sestavy specifická upozornění jako chyby.|
|[-win32icon](win32icon-compiler-option.md)|Tato ikona se použije pro výstup.|
|[-win32manifest](win32manifest-compiler-option.md)|Určuje soubor manifestu win32 vlastní.|
|[-win32res](win32res-compiler-option.md)|Určuje soubor prostředku win32 (.res).|

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](index.md)
- [Možnosti kompilátoru jazyka C# uvedené podle kategorie](listed-by-category.md)
- [Postupy: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<Kompilátor > – Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
