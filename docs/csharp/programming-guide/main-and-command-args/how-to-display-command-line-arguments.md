---
title: Jak zobrazit argumenty příkazového řádku – Průvodce programováním v C#
description: Naučte se zobrazovat argumenty příkazového řádku. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 1ac5dc5a5f4e974c9202d2ce23f61071494e1977
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381811"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="c57f3-104">Jak zobrazit argumenty příkazového řádku (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c57f3-104">How to display command-line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="c57f3-105">Argumenty poskytované spustitelnému souboru na příkazovém řádku jsou přístupné prostřednictvím volitelného parametru `Main` .</span><span class="sxs-lookup"><span data-stu-id="c57f3-105">Arguments provided to an executable on the command line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="c57f3-106">Argumenty jsou k dispozici ve formě pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="c57f3-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="c57f3-107">Každý prvek pole obsahuje jeden argument.</span><span class="sxs-lookup"><span data-stu-id="c57f3-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="c57f3-108">Odeberou se prázdné místo mezi argumenty.</span><span class="sxs-lookup"><span data-stu-id="c57f3-108">White-space between arguments is removed.</span></span> <span data-ttu-id="c57f3-109">Například zvažte tyto vyvolání příkazového řádku fiktivního spustitelného souboru:</span><span class="sxs-lookup"><span data-stu-id="c57f3-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="c57f3-110">Vstup na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="c57f3-110">Input on command line</span></span>|<span data-ttu-id="c57f3-111">Pole řetězců předaných do Main</span><span class="sxs-lookup"><span data-stu-id="c57f3-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="c57f3-112">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="c57f3-112">**executable.exe a b c**</span></span>|<span data-ttu-id="c57f3-113">určitého</span><span class="sxs-lookup"><span data-stu-id="c57f3-113">"a"</span></span><br /><br /> <span data-ttu-id="c57f3-114">b</span><span class="sxs-lookup"><span data-stu-id="c57f3-114">"b"</span></span><br /><br /> <span data-ttu-id="c57f3-115">r</span><span class="sxs-lookup"><span data-stu-id="c57f3-115">"c"</span></span>|  
|<span data-ttu-id="c57f3-116">**executable.exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="c57f3-116">**executable.exe one two**</span></span>|<span data-ttu-id="c57f3-117">hodinu</span><span class="sxs-lookup"><span data-stu-id="c57f3-117">"one"</span></span><br /><br /> <span data-ttu-id="c57f3-118">Druhá</span><span class="sxs-lookup"><span data-stu-id="c57f3-118">"two"</span></span>|  
|<span data-ttu-id="c57f3-119">**executable.exe "1 2" 3**</span><span class="sxs-lookup"><span data-stu-id="c57f3-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="c57f3-120">"one two"</span><span class="sxs-lookup"><span data-stu-id="c57f3-120">"one two"</span></span><br /><br /> <span data-ttu-id="c57f3-121">3</span><span class="sxs-lookup"><span data-stu-id="c57f3-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c57f3-122">Při spuštění aplikace v aplikaci Visual Studio můžete zadat argumenty příkazového řádku na [stránce ladění, Návrháři projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="c57f3-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c57f3-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="c57f3-123">Example</span></span>  
 <span data-ttu-id="c57f3-124">Tento příklad zobrazuje argumenty příkazového řádku předané aplikaci příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c57f3-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="c57f3-125">Zobrazený výstup je pro první položku v tabulce výše.</span><span class="sxs-lookup"><span data-stu-id="c57f3-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c57f3-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c57f3-126">See also</span></span>

- [<span data-ttu-id="c57f3-127">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c57f3-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c57f3-128">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="c57f3-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="c57f3-129">Argumenty Main () a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c57f3-129">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="c57f3-130">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="c57f3-130">Main() Return Values</span></span>](./main-return-values.md)
