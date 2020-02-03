---
title: Nastavení atributů písma pro ovládací prvek RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: f27256c155223df576ee3c42e6bf65270c870b0f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744863"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="8e901-102">Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8e901-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="8e901-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> má mnoho možností formátování textu, který zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="8e901-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="8e901-104">Vybrané znaky můžete nastavit jako tučné, podtržené nebo kurzívu pomocí vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e901-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="8e901-105">Tuto vlastnost můžete také použít ke změně velikosti a řezu písma vybraných znaků.</span><span class="sxs-lookup"><span data-stu-id="8e901-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="8e901-106">Vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> umožňuje změnit barvu vybraných znaků.</span><span class="sxs-lookup"><span data-stu-id="8e901-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="8e901-107">Změna vzhledu znaků</span><span class="sxs-lookup"><span data-stu-id="8e901-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="8e901-108">Vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> nastavte na příslušné písmo.</span><span class="sxs-lookup"><span data-stu-id="8e901-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="8e901-109">Pokud chcete uživatelům umožnit, aby v aplikaci nastavili rodinu písem, velikost a řez písma, obvykle byste použili komponentu <xref:System.Windows.Forms.FontDialog>.</span><span class="sxs-lookup"><span data-stu-id="8e901-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="8e901-110">Přehled naleznete v tématu [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8e901-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="8e901-111">Vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> nastavte na odpovídající barvu.</span><span class="sxs-lookup"><span data-stu-id="8e901-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="8e901-112">Chcete-li uživatelům umožnit nastavení barev v aplikaci, obvykle byste použili komponentu <xref:System.Windows.Forms.ColorDialog>.</span><span class="sxs-lookup"><span data-stu-id="8e901-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="8e901-113">Přehled naleznete v tématu [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8e901-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="8e901-114">Tyto vlastnosti ovlivní pouze vybraný text, nebo, pokud není vybrán žádný text, text, který je zadán v aktuálním umístění bodu vložení.</span><span class="sxs-lookup"><span data-stu-id="8e901-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="8e901-115">Informace o tom, jak text programově vybírat, najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e901-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e901-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e901-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="8e901-117">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8e901-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="8e901-118">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e901-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
