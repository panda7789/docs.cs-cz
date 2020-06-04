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
ms.openlocfilehash: cd53a6079c1564a8c73a0a1a6273fc166d18d3e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409933"
---
# <a name="region-directive"></a><span data-ttu-id="8c7c0-102">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="8c7c0-102">#Region Directive</span></span>

<span data-ttu-id="8c7c0-103">Sbalí a skryje části kódu v souborech Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c7c0-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="8c7c0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8c7c0-105">Parts</span></span>  
  
|<span data-ttu-id="8c7c0-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="8c7c0-106">Term</span></span>|<span data-ttu-id="8c7c0-107">Definice</span><span class="sxs-lookup"><span data-stu-id="8c7c0-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="8c7c0-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-108">Required.</span></span> <span data-ttu-id="8c7c0-109">Řetězec, který slouží jako název oblasti při sbalení.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="8c7c0-110">Oblasti jsou ve výchozím nastavení sbaleny.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="8c7c0-111">Ukončí `#Region` blok.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c7c0-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c7c0-112">Remarks</span></span>  

 <span data-ttu-id="8c7c0-113">Pomocí `#Region` direktivy určete blok kódu, který se má rozbalit nebo sbalit při použití funkce sbalení editoru Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="8c7c0-114">Můžete umístit nebo *vnořovat*oblasti v rámci jiných oblastí a seskupovat podobné oblasti dohromady.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c7c0-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c7c0-115">Example</span></span>  

 <span data-ttu-id="8c7c0-116">V tomto příkladu se používá `#Region` direktiva.</span><span class="sxs-lookup"><span data-stu-id="8c7c0-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8c7c0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c7c0-117">See also</span></span>

- [<span data-ttu-id="8c7c0-118">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="8c7c0-118">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="8c7c0-119">Sbalování</span><span class="sxs-lookup"><span data-stu-id="8c7c0-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="8c7c0-120">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="8c7c0-120">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
