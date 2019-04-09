---
title: 'Postupy: Určení velikosti ovládacího prvku Windows Forms Label k zobrazení jeho obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: f9e7fad1f8b2b4e962f46a1e32522f47f01de2b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191871"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="af138-102">Postupy: Určení velikosti ovládacího prvku Windows Forms Label k zobrazení jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="af138-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="af138-103">Windows Forms <xref:System.Windows.Forms.Label> ovládací prvek může být jednořádkové nebo víceřádkové, a může být buď pevnou velikost nebo můžete automaticky měnit velikost tak, aby vyhovovaly titulek.</span><span class="sxs-lookup"><span data-stu-id="af138-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="af138-104"><xref:System.Windows.Forms.Label.AutoSize%2A> Vlastnost umožňuje velikost ovládacích prvků podle větší nebo menší popisky, které je zvláště užitečný, pokud popisek se změní za běhu.</span><span class="sxs-lookup"><span data-stu-id="af138-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="af138-105">Chcete-li změnit dynamicky velikost podle svého obsahu ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="af138-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="af138-106">Nastavte jeho <xref:System.Windows.Forms.Label.AutoSize%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="af138-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="af138-107">Pokud <xref:System.Windows.Forms.Label.AutoSize%2A> je nastavena na `false`, v zadaných slov <xref:System.Windows.Forms.Label.Text%2A> vlastnost se zalomí na další řádek Pokud je to možné, ale nebude zvětšovat ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="af138-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af138-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af138-108">See also</span></span>

- [<span data-ttu-id="af138-109">Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="af138-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="af138-110">Přehled ovládacího prvku Label</span><span class="sxs-lookup"><span data-stu-id="af138-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="af138-111">Ovládací prvek Label</span><span class="sxs-lookup"><span data-stu-id="af138-111">Label Control</span></span>](label-control-windows-forms.md)
