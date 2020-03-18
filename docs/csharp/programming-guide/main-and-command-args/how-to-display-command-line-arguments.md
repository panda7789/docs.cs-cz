---
title: Jak zobrazit argumenty příkazového řádku - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712023"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="b66df-102">Jak zobrazit argumenty příkazového řádku (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b66df-102">How to display command line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="b66df-103">Argumenty poskytnuté spustitelnému souboru na příkazovém řádku `Main`jsou přístupné prostřednictvím volitelného parametru .</span><span class="sxs-lookup"><span data-stu-id="b66df-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="b66df-104">Argumenty jsou k dispozici ve formě pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="b66df-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="b66df-105">Každý prvek pole obsahuje jeden argument.</span><span class="sxs-lookup"><span data-stu-id="b66df-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="b66df-106">Prázdné místo mezi argumenty je odebráno.</span><span class="sxs-lookup"><span data-stu-id="b66df-106">White-space between arguments is removed.</span></span> <span data-ttu-id="b66df-107">Zvažte například tato vyvolání příkazového řádku fiktivního spustitelného souboru:</span><span class="sxs-lookup"><span data-stu-id="b66df-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="b66df-108">Vstup na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="b66df-108">Input on Command-line</span></span>|<span data-ttu-id="b66df-109">Pole řetězců předaných main</span><span class="sxs-lookup"><span data-stu-id="b66df-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="b66df-110">**spustitelný.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="b66df-110">**executable.exe a b c**</span></span>|<span data-ttu-id="b66df-111">"a"</span><span class="sxs-lookup"><span data-stu-id="b66df-111">"a"</span></span><br /><br /> <span data-ttu-id="b66df-112">"b"</span><span class="sxs-lookup"><span data-stu-id="b66df-112">"b"</span></span><br /><br /> <span data-ttu-id="b66df-113">"c"</span><span class="sxs-lookup"><span data-stu-id="b66df-113">"c"</span></span>|  
|<span data-ttu-id="b66df-114">**spustitelný soubor exe jeden dva**</span><span class="sxs-lookup"><span data-stu-id="b66df-114">**executable.exe one two**</span></span>|<span data-ttu-id="b66df-115">"jedna"</span><span class="sxs-lookup"><span data-stu-id="b66df-115">"one"</span></span><br /><br /> <span data-ttu-id="b66df-116">"dva"</span><span class="sxs-lookup"><span data-stu-id="b66df-116">"two"</span></span>|  
|<span data-ttu-id="b66df-117">**spustitelný soubor exe "jedna dvě" tři**</span><span class="sxs-lookup"><span data-stu-id="b66df-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="b66df-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="b66df-118">"one two"</span></span><br /><br /> <span data-ttu-id="b66df-119">"tři"</span><span class="sxs-lookup"><span data-stu-id="b66df-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b66df-120">Pokud spouštěte aplikaci v sadě Visual Studio, můžete zadat argumenty příkazového řádku na [stránce ladění, Návrháře projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="b66df-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b66df-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="b66df-121">Example</span></span>  
 <span data-ttu-id="b66df-122">V tomto příkladu jsou zobrazeny argumenty příkazového řádku předané aplikaci příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="b66df-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="b66df-123">Zobrazený výstup je pro první položku ve výše uvedené tabulce.</span><span class="sxs-lookup"><span data-stu-id="b66df-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b66df-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b66df-124">See also</span></span>

- [<span data-ttu-id="b66df-125">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b66df-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b66df-126">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="b66df-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="b66df-127">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b66df-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="b66df-128">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="b66df-128">Main() Return Values</span></span>](./main-return-values.md)
