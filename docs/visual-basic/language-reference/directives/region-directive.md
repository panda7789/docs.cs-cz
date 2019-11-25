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
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343795"
---
# <a name="region-directive"></a><span data-ttu-id="e590b-102">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="e590b-102">#Region Directive</span></span>

<span data-ttu-id="e590b-103">Collapses and hides sections of code in Visual Basic files.</span><span class="sxs-lookup"><span data-stu-id="e590b-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e590b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e590b-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="e590b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e590b-105">Parts</span></span>  
  
|<span data-ttu-id="e590b-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e590b-106">Term</span></span>|<span data-ttu-id="e590b-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e590b-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="e590b-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e590b-108">Required.</span></span> <span data-ttu-id="e590b-109">String that acts as the title of a region when it is collapsed.</span><span class="sxs-lookup"><span data-stu-id="e590b-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="e590b-110">Regions are collapsed by default.</span><span class="sxs-lookup"><span data-stu-id="e590b-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="e590b-111">Terminates the `#Region` block.</span><span class="sxs-lookup"><span data-stu-id="e590b-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e590b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e590b-112">Remarks</span></span>  

 <span data-ttu-id="e590b-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span><span class="sxs-lookup"><span data-stu-id="e590b-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="e590b-114">You can place, or *nest*, regions within other regions to group similar regions together.</span><span class="sxs-lookup"><span data-stu-id="e590b-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e590b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e590b-115">Example</span></span>  

 <span data-ttu-id="e590b-116">This example uses the `#Region` directive.</span><span class="sxs-lookup"><span data-stu-id="e590b-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e590b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e590b-117">See also</span></span>

- [<span data-ttu-id="e590b-118">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="e590b-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="e590b-119">Sbalení</span><span class="sxs-lookup"><span data-stu-id="e590b-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="e590b-120">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="e590b-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
