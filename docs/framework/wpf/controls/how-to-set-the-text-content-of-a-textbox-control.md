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
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459299"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="41c1f-102">Postupy: Nastavení obsahu textu ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="41c1f-102">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="41c1f-103">Tento příklad ukazuje, jak použít vlastnost <xref:System.Windows.Controls.TextBox.Text%2A> k nastavení počátečního textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="41c1f-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="41c1f-104">I když [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] verze příkladu může použít značky `<TextBox.Text>` kolem textu <xref:System.Windows.Controls.TextBox> obsahu jednotlivých tlačítek, není nutné, protože <xref:System.Windows.Controls.TextBox> použije atribut <xref:System.Windows.Markup.ContentPropertyAttribute> na vlastnost <xref:System.Windows.Controls.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="41c1f-104">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="41c1f-105">Další informace naleznete v tématu [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="41c1f-105">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="41c1f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="41c1f-106">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="41c1f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="41c1f-107">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="41c1f-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41c1f-108">See also</span></span>

- [<span data-ttu-id="41c1f-109">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="41c1f-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="41c1f-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="41c1f-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
