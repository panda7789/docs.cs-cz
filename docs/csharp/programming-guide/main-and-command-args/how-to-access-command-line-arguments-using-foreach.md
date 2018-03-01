---
title: "Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="32b33-102">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="32b33-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="32b33-103">Další postup pro iterování přes pole je použití [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz, jak je znázorněno v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="32b33-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="32b33-104">Příkaz `foreach` lze použít k iteraci přes pole, kolekci třídy rozhraní .NET Framework nebo jakékoli třídy nebo struktury, která implementuje rozhraní <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="32b33-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32b33-105">Při spuštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku v [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="32b33-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b33-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="32b33-106">Example</span></span>  
 <span data-ttu-id="32b33-107">Tento příklad ukazuje, jak vytisknout argumenty příkazového řádku pomocí příkazu `foreach`.</span><span class="sxs-lookup"><span data-stu-id="32b33-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="32b33-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="32b33-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="32b33-109">Sestavování pomocí csc.exe</span><span class="sxs-lookup"><span data-stu-id="32b33-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="32b33-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="32b33-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="32b33-111">foreach v</span><span class="sxs-lookup"><span data-stu-id="32b33-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="32b33-112">Main() a argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="32b33-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="32b33-113">Postupy: Zobrazení argumentů příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="32b33-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="32b33-114">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="32b33-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
