---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 44f0116511165c021f8e3dc35fb14e5cfb6f619e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686917"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="77aec-102">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox</span><span class="sxs-lookup"><span data-stu-id="77aec-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="77aec-103">Windows Forms <xref:System.Windows.Forms.GroupBox> ovládací prvky se používají k seskupování další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="77aec-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="77aec-104">Existují tři hlavní důvody k seskupování ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="77aec-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="77aec-105">Chcete-li vytvořit vizuální seskupení elementů související formuláře pro jasné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="77aec-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="77aec-106">Chcete-li vytvořit programový seskupení (přepínačů, například).</span><span class="sxs-lookup"><span data-stu-id="77aec-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="77aec-107">K přesunutí ovládacích prvků jako jednotka v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="77aec-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="77aec-108">Chcete-li vytvořit skupinu ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="77aec-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="77aec-109">Vykreslení <xref:System.Windows.Forms.GroupBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="77aec-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="77aec-110">Přidejte další ovládací prvky do pole skupiny, kreslení každý uvnitř skupinového rámečku.</span><span class="sxs-lookup"><span data-stu-id="77aec-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="77aec-111">Pokud máte existující ovládací prvky, které chcete uzavřít do skupinového rámečku, můžete vybrat všechny ovládací prvky, vyjmout data do schránky, vyberte <xref:System.Windows.Forms.GroupBox> ovládací prvek a pak je vložte do pole pro skupiny.</span><span class="sxs-lookup"><span data-stu-id="77aec-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="77aec-112">Můžete také přetáhnout do pole skupiny.</span><span class="sxs-lookup"><span data-stu-id="77aec-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="77aec-113">Nastavte <xref:System.Windows.Forms.GroupBox.Text%2A> vlastnost skupinový rámeček pro příslušný popisek.</span><span class="sxs-lookup"><span data-stu-id="77aec-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77aec-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77aec-114">See also</span></span>
- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="77aec-115">Ovládací prvek GroupBox</span><span class="sxs-lookup"><span data-stu-id="77aec-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
