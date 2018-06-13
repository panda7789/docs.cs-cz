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
ms.openlocfilehash: 4ea0254add0592c0c79c03f4e94f02526f9fe689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580767"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="5ea07-102">Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze</span><span class="sxs-lookup"><span data-stu-id="5ea07-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="5ea07-103">Tento dokument ukazuje, jak zabránit v připojení k nadřazené úlohy podřízené úlohy.</span><span class="sxs-lookup"><span data-stu-id="5ea07-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="5ea07-104">Brání připojení k nadřazené podřízené úlohy je užitečné, když zavoláte komponentu, která jsou zapsána třetích stran a také používající úlohy.</span><span class="sxs-lookup"><span data-stu-id="5ea07-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="5ea07-105">Například komponenty třetích stran, která používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvořit <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekt může způsobit problémy ve vašem kódu, pokud je dlouhotrvající nebo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="5ea07-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea07-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ea07-106">Example</span></span>  
 <span data-ttu-id="5ea07-107">Následující příklad porovnává důsledky použití výchozích možností pro důsledky z znemožňuje připojení k nadřazené podřízené úlohy.</span><span class="sxs-lookup"><span data-stu-id="5ea07-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="5ea07-108">V příkladu se vytváří <xref:System.Threading.Tasks.Task> objekt, který volá do knihovny třetí strany, který také používá <xref:System.Threading.Tasks.Task> objektu.</span><span class="sxs-lookup"><span data-stu-id="5ea07-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="5ea07-109">Knihovna třetích stran používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost vytvořit <xref:System.Threading.Tasks.Task> objektu.</span><span class="sxs-lookup"><span data-stu-id="5ea07-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="5ea07-110">Aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost vytvořit úlohu nadřazené.</span><span class="sxs-lookup"><span data-stu-id="5ea07-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="5ea07-111">Tato možnost dá pokyn modulu runtime odebrat <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specifikace v podřízené úlohy.</span><span class="sxs-lookup"><span data-stu-id="5ea07-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="5ea07-112">Protože nadřazené úkolů nedokončí, dokud nedokončí všechny podřízené úlohy, dlouhodobé podřízené úlohy může způsobit celkové aplikace provést špatně.</span><span class="sxs-lookup"><span data-stu-id="5ea07-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="5ea07-113">V tomto příkladu Pokud aplikace používá výchozí možnosti pro vytvoření nadřazené úlohy, podřízené úlohy musí dokončit před nadřazený úkol dokončí.</span><span class="sxs-lookup"><span data-stu-id="5ea07-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="5ea07-114">Pokud aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost, podřízený objekt není připojen k nadřazené.</span><span class="sxs-lookup"><span data-stu-id="5ea07-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="5ea07-115">Proto aplikace provádět další kroky po dokončení této úlohy nadřazené a předtím, než se musí počkat na dokončení úlohy podřízené.</span><span class="sxs-lookup"><span data-stu-id="5ea07-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5ea07-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5ea07-116">Compiling the Code</span></span>  
 <span data-ttu-id="5ea07-117">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DenyChildAttach.cs` (`DenyChildAttach.vb` jazyka Visual Basic), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="5ea07-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="5ea07-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="5ea07-118">Visual C#</span></span>  
  
 <span data-ttu-id="5ea07-119">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="5ea07-119">**csc.exe DenyChildAttach.cs**</span></span>  
  
 <span data-ttu-id="5ea07-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ea07-120">Visual Basic</span></span>  
  
 <span data-ttu-id="5ea07-121">**Vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="5ea07-121">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5ea07-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="5ea07-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea07-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ea07-123">See Also</span></span>  
 [<span data-ttu-id="5ea07-124">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="5ea07-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
