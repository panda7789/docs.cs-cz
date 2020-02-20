---
title: Návratové hodnoty Main () C# – Průvodce programováním
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: eaa78c33613093bb0e108870669392d07d346a95
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503998"
---
# <a name="main-return-values-c-programming-guide"></a>Návratové hodnoty Main ()C# (Průvodce programováním)

Metoda `Main` může vracet `void`:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Může také vracet `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Pokud se návratová hodnota z `Main` nepoužívá, vrátí `void` možnost pro mírně jednodušší kód. Vrácení celého čísla ale umožňuje programu sdělit informace o stavu jiným programům nebo skriptům, které vyvolávají spustitelný soubor. Návratová hodnota z `Main` je považována za ukončovací kód procesu. Pokud se `void` vrátí z `Main` ukončovací kód bude implicitně `0`. Následující příklad ukazuje, jak je možné získat pøístup k návratové hodnotě z `Main`.

## <a name="example"></a>Příklad

V tomto příkladu se používají nástroje příkazového řádku [.NET Core](../../../core/index.md) . Pokud si nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete o nich získat informace v tomto [tématu Začínáme](../../../core/tutorials/cli-create-console-app.md).

Metodu `Main` v *program.cs* upravte takto:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Když je program spuštěn ve Windows, všechny hodnoty vrácené funkcí `Main` jsou uloženy v proměnné prostředí. Tato proměnná prostředí se dá načíst pomocí `ERRORLEVEL` ze souboru Batch nebo `$LastExitCode` z PowerShellu.

Aplikaci můžete sestavit pomocí příkazu [DOTNET CLI](../../../core/tools/dotnet.md) `dotnet build`.

Potom vytvořte powershellový skript, který spustí aplikaci a zobrazí výsledek. Vložte následující kód do textového souboru a uložte jej jako `test.ps1` ve složce, která obsahuje projekt. Spusťte skript prostředí PowerShell zadáním `test.ps1` na příkazovém řádku PowerShellu.

Vzhledem k tomu, že kód vrátí hodnotu nula, dávkový soubor ohlásí úspěch. Pokud ale změníte MainReturnValTest.cs a vrátíte nenulovou hodnotu a pak znovu zkompilujete program, při následném spuštění skriptu PowerShellu se nahlásí chyba.

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

Když vstupní bod aplikace vrátí `Task` nebo `Task<int>`, kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu deklarovanou v kódu aplikace. Za předpokladu, že se tento vstupní bod nazývá `$GeneratedMain`, kompilátor generuje pro tyto vstupní body následující kód:

- `static Task Main()` vede k vygenerování ekvivalentu `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` kompilátoru.
- `static Task Main(string[])` vede k vygenerování ekvivalentu `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` kompilátoru.
- `static Task<int> Main()` vede k vygenerování ekvivalentu `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` kompilátoru.
- `static Task<int> Main(string[])` vede k vygenerování ekvivalentu `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` kompilátoru.

> [!NOTE]
>Pokud příklady použité `async` modifikátorem metody `Main`, kompilátor vygeneruje stejný kód.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [C#Odkaz](../index.md)
- [Argumenty Main() a příkazového řádku](index.md)
- [Jak zobrazit argumenty příkazového řádku](./how-to-display-command-line-arguments.md)
