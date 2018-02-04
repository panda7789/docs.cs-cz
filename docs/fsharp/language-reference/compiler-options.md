---
title: "Možnosti kompilátoru (F#)"
description: "K řízení kompilace aplikacím F # a knihovny, použijte možnosti F # kompilátoru příkazového řádku."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c797cf0b-5953-4053-8626-0558e9eaf10f
ms.openlocfilehash: 23731832141bc2f74a04c5f4027fc210b5589537
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="compiler-options"></a>Možnosti kompilátoru

Toto téma popisuje možnosti kompilátoru příkazového řádku pro kompilátor F # fsc.exe. Kompilace prostředí můžete také řízena nastavením vlastností projektu.


## <a name="compiler-options-listed-alphabetically"></a>Možnosti kompilátoru (abecední pořadí)
V následující tabulce jsou uvedeny možnosti kompilátoru uvedené podle abecedy. Některé z možností kompilátoru F # jsou podobné možnosti kompilátoru C#. Pokud je to tento případ, je k dispozici odkaz na téma možnosti kompilátoru C#.



|– Možnost kompilátoru|Popis|
|---------------|-----------|
|**-a ***&lt;název výstupního souboru&gt;**|Generuje knihovny a určuje její název souboru. Tato možnost je zkratka pro **– target: library ***&lt;filename&gt;**.|
|**--baseaddress:&lt;string&gt;**|Určuje základní adresu knihovnu, která má být sestaven.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; baseaddress &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|**codepage –:&lt;int&gt;**|Určuje codepage použít ke čtení zdrojové soubory.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; codepage &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/w0kyekyh.aspx).|
|**--consolecolors**|Určuje, že chyby a upozornění používat barevně text v konzole.|
|**--crossoptimize**[**+**&#124;**-**]|Povolí nebo zakáže cross-module optimalizace.|
|**--delaysign**[**+**&#124;**-**]|Podepíše sestavení pomocí veřejné části složitý název klíče.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; delaysign &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|**--checked**[**+**&#124;**-**]|Povolí nebo zakáže generování kontroly přetečení.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; zaškrtnutí &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|**--debug**[**+**&#124;**-**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**--debug**:[**full**&#124;**pdbonly**]<br /><br />**-g:** [**úplné**&#124; **pdbonly**]|Povolí nebo zakáže generování ladicích informací nebo určuje typ ladicí informace pro generování. Výchozí hodnota je úplná, což umožňuje připojení ke spuštěným programem. Zvolte **pdbonly** omezené ladění informace uložené v souboru pdb (databázi programu).<br /><br />Ekvivalent možnosti kompilátoru C# se stejným názvem. Další informace naleznete v tématu<br /><br />[&#47; ladění &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|**--definovat:&lt;řetězec&gt;**<br /><br />**-d:&lt;řetězec&gt;**|Definuje symbol pro použití v Podmíněná kompilace.|
|**--deterministic**[**+**&#124;**-**]|Vytvořit deterministickou sestavení (včetně verze modulu GUID a časové razítko).  To nelze použít s čísla verzí zástupný znak a podporuje pouze vložené a přenosné ladění typy|
|**--doc:&lt;xmldoc-filename&gt;**|Dá pokyn kompilátoru generovat dokumentační komentáře XML do zadaného souboru. Další informace najdete v tématu [dokumentace XML](xml-documentation.md).<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; doc &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|**--fullpaths**|Dá pokyn kompilátoru generovat úplné cesty.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; fullpaths &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/d315xc66.aspx).|
|**--help**<br /><br />**-?**|Zobrazí informace o využití, včetně všech možností kompilátoru stručný popis.|
|**--highentropyva**[**+**&#124;**-**]|Povolí nebo zakáže adresu vysokou entropií místo rozložení náhodného přeskupování (technologie ASLR), o funkci Rozšířené zabezpečení. Operační systém randomizes umístění v paměti, ve kterém jsou načtená infrastruktury pro aplikace (například zásobníku a haldy). Pokud povolíte tuto možnost, operačních systémů můžete použít tento náhodného přeskupování využít úplná adresa 64-bit místo na 64bitový počítač.|
|**--keycontainer:&lt;string&gt;**|Určuje kontejner klíče se silným názvem.|
|**--keyfile:&lt;filename&gt;**|Určuje název souboru veřejného klíče pro podepisování vygenerované sestavení.|
|**--lib:&lt;folder-name&gt;**<br /><br />**-I:&lt;folder-name&gt;**|Určuje adresář, který má být vyhledán sestavení, které odkazují.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; lib &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|**--linkresource**:**&lt;resource-info&gt;**|Zadaný prostředek odkazuje na sestavení. Formát prostředku údajů je *filename*[,*název*[,*veřejné*&#124; *privátní*]]<br /><br />Propojování jeden prostředek pomocí této možnosti je alternativa k vložení souboru celý zdroj **– prostředek** možnost.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; linkresource &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|**--mlcompatibility**|Ignoruje upozornění, která se při použití funkce, které jsou navrženy pro kompatibilitu s jinými verzemi ML.|
|**--noframework**|Zakáže výchozí odkaz na sestavení rozhraní .NET Framework.|
|**--nointerfacedata**|Dá pokyn kompilátoru vynechat prostředků obvykle přidá k sestavení, která zahrnuje F # – konkrétních metadat.|
|**--nologo**|Při spuštění kompilátor a ta nezobrazí text hlavičky.|
|**--nooptimizationdata**|Dá pokyn kompilátoru zahrnout pouze optimalizace, které jsou nezbytné k implementaci vložená konstrukce. Omezuje cross-module vložené ale binární kompatibilitu.|
|**--nowin32manifest**|Dá pokyn kompilátoru vynechat manifest Win32 výchozí.|
|**--nowarn:&lt;int-list&gt;**|Zakáže konkrétní varování uvedené podle čísla. Všechna čísla upozornění oddělte čárkou. Můžete zjistit počet upozornění pro všechna upozornění týkající se z výstupu kompilace.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; nowarn &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|**--optimize**[**+**&#124;**-**]**[&lt;string-list&gt;]**<br /><br />**-O [+ &#124;-] [&lt;seznamu řetězců&gt;]**|Povolí nebo zakáže optimalizace. Některé možnosti optimalizace můžete zakázat nebo povolit selektivně tak, že je uvedete. Jsou to: **nojitoptimize**, **nojittracking**, **nolocaloptimize**, **nocrossoptimize**, **notailcalls**.|
|**– out:&lt;název výstupního souboru&gt;**<br /><br />**-o:&lt;název výstupního souboru&gt;**|Určuje název kompilované sestavení nebo modul.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; se na &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|**--pdb:&lt;pdb-filename&gt;**|Názvy výstupního souboru PDB (databázi programu) ladění. Tato možnost platí pouze při **– ladění** zapnuta.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; pdb &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/ms228625.aspx).|
|**--platformy:&lt;název platformy&gt;**|Určuje, že generovaný kód lze spustit pouze v zadanou platformu (**x86**, **Itanium**, nebo **x64**), nebo pokud název platformy **anycpu**je vybrána, určuje, že generovaný kód můžete spustit na jakékoli platformě.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; platformy &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|**preferreduilang –:&lt;jazyk&gt;**| Určuje název jazykové verze jazyka upřednostňované výstup (například es-ES, ja-JP). |
|**--quotations-debug**|Určuje, že by měl pro výrazy, které jsou odvozeny od uvozovek literály F # a reflektován definice vygenerované velmi ladicí informace. Informace o ladění se přidá do vlastní atributy uzlu stromu výraz F #. V tématu [Code uvozovky](code-quotations.md) a [Expr.CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--reference:&lt;assembly-filename&gt;**<br /><br />**-r** &lt; **filename sestavení&gt;**|Zpřístupní kódu ze sestavení F # nebo rozhraní .NET Framework se zkompilování kódu.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; odkaz &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|**--prostředků:&lt;filename prostředků&gt;**|Vloží soubor spravovaných prostředků do vygenerované sestavení.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; prostředků &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|**sig –**:&lt;**filename podpis&gt;**|Generuje soubor podpisu podle vygenerované sestavení. Další informace o souborech podpis najdete v tématu [podpisy](signatures.md).|
|**--simpleresolution**|Určuje, že odkazy na sestavení by se měly vyřešit pomocí Mono pravidla založená na adresář, nikoli MSBuild řešení. Výchozí hodnota je použití nástroje MSBuild řešení s výjimkou při spuštění v rámci Mono.|
|**--standalone**|Určuje vytváření sestavení, které obsahuje všechny jeho závislé součásti tak, aby běžel samostatně bez nutnosti dalších sestavení, například knihovny F #.|
|**staticlink –:&lt;název sestavení**&gt;|Staticky odkazuje zadaného sestavení a všechny odkazované knihovny DLL, které jsou závislé na toto sestavení. Použijte název sestavení, nikoli na název knihovny DLL.|
|**--subsystemversion**|Určuje verzi operačního systému subsystému má být používána generovaného spustitelný soubor. Použijte 6.02 pro Windows 8.1, 6.01 pro systém Windows 7, 6.00 pro systém Windows Vista. Tato možnost jenom platí pro spustitelné soubory, není knihovny DLL a je nutno použít pouze pokud je aplikace závislá na konkrétní bezpečnostní funkce, které jsou k dispozici pouze na určité verze operačního systému. Pokud tato možnost se používá, a uživatel se pokusí spustit aplikaci na nižší verzi operačního systému, se nezdaří s chybovou zprávou.|
|**tailcalls –**[**+**&#124; **-**]|Povolí nebo zakáže použití pokyn IL tail, což způsobí, že rámce zásobníku znovu použije pro rekurzivní funkce tail. Tato možnost je povolená ve výchozím nastavení.|
|**--Cíl**: [**exe** &#124; **winexe** &#124; **knihovny** &#124; **modulu** ]  **&lt;název výstupního souboru&gt;**|Určuje typ a název souboru kompilované generovaného kódu.<ul><li>**exe** znamená konzolové aplikace.<br /></li><li>**winexe** znamená aplikace systému Windows, který se liší od konzolové aplikace v tom, že nemá standardní vstupní/výstupní datové proudy (stdin, stdout a stderr) definované.<br /></li><li>**Knihovna** je sestavení bez vstupního bodu.<br /></li><li>**modul** je modul rozhraní .NET Framework (.netmodule), který lze později kombinovat s z ostatních modulů do sestavení.<br /></li><ul/>Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; cílový &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|**--časy**|Zobrazí informace o časování pro kompilaci.|
|**--utf8output**|Umožňuje tisk výstupu kompilátoru s kódováním UTF-8.|
|**--warn:&lt;warning-level&gt;**|Nastaví úroveň pro upozornění (0 až 5). Výchozí úroveň je 3. Každé upozornění se přiřadí úroveň na základě jejich jeho závažnosti. Úroveň 5 nabízí další, ale méně závažné, upozornění než úroveň 1.<br /><br />Upozornění na úrovni 5 jsou: (rekurzivní použijte zaškrtnutí za běhu) 21, 22 (**umožní rec** vyhodnotit mimo pořadí), 45 (abstrakce úplné) a 52 (Obranným kopie). Všechny další upozornění jsou úroveň 2.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; upozornit &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|**--warnon:&lt;int-list&gt;**|Povolte konkrétní varování, které může být vypnuto ve výchozím nastavení nebo zakázal jinou možnost příkazového řádku. V F # 3.0 pouze upozornění. 1182 (nepoužívané proměnné) je vypnuto ve výchozím nastavení.|
|**--warnaserror**[**+**&#124;**-**] [**&lt;int-list&gt;**]|Povolí nebo zakáže možnost sestavy upozornění jako chyby. Můžete zadat konkrétní čísel upozornění na zakázat nebo povolit. Možnosti později v příkazovém řádku přepsat možnosti dříve v příkazovém řádku. Například pokud chcete nastavit upozornění, které nechcete použít hlášen jako chyby, zadejte **– warnaserror + warnaserror –-:&lt;int seznamu&gt;**.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; warnaserror &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|**--win32manifest:manifest-filename**|Přidá soubor manifestu Win32 kompilace. Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; win32manifest &#40; C &#35; Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/bb545961.aspx).|
|**--win32res:resource-filename**|Přidá zdrojového souboru Win32 kompilace.<br /><br />Tato možnost kompilátoru je ekvivalentem možnosti kompilátoru C# se stejným názvem. Další informace najdete v tématu [&#47; win32res (&#40; C & #35); Možnosti kompilátoru &#41; ](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-topics"></a>Související témata


|Název|Popis|
|-----|-----------|
|[Možnosti F# Interactive](fsharp-interactive-options.md)|Popisuje možnosti příkazového řádku překladač F # nepodporuje fsi.exe.|
|[Referenční dokumentace k vlastnostem projektu](/visualstudio/ide/reference/project-properties-reference)|Popisuje uživatelské rozhraní pro projekty, včetně stránek vlastností projektu, které poskytují možnosti sestavení.|
