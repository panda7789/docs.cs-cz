---
title: "Postupy: Zobrazení posuvníků v ovládacím prvku Windows Forms RichTextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b20c526b27eb185bf79eaf0ace47e5a9fded42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="77478-102">Postupy: Zobrazení posuvníků v ovládacím prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="77478-102">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="77478-103">Ve výchozím nastavení Windows Forms <xref:System.Windows.Forms.RichTextBox> zobrazí vodorovného a svislého posuvníky podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="77478-103">By default, the Windows Forms <xref:System.Windows.Forms.RichTextBox> control displays horizontal and vertical scroll bars as necessary.</span></span> <span data-ttu-id="77478-104">Je sedm možných hodnot pro <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> řízení, které jsou popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="77478-104">There are seven possible values for the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property of the <xref:System.Windows.Forms.RichTextBox> control, which are described in the table below.</span></span>  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a><span data-ttu-id="77478-105">Zobrazení posuvníků v ovládacím prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="77478-105">To display scroll bars in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="77478-106">Nastavte <xref:System.Windows.Forms.RichTextBox.Multiline%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="77478-106">Set the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="77478-107">Žádný typ posuvník, včetně vodorovně, se zobrazí, pokud <xref:System.Windows.Forms.RichTextBox.Multiline%2A> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="77478-107">No type of scroll bar, including horizontal, will display if the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property is set to `false`.</span></span>  
  
2.  <span data-ttu-id="77478-108">Nastavit <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> vlastnost, která má odpovídající hodnotu <xref:System.Windows.Forms.RichTextBoxScrollBars> výčtu.</span><span class="sxs-lookup"><span data-stu-id="77478-108">Set the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property to an appropriate value of the <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeration.</span></span>  
  
    |<span data-ttu-id="77478-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="77478-109">Value</span></span>|<span data-ttu-id="77478-110">Popis</span><span class="sxs-lookup"><span data-stu-id="77478-110">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="77478-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="77478-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (default)</span></span>|<span data-ttu-id="77478-112">Zobrazí vodorovné nebo svislé posuvníky nebo obojího jenom v případě, že text překračuje šířky nebo délky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77478-112">Displays horizontal or vertical scroll bars, or both, only when text exceeds the width or length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|<span data-ttu-id="77478-113">Nikdy zobrazí libovolného typu posuvníku.</span><span class="sxs-lookup"><span data-stu-id="77478-113">Never displays any type of scroll bar.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|<span data-ttu-id="77478-114">Zobrazí vodorovného posunování panelu pouze když text překračuje šířku ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77478-114">Displays a horizontal scroll bar only when the text exceeds the width of the control.</span></span> <span data-ttu-id="77478-115">(K tomu došlo, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> musí být nastavena na `false`.)</span><span class="sxs-lookup"><span data-stu-id="77478-115">(For this to occur, the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property must be set to `false`.)</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|<span data-ttu-id="77478-116">Zobrazí svislý posuvník pouze když text překračuje výšku ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77478-116">Displays a vertical scroll bar only when the text exceeds the height of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<span data-ttu-id="77478-117">Zobrazí vodorovného posuvníku při zpracování <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="77478-117">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="77478-118">Posuvník zobrazeno šedě, když text není delší než šířka ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77478-118">The scroll bar appears dimmed when text does not exceed the width of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|<span data-ttu-id="77478-119">Vždy zobrazí svislého posuvníku.</span><span class="sxs-lookup"><span data-stu-id="77478-119">Always displays a vertical scroll bar.</span></span> <span data-ttu-id="77478-120">Když text není delší než délka ovládací prvek typu posuvník šedé.</span><span class="sxs-lookup"><span data-stu-id="77478-120">The scroll bar appears dimmed when text does not exceed the length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|<span data-ttu-id="77478-121">Vždy zobrazí svislý posuvník.</span><span class="sxs-lookup"><span data-stu-id="77478-121">Always displays a vertical scrollbar.</span></span> <span data-ttu-id="77478-122">Zobrazí vodorovného posuvníku při zpracování <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="77478-122">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="77478-123">Když text není delší než šířky nebo délky ovládacího prvku zobrazí šedým posuvníky.</span><span class="sxs-lookup"><span data-stu-id="77478-123">The scroll bars appear grayed when text does not exceed the width or length of the control.</span></span>|  
  
3.  <span data-ttu-id="77478-124">Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="77478-124">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="77478-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="77478-125">Value</span></span>|<span data-ttu-id="77478-126">Popis</span><span class="sxs-lookup"><span data-stu-id="77478-126">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="77478-127">Text v ovládacím prvku není úpravě automaticky šířku ovládacího prvku, takže ho se posuňte doprava, dokud nebude dosaženo konce řádku.</span><span class="sxs-lookup"><span data-stu-id="77478-127">Text in the control is not automatically adjusted to fit the width of the control, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="77478-128">Tuto hodnotu použijte, pokud jste zvolili vodorovné posuvníky nebo obojí, výše.</span><span class="sxs-lookup"><span data-stu-id="77478-128">Use this value if you chose horizontal scroll bars or both, above.</span></span>|  
    |<span data-ttu-id="77478-129">`true`(výchozí)</span><span class="sxs-lookup"><span data-stu-id="77478-129">`true` (default)</span></span>|<span data-ttu-id="77478-130">Text v ovládacím prvku je automaticky upravována podle šířky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77478-130">Text in the control is automatically adjusted to fit the width of the control.</span></span> <span data-ttu-id="77478-131">Vodorovný posuvník se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="77478-131">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="77478-132">Tuto hodnotu použijte, pokud jste zvolili svislé posuvníky nebo hodnotu none, výše, chcete-li zobrazit jeden nebo více odstavců.</span><span class="sxs-lookup"><span data-stu-id="77478-132">Use this value if you chose vertical scroll bars or none, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77478-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="77478-133">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="77478-134">RichTextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="77478-134">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="77478-135">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="77478-135">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
