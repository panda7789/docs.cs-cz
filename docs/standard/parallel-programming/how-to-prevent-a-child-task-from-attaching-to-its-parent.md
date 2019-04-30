---
title: 'Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7506a57e29b7942bd06141baa2d2b048ed998214
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937433"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="552e4-102">Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze</span><span class="sxs-lookup"><span data-stu-id="552e4-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="552e4-103">Tento dokument ukazuje, jak zabránit podřízené úloze v připojení k nadřazené úloze.</span><span class="sxs-lookup"><span data-stu-id="552e4-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="552e4-104">Zabránění podřízené úloze, mohla připojit k nadřazené je užitečné, když voláte komponentu, která je vytvořená systémem třetích stran a také používající úlohy.</span><span class="sxs-lookup"><span data-stu-id="552e4-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="552e4-105">Například komponenty třetích stran, která se používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvořit <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekt může způsobit problémy v kódu, pokud je dlouho běžící nebo dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="552e4-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="552e4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="552e4-106">Example</span></span>  
 <span data-ttu-id="552e4-107">Následující příklad porovnává důsledky použití výchozích možností účinkům zabránit podřízené úloze v připojení k nadřazené.</span><span class="sxs-lookup"><span data-stu-id="552e4-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="552e4-108">V příkladu se vytvoří <xref:System.Threading.Tasks.Task> objekt, který volá knihovnu třetí strany, který také používá <xref:System.Threading.Tasks.Task> objektu.</span><span class="sxs-lookup"><span data-stu-id="552e4-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="552e4-109">Používá knihovnu třetí strany <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost vytvořit <xref:System.Threading.Tasks.Task> objektu.</span><span class="sxs-lookup"><span data-stu-id="552e4-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="552e4-110">Aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> můžete vytvořit nadřazené úloze.</span><span class="sxs-lookup"><span data-stu-id="552e4-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="552e4-111">Tato možnost dá pokyn modulu runtime pro odebrání <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specifikace v podřízených úloh.</span><span class="sxs-lookup"><span data-stu-id="552e4-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="552e4-112">Protože nadřazenou úlohu nedokončí až do dokončení všech podřízených úloh, může způsobit dlouhotrvající podřízená úloha celkové aplikace nízký výkon.</span><span class="sxs-lookup"><span data-stu-id="552e4-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="552e4-113">V tomto příkladu Pokud aplikace používá výchozí možnosti pro vytvoření nadřazené úlohy, podřízená úloha musí dokončit předtím, než nadřazená úloha dokončí.</span><span class="sxs-lookup"><span data-stu-id="552e4-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="552e4-114">Pokud aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost podřízené není připojena k nadřazené.</span><span class="sxs-lookup"><span data-stu-id="552e4-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="552e4-115">Aplikace proto můžete provést další práce po dokončení nadřazených úloh, a předtím, než je třeba počkat na dokončení úloh podřízené.</span><span class="sxs-lookup"><span data-stu-id="552e4-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="552e4-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="552e4-116">Compiling the Code</span></span>  
 <span data-ttu-id="552e4-117">Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `DenyChildAttach.cs` (`DenyChildAttach.vb` v jazyce Visual Basic), a pak spuštěním následujícího příkazu na příkazovém řádku pro vývojáře pro Visual Studio okno.</span><span class="sxs-lookup"><span data-stu-id="552e4-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for Visual Basic), and then run the following command in a Developer Command Prompt for Visual Studio window.</span></span>  
  
 <span data-ttu-id="552e4-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="552e4-118">Visual C#</span></span>  
  
 <span data-ttu-id="552e4-119">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="552e4-119">**csc.exe DenyChildAttach.cs**</span></span>  
  
 <span data-ttu-id="552e4-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="552e4-120">Visual Basic</span></span>  
  
 <span data-ttu-id="552e4-121">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="552e4-121">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="552e4-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="552e4-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="552e4-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="552e4-123">See also</span></span>

- [<span data-ttu-id="552e4-124">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="552e4-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
