---
title: Velikost ovládacího prvku popisek podle jeho obsahu
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743782"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="8cb9e-102">Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="8cb9e-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="8cb9e-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.Label> může být jednořádkový nebo víceřádkový a může být buď pevně stanovený, nebo se může automaticky změnit jeho velikost tak, aby odpovídala jeho titulku.</span><span class="sxs-lookup"><span data-stu-id="8cb9e-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="8cb9e-104">Vlastnost <xref:System.Windows.Forms.Label.AutoSize%2A> pomáhá nastavit velikost ovládacích prvků tak, aby vyhovovala větším nebo menším titulkům, což je zvláště užitečné, pokud se titulek v době běhu změní.</span><span class="sxs-lookup"><span data-stu-id="8cb9e-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="8cb9e-105">Chcete-li změnit velikost ovládacího prvku popisku dynamicky tak, aby odpovídal jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="8cb9e-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="8cb9e-106">Vlastnost <xref:System.Windows.Forms.Label.AutoSize%2A> nastavte na `true`.</span><span class="sxs-lookup"><span data-stu-id="8cb9e-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="8cb9e-107">Pokud je <xref:System.Windows.Forms.Label.AutoSize%2A> nastaveno na hodnotu `false`, slova zadaná ve vlastnosti <xref:System.Windows.Forms.Label.Text%2A> budou zabalena do dalšího řádku, pokud je to možné, ale ovládací prvek se nebude zvětšovat.</span><span class="sxs-lookup"><span data-stu-id="8cb9e-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb9e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cb9e-108">See also</span></span>

- [<span data-ttu-id="8cb9e-109">Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="8cb9e-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="8cb9e-110">Přehled ovládacího prvku Label</span><span class="sxs-lookup"><span data-stu-id="8cb9e-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="8cb9e-111">Ovládací prvek Label</span><span class="sxs-lookup"><span data-stu-id="8cb9e-111">Label Control</span></span>](label-control-windows-forms.md)
