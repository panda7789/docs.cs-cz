---
title: 'Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 5813ad573e89886ba991ca8cbcebb7232af05821
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971673"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="b836a-102">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b836a-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="b836a-103">Dalším přístupem k iterování přes pole je použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) jak je uvedeno v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="b836a-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="b836a-104">Příkaz `foreach` lze použít k iteraci přes pole, kolekci třídy rozhraní .NET Framework nebo jakékoli třídy nebo struktury, která implementuje rozhraní <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="b836a-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b836a-105">Při spuštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="b836a-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b836a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b836a-106">Example</span></span>  
 <span data-ttu-id="b836a-107">Tento příklad ukazuje, jak vytisknout argumenty příkazového řádku pomocí příkazu `foreach`.</span><span class="sxs-lookup"><span data-stu-id="b836a-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class2.cs#10)]  
  
 [!code-csharp[csProgGuideMain#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="b836a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b836a-108">See also</span></span>

- <xref:System.Array>
- <xref:System.Collections>
- [<span data-ttu-id="b836a-109">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="b836a-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="b836a-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b836a-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b836a-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="b836a-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="b836a-112">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b836a-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="b836a-113">Postupy: Zobrazení argumentů příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b836a-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="b836a-114">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="b836a-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
