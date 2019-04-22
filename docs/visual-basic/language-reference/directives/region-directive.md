---
title: '#Region – direktiva (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: eaaf0f8279ec905767be3f364a88357f0d393bba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818866"
---
# <a name="region-directive"></a><span data-ttu-id="4071f-102">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="4071f-102">#Region Directive</span></span>
<span data-ttu-id="4071f-103">Sbalí a skryje části kódu v souborech Visual Basicu.</span><span class="sxs-lookup"><span data-stu-id="4071f-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4071f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4071f-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="4071f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4071f-105">Parts</span></span>  
  
|<span data-ttu-id="4071f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="4071f-106">Term</span></span>|<span data-ttu-id="4071f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="4071f-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="4071f-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4071f-108">Required.</span></span> <span data-ttu-id="4071f-109">Řetězec, který funguje jako název oblasti, když je sbalené.</span><span class="sxs-lookup"><span data-stu-id="4071f-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="4071f-110">Ve výchozím nastavení je sbalený oblastech.</span><span class="sxs-lookup"><span data-stu-id="4071f-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="4071f-111">Ukončuje `#Region` bloku.</span><span class="sxs-lookup"><span data-stu-id="4071f-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4071f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4071f-112">Remarks</span></span>  
 <span data-ttu-id="4071f-113">Použití `#Region` směrnice určit blok kódu, který rozbalit nebo sbalit při použití funkce sbalování z editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4071f-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="4071f-114">Můžete umístit, nebo *vnořit*, oblastem v jiných oblastech, které chcete seskupit podobné oblastech.</span><span class="sxs-lookup"><span data-stu-id="4071f-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4071f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4071f-115">Example</span></span>  
 <span data-ttu-id="4071f-116">V tomto příkladu `#Region` směrnice.</span><span class="sxs-lookup"><span data-stu-id="4071f-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4071f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4071f-117">See also</span></span>

- [<span data-ttu-id="4071f-118">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="4071f-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="4071f-119">Sbalení</span><span class="sxs-lookup"><span data-stu-id="4071f-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="4071f-120">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="4071f-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
