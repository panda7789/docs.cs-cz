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
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="793fc-103">Zrušení asynchronních úloh po určitém časovém intervalu (C#)</span><span class="sxs-lookup"><span data-stu-id="793fc-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="793fc-104">Asynchronní operaci můžete zrušit po časovém intervalu pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, pokud nechcete čekat na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="793fc-104">You can cancel an asynchronous operation after a period of time by using the <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="793fc-105">Tato metoda naplánuje zrušení všech přidružených úloh, které nejsou dokončeny v časovém období určeném `CancelAfter` výrazem.</span><span class="sxs-lookup"><span data-stu-id="793fc-105">This method schedules the cancellation of any associated tasks that aren't complete within the period of time that's designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="793fc-106">Tento příklad přidá do kódu, který je vyvinut v části [zrušení seznamu úkolů (C#)](cancel-an-async-task-or-a-list-of-tasks.md) pro stažení seznamu webů a zobrazení délky obsahu každého z nich.</span><span class="sxs-lookup"><span data-stu-id="793fc-106">This example adds to the code that's developed in [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

<span data-ttu-id="793fc-107">Tento kurz zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="793fc-107">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="793fc-108">Aktualizace existující konzolové aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="793fc-108">Updating an existing .NET console application</span></span>
> - <span data-ttu-id="793fc-109">Plánování zrušení</span><span class="sxs-lookup"><span data-stu-id="793fc-109">Scheduling a cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="793fc-110">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="793fc-110">Prerequisites</span></span>

<span data-ttu-id="793fc-111">V tomto kurzu budete potřebovat následující:</span><span class="sxs-lookup"><span data-stu-id="793fc-111">This tutorial requires the following:</span></span>

- <span data-ttu-id="793fc-112">Očekáváte, že jste vytvořili aplikaci v kurzu [zrušení seznamu úkolů (C#)](cancel-an-async-task-or-a-list-of-tasks.md) .</span><span class="sxs-lookup"><span data-stu-id="793fc-112">You're expected to have created an application in the [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) tutorial</span></span>
- [<span data-ttu-id="793fc-113">.NET 5,0 nebo novější SDK</span><span class="sxs-lookup"><span data-stu-id="793fc-113">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="793fc-114">Integrované vývojové prostředí (IDE)</span><span class="sxs-lookup"><span data-stu-id="793fc-114">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="793fc-115">Doporučujeme Visual Studio, Visual Studio Code nebo Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="793fc-115">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a><span data-ttu-id="793fc-116">Aktualizovat vstupní bod aplikace</span><span class="sxs-lookup"><span data-stu-id="793fc-116">Update application entry point</span></span>

<span data-ttu-id="793fc-117">Existující metodu nahraďte `Main` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="793fc-117">Replace the existing `Main` method with the following:</span></span>

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

<span data-ttu-id="793fc-118">Aktualizovaná `Main` Metoda zapisuje několik pokynů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="793fc-118">The updated `Main` method writes a few instructional messages to the console.</span></span> <span data-ttu-id="793fc-119">V rámci [try catch](../../../language-reference/keywords/try-catch.md)volání metody <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> k naplánování zrušení.</span><span class="sxs-lookup"><span data-stu-id="793fc-119">Within the [try catch](../../../language-reference/keywords/try-catch.md), a call to <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> to schedule a cancellation.</span></span> <span data-ttu-id="793fc-120">Tím se zruší rušení po určité době.</span><span class="sxs-lookup"><span data-stu-id="793fc-120">This will signal cancellation after a period of time.</span></span>

<span data-ttu-id="793fc-121">Dále `SumPageSizesAsync` je očekávána metoda.</span><span class="sxs-lookup"><span data-stu-id="793fc-121">Next, the `SumPageSizesAsync` method is awaited.</span></span> <span data-ttu-id="793fc-122">Pokud zpracování všech adres URL probíhá rychleji než naplánované zrušení, aplikace skončí.</span><span class="sxs-lookup"><span data-stu-id="793fc-122">If processing all of the URLs occurs faster than the scheduled cancellation, the application ends.</span></span> <span data-ttu-id="793fc-123">Pokud je však naplánované zrušení aktivováno před zpracováním všech adres URL, <xref:System.Threading.Tasks.TaskCanceledException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="793fc-123">However, if the scheduled cancellation is triggered before all of the URLs are processed, a <xref:System.Threading.Tasks.TaskCanceledException> is thrown.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="793fc-124">Příklad výstupu aplikace</span><span class="sxs-lookup"><span data-stu-id="793fc-124">Example application output</span></span>

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="793fc-125">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="793fc-125">Complete example</span></span>

<span data-ttu-id="793fc-126">Následující kód je úplný text souboru *program.cs* pro příklad.</span><span class="sxs-lookup"><span data-stu-id="793fc-126">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="793fc-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="793fc-127">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="793fc-128">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="793fc-128">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="793fc-129">Zrušení seznamu úkolů (C#)</span><span class="sxs-lookup"><span data-stu-id="793fc-129">Cancel a list of tasks (C#)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
