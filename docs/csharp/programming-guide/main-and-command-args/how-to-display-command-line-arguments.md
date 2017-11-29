---
title: "Postupy: Zobrazení argumentů příkazového řádku (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="ef67c-102">Postupy: Zobrazení argumentů příkazového řádku (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ef67c-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="ef67c-103">Argumenty spustitelný soubor na příkazovém řádku jsou přístupné prostřednictvím volitelný parametr pro `Main`.</span><span class="sxs-lookup"><span data-stu-id="ef67c-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="ef67c-104">Argumenty, které jsou uvedeny v podobě pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="ef67c-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="ef67c-105">Každý element pole obsahuje jeden argument.</span><span class="sxs-lookup"><span data-stu-id="ef67c-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="ef67c-106">Odeberou se mezer mezi argumenty.</span><span class="sxs-lookup"><span data-stu-id="ef67c-106">White-space between arguments is removed.</span></span> <span data-ttu-id="ef67c-107">Představte si třeba tyto volání fiktivní spustitelný soubor příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="ef67c-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="ef67c-108">Zadejte na příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="ef67c-108">Input on Command-line</span></span>|<span data-ttu-id="ef67c-109">Pole řetězců předaný Main</span><span class="sxs-lookup"><span data-stu-id="ef67c-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="ef67c-110">**Executable.exe b c**</span><span class="sxs-lookup"><span data-stu-id="ef67c-110">**executable.exe a b c**</span></span>|<span data-ttu-id="ef67c-111">"a"</span><span class="sxs-lookup"><span data-stu-id="ef67c-111">"a"</span></span><br /><br /> <span data-ttu-id="ef67c-112">"b"</span><span class="sxs-lookup"><span data-stu-id="ef67c-112">"b"</span></span><br /><br /> <span data-ttu-id="ef67c-113">"c"</span><span class="sxs-lookup"><span data-stu-id="ef67c-113">"c"</span></span>|  
|<span data-ttu-id="ef67c-114">**Executable.exe jeden dva**</span><span class="sxs-lookup"><span data-stu-id="ef67c-114">**executable.exe one two**</span></span>|<span data-ttu-id="ef67c-115">"jedna"</span><span class="sxs-lookup"><span data-stu-id="ef67c-115">"one"</span></span><br /><br /> <span data-ttu-id="ef67c-116">"dva"</span><span class="sxs-lookup"><span data-stu-id="ef67c-116">"two"</span></span>|  
|<span data-ttu-id="ef67c-117">**Executable.exe "jeden dva" tři**</span><span class="sxs-lookup"><span data-stu-id="ef67c-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="ef67c-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="ef67c-118">"one two"</span></span><br /><br /> <span data-ttu-id="ef67c-119">"tři"</span><span class="sxs-lookup"><span data-stu-id="ef67c-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ef67c-120">Když aplikace běží v sadě Visual Studio, můžete zadat argumenty příkazového řádku v [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="ef67c-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef67c-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef67c-121">Example</span></span>  
 <span data-ttu-id="ef67c-122">Tento příklad zobrazuje argumenty příkazového řádku předaný aplikace příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ef67c-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="ef67c-123">Výstup ukazuje je pro první položku v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="ef67c-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ef67c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef67c-124">See Also</span></span>  
 [<span data-ttu-id="ef67c-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ef67c-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ef67c-126">Sestavování pomocí csc.exe</span><span class="sxs-lookup"><span data-stu-id="ef67c-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="ef67c-127">Main() a argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ef67c-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="ef67c-128">Postupy: přístup příkazového řádku argumenty pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="ef67c-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="ef67c-129">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="ef67c-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
