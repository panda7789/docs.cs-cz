---
title: Zobrazit více řádků v ovládacím prvku TextBox
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
ms.openlocfilehash: 61ea671c1e86fa8254bfc1b043a46f3b7aa6af1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728286"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="be0e3-102">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="be0e3-103">Ve výchozím nastavení ovládací prvek model Windows Forms <xref:System.Windows.Forms.TextBox> zobrazuje jeden řádek textu a nezobrazuje posuvníky.</span><span class="sxs-lookup"><span data-stu-id="be0e3-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="be0e3-104">Pokud je text delší než dostupný prostor, je viditelná pouze část textu.</span><span class="sxs-lookup"><span data-stu-id="be0e3-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="be0e3-105">Toto výchozí chování můžete změnit nastavením vlastností <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na příslušné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="be0e3-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="be0e3-106">Zobrazení návratového znaku v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-106">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="be0e3-107">Chcete-li zobrazit znak návratu do víceřádkové <xref:System.Windows.Forms.TextBox>, použijte vlastnost <xref:System.Environment.NewLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="be0e3-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="be0e3-108">Upozorňujeme, že výklad řídicích znaků (\\) je specifický pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="be0e3-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="be0e3-109">Visual Basic používá `Chr$(13) & Chr$(10)` kombinaci znaků návratového řádku a znaku odřádkování.</span><span class="sxs-lookup"><span data-stu-id="be0e3-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="be0e3-110">Zobrazení více řádků v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-110">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="be0e3-111">Nastavte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="be0e3-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="be0e3-112">Pokud je <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> `true` (výchozí), pak se text v ovládacím prvku zobrazí jako jeden nebo více odstavců. v opačném případě se zobrazí jako seznam, ve kterém mohou být některé řádky oříznuty na okraji ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="be0e3-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="be0e3-113">Vlastnost <xref:System.Windows.Forms.TextBox.ScrollBars%2A> nastavte na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="be0e3-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="be0e3-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="be0e3-114">Value</span></span>|<span data-ttu-id="be0e3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="be0e3-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="be0e3-116">Tuto hodnotu použijte, pokud bude text odstavcem, který téměř vždy odpovídá ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="be0e3-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="be0e3-117">Uživatel může použít ukazatel myši k přesunu uvnitř ovládacího prvku, pokud je text příliš dlouhý pro zobrazení všech najednou.</span><span class="sxs-lookup"><span data-stu-id="be0e3-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="be0e3-118">Tuto hodnotu použijte, pokud chcete zobrazit seznam řádků, některé z nich mohou být delší než šířka ovládacího prvku <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="be0e3-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="be0e3-119">Tuto hodnotu použijte, pokud seznam může být delší než výška ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="be0e3-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="be0e3-120">Vlastnost <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> nastavte na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="be0e3-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="be0e3-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="be0e3-121">Value</span></span>|<span data-ttu-id="be0e3-122">Popis</span><span class="sxs-lookup"><span data-stu-id="be0e3-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="be0e3-123">Text v ovládacím prvku nebude automaticky zabalen, takže se posune doprava, dokud není dosaženo konce řádku.</span><span class="sxs-lookup"><span data-stu-id="be0e3-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="be0e3-124">Tuto hodnotu použijte, pokud jste zvolili <xref:System.Windows.Forms.ScrollBars.Horizontal> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.Both>.</span><span class="sxs-lookup"><span data-stu-id="be0e3-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="be0e3-125">`true` (výchozí)</span><span class="sxs-lookup"><span data-stu-id="be0e3-125">`true` (default)</span></span>|<span data-ttu-id="be0e3-126">Vodorovný posuvník se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="be0e3-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="be0e3-127">Tuto hodnotu použijte, pokud jste zvolili <xref:System.Windows.Forms.ScrollBars.Vertical> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.None>výše, aby se zobrazil jeden nebo více odstavců.</span><span class="sxs-lookup"><span data-stu-id="be0e3-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be0e3-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be0e3-128">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="be0e3-129">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-129">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="be0e3-130">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="be0e3-131">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="be0e3-132">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0e3-132">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="be0e3-133">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="be0e3-133">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="be0e3-134">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="be0e3-135">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="be0e3-135">TextBox Control</span></span>](textbox-control-windows-forms.md)
