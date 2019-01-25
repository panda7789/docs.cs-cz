---
title: 'Postupy: Nastavení fokusu v ovládacím prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: 1ab7fa5f5ce895d163e3db3dd020fee3f29b7153
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590705"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="30327-102">Postupy: Nastavení fokusu v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="30327-102">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="30327-103">Tento příklad ukazuje způsob použití <xref:System.Windows.UIElement.Focus%2A> zaměřit se na metodu <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="30327-103">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30327-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="30327-104">Example</span></span>  
 <span data-ttu-id="30327-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad popisuje jednoduchý <xref:System.Windows.Controls.TextBox> ovládací prvek s názvem *tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="30327-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="30327-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="30327-106">Example</span></span>  
 <span data-ttu-id="30327-107">Následující příklad volá <xref:System.Windows.UIElement.Focus%2A> metoda se zaměřit na <xref:System.Windows.Controls.TextBox> ovládací prvek s názvem *tbFocusMe*.</span><span class="sxs-lookup"><span data-stu-id="30327-107">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="30327-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30327-108">See also</span></span>
- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [<span data-ttu-id="30327-109">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="30327-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="30327-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="30327-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
