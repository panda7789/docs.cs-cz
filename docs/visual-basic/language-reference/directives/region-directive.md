---
title: '#Region – direktiva'
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
ms.openlocfilehash: d25871140ef0674c013fc70d1306b2b4d0858556
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588432"
---
# <a name="region-directive"></a><span data-ttu-id="a4247-102">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="a4247-102">#Region Directive</span></span>
<span data-ttu-id="a4247-103">Sbalí a skrytí sekcí kódu v souborech jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a4247-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4247-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4247-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="a4247-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a4247-105">Parts</span></span>  
  
|<span data-ttu-id="a4247-106">Termín</span><span class="sxs-lookup"><span data-stu-id="a4247-106">Term</span></span>|<span data-ttu-id="a4247-107">Definice</span><span class="sxs-lookup"><span data-stu-id="a4247-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="a4247-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a4247-108">Required.</span></span> <span data-ttu-id="a4247-109">Řetězec, který funguje jako název oblasti, když je sbalená.</span><span class="sxs-lookup"><span data-stu-id="a4247-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="a4247-110">Ve výchozím nastavení jsou sbaleny oblasti.</span><span class="sxs-lookup"><span data-stu-id="a4247-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="a4247-111">Ukončí `#Region` bloku.</span><span class="sxs-lookup"><span data-stu-id="a4247-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4247-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4247-112">Remarks</span></span>  
 <span data-ttu-id="a4247-113">Použití `#Region` – direktiva blok kódu rozbalit nebo sbalit, když používáte funkci osnovy z editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4247-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="a4247-114">Můžete umístit, nebo *vnořit*, oblastem v jiných oblastech chcete seskupit podobné oblasti.</span><span class="sxs-lookup"><span data-stu-id="a4247-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4247-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4247-115">Example</span></span>  
 <span data-ttu-id="a4247-116">Tento příklad používá `#Region` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="a4247-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a4247-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4247-117">See Also</span></span>  
 [<span data-ttu-id="a4247-118">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="a4247-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="a4247-119">Sbalení</span><span class="sxs-lookup"><span data-stu-id="a4247-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="a4247-120">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="a4247-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
