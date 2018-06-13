---
title: Interaktivní referenční dokumentace F# (fsi.exe)
description: 'Zjistěte, jak F # interaktivní (fsi.exe) se používá interaktivní spuštění F # – kód v konzole nebo spuštění skriptů F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b16ebcfe361ef50c7c7ba8510f01f6704e62ce3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564875"
---
# <a name="interactive-programming-with-f"></a>Interaktivní programování s jazykem F# #

> [!NOTE]
Tento článek popisuje aktuálně prostředí jenom pro Windows.  Bude přepsán.

> [!NOTE]
Rozhraní API použití odkazu přejdete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Program F# Interactive (fsi.exe) se používá pro interaktivní spuštění kódu jazyka F# v konzole nebo pro spuštění skriptů jazyka F#. Jinými slovy, interaktivní jazyk F# provede operace REPL (čtení, vyhodnocení, smyčka tisku) pro jazyk F#.

Chcete-li spustit jazyk F# Interactive z konzoly, spusťte program fsi.exe.  Zjistíte, fsi.exe v "c:\Program soubory (x86) \Microsoft SDKs\F#\<verze > \Framework\<verze >\". Informace o dostupných možnostech příkazového řádku najdete v tématu [interaktivní možnosti F #](../../language-reference/fsharp-interactive-options.md).

Pokud chcete spustit F # interaktivní pomocí sady Visual Studio, můžete kliknutím na tlačítko příslušný panel nástrojů s názvem bez přípony **F # interaktivní**, nebo použijte klávesy se **Ctrl + Alt + F**. Tím otevřete interaktivní okno nástroje, ve kterém běží relace jazyka F# Interactive. Můžete také vybrat určitý kód, který chcete spustit v okně interaktivní a stiskněte kombinaci kláves **ALT + ENTER**. F # interaktivní se spustí v okně nástroje s názvem bez přípony **F # interaktivní**. Použijete-li tuto kombinaci kláves, ujistěte se, že má okno editoru fokus.

Pokud používáte konzolu nebo sadu Visual Studio, zobrazí se příkazový řádek a překladač čeká na zadání. Zde je možné zadat kód stejně jako v souboru kódu. Pro zkompilování a spuštění kódu, zadejte dva středníky (**;** ) ukončit nebo více řádků vstupu.

Jazyk F# Interactive se pokusí zkompilovat kód a v případě úspěchu kód spustí a vytiskne podpis zkompilovaných typů a hodnot. Pokud dojde k chybám, překladač vytiskne chybové zprávy.

Kód zadaný ve stejné relaci má přístup k libovolné konstrukci zadané dříve, takže lze sestavit programy. Rozsáhlá vyrovnávací paměť okna nástroje umožňuje v případě potřeby zkopírovat kód do souboru.

Při spuštění v sadě Visual Studio se jazyk F# Interactive spustí nezávisle na projektu, tedy například nelze použít konstrukce definované v projektu v jazyce F# Interactive, pokud nezkopírujete kód této funkce do interaktivního okna.

Pokud máte otevřený projekt, který odkazuje na některé knihovny, můžete odkazovat v F # interaktivní prostřednictvím **Průzkumníku řešení**. Chcete-li knihovnu v F # interaktivní, rozbalte **odkazy** uzlu, otevřete místní nabídku pro knihovnu a zvolte **poslat F # interaktivní**.

Argumenty příkazového řádku (možnosti) jazyka F# Interactive lze řídit úpravou nastavení. Na **nástroje** nabídce vyberte možnost **možnosti...** a potom rozbalte **nástroje F #**. Jsou dvě nastavení, které je možné změnit F # interaktivní možnosti a **64-bit F # interaktivní** nastavení, které se týkají jenom v případě, že používáte F # interaktivní na 64bitový počítač. Toto nastavení určuje, zda chcete spustit vyhrazenou 64bitovou verzi programu fsi.exe nebo fsianycpu.exe, který pomocí architektury počítače určí, zda se má spustit jako 32bitový nebo 64bitový proces.


## <a name="scripting-with-f"></a>Skriptování pomocí jazyka F# #
Skripty používat příponu souboru **.fsx** nebo **.fsscript**. Místo kompilování zdrojového kódu a pak spustit kompilované sestavení, můžete stačí spustit **fsi.exe** a zadejte název souboru skriptu zdrojového kódu F # a F # interaktivní kód načte a spustí v reálném čase.


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Rozdíly mezi interaktivním, skriptovacím a kompilovaným prostředím
Při kompilování kódu v F # interaktivní, zda používáte systém interaktivně, nebo spuštění skriptu, symbol **interaktivní** je definována. Když jsou kompilování kódu v kompilátoru, symbol **ZKOMPILOVANÉ** je definována. Pokud tedy kód potřebujete v kompilovaném a interaktivním režimu odlišit, lze pomocí direktivy preprocesoru podmíněné kompilace určit, který kód chcete použít.

Některé direktivy, které jsou k dispozici při spuštění skriptů v jazyce F# Interactive, nejsou k dispozici, pokud jsou spuštěny kompilátorem. Následující tabulka uvádí direktivy, které jsou k dispozici při použití jazyka F# Interactive.

|– Direktiva|Popis|
|---------|-----------|
|**#help**|Zobrazí informace o dostupných direktivách.|
|**#I**|Určí vyhledávací cestu k sestavení v uvozovkách.|
|**#load**|Přečte zdrojový soubor, zkompiluje jej a spustí.|
|**#quit**|Ukončí relaci jazyka F# Interactive.|
|**#r**|Odkazuje na sestavení.|
|**#time ["na"&#124;"vypnuto"]**|Samostatně **#time** přepíná, jestli se má zobrazit informace o výkonu. Pokud je povolena, jazyk F# Interactive měří reálný čas, čas procesoru a informace uvolňování paměti pro každou část kódu, která je interpretována a spuštěna.|

Pokud v jazyce F# Interactive určíte soubory nebo cesty, očekává se textový literál. Proto musí být soubory a cesty v uvozovkách a musí být použity obvyklé řídicí znaky. Lze také použít znak @, který způsobí, že jazyk F# Interactive interpretuje řetězec obsahující cestu jako doslovný řetězec. To způsobí, že jazyk F# Interactive ignoruje jakékoli řídicí znaky.

Jedním z rozdílů mezi kompilovaným a interaktivním režimem je způsob přístupu k argumentům příkazového řádku. V režimu kompilované pomocí **System.Environment.GetCommandLineArgs**. Ve skriptech, použijte **fsi.CommandLineArgs**.

Následující kód ukazuje, jak vytvořit funkci, která čte argumenty příkazového řádku ve skriptu, a také ukazuje, jak ze skriptu odkazovat na jiné sestavení. První soubor kódu **MyAssembly.fs**, je kód pro sestavení se na ně odkazovat. Kompilace tento soubor s příkazovým řádkem: **fsc - a MyAssembly.fs** a potom spusťte druhý soubor jako skript s příkazovým řádkem: **fsi – exec file1.fsx** testování

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

Výstup vypadá takto:

```
Command line arguments: 
file1.fsx
test
90
```

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Možnosti F# Interactive](../../language-reference/fsharp-interactive-options.md)|Popisuje syntaxe příkazového řádku a možnosti pro F # interaktivní, fsi.exe.|
|[Referenční dokumentace interaktivní knihovny F #](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Popisuje funkce knihovny, které jsou k dispozici při spuštění kódu v jazyce F# Interactive.|
