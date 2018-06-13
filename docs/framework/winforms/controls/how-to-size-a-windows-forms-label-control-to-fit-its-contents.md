---
title: 'Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533725"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="e9c8e-102">Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="e9c8e-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="e9c8e-103">Windows Forms <xref:System.Windows.Forms.Label> ovládací prvek může být v jednom nebo více řádky, a může být buď pevnou velikost nebo můžete automaticky měnit velikost pro umístění titulek.</span><span class="sxs-lookup"><span data-stu-id="e9c8e-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="e9c8e-104"><xref:System.Windows.Forms.Label.AutoSize%2A> Vlastnost umožňuje ovládacích prvků k přizpůsobení titulků větší nebo menší velikost, která je zvlášť užitečné, pokud titulek se změní za běhu.</span><span class="sxs-lookup"><span data-stu-id="e9c8e-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="e9c8e-105">Chcete-li ovládací prvek popisek dynamicky Změna velikosti podle obsahu</span><span class="sxs-lookup"><span data-stu-id="e9c8e-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="e9c8e-106">Nastavte její <xref:System.Windows.Forms.Label.AutoSize%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="e9c8e-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="e9c8e-107">Pokud <xref:System.Windows.Forms.Label.AutoSize%2A> je nastaven na `false`, slova zadaný v <xref:System.Windows.Forms.Label.Text%2A> vlastnost budou zahrnovat na další řádek Pokud je to možné, ale ovládací prvek nebude zvětšovat.</span><span class="sxs-lookup"><span data-stu-id="e9c8e-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c8e-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9c8e-108">See Also</span></span>  
 [<span data-ttu-id="e9c8e-109">Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="e9c8e-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [<span data-ttu-id="e9c8e-110">Přehled ovládacího prvku Label</span><span class="sxs-lookup"><span data-stu-id="e9c8e-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="e9c8e-111">Ovládací prvek Label</span><span class="sxs-lookup"><span data-stu-id="e9c8e-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
