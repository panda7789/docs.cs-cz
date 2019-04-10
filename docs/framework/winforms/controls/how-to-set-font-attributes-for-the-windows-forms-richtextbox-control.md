---
title: 'Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox'
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
ms.openlocfilehash: a6fe5b30c457fae2d53c946092b214f492fe5e9b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331205"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="b9617-102">Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b9617-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="b9617-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek má mnoho možností pro formátování textu se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b9617-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="b9617-104">Provedením vybrané znaky tučně nebo kurzívy, pomocí <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b9617-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="b9617-105">Tuto vlastnost můžete také změnit velikost a písmo vybrané znaky.</span><span class="sxs-lookup"><span data-stu-id="b9617-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="b9617-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Vlastnost umožňuje změnit barvu vybrané znaky.</span><span class="sxs-lookup"><span data-stu-id="b9617-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="b9617-107">Chcete-li změnit vzhled znaků</span><span class="sxs-lookup"><span data-stu-id="b9617-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="b9617-108">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> vlastnosti k odpovídající písmo.</span><span class="sxs-lookup"><span data-stu-id="b9617-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="b9617-109">Pokud chcete povolit uživatelům nastavit rodina písem, velikost a písmo v aplikaci, obvykle použijete <xref:System.Windows.Forms.FontDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="b9617-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="b9617-110">Přehled najdete v tématu [FontDialog – přehled komponenty](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b9617-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="b9617-111">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> vlastnost na požadovanou barvu.</span><span class="sxs-lookup"><span data-stu-id="b9617-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="b9617-112">Pokud chcete povolit uživatelům nastavit barvu v aplikaci, obvykle použijete <xref:System.Windows.Forms.ColorDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="b9617-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="b9617-113">Přehled najdete v tématu [ColorDialog – přehled komponenty](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b9617-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
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
    >  <span data-ttu-id="b9617-114">Těchto vlastností ovlivní pouze vybraný text nebo, pokud není vybraný žádný text, text, který je zadaný na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="b9617-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="b9617-115">Další informace o výběru textu prostřednictvím kódu programu, najdete v článku <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9617-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9617-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9617-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="b9617-117">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b9617-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="b9617-118">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9617-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
