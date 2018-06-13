---
title: 'Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552949"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="a299e-102">Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="a299e-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="a299e-103">Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> události spuštění metody vždy, když text v <xref:System.Windows.Controls.TextBox> došlo ke změně ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a299e-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="a299e-104">Ve třídě kódu pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahující <xref:System.Windows.Controls.TextBox> vložit ovládací prvek, který chcete monitorovat změny, metoda k volání vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="a299e-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="a299e-105">Tato metoda musí mít podpis, který odpovídá očekávané pomocí <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="a299e-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="a299e-106">Je volána obslužná rutina události vždy, když obsah <xref:System.Windows.Controls.TextBox> řízení se změní, uživatelem nebo prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="a299e-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="a299e-107">**Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> řízení se vytvoří a zpočátku zobrazí s textem.</span><span class="sxs-lookup"><span data-stu-id="a299e-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a299e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a299e-108">Example</span></span>  
 <span data-ttu-id="a299e-109">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který definuje váš <xref:System.Windows.Controls.TextBox> řídit, zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributu s hodnotou, která odpovídá názvu metoda obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="a299e-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="a299e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a299e-110">Example</span></span>  
 <span data-ttu-id="a299e-111">Ve třídě kódu pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahující <xref:System.Windows.Controls.TextBox> vložit ovládací prvek, který chcete monitorovat změny, metoda k volání vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="a299e-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="a299e-112">Tato metoda musí mít podpis, který odpovídá očekávané pomocí <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="a299e-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="a299e-113">Je volána obslužná rutina události vždy, když obsah <xref:System.Windows.Controls.TextBox> řízení se změní, uživatelem nebo prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="a299e-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="a299e-114">**Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> řízení se vytvoří a zpočátku zobrazí s textem.</span><span class="sxs-lookup"><span data-stu-id="a299e-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="a299e-115">Komentáře</span><span class="sxs-lookup"><span data-stu-id="a299e-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a299e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a299e-116">See Also</span></span>  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [<span data-ttu-id="a299e-117">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="a299e-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="a299e-118">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="a299e-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
