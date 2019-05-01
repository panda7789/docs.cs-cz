---
title: Interaktivní referenční dokumentace F# (fsi.exe)
description: Zjistěte, jak F# Interactive (fsi.exe) se používá ke spouštění F# kódu interaktivní konzoly nebo k provádění F# skripty.
ms.date: 05/16/2016
ms.openlocfilehash: 9ec780ca51eaa5ae0aa791eb509d8ad0865dc26f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982737"
---
# <a name="interactive-programming-with-f"></a>Interaktivní programování s F\#

> [!NOTE]
> Tento článek popisuje aktuálně prostředí jenom pro Windows.  Bude přepsán.

> [!NOTE]
> Odkaz rozhraní API se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

Program F# Interactive (fsi.exe) se používá pro interaktivní spuštění kódu jazyka F# v konzole nebo pro spuštění skriptů jazyka F#. Jinými slovy, interaktivní jazyk F# provede operace REPL (čtení, vyhodnocení, smyčka tisku) pro jazyk F#.

Chcete-li spustit jazyk F# Interactive z konzoly, spusťte program fsi.exe.  Zjistíte fsi.exe v:

```console
C:\Program Files (x86)\Microsoft Visual Studio\2017\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

kde `sku` je buď `Community`, `Professional`, nebo `Enterprise`.

Informace o dostupných možnostech příkazového řádku najdete v tématu [ F# interaktivní možnosti](../../language-reference/fsharp-interactive-options.md).

Ke spuštění F# interaktivní prostřednictvím sady Visual Studio, můžete kliknutí na příslušné tlačítko s popiskem  **F# interaktivní**, nebo pomocí kláves **Ctrl + Alt + F**. Tím otevřete interaktivní okno nástroje, ve kterém běží relace jazyka F# Interactive. Můžete také vybrat část kódu, které chcete spustit v interaktivním okně a stisknout kombinaci kláves **ALT + ENTER**. F#V panelu nástrojů označené jako interaktivní spuštění  **F# interaktivní**. Použijete-li tuto kombinaci kláves, ujistěte se, že má okno editoru fokus.

Pokud používáte konzolu nebo sadu Visual Studio, zobrazí se příkazový řádek a překladač čeká na zadání. Zde je možné zadat kód stejně jako v souboru kódu. Chcete-li zkompilovat a spustit kód, zadáním dvou středníků (**;** ) ukončete řádek nebo několik řádků vstupu.

Jazyk F# Interactive se pokusí zkompilovat kód a v případě úspěchu kód spustí a vytiskne podpis zkompilovaných typů a hodnot. Pokud dojde k chybám, překladač vytiskne chybové zprávy.

Kód zadaný ve stejné relaci má přístup k libovolné konstrukci zadané dříve, takže lze sestavit programy. Rozsáhlá vyrovnávací paměť okna nástroje umožňuje v případě potřeby zkopírovat kód do souboru.

Při spuštění v sadě Visual Studio se jazyk F# Interactive spustí nezávisle na projektu, tedy například nelze použít konstrukce definované v projektu v jazyce F# Interactive, pokud nezkopírujete kód této funkce do interaktivního okna.

Pokud máte-li otevřen projekt, který odkazuje na některé knihovny, můžete odkazovat v F# interaktivní prostřednictvím **Průzkumníka řešení**. Odkaz knihovny F# interaktivní, rozbalte **odkazy** uzel, otevřete místní nabídku knihovny a zvolte **odeslat F# interaktivní**.

Argumenty příkazového řádku (možnosti) jazyka F# Interactive lze řídit úpravou nastavení. Na **nástroje** příkaz **možnosti...** a potom rozbalte  **F# nástroje**. Jsou dvě nastavení, které můžete změnit F# interaktivní možnosti a **64-bit F# interaktivní** nastavení, která je relevantní pouze v případě, že používáte F# Interactive v 64bitovém počítači. Toto nastavení určuje, zda chcete spustit vyhrazenou 64bitovou verzi programu fsi.exe nebo fsianycpu.exe, který pomocí architektury počítače určí, zda se má spustit jako 32bitový nebo 64bitový proces.

## <a name="scripting-with-f"></a>Skriptování s F\#
Skripty používají příponu souboru **.fsx** nebo **.fsscript**. Namísto zkompilování zdrojového kódu a následného spuštění zkompilovaného sestavení, lze pouze spustit **fsi.exe** a zadejte název souboru skriptu F# zdrojový kód, a F# interactive tento kód načte a spustí v reálném čas.

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Rozdíly mezi interaktivním, skriptovacím a kompilovaným prostředím
Při kompilaci kódu v F# interaktivní, zda jsou spustíte interaktivně nebo spustíte skript, symbol **interaktivní** je definována. Při kompilaci kódu v kompilátoru, symbol **ZKOMPILOVANÉ** je definována. Pokud tedy kód potřebujete v kompilovaném a interaktivním režimu odlišit, lze pomocí direktivy preprocesoru podmíněné kompilace určit, který kód chcete použít.

Některé direktivy, které jsou k dispozici při spuštění skriptů v jazyce F# Interactive, nejsou k dispozici, pokud jsou spuštěny kompilátorem. Následující tabulka uvádí direktivy, které jsou k dispozici při použití jazyka F# Interactive.

|– Direktiva|Popis|
|---------|-----------|
|**#help**|Zobrazí informace o dostupných direktivách.|
|**#I**|Určí vyhledávací cestu k sestavení v uvozovkách.|
|**#load**|Přečte zdrojový soubor, zkompiluje jej a spustí.|
|**#quit**|Ukončí relaci jazyka F# Interactive.|
|**#r**|Odkazuje na sestavení.|
|**#time ["na"&#124;"off"]**|Samostatně **#time** přepíná, jestli se má zobrazit informace o výkonu. Pokud je povolena, jazyk F# Interactive měří reálný čas, čas procesoru a informace uvolňování paměti pro každou část kódu, která je interpretována a spuštěna.|

Pokud v jazyce F# Interactive určíte soubory nebo cesty, očekává se textový literál. Proto musí být soubory a cesty v uvozovkách a musí být použity obvyklé řídicí znaky. Lze také použít znak @, který způsobí, že jazyk F# Interactive interpretuje řetězec obsahující cestu jako doslovný řetězec. To způsobí, že jazyk F# Interactive ignoruje jakékoli řídicí znaky.

Jedním z rozdílů mezi kompilovaným a interaktivním režimem je způsob přístupu k argumentům příkazového řádku. V kompilovaném režimu použijte **System.Environment.GetCommandLineArgs**. Ve skriptech použijte **fsi.CommandLineArgs**.

Následující kód ukazuje, jak vytvořit funkci, která čte argumenty příkazového řádku ve skriptu, a také ukazuje, jak ze skriptu odkazovat na jiné sestavení. První soubor kódu **MyAssembly.fs**, je kód pro sestavení, na kterou se odkazuje. Zkompilujte tento soubor s příkazovým řádkem: **fsc - a MyAssembly.fs** a potom spusťte druhý soubor jako skript s příkazovým řádkem: **fsi - exec file1.fsx** testování

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

Výstup je následující:

```
Command line arguments: 
file1.fsx
test
90
```

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Možnosti F# Interactive](../../language-reference/fsharp-interactive-options.md)|Popisuje syntaxi příkazového řádku a možnosti F# Interactive, fsi.exe.|
|[F#Interaktivní referenční dokumentace knihovny](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Popisuje funkce knihovny, které jsou k dispozici při spuštění kódu v jazyce F# Interactive.|