---
title: Interaktivní možnosti
description: Přečtěte si o možnostech příkazového řádku, které podporuje F# Interactive, fsi.exe.
ms.date: 07/22/2020
ms.openlocfilehash: abddd1fd990be18ede139ab26ffe80513ba6e0dd
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855345"
---
# <a name="f-interactive-options"></a>Možnosti F# Interactive

Tento článek popisuje možnosti příkazového řádku, které podporuje F# Interactive, `fsi.exe` . F# Interactive přijímá mnoho ze stejných možností příkazového řádku jako kompilátor F #, ale také přijímá některé další možnosti.

## <a name="use-f-interactive-for-scripting"></a>Použití F# Interactive pro skriptování

F# Interactive, `dotnet fsi` , lze spustit interaktivně nebo je lze spustit z příkazového řádku pro spuštění skriptu. Syntaxe příkazového řádku je

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

Přípona souboru pro soubory skriptu F # je `.fsx` .

## <a name="table-of-f-interactive-options"></a>Tabulka možností F# Interactive

Následující tabulka shrnuje možnosti podporované nástrojem F# Interactive. Tyto možnosti lze nastavit na příkazovém řádku nebo v integrovaném vývojovém prostředí sady Visual Studio. Chcete-li nastavit tyto možnosti v integrovaném vývojovém prostředí sady Visual Studio, otevřete nabídku **nástroje** , vyberte možnost **Možnosti**, rozbalte uzel **nástroje F #** a vyberte možnost **F# Interactive**.

Kde se zobrazí seznamy v argumentech možností F# Interactive, prvky seznamu jsou odděleny středníky ( `;` ).

|Možnost|Popis|
|------|-----------|
|**--**|Slouží k pokynu F# Interactive, aby považovala zbývající argumenty za argumenty příkazového řádku pro program nebo skript jazyka F #, ke kterému můžete přistupovat v kódu pomocí seznamu **FSI. CommandLineArgs –**.|
|**--zaškrtnuto**[ **+**&#124;**-** ]|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--codepage: &lt; int&gt;**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--consolecolors**[ **+**&#124;**-** ]|Vypíše upozornění a chybové zprávy barevně.|
|**--crossoptimize**[ **+**&#124;**-** ]|Povolí nebo zakáže optimalizace mezi moduly.|
|**--Debug**[ **+**&#124;**-** ]<br /><br />**--debug:**[**full**&#124;**pdbonly**&#124;**přenosných**&#124;**vložených**]<br /><br />**-g**[ **+**&#124;**-** ]<br /><br />**-g:**[**full**&#124;**pdbonly**&#124;**přenosných**&#124;**vložených**]|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--define: &lt; String&gt;**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--deterministické**[ **+**&#124;**-** ]|Vytvoří deterministické sestavení (včetně GUID verze modulu a časového razítka).|
|**--Exec**|Instruuje F # Interactive, aby se ukončil po načtení souborů nebo spuštění souboru skriptu zadaného na příkazovém řádku.|
|**--fullpaths –**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--GUI**[ **+**&#124;**-** ]|Povolí nebo zakáže smyčku události model Windows Forms. Výchozí hodnota je povolena.|
|**--Help**<br /><br />**-?**|Slouží k zobrazení syntaxe příkazového řádku a stručný popis jednotlivých možností.|
|**--lib: &lt; Folder-list&gt;**<br /><br />**-I: &lt; seznam složek&gt;**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--Load: &lt; filename&gt;**|Zkompiluje daný zdrojový kód při spuštění a načte zkompilované konstrukce F # do relace. Pokud cílový zdroj obsahuje direktivy skriptování, například **#use** nebo **#load**, je nutné místo **--Load** nebo **#load**použít **--Use** nebo **#use** .|
|**--mlcompatibility**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--nerozhraní**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace najdete v tématu [Možnosti kompilátoru](compiler-options.md) .|
|**--logo**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--upozornit: &lt; Upozornění – seznam&gt;**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--optimize**[ **+**&#124;**-** ]|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--preferreduilang –: &lt; lang&gt;**| Určuje preferovaný název jazykové verze jazyka (například ES-ES, ja-JP). |
|**--quiet**|Potlačí výstup F# Interactive do datového proudu **stdout** .|
|**--quotes – ladění**|Určuje, že se mají vygenerovat dodatečné informace o ladění pro výrazy, které jsou odvozeny z literálů uvozovek F # a reflektované definice. Informace o ladění jsou přidány do vlastních atributů uzlu stromu výrazu F #. Viz [citace kódu](code-quotations.md) a [expr. CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--ReadLine**[ **+**&#124;**-** ]|Povolí nebo zakáže dokončování tabulátorů v interaktivním režimu.|
|**--Reference: &lt; filename&gt;**<br /><br />**-r: &lt; název souboru&gt;**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--volání funkce tail**[ **+**&#124;**-** ]|Povolí nebo zakáže použití instrukcí Tail IL, což způsobí, že se rámec zásobníku znovu použije pro rekurzivní funkce tail. Tato možnost je ve výchozím nastavení povolená.|
|**--targetprofile: &lt; String&gt;**|Určuje profil cílového rozhraní tohoto sestavení. Platné hodnoty jsou `mscorlib` , `netcore` nebo `netstandard` . Výchozí formát je `mscorlib`.|
|**--použít: &lt; filename&gt;**|Říká Překladači použití daného souboru při spuštění jako počáteční vstup.|
|**--Utf8Output –**|Stejné jako možnost kompilátoru fsc.exe. Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--Warn: &lt; úroveň upozornění&gt;**|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--warnaserror –**[ **+**&#124;**-** ]|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--warnaserror –**[ **+**&#124;**-** ]:** &lt; int-list &gt; **|Stejné jako možnost kompilátoru **fsc.exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|

## <a name="f-interactive-structured-printing"></a>F# Interactive strukturovaný tisk

F# Interactive ( `dotnet fsi` ) používá rozšířenou verzi [strukturovaného formátování prostého textu](plaintext-formatting.md) k sestavování hodnot.

1. Podporují se všechny funkce `%A` formátování prostého textu a některé jsou navíc přizpůsobitelné.

2. Tisk je barevný, pokud konzola výstupu podporuje barvy.

3. Limit je umístěn na délku zobrazených řetězců, pokud tento řetězec výslovně nevyhodnocujete.

4. Sada uživatelsky definovaných nastavení je k dispozici prostřednictvím `fsi` objektu.

Dostupná nastavení pro přizpůsobení formátu prostého textu pro hlášené hodnoty jsou:

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a>Přizpůsobení pomocí `AddPrinter` a`AddPrintTransformer`

Tisk v F# Interactive výstupech lze přizpůsobit pomocí `fsi.AddPrinter` a `fsi.AddPrintTransformer` .
První funkce poskytuje text, který nahradí tisk objektu. Druhá funkce vrátí náhradní objekt, který se zobrazí místo toho. Zvažte například následující kód F #:

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

Pokud spustíte příklad v F# Interactive, vypíše se výstup na základě sady možností formátování. V takovém případě má vliv na formátování data a času:

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

`fsi.AddPrintTransformer`dá se použít k poskytnutí náhradního objektu pro tisk:

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

Tyto výstupy:

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

Pokud předaná funkce Transformer předává `fsi.AddPrintTransformer` zpět `null` , je transformátor tisku ignorován.
To lze použít k filtrování libovolné vstupní hodnoty, a to od typu `obj` .  Příklad:

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

Tyto výstupy:

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku, které jsou k dispozici pro kompilátor jazyka F # **fsc.exe**.|
