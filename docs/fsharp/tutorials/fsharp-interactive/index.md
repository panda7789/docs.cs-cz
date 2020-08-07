---
title: Interaktivní referenční dokumentace F# (fsi.exe)
description: 'Přečtěte si, jak se F# Interactive (fsi.exe) používá ke interaktivnímu spouštění kódu F # v konzole nebo ke spouštění skriptů F #.'
ms.date: 05/16/2016
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 8bb1563ad34e65101fb9f09d6e347278e4b0de78
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854942"
---
# <a name="interactive-programming-with-f"></a>Interaktivní programování s použitím F\#

> [!NOTE]
> V tomto článku se aktuálně popisuje prostředí jenom pro Windows.

Program F# Interactive (fsi.exe) se používá pro interaktivní spuštění kódu jazyka F# v konzole nebo pro spuštění skriptů jazyka F#. Jinými slovy, interaktivní jazyk F# provede operace REPL (čtení, vyhodnocení, smyčka tisku) pro jazyk F#.

Chcete-li spustit jazyk F# Interactive z konzoly, spusťte program fsi.exe. Najdete fsi.exe v:

```console
C:\Program Files (x86)\Microsoft Visual Studio\2019\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

kde `sku` je buď `Community` , `Professional` nebo `Enterprise` .

Informace o dostupných možnostech příkazového řádku naleznete v tématu [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).

Pokud chcete spustit F# Interactive prostřednictvím sady Visual Studio, můžete kliknout na příslušné tlačítko panelu nástrojů s označením **F# Interactive**nebo použít klávesy **CTRL + ALT + F**. Tím otevřete interaktivní okno nástroje, ve kterém běží relace jazyka F# Interactive. Můžete také vybrat nějaký kód, který chcete spustit v interaktivním okně, a stisknout kombinaci kláves **ALT + ENTER**. F# Interactive se spustí v okně nástroje s označením **F# Interactive**. Použijete-li tuto kombinaci kláves, ujistěte se, že má okno editoru fokus.

Pokud používáte konzolu nebo sadu Visual Studio, zobrazí se příkazový řádek a překladač čeká na zadání. Zde je možné zadat kód stejně jako v souboru kódu. Chcete-li zkompilovat a spustit kód, zadejte dvě středníky (**;;**) pro ukončení řádku nebo několika řádků vstupu.

Jazyk F# Interactive se pokusí zkompilovat kód a v případě úspěchu kód spustí a vytiskne podpis zkompilovaných typů a hodnot. Pokud dojde k chybám, překladač vytiskne chybové zprávy.

Kód zadaný ve stejné relaci má přístup k libovolné konstrukci zadané dříve, takže lze sestavit programy. Rozsáhlá vyrovnávací paměť okna nástroje umožňuje v případě potřeby zkopírovat kód do souboru.

Při spuštění v sadě Visual Studio se jazyk F# Interactive spustí nezávisle na projektu, tedy například nelze použít konstrukce definované v projektu v jazyce F# Interactive, pokud nezkopírujete kód této funkce do interaktivního okna.

Pokud máte otevřený projekt, který odkazuje na některé knihovny, můžete na ně odkazovat pomocí **Průzkumník řešení**F# Interactive. Chcete-li odkazovat na knihovnu v F# Interactive, rozbalte uzel **odkazy** , otevřete místní nabídku knihovny a vyberte možnost **Odeslat do F# Interactive**.

Argumenty příkazového řádku (možnosti) jazyka F# Interactive lze řídit úpravou nastavení. V nabídce **nástroje** vyberte **Možnosti...** a potom rozbalte **Nástroje jazyka F #**. Dvě nastavení, která můžete změnit, jsou možnosti F# Interactive a nastavení **64 F# Interactive** , které je relevantní pouze v případě, že používáte F# Interactive na 64 počítači. Toto nastavení určuje, zda chcete spustit vyhrazenou 64bitovou verzi programu fsi.exe nebo fsianycpu.exe, který pomocí architektury počítače určí, zda se má spustit jako 32bitový nebo 64bitový proces.

## <a name="scripting-with-f"></a>Skriptování s F\#

Skripty používají příponu souboru **. fsx** nebo **. fsscript**. Namísto kompilování zdrojového kódu a pozdějšího spuštění zkompilovaného sestavení můžete pouze spustit **fsi.exe** a zadat název souboru skriptu zdrojového kódu f # a f # Interactive přečte kód a provede ho v reálném čase.

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Rozdíly mezi interaktivním, skriptovacím a zkompilovaným prostředím

Pokud kompilujete kód v F# Interactive bez ohledu na to, jestli používáte interaktivně nebo spuštěný skript, je definovaný symbol **Interactive** . Při kompilování kódu v kompilátoru je definován symbol **kompilovaný** . Pokud tedy kód potřebujete v kompilovaném a interaktivním režimu odlišit, lze pomocí direktivy preprocesoru podmíněné kompilace určit, který kód chcete použít.

Některé direktivy, které jsou k dispozici při spuštění skriptů v jazyce F# Interactive, nejsou k dispozici, pokud jsou spuštěny kompilátorem. Následující tabulka uvádí direktivy, které jsou k dispozici při použití jazyka F# Interactive.

|Směrnici|Popis|
|---------|-----------|
|**#help**|Zobrazí informace o dostupných direktivách.|
|**#I**|Určí vyhledávací cestu k sestavení v uvozovkách.|
|**#load**|Přečte zdrojový soubor, zkompiluje jej a spustí.|
|**#quit**|Ukončí relaci jazyka F# Interactive.|
|**#r**|Odkazuje na sestavení.|
|**#time ["on" &#124; "]**|**#Time** sám o sobě přepíná, zda se mají zobrazovat informace o výkonu. Pokud je povolena, jazyk F# Interactive měří reálný čas, čas procesoru a informace uvolňování paměti pro každou část kódu, která je interpretována a spuštěna.|

Pokud v jazyce F# Interactive určíte soubory nebo cesty, očekává se textový literál. Proto musí být soubory a cesty v uvozovkách a musí být použity obvyklé řídicí znaky. Lze také použít znak @, který způsobí, že jazyk F# Interactive interpretuje řetězec obsahující cestu jako doslovný řetězec. To způsobí, že jazyk F# Interactive ignoruje jakékoli řídicí znaky.

Jedním z rozdílů mezi kompilovaným a interaktivním režimem je způsob přístupu k argumentům příkazového řádku. V kompilovaném režimu použijte **System. Environment. GetCommandLineArgs**. Ve skriptech použijte **FSI. CommandLineArgs –**.

Následující kód ukazuje, jak vytvořit funkci, která čte argumenty příkazového řádku ve skriptu, a také ukazuje, jak ze skriptu odkazovat na jiné sestavení. První soubor kódu, **MyAssembly. FS**, je kód pro odkazované sestavení. Zkompilujte tento soubor pomocí příkazového řádku: **FSC-a MyAssembly. FS** a potom spusťte druhý soubor jako skript s příkazovým řádkem: **FSI--exec Soubor1. fsx** test

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

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="related-articles"></a>Související články

|Nadpis|Popis|
|-----|-----------|
|[Možnosti F# Interactive](../../language-reference/fsharp-interactive-options.md)|Popisuje syntaxi a možnosti příkazového řádku pro F# Interactive fsi.exe.|
|[Odkaz na knihovnu F# Interactive](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Popisuje funkce knihovny, které jsou k dispozici při spuštění kódu v jazyce F# Interactive.|
