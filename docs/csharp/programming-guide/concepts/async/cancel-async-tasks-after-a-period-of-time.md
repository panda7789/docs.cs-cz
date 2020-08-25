---
title: Zrušení asynchronních úloh po určitém časovém intervalu (C#)
description: Naučte se naplánovat zrušení všech přidružených úloh, které nejsou dokončené v časovém intervalu.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: ad9064f8f45a737982ffc35ab4ea2395ddae9016
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811415"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zrušení asynchronních úloh po určitém časovém intervalu (C#)

Asynchronní operaci můžete zrušit po časovém intervalu pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, pokud nechcete čekat na dokončení operace. Tato metoda naplánuje zrušení všech přidružených úloh, které nejsou dokončeny v časovém období určeném `CancelAfter` výrazem.

Tento příklad přidá do kódu, který je vyvinut v části [zrušení seznamu úkolů (C#)](cancel-an-async-task-or-a-list-of-tasks.md) pro stažení seznamu webů a zobrazení délky obsahu každého z nich.

Tento kurz zahrnuje:

> [!div class="checklist"]
>
> - Aktualizace existující konzolové aplikace .NET
> - Plánování zrušení

## <a name="prerequisites"></a>Předpoklady

V tomto kurzu budete potřebovat následující:

- Očekáváte, že jste vytvořili aplikaci v kurzu [zrušení seznamu úkolů (C#)](cancel-an-async-task-or-a-list-of-tasks.md) .
- [.NET 5,0 nebo novější SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- Integrované vývojové prostředí (IDE)
  - [Doporučujeme Visual Studio, Visual Studio Code nebo Visual Studio pro Mac](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a>Aktualizovat vstupní bod aplikace

Existující metodu nahraďte `Main` následujícím způsobem:

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");

    try
    {
        s_cts.CancelAfter(3500);

        await SumPageSizesAsync();
    }
    catch (TaskCanceledException)
    {
        Console.WriteLine("\nTasks cancelled: timed out.\n");
    }

    Console.WriteLine("Application ending.");
}
```

Aktualizovaná `Main` Metoda zapisuje několik pokynů do konzoly. V rámci [try catch](../../../language-reference/keywords/try-catch.md)volání metody <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> k naplánování zrušení. Tím se zruší rušení po určité době.

Dále `SumPageSizesAsync` je očekávána metoda. Pokud zpracování všech adres URL probíhá rychleji než naplánované zrušení, aplikace skončí. Pokud je však naplánované zrušení aktivováno před zpracováním všech adres URL, <xref:System.Threading.Tasks.TaskCanceledException> je vyvolána výjimka.

### <a name="example-application-output"></a>Příklad výstupu aplikace

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný text souboru *program.cs* pro příklad.

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a>Viz také

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](index.md)
- [Zrušení seznamu úkolů (C#)](cancel-an-async-task-or-a-list-of-tasks.md)
