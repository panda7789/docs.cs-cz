---
title: Seskupení ovládacích prvků s ovládacím prvkem skupinový rámeček
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: bb7476c410d2802b5d32cc9842a778f290765e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736653"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="f73ad-102">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox</span><span class="sxs-lookup"><span data-stu-id="f73ad-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="f73ad-103">Ovládací prvky <xref:System.Windows.Forms.GroupBox> model Windows Forms slouží k seskupení dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f73ad-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="f73ad-104">Existují tři důvody pro seskupení ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="f73ad-104">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="f73ad-105">Chcete-li vytvořit vizuální seskupení souvisejících prvků formuláře pro jasné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f73ad-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="f73ad-106">Vytvoření programového seskupení (například přepínačů).</span><span class="sxs-lookup"><span data-stu-id="f73ad-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="f73ad-107">Pro přesunutí ovládacích prvků jako jednotky v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="f73ad-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="f73ad-108">Vytvoření skupiny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f73ad-108">To create a group of controls</span></span>  
  
1. <span data-ttu-id="f73ad-109">Nakreslete ovládací prvek <xref:System.Windows.Forms.GroupBox> na formuláři.</span><span class="sxs-lookup"><span data-stu-id="f73ad-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="f73ad-110">Do pole skupiny přidejte další ovládací prvky, které vykreslí do skupinového pole.</span><span class="sxs-lookup"><span data-stu-id="f73ad-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="f73ad-111">Pokud máte ovládací prvky, které chcete zahrnout do skupinového pole, můžete vybrat všechny ovládací prvky, vyjmout je do schránky, vybrat ovládací prvek <xref:System.Windows.Forms.GroupBox> a pak je vložit do skupinového pole.</span><span class="sxs-lookup"><span data-stu-id="f73ad-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="f73ad-112">Můžete je také přetáhnout do pole skupiny.</span><span class="sxs-lookup"><span data-stu-id="f73ad-112">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="f73ad-113">Nastavte vlastnost <xref:System.Windows.Forms.GroupBox.Text%2A> skupinového pole na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="f73ad-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f73ad-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f73ad-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="f73ad-115">Ovládací prvek GroupBox</span><span class="sxs-lookup"><span data-stu-id="f73ad-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
