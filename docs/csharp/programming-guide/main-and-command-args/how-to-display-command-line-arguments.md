---
title: 'Postupy: Zobrazení argumentů příkazového řádku (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: a6067482b4a225abc31592affb2cfab38847cd53
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502669"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="bb498-102">Postupy: Zobrazení argumentů příkazového řádku (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bb498-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="bb498-103">Argumenty pro spustitelný soubor na příkazovém řádku k dispozici jsou přístupné prostřednictvím volitelný parametr pro `Main`.</span><span class="sxs-lookup"><span data-stu-id="bb498-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="bb498-104">Argumenty jsou k dispozici ve formě pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="bb498-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="bb498-105">Každý prvek pole obsahuje jeden argument.</span><span class="sxs-lookup"><span data-stu-id="bb498-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="bb498-106">Odeberou se prázdné znaky mezi argumenty.</span><span class="sxs-lookup"><span data-stu-id="bb498-106">White-space between arguments is removed.</span></span> <span data-ttu-id="bb498-107">Představte si třeba tyto příkazového řádku volání fiktivní spustitelný soubor:</span><span class="sxs-lookup"><span data-stu-id="bb498-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="bb498-108">Zadejte na příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="bb498-108">Input on Command-line</span></span>|<span data-ttu-id="bb498-109">Pole řetězců, které jsou předány do hlavní</span><span class="sxs-lookup"><span data-stu-id="bb498-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="bb498-110">**Executable.exe a b c.**</span><span class="sxs-lookup"><span data-stu-id="bb498-110">**executable.exe a b c**</span></span>|<span data-ttu-id="bb498-111">"a"</span><span class="sxs-lookup"><span data-stu-id="bb498-111">"a"</span></span><br /><br /> <span data-ttu-id="bb498-112">"b"</span><span class="sxs-lookup"><span data-stu-id="bb498-112">"b"</span></span><br /><br /> <span data-ttu-id="bb498-113">"c"</span><span class="sxs-lookup"><span data-stu-id="bb498-113">"c"</span></span>|  
|<span data-ttu-id="bb498-114">**Executable.exe jeden dvě**</span><span class="sxs-lookup"><span data-stu-id="bb498-114">**executable.exe one two**</span></span>|<span data-ttu-id="bb498-115">"jedna"</span><span class="sxs-lookup"><span data-stu-id="bb498-115">"one"</span></span><br /><br /> <span data-ttu-id="bb498-116">"dvě"</span><span class="sxs-lookup"><span data-stu-id="bb498-116">"two"</span></span>|  
|<span data-ttu-id="bb498-117">**Executable.exe "jeden dvě" tři**</span><span class="sxs-lookup"><span data-stu-id="bb498-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="bb498-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="bb498-118">"one two"</span></span><br /><br /> <span data-ttu-id="bb498-119">"tři"</span><span class="sxs-lookup"><span data-stu-id="bb498-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="bb498-120">Při spouštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="bb498-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb498-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb498-121">Example</span></span>  
 <span data-ttu-id="bb498-122">Tento příklad zobrazuje argumenty příkazového řádku předané do aplikace příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="bb498-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="bb498-123">Výstup se pro první položku v tabulce výše.</span><span class="sxs-lookup"><span data-stu-id="bb498-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bb498-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb498-124">See Also</span></span>

- [<span data-ttu-id="bb498-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bb498-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bb498-126">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="bb498-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="bb498-127">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="bb498-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="bb498-128">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="bb498-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [<span data-ttu-id="bb498-129">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="bb498-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
