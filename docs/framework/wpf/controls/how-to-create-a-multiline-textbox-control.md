---
title: 'Postupy: Vytvoření víceřádkového ovládacího prvku TextBox'
description: Naučte se používat XAML k definování ovládacího prvku TextBox, který se rozbalí, aby odpovídal více řádkům textu v aplikaci Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166247"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="a1b81-103">Postupy: Vytvoření víceřádkového ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="a1b81-103">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="a1b81-104">Tento příklad ukazuje, jak použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládacího prvku, který se automaticky rozbalí, aby odpovídal více řádkům textu.</span><span class="sxs-lookup"><span data-stu-id="a1b81-104">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1b81-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1b81-105">Example</span></span>  
 <span data-ttu-id="a1b81-106">Nastavením <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributu pro **zabalení** dojde k zabalení zadaného textu do nového řádku, pokud <xref:System.Windows.Controls.TextBox> je dosaženo okraje ovládacího prvku, automatické rozšíření <xref:System.Windows.Controls.TextBox> ovládacího prvku tak, aby v případě potřeby zahrnoval prostor pro nový řádek.</span><span class="sxs-lookup"><span data-stu-id="a1b81-106">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="a1b81-107">Nastavením <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributu na **hodnotu true** dojde k vložení nového řádku při stisknutí návratového klíče, jakmile se znovu automaticky rozbalí, <xref:System.Windows.Controls.TextBox> aby obsahovalo místo pro nový řádek (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="a1b81-107">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="a1b81-108"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>Atribut přidá posuvník do <xref:System.Windows.Controls.TextBox> , aby bylo možné obsah ovládacího panelu Procházet, <xref:System.Windows.Controls.TextBox> Pokud se <xref:System.Windows.Controls.TextBox> rozšíří nad rámec velikosti rámce nebo okna, které ho obklopuje.</span><span class="sxs-lookup"><span data-stu-id="a1b81-108">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="a1b81-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1b81-109">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="a1b81-110">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="a1b81-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="a1b81-111">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="a1b81-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
