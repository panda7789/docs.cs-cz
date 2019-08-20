---
title: Návratové hodnoty Main () C# – Průvodce programováním
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 1be04f98a4dec1317c485c7e482568cfe48ea9bf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588882"
---
# <a name="main-return-values-c-programming-guide"></a>Návratové hodnoty Main ()C# (Průvodce programováním)

Metoda může vracet `void`: `Main`

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Může také vrátit `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Pokud se návratová hodnota `Main` nepoužívá `void` , vrátí návrat umožňuje mírně jednodušší kód. Vrácení celého čísla ale umožňuje programu sdělit informace o stavu jiným programům nebo skriptům, které vyvolávají spustitelný soubor. Návratová hodnota z `Main` je považována za ukončovací kód procesu. Pokud `void` je vrácen z `Main` ukončovacího `0`kódu, bude implicitně. Následující příklad ukazuje, jak `Main` lze získat pøístup k návratové hodnotě.

## <a name="example"></a>Příklad

V tomto příkladu se používají nástroje příkazového řádku [.NET Core](../../../core/index.md) . Pokud si nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete o nich získat informace v tomto [tématu Začínáme](../../../core/tutorials/using-with-xplat-cli.md).

Upravte metodu v program.cs následujícím způsobem: `Main`

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Když je program spuštěn ve Windows, všechny hodnoty vrácené `Main` funkcí jsou uloženy v proměnné prostředí. Tato proměnná prostředí se dá načíst pomocí `ERRORLEVEL` dávkového souboru nebo `$LastExitCode` z PowerShellu.

Aplikaci můžete vytvořit pomocí příkazu [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` .

Potom vytvořte powershellový skript, který spustí aplikaci a zobrazí výsledek. Vložte následující kód do textového souboru a uložte jej jako `test.ps1` ve složce, která obsahuje projekt. Spusťte skript prostředí PowerShell zadáním `test.ps1` příkazu do příkazového řádku PowerShellu.

Vzhledem k tomu, že kód vrátí hodnotu nula, dávkový soubor ohlásí úspěch. Pokud ale změníte MainReturnValTest.cs a vrátíte nenulovou hodnotu a pak znovu zkompilujete program, při následném spuštění skriptu PowerShellu se nahlásí chyba.

```powershell
dotnet run
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

## <a name="async-main-return-values"></a>Asynchronní hlavní návratové hodnoty

Asynchronní hlavní návratové hodnoty přesunou často používaný kód, který je nezbytný pro volání asynchronních metod v `Main` kódu generovaném kompilátorem. Dříve museli jste napsat tuto konstrukci pro volání asynchronního kódu a zajistěte, aby byl program spuštěn až do dokončení asynchronní operace:

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

Teď to může nahradit:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Výhodou nové syntaxe je, že kompilátor vždy generuje správný kód.

## <a name="compiler-generated-code"></a>Kód generovaný kompilátorem

Když vstupní bod aplikace vrátí `Task` nebo `Task<int>`, kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu deklarovanou v kódu aplikace. Za předpokladu, že je volán `$GeneratedMain`tento vstupní bod, kompilátor generuje pro tyto vstupní body následující kód:

- `static Task Main()`Výsledkem je, že kompilátor emituje ekvivalent`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`Výsledkem je, že kompilátor emituje ekvivalent`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`Výsledkem je, že kompilátor emituje ekvivalent`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`Výsledkem je, že kompilátor emituje ekvivalent`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Pokud příklady použili `async` modifikátor `Main` metody, kompilátor vygeneruje stejný kód.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [C#Odkaz](../index.md)
- [Argumenty Main() a příkazového řádku](index.md)
- [Postupy: Zobrazit argumenty příkazového řádku](./how-to-display-command-line-arguments.md)
