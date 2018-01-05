---
title: "Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e892ce1ecea450e9c3bf300283492913cdb80e07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="fec63-102">Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fec63-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="fec63-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> spoustu možností pro formátování textu, zobrazí se má ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fec63-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="fec63-104">Lze vytvořit vybrané znaků tučné nebo kurzívy, pomocí <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fec63-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="fec63-105">Tato vlastnost také můžete změnit velikost a řez písma vybraných znaků.</span><span class="sxs-lookup"><span data-stu-id="fec63-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="fec63-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Vlastnost umožňuje změnit barvu vybrané znaky.</span><span class="sxs-lookup"><span data-stu-id="fec63-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="fec63-107">Chcete-li změnit vzhled znaků</span><span class="sxs-lookup"><span data-stu-id="fec63-107">To change the appearance of characters</span></span>  
  
1.  <span data-ttu-id="fec63-108">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> vlastnost pro příslušné písmo.</span><span class="sxs-lookup"><span data-stu-id="fec63-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="fec63-109">Pokud chcete povolit uživatelům nastavení rodiny písem, velikost a řez písma v aplikaci, obvykle použijete <xref:System.Windows.Forms.FontDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="fec63-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="fec63-110">Přehled najdete v tématu [FontDialog – přehled komponenty](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fec63-110">For an overview, see [FontDialog Component Overview](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="fec63-111">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> vlastnost, která má odpovídající barev.</span><span class="sxs-lookup"><span data-stu-id="fec63-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="fec63-112">Pokud chcete povolit uživatelům nastavení barvy v aplikaci, obvykle použijete <xref:System.Windows.Forms.ColorDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="fec63-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="fec63-113">Přehled najdete v tématu [ColorDialog – přehled komponenty](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fec63-113">For an overview, see [ColorDialog Component Overview](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span></span>  
  
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
    >  <span data-ttu-id="fec63-114">Tyto vlastnosti ovlivňují jenom vybraný text nebo, pokud není vybraný žádný text, text, který je typu na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="fec63-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="fec63-115">Informace o výběr textu pomocí programu najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="fec63-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec63-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fec63-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="fec63-117">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fec63-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="fec63-118">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fec63-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
