---
title: 'Postupy: Vytvoření víceřádkového ovládacího prvku TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 29fb4c9498fe163c36e71680242d3ef8cf98c089
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181165"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="6fc90-102">Postupy: Vytvoření víceřádkového ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="6fc90-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="6fc90-103">Tento příklad ukazuje způsob použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládací prvek, který se rozbalí automaticky tak, aby vyhovovaly více řádků textu.</span><span class="sxs-lookup"><span data-stu-id="6fc90-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc90-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fc90-104">Example</span></span>  
 <span data-ttu-id="6fc90-105">Nastavení <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atribut **zabalení** způsobí, že zadaný text zabalit do nového řádku na okraj <xref:System.Windows.Controls.TextBox> ovládací prvek je dosaženo, automatické rozbalování <xref:System.Windows.Controls.TextBox> ovládacího prvku zahrnout místa pro nový řádek, pokud nezbytné.</span><span class="sxs-lookup"><span data-stu-id="6fc90-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="6fc90-106">Nastavení <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atribut **true** způsobí, že nový řádek má být vložen při stisknutí klávesy RETURN, znovu automaticky rozšiřuje <xref:System.Windows.Controls.TextBox> zahrnout místa pro nový řádek, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="6fc90-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="6fc90-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Přidá posuvník pro atribut <xref:System.Windows.Controls.TextBox>tak, aby obsah <xref:System.Windows.Controls.TextBox> posunout Pokud <xref:System.Windows.Controls.TextBox> rozbalí nad rámec velikost rámu nebo okna, který ji obklopuje.</span><span class="sxs-lookup"><span data-stu-id="6fc90-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="6fc90-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fc90-108">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="6fc90-109">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="6fc90-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="6fc90-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="6fc90-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
