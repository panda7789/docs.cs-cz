---
title: 'Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox'
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
ms.openlocfilehash: 893782e041b1397fe0598394b69575a5c9e53806
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625400"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="43a2d-102">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="43a2d-103">Ve výchozím nastavení, Windows Forms <xref:System.Windows.Forms.TextBox> ovládací prvek zobrazí jeden řádek textu a posuvníky nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="43a2d-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="43a2d-104">Je-li text je delší než dostupný prostor, zobrazí se pouze část textu.</span><span class="sxs-lookup"><span data-stu-id="43a2d-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="43a2d-105">Toto výchozí chování můžete změnit nastavením <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnosti na odpovídající hodnoty.</span><span class="sxs-lookup"><span data-stu-id="43a2d-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="43a2d-106">Chcete-li zobrazit zalomení řádku v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-106">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="43a2d-107">Chcete-li zobrazit návrat do více řádků <xref:System.Windows.Forms.TextBox>, použijte <xref:System.Environment.NewLine%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="43a2d-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="43a2d-108">Mějte na paměti, která výklad řídicí znaky (\\) je specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="43a2d-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="43a2d-109">Jazyk Visual Basic používá `Chr$(13) & Chr$(10)` pro návrat na začátek řádku kombinaci znaků vrácených hodnot a znak odřádkování.</span><span class="sxs-lookup"><span data-stu-id="43a2d-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="43a2d-110">Chcete-li zobrazit více řádků v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-110">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="43a2d-111">Nastavte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="43a2d-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="43a2d-112">Pokud <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je `true` (výchozí), pak textu v ovládacím prvku se zobrazí jako jeden nebo více odstavců; v opačném případě se zobrazí jako seznam, ve kterém může být některé řádky oříznut na okraji ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="43a2d-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="43a2d-113">Nastavte <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="43a2d-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="43a2d-114">Value</span><span class="sxs-lookup"><span data-stu-id="43a2d-114">Value</span></span>|<span data-ttu-id="43a2d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="43a2d-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="43a2d-116">Tuto hodnotu použijte, pokud má být tento text odstavce, který téměř vždy vyhovovat ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="43a2d-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="43a2d-117">Uživatele můžete použít umístění ukazatele myši na pohyb uvnitř ovládacího prvku, pokud je text příliš dlouhý, chcete-li zobrazit všechny najednou.</span><span class="sxs-lookup"><span data-stu-id="43a2d-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="43a2d-118">Tuto hodnotu použijte, pokud chcete zobrazit seznam řádků, z nichž některé mohou být delší než šířka <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="43a2d-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="43a2d-119">Tuto hodnotu použijte, pokud v seznamu může být delší než výška ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="43a2d-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="43a2d-120">Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="43a2d-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="43a2d-121">Value</span><span class="sxs-lookup"><span data-stu-id="43a2d-121">Value</span></span>|<span data-ttu-id="43a2d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="43a2d-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="43a2d-123">Text v ovládacím prvku nebude automaticky zabalená, takže ho se posuňte doprava, dokud nebude dosaženo konce řádku.</span><span class="sxs-lookup"><span data-stu-id="43a2d-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="43a2d-124">Pokud jste zvolili, používejte tuto hodnotu <xref:System.Windows.Forms.ScrollBars.Horizontal> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.Both>výše.</span><span class="sxs-lookup"><span data-stu-id="43a2d-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="43a2d-125">`true` (výchozí)</span><span class="sxs-lookup"><span data-stu-id="43a2d-125">`true` (default)</span></span>|<span data-ttu-id="43a2d-126">Vodorovný posuvník nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="43a2d-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="43a2d-127">Pokud jste zvolili, používejte tuto hodnotu <xref:System.Windows.Forms.ScrollBars.Vertical> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.None>, výše a zobrazte jeden nebo více odstavcích.</span><span class="sxs-lookup"><span data-stu-id="43a2d-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43a2d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43a2d-128">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="43a2d-129">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-129">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="43a2d-130">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="43a2d-131">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="43a2d-132">Postupy: Vytvoření pole jen pro čtení textu</span><span class="sxs-lookup"><span data-stu-id="43a2d-132">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="43a2d-133">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="43a2d-133">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="43a2d-134">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="43a2d-135">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="43a2d-135">TextBox Control</span></span>](textbox-control-windows-forms.md)
