---
title: Seskupení ovládacích prvků s ovládacím prvkem skupinový rámeček
description: Naučte se seskupovat ovládací prvky pomocí ovládacího prvku skupinový rámeček model Windows Forms, abyste mohli vytvořit vizuální seskupení souvisejících prvků.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618061"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="62903-103">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox</span><span class="sxs-lookup"><span data-stu-id="62903-103">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="62903-104"><xref:System.Windows.Forms.GroupBox>Ovládací prvky model Windows Forms slouží k seskupení dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="62903-104">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="62903-105">Existují tři důvody pro seskupení ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="62903-105">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="62903-106">Chcete-li vytvořit vizuální seskupení souvisejících prvků formuláře pro jasné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="62903-106">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="62903-107">Vytvoření programového seskupení (například přepínačů).</span><span class="sxs-lookup"><span data-stu-id="62903-107">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="62903-108">Pro přesunutí ovládacích prvků jako jednotky v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="62903-108">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="62903-109">Vytvoření skupiny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="62903-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="62903-110">Nakreslete <xref:System.Windows.Forms.GroupBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="62903-110">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="62903-111">Do pole skupiny přidejte další ovládací prvky, které vykreslí do skupinového pole.</span><span class="sxs-lookup"><span data-stu-id="62903-111">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="62903-112">Pokud máte ovládací prvky, které chcete zahrnout do skupinového pole, můžete vybrat všechny ovládací prvky, vyjmout je do schránky, vybrat <xref:System.Windows.Forms.GroupBox> ovládací prvek a vložit je do skupinového pole.</span><span class="sxs-lookup"><span data-stu-id="62903-112">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="62903-113">Můžete je také přetáhnout do pole skupiny.</span><span class="sxs-lookup"><span data-stu-id="62903-113">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="62903-114">Nastavte <xref:System.Windows.Forms.GroupBox.Text%2A> vlastnost pole skupiny na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="62903-114">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62903-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62903-115">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="62903-116">Ovládací prvek GroupBox</span><span class="sxs-lookup"><span data-stu-id="62903-116">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
