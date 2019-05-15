---
title: 'Postupy: Implementace vlastního prvku ToolStripRenderer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: 4a84571bf8b81cd26c864edcd4d313a4009dda16
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592421"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="99cab-102">Postupy: Implementace vlastního prvku ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="99cab-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="99cab-103">Můžete přizpůsobit vzhled <xref:System.Windows.Forms.ToolStrip> ovládacího prvku pomocí implementace, která je odvozena z třídy <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="99cab-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="99cab-104">To vám dává flexibilitu pro vytvoření vzhledu, která se liší od vzhled k dispozici <xref:System.Windows.Forms.ToolStripProfessionalRenderer> a <xref:System.Windows.Forms.ToolStripSystemRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="99cab-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99cab-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="99cab-105">Example</span></span>  
 <span data-ttu-id="99cab-106">Následující příklad kódu ukazuje, jak implementovat vlastní <xref:System.Windows.Forms.ToolStripRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="99cab-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="99cab-107">V tomto příkladu `GridStrip` ovládací prvek implementuje díl stavebnice klouzavé dlaždice, což mu umožní přesunout dlaždice v tabulkové rozložení a vytvoří bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="99cab-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="99cab-108">Vlastní <xref:System.Windows.Forms.ToolStrip> uspořádá ovládací prvek jeho <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků v případě rozložení mřížky.</span><span class="sxs-lookup"><span data-stu-id="99cab-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="99cab-109">Rozložení obsahuje jeden prázdné buňky, do kterého může uživatel snímků sousední dlaždici pomocí operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="99cab-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="99cab-110">Dlaždice, které uživatel může přesunout jsou zvýrazněné.</span><span class="sxs-lookup"><span data-stu-id="99cab-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="99cab-111">`GridStripRenderer` Třídy přizpůsobí tři aspekty `GridStrip` vzhled ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="99cab-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
- <span data-ttu-id="99cab-112">`GridStrip` Ohraničení</span><span class="sxs-lookup"><span data-stu-id="99cab-112">`GridStrip` border</span></span>  
  
- <span data-ttu-id="99cab-113"><xref:System.Windows.Forms.ToolStripButton> Ohraničení</span><span class="sxs-lookup"><span data-stu-id="99cab-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
- <span data-ttu-id="99cab-114"><xref:System.Windows.Forms.ToolStripButton> Bitové kopie</span><span class="sxs-lookup"><span data-stu-id="99cab-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99cab-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="99cab-115">Compiling the Code</span></span>  
 <span data-ttu-id="99cab-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="99cab-116">This example requires:</span></span>  
  
- <span data-ttu-id="99cab-117">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="99cab-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cab-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99cab-118">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="99cab-119">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="99cab-119">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
