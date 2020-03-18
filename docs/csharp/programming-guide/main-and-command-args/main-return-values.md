---
title: Main() Návratové hodnoty - Průvodce programováním Jazyka C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: eaa78c33613093bb0e108870669392d07d346a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503998"
---
# <a name="main-return-values-c-programming-guide"></a>Main() vrácené hodnoty (Průvodce programováním Jazyka C#)

Metoda `Main` může `void`vrátit :

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Může také vrátit `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Pokud se návratová hodnota z `Main` `void` nepoužívá, vrácení umožňuje mírně jednodušší kód. Vrácení celého čísla však umožňuje programu sdělit informace o stavu jiným programům nebo skriptům, které vyvolávají spustitelný soubor. Vrácená hodnota `Main` z je považována za ukončovací kód procesu. Pokud `void` je `Main` vrácena z ukončovací kód bude implicitně `0`. Následující příklad ukazuje, jak `Main` lze získat přístup k vrácené hodnotě z.

## <a name="example"></a>Příklad

Tento příklad používá nástroje příkazového řádku [.NET Core.](../../../core/index.md) Pokud nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete se o nich dozvědět v tomto [tématu Začínáme](../../../core/tutorials/cli-create-console-app.md).

Metodu `Main` v *program.cs* upravte takto:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Při spuštění programu v systému Windows je `Main` jakákoli hodnota vrácená z funkce uložena v proměnné prostředí. Tuto proměnnou prostředí lze `ERRORLEVEL` načíst pomocí `$LastExitCode` dávkového souboru nebo z prostředí PowerShell.

Aplikaci můžete sestavit pomocí příkazu [dotnet CLI.](../../../core/tools/dotnet.md) `dotnet build`

Dále vytvořte skript Powershellu pro spuštění aplikace a zobrazení výsledku. Vložte následující kód do textového `test.ps1` souboru a uložte jej jako ve složce, která obsahuje projekt. Spusťte skript powershellu zadáním `test.ps1` na výzvu powershellu.

Vzhledem k tomu, že kód vrátí nulu, dávkový soubor bude hlásit úspěch. Pokud však změníte MainReturnValTest.cs vrátíte nenulovou hodnotu a potom program znovu zkompilujete, následné spuštění skriptu prostředí PowerShell oznámí chybu.

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Ukázkový výstup

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Asynchronní hlavní vrácené hodnoty

Asynchronní hlavní vrácené hodnoty přesunout často používaný kód `Main` potřebný pro volání asynchronní metody v kódu generovanékompilátorem. Dříve budete muset napsat tuto konstrukci volat asynchronní kód a ujistěte se, že program běžel, dokud asynchronní operace dokončena:

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Nyní může být nahrazen:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Výhodou nové syntaxe je, že kompilátor vždy generuje správný kód.

## <a name="compiler-generated-code"></a>Kód generovaný kompilátorem

Pokud vstupní bod aplikace `Task` `Task<int>`vrátí a , kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu deklarovanou v kódu aplikace. Za předpokladu, že `$GeneratedMain`je tento vstupní bod volán , kompilátor generuje následující kód pro tyto vstupní body:

- `static Task Main()`výsledkem je, že kompilátor vyzařuje ekvivalent`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`výsledkem je, že kompilátor vyzařuje ekvivalent`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`výsledkem je, že kompilátor vyzařuje ekvivalent`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`výsledkem je, že kompilátor vyzařuje ekvivalent`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Pokud jsou použity `async` příklady `Main` modifikátor u metody, kompilátor by generovat stejný kód.

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Odkaz jazyka C#](../index.md)
- [Argumenty Main() a příkazového řádku](index.md)
- [Jak zobrazit argumenty příkazového řádku](./how-to-display-command-line-arguments.md)
