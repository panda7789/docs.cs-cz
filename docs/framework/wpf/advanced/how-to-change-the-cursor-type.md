---
title: 'Postupy: Změna typu kurzoru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 2330cdd3be35dc4e4b555db6401dd55d9946ed1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745048"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="a6353-102">Postupy: Změna typu kurzoru</span><span class="sxs-lookup"><span data-stu-id="a6353-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="a6353-103">Tento příklad ukazuje, jak změnit <xref:System.Windows.Input.Cursor> ukazatele myši pro konkrétní elementu a pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a6353-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="a6353-104">Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="a6353-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6353-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6353-105">Example</span></span>  
 <span data-ttu-id="a6353-106">Vytvoření uživatelského rozhraní, která se skládá z <xref:System.Windows.Controls.ComboBox> vyberte požadovaný <xref:System.Windows.Input.Cursor>, dvojici <xref:System.Windows.Controls.RadioButton> objekty určují, jestli změna kurzor platí pro pouze jeden element nebo platí pro celou aplikaci a <xref:System.Windows.Controls.Border> což je element, který se použije nový ukazatel na.</span><span class="sxs-lookup"><span data-stu-id="a6353-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="a6353-107">Následující kód vytvoří <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obslužná rutina události, která je volána, když typ kurzoru se změní v <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="a6353-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="a6353-108">Příkaz switch filtry na název kurzoru a nastaví <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> který se nazývá *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="a6353-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="a6353-109">Pokud změna kurzoru je nastavená na "Celou aplikaci" <xref:System.Windows.Input.Mouse.OverrideCursor%2A> je nastavena na <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a6353-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="a6353-110">To přinutí kurzor, chcete-li změnit pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a6353-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="a6353-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6353-111">See also</span></span>
- [<span data-ttu-id="a6353-112">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="a6353-112">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
