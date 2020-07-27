---
title: 'Postupy: Nastavení fokusu v ovládacím prvku TextBox'
description: Naučte se používat metodu Focus k nastavení fokusu na ovládací prvek TextBox Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: e107c22a3c5b701e02cbc8506d10fa35ee15c79d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168063"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="b0971-103">Postupy: Nastavení fokusu v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="b0971-103">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="b0971-104">Tento příklad ukazuje, jak použít <xref:System.Windows.UIElement.Focus%2A> metodu pro nastavení fokusu na <xref:System.Windows.Controls.TextBox> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b0971-104">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0971-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0971-105">Example</span></span>  
 <span data-ttu-id="b0971-106">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad popisuje jednoduchý <xref:System.Windows.Controls.TextBox> ovládací prvek s názvem *tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="b0971-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="b0971-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0971-107">Example</span></span>  
 <span data-ttu-id="b0971-108">Následující příklad volá <xref:System.Windows.UIElement.Focus%2A> metodu pro nastavení fokusu na <xref:System.Windows.Controls.TextBox> ovládací prvek s názvem *tbFocusMe*.</span><span class="sxs-lookup"><span data-stu-id="b0971-108">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="b0971-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0971-109">See also</span></span>

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [<span data-ttu-id="b0971-110">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="b0971-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="b0971-111">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="b0971-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
