---
title: Postup zobrazení argumentů příkazového řádku – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712023"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="217ef-102">Postup zobrazení argumentů příkazového řádku (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="217ef-102">How to display command line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="217ef-103">Argumenty poskytované spustitelnému souboru na příkazovém řádku jsou přístupné prostřednictvím volitelného parametru pro `Main`.</span><span class="sxs-lookup"><span data-stu-id="217ef-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="217ef-104">Argumenty jsou k dispozici ve formě pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="217ef-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="217ef-105">Každý prvek pole obsahuje jeden argument.</span><span class="sxs-lookup"><span data-stu-id="217ef-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="217ef-106">Odeberou se prázdné místo mezi argumenty.</span><span class="sxs-lookup"><span data-stu-id="217ef-106">White-space between arguments is removed.</span></span> <span data-ttu-id="217ef-107">Například zvažte tyto vyvolání příkazového řádku fiktivního spustitelného souboru:</span><span class="sxs-lookup"><span data-stu-id="217ef-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="217ef-108">Vstup na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="217ef-108">Input on Command-line</span></span>|<span data-ttu-id="217ef-109">Pole řetězců předaných do Main</span><span class="sxs-lookup"><span data-stu-id="217ef-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="217ef-110">**spustitelný soubor. exe a b c**</span><span class="sxs-lookup"><span data-stu-id="217ef-110">**executable.exe a b c**</span></span>|<span data-ttu-id="217ef-111">určitého</span><span class="sxs-lookup"><span data-stu-id="217ef-111">"a"</span></span><br /><br /> <span data-ttu-id="217ef-112">b</span><span class="sxs-lookup"><span data-stu-id="217ef-112">"b"</span></span><br /><br /> <span data-ttu-id="217ef-113">r</span><span class="sxs-lookup"><span data-stu-id="217ef-113">"c"</span></span>|  
|<span data-ttu-id="217ef-114">**spustitelný soubor. exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="217ef-114">**executable.exe one two**</span></span>|<span data-ttu-id="217ef-115">hodinu</span><span class="sxs-lookup"><span data-stu-id="217ef-115">"one"</span></span><br /><br /> <span data-ttu-id="217ef-116">"two"</span><span class="sxs-lookup"><span data-stu-id="217ef-116">"two"</span></span>|  
|<span data-ttu-id="217ef-117">**spustitelný soubor. exe "1 2" 3**</span><span class="sxs-lookup"><span data-stu-id="217ef-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="217ef-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="217ef-118">"one two"</span></span><br /><br /> <span data-ttu-id="217ef-119">3</span><span class="sxs-lookup"><span data-stu-id="217ef-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="217ef-120">Při spuštění aplikace v aplikaci Visual Studio můžete zadat argumenty příkazového řádku na [stránce ladění, Návrháři projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="217ef-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="217ef-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="217ef-121">Example</span></span>  
 <span data-ttu-id="217ef-122">Tento příklad zobrazuje argumenty příkazového řádku předané aplikaci příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="217ef-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="217ef-123">Zobrazený výstup je pro první položku v tabulce výše.</span><span class="sxs-lookup"><span data-stu-id="217ef-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="217ef-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="217ef-124">See also</span></span>

- [<span data-ttu-id="217ef-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="217ef-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="217ef-126">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="217ef-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="217ef-127">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="217ef-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="217ef-128">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="217ef-128">Main() Return Values</span></span>](./main-return-values.md)
