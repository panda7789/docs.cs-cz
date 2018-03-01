---
title: "Návratové hodnoty Main() (Průvodce programováním v C#)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f317879a4941adfd3d125c7697226f8a510254c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="main-return-values-c-programming-guide"></a>Návratové hodnoty Main() (C# Průvodce programováním)

`Main` Metoda může vrátit `void`:

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

Také můžete vrátit `int`:

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

Pokud z hodnoty návratový `Main` se nepoužívá, vrácení `void` umožňuje mírně jednodušší kódu. Vrací celé číslo, ale umožňuje programu předávat informace o stavu do jiných programů nebo skriptů, které vyvolají spustitelný soubor. Vrácená hodnota z `Main` je považován za kód ukončení procesu. Následující příklad ukazuje, jak z hodnoty návratový `Main` je přístupná.

## <a name="example"></a>Příklad

Tento příklad používá [.NET Core](../../../core/index.md) nástroje příkazového řádku. Pokud jste unfamilar pomocí nástroje příkazového řádku .NET Core, informace o najdete je v tomto [Get Začínáme tématu](../../../core/tutorials/using-with-xplat-cli.md).

Změnit `Main` metoda v *program.cs* následujícím způsobem:

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

Když program se spustí v systému Windows, libovolná hodnota vrácená z `Main` funkce je uložené v proměnné prostředí. Tato proměnná prostředí se dá načíst pomocí `ERRORLEVEL` z dávkového souboru nebo `$LastExitCode` z prostředí powershell.

Můžete vytvořit aplikace pomocí [dotnet rozhraní příkazového řádku](../../../core/tools/dotnet.md) `dotnet build` příkaz.

Dále vytvořte skript prostředí Powershell a spusťte aplikaci zobrazit výsledek. Vložte následující kód do textového souboru a uložte ho jako `test.ps1` ve složce, která obsahuje projektu. Spustit skript prostředí powershell zadáním `test.ps1` v příkazovém řádku prostředí powershell.

Protože kód vrátí hodnotu 0, dávkového souboru oznámí úspěšné. Pokud změníte MainReturnValTest.cs vrátí nenulovou hodnotu a pak znovu kompilace programu, však následné provádění skriptu prostředí powershell oznámí selhání.

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

## <a name="async-main-return-values"></a>Hlavní asynchronní návratové hodnoty

Asynchronní hlavní vrátit hodnoty přesunout často používaný kód, který je nezbytný pro volání asynchronních metod v `Main` generované kompilátorem kódu. Dříve museli byste tento konstrukce volání asynchronní kódu a ujistěte se, že vaše aplikace spuštěna až do dokončení asynchronní operaci zápisu:

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

Teď to může být nahrazen:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Výhodou nové syntaxe je, že kompilátor vždy generuje správný kód.

## <a name="compiler-generated-code"></a>Kompilátor vygeneruje kód

Když se vrátí vstupní bod aplikace `Task` nebo `Task<int>`, kompilátor vygeneruje nový vstupní bod, který volá metoda deklarované v kódu aplikace. Za předpokladu, že tento vstupní bod se nazývá `$GeneratedMain`, kompilátor generuje následující kód pro tyto vstupní body:

- `static Task Main()`výsledky v kompilátoru emitování ekvivalent`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`výsledky v kompilátoru emitování ekvivalent`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`výsledky v kompilátoru emitování ekvivalent`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`výsledky v kompilátoru emitování ekvivalent`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Pokud se používá v příkladech `async` modifikátor na `Main` metoda, kompilátor by generovat stejný kód.

## <a name="see-also"></a>Viz také
[Průvodce programováním v C#](../../programming-guide/index.md)
[referenční dokumentace jazyka C#](../index.md)
[Main() a příkazového řádku argumenty](index.md)
[postupy: zobrazení příkazového řádku Argumenty](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[postupy: přístup příkazového řádku argumenty pomocí příkazu foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
