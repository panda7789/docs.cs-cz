---
title: "Postupy: Vytvoření víceřádkového ovládacího prvku TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a6885a594e5fcd747f85dedf1afbd39ec644717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="25746-102">Postupy: Vytvoření víceřádkového ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="25746-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="25746-103">Tento příklad ukazuje, jak používat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládací prvek, který bude automaticky rozšířit, aby odpovídala více řádků textu.</span><span class="sxs-lookup"><span data-stu-id="25746-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25746-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="25746-104">Example</span></span>  
 <span data-ttu-id="25746-105">Nastavení <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atribut **zabalení** způsobí, že zadané text jej do nového řádku při okraji <xref:System.Windows.Controls.TextBox> ovládací prvek je dosaženo, automaticky se zvětšující <xref:System.Windows.Controls.TextBox> řízení zahrnout prostor pro nový řádek, pokud nezbytné.</span><span class="sxs-lookup"><span data-stu-id="25746-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="25746-106">Nastavení <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atribut **true** způsobí, že má být vložen při stisknutí klávesy NÁVRATOVÝ, znovu automaticky rozšiřování nový řádek <xref:System.Windows.Controls.TextBox> zahrnout prostor pro nový řádek, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="25746-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="25746-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Přidá posuvníku do atribut <xref:System.Windows.Controls.TextBox>tak, aby obsah <xref:System.Windows.Controls.TextBox> posunout prostřednictvím Pokud <xref:System.Windows.Controls.TextBox> rozšíří překračuje velikost rámce nebo v okně, která obklopuje ho.</span><span class="sxs-lookup"><span data-stu-id="25746-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="25746-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="25746-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="25746-109">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="25746-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="25746-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="25746-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
