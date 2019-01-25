---
title: 'Postupy: Zobrazení argumentů příkazového řádku - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 948ff6e752b3f5cce870b483340cbbf9f4e78b01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607712"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="87136-102">Postupy: Zobrazení argumentů příkazového řádku (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="87136-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="87136-103">Argumenty pro spustitelný soubor na příkazovém řádku k dispozici jsou přístupné prostřednictvím volitelný parametr pro `Main`.</span><span class="sxs-lookup"><span data-stu-id="87136-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="87136-104">Argumenty jsou k dispozici ve formě pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="87136-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="87136-105">Každý prvek pole obsahuje jeden argument.</span><span class="sxs-lookup"><span data-stu-id="87136-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="87136-106">Odeberou se prázdné znaky mezi argumenty.</span><span class="sxs-lookup"><span data-stu-id="87136-106">White-space between arguments is removed.</span></span> <span data-ttu-id="87136-107">Představte si třeba tyto příkazového řádku volání fiktivní spustitelný soubor:</span><span class="sxs-lookup"><span data-stu-id="87136-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="87136-108">Zadejte na příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="87136-108">Input on Command-line</span></span>|<span data-ttu-id="87136-109">Pole řetězců, které jsou předány do hlavní</span><span class="sxs-lookup"><span data-stu-id="87136-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="87136-110">**Executable.exe a b c.**</span><span class="sxs-lookup"><span data-stu-id="87136-110">**executable.exe a b c**</span></span>|<span data-ttu-id="87136-111">"a"</span><span class="sxs-lookup"><span data-stu-id="87136-111">"a"</span></span><br /><br /> <span data-ttu-id="87136-112">"b"</span><span class="sxs-lookup"><span data-stu-id="87136-112">"b"</span></span><br /><br /> <span data-ttu-id="87136-113">"c"</span><span class="sxs-lookup"><span data-stu-id="87136-113">"c"</span></span>|  
|<span data-ttu-id="87136-114">**Executable.exe jeden dvě**</span><span class="sxs-lookup"><span data-stu-id="87136-114">**executable.exe one two**</span></span>|<span data-ttu-id="87136-115">"jedna"</span><span class="sxs-lookup"><span data-stu-id="87136-115">"one"</span></span><br /><br /> <span data-ttu-id="87136-116">"two"</span><span class="sxs-lookup"><span data-stu-id="87136-116">"two"</span></span>|  
|<span data-ttu-id="87136-117">**Executable.exe "jeden dvě" tři**</span><span class="sxs-lookup"><span data-stu-id="87136-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="87136-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="87136-118">"one two"</span></span><br /><br /> <span data-ttu-id="87136-119">"tři"</span><span class="sxs-lookup"><span data-stu-id="87136-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="87136-120">Při spouštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="87136-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87136-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="87136-121">Example</span></span>  
 <span data-ttu-id="87136-122">Tento příklad zobrazuje argumenty příkazového řádku předané do aplikace příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="87136-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="87136-123">Výstup se pro první položku v tabulce výše.</span><span class="sxs-lookup"><span data-stu-id="87136-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="87136-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87136-124">See also</span></span>

- [<span data-ttu-id="87136-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="87136-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="87136-126">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="87136-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="87136-127">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="87136-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="87136-128">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="87136-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [<span data-ttu-id="87136-129">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="87136-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
