---
title: "Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2cab2fb9c26a8ddaa868cafebac718e5dfd6baa0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="25600-102">Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze</span><span class="sxs-lookup"><span data-stu-id="25600-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="25600-103">Tento dokument ukazuje, jak zabránit v připojení k nadřazené úlohy podřízené úlohy.</span><span class="sxs-lookup"><span data-stu-id="25600-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="25600-104">Brání připojení k nadřazené podřízené úlohy je užitečné, když zavoláte komponentu, která jsou zapsána třetích stran a také používající úlohy.</span><span class="sxs-lookup"><span data-stu-id="25600-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="25600-105">Například komponenty třetích stran, která používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvořit <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekt může způsobit problémy ve vašem kódu, pokud je dlouhotrvající nebo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="25600-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25600-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="25600-106">Example</span></span>  
 <span data-ttu-id="25600-107">Následující příklad porovnává důsledky použití výchozích možností pro důsledky z znemožňuje připojení k nadřazené podřízené úlohy.</span><span class="sxs-lookup"><span data-stu-id="25600-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="25600-108">V příkladu se vytváří <xref:System.Threading.Tasks.Task> objekt, který volá do knihovny třetí strany, který také používá <xref:System.Threading.Tasks.Task> objektu.</span><span class="sxs-lookup"><span data-stu-id="25600-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="25600-109">Knihovna třetích stran používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost vytvořit <xref:System.Threading.Tasks.Task> objektu.</span><span class="sxs-lookup"><span data-stu-id="25600-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="25600-110">Aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost vytvořit úlohu nadřazené.</span><span class="sxs-lookup"><span data-stu-id="25600-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="25600-111">Tato možnost dá pokyn modulu runtime odebrat <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specifikace v podřízené úlohy.</span><span class="sxs-lookup"><span data-stu-id="25600-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="25600-112">Protože nadřazené úkolů nedokončí, dokud nedokončí všechny podřízené úlohy, dlouhodobé podřízené úlohy může způsobit celkové aplikace provést špatně.</span><span class="sxs-lookup"><span data-stu-id="25600-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="25600-113">V tomto příkladu Pokud aplikace používá výchozí možnosti pro vytvoření nadřazené úlohy, podřízené úlohy musí dokončit před nadřazený úkol dokončí.</span><span class="sxs-lookup"><span data-stu-id="25600-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="25600-114">Pokud aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost, podřízený objekt není připojen k nadřazené.</span><span class="sxs-lookup"><span data-stu-id="25600-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="25600-115">Proto aplikace provádět další kroky po dokončení této úlohy nadřazené a předtím, než se musí počkat na dokončení úlohy podřízené.</span><span class="sxs-lookup"><span data-stu-id="25600-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25600-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="25600-116">Compiling the Code</span></span>  
 <span data-ttu-id="25600-117">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DenyChildAttach.cs` (`DenyChildAttach.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="25600-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="25600-118">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="25600-118">**csc.exe DenyChildAttach.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="25600-119">**Vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="25600-119">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="25600-120">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="25600-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25600-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="25600-121">See Also</span></span>  
 [<span data-ttu-id="25600-122">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="25600-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
