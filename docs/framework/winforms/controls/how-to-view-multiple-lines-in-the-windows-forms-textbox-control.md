---
title: Zobrazit více řádků v ovládacím prvku TextBox
description: Přečtěte si, jak zobrazit více řádků v ovládacím prvku model Windows Forms TextBox nastavením vlastností víceřádkových, WordWrap a ScrollBar.
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174468"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="7174d-103">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7174d-103">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="7174d-104">Ve výchozím nastavení model Windows Forms <xref:System.Windows.Forms.TextBox> ovládací prvek zobrazuje jeden řádek textu a nezobrazuje posuvníky.</span><span class="sxs-lookup"><span data-stu-id="7174d-104">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="7174d-105">Pokud je text delší než dostupný prostor, je viditelná pouze část textu.</span><span class="sxs-lookup"><span data-stu-id="7174d-105">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="7174d-106">Toto výchozí chování můžete změnit nastavením <xref:System.Windows.Forms.TextBox.Multiline%2A> <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastností, a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na příslušné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7174d-106">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="7174d-107">Zobrazení návratového znaku v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="7174d-107">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="7174d-108">Chcete-li zobrazit návrat vozíku na více řádků <xref:System.Windows.Forms.TextBox> , použijte <xref:System.Environment.NewLine%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7174d-108">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="7174d-109">Upozorňujeme, že výklad řídicích znaků ( \\ ) je specifický pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="7174d-109">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="7174d-110">Visual Basic používá `Chr$(13) & Chr$(10)` kombinaci znaků pro návrat na začátek řádku a znak odřádkování.</span><span class="sxs-lookup"><span data-stu-id="7174d-110">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="7174d-111">Zobrazení více řádků v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="7174d-111">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="7174d-112">Nastavte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="7174d-112">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="7174d-113">Pokud <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je `true` (výchozí), pak se text v ovládacím prvku zobrazí jako jeden nebo více odstavců. v opačném případě se zobrazí jako seznam, ve kterém mohou být některé řádky oříznuty na okraji ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7174d-113">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="7174d-114">Nastavte <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7174d-114">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="7174d-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7174d-115">Value</span></span>|<span data-ttu-id="7174d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7174d-116">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="7174d-117">Tuto hodnotu použijte, pokud bude text odstavcem, který téměř vždy odpovídá ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="7174d-117">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="7174d-118">Uživatel může použít ukazatel myši k přesunu uvnitř ovládacího prvku, pokud je text příliš dlouhý pro zobrazení všech najednou.</span><span class="sxs-lookup"><span data-stu-id="7174d-118">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="7174d-119">Tuto hodnotu použijte, pokud chcete zobrazit seznam řádků, některé z nich mohou být delší než šířka <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7174d-119">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="7174d-120">Tuto hodnotu použijte, pokud seznam může být delší než výška ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7174d-120">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="7174d-121">Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7174d-121">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="7174d-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7174d-122">Value</span></span>|<span data-ttu-id="7174d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7174d-123">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="7174d-124">Text v ovládacím prvku nebude automaticky zabalen, takže se posune doprava, dokud není dosaženo konce řádku.</span><span class="sxs-lookup"><span data-stu-id="7174d-124">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="7174d-125">Tuto hodnotu použijte, pokud jste zvolili <xref:System.Windows.Forms.ScrollBars.Horizontal> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.Both> nahoře.</span><span class="sxs-lookup"><span data-stu-id="7174d-125">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="7174d-126">`true`výchozí</span><span class="sxs-lookup"><span data-stu-id="7174d-126">`true` (default)</span></span>|<span data-ttu-id="7174d-127">Vodorovný posuvník se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="7174d-127">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="7174d-128">Tuto hodnotu použijte, pokud vyberete <xref:System.Windows.Forms.ScrollBars.Vertical> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.None> nahoře a zobrazíte jeden nebo více odstavců.</span><span class="sxs-lookup"><span data-stu-id="7174d-128">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7174d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7174d-129">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="7174d-130">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="7174d-130">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="7174d-131">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7174d-131">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="7174d-132">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7174d-132">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="7174d-133">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7174d-133">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="7174d-134">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="7174d-134">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="7174d-135">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7174d-135">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="7174d-136">TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7174d-136">TextBox Control</span></span>](textbox-control-windows-forms.md)
