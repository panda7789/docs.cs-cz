---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 718367e9da9efda20c79fbff3bd2f14f11c96ee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531921"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="dbf6a-102">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox</span><span class="sxs-lookup"><span data-stu-id="dbf6a-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="dbf6a-103">Windows Forms <xref:System.Windows.Forms.GroupBox> ovládací prvky slouží k seskupení další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="dbf6a-104">Existují tři důvodů, proč seskupování ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="dbf6a-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="dbf6a-105">Chcete-li vytvořit visual seskupení prvků související formuláře pro zrušte uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="dbf6a-106">Chcete-li vytvořit programový seskupení (přepínačů, např.).</span><span class="sxs-lookup"><span data-stu-id="dbf6a-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="dbf6a-107">Pro přesun ovládací prvky jako jednotku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="dbf6a-108">Chcete-li vytvořit skupinu ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="dbf6a-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="dbf6a-109">Kreslení <xref:System.Windows.Forms.GroupBox> prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="dbf6a-110">Přidání dalších ovládacích prvků do pole skupiny kreslení každý uvnitř pole skupiny.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="dbf6a-111">Pokud máte stávající ovládací prvky, které chcete uzavřete ve skupinovém rámečku, můžete vybrat všechny ovládací prvky, je vyjmout data do schránky, vyberte <xref:System.Windows.Forms.GroupBox> řízení a pak je vložte do pole skupiny.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="dbf6a-112">Můžete je také přetáhnout do pole skupiny.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="dbf6a-113">Nastavte <xref:System.Windows.Forms.GroupBox.Text%2A> vlastnost pole skupiny do příslušné titulek.</span><span class="sxs-lookup"><span data-stu-id="dbf6a-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf6a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbf6a-114">See Also</span></span>  
 <xref:System.Windows.Forms.GroupBox>  
 [<span data-ttu-id="dbf6a-115">Ovládací prvek GroupBox</span><span class="sxs-lookup"><span data-stu-id="dbf6a-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
