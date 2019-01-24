---
title: 'Postupy: Nastavení obsahu textu ovládacího prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 8d37fd4a969de2c6fddb26e2e2151f490cb85e32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563623"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="8c983-102">Postupy: Nastavení obsahu textu ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="8c983-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="8c983-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.TextBox.Text%2A> vlastnosti chcete nastavit počáteční textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8c983-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="8c983-104">**Poznámka:** i když [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] použít verzi v příkladu `<TextBox.Text>` značky kolem textu každé tlačítko <xref:System.Windows.Controls.TextBox> obsahu, není nutné protože <xref:System.Windows.Controls.TextBox> se vztahuje <xref:System.Windows.Markup.ContentPropertyAttribute> atribut <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8c983-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="8c983-105">Další informace najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="8c983-105">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c983-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c983-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="8c983-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c983-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="8c983-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c983-108">See also</span></span>
- [<span data-ttu-id="8c983-109">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="8c983-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="8c983-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="8c983-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
