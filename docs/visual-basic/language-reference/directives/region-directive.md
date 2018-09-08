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
ms.openlocfilehash: 204b53751fce4f9a3e038ae7c44634522d54657c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190712"
---
# <a name="region-directive"></a><span data-ttu-id="46c46-102">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="46c46-102">#Region Directive</span></span>
<span data-ttu-id="46c46-103">Sbalí a skryje části kódu v souborech Visual Basicu.</span><span class="sxs-lookup"><span data-stu-id="46c46-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46c46-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="46c46-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="46c46-105">Parts</span></span>  
  
|<span data-ttu-id="46c46-106">Termín</span><span class="sxs-lookup"><span data-stu-id="46c46-106">Term</span></span>|<span data-ttu-id="46c46-107">Definice</span><span class="sxs-lookup"><span data-stu-id="46c46-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="46c46-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="46c46-108">Required.</span></span> <span data-ttu-id="46c46-109">Řetězec, který funguje jako název oblasti, když je sbalené.</span><span class="sxs-lookup"><span data-stu-id="46c46-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="46c46-110">Ve výchozím nastavení je sbalený oblastech.</span><span class="sxs-lookup"><span data-stu-id="46c46-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="46c46-111">Ukončuje `#Region` bloku.</span><span class="sxs-lookup"><span data-stu-id="46c46-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46c46-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46c46-112">Remarks</span></span>  
 <span data-ttu-id="46c46-113">Použití `#Region` směrnice určit blok kódu, který rozbalit nebo sbalit při použití funkce sbalování z editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46c46-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="46c46-114">Můžete umístit, nebo *vnořit*, oblastem v jiných oblastech, které chcete seskupit podobné oblastech.</span><span class="sxs-lookup"><span data-stu-id="46c46-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c46-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="46c46-115">Example</span></span>  
 <span data-ttu-id="46c46-116">V tomto příkladu `#Region` směrnice.</span><span class="sxs-lookup"><span data-stu-id="46c46-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="46c46-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="46c46-117">See Also</span></span>  
 [<span data-ttu-id="46c46-118">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="46c46-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="46c46-119">Sbalení</span><span class="sxs-lookup"><span data-stu-id="46c46-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="46c46-120">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="46c46-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
