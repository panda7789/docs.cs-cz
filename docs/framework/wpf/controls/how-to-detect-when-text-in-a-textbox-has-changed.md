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
ms.openlocfilehash: 72441e53d21df47d34a0600dafdf0b4b04c11cad
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352370"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="2035c-102">Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="2035c-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="2035c-103">Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> události a metody pokaždé, když se text v <xref:System.Windows.Controls.TextBox> ovládacího prvku se změnil.</span><span class="sxs-lookup"><span data-stu-id="2035c-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="2035c-104">Ve třídě použití modelu code-behind pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , která obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat změny vložit metodu volat pokaždé, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> dojde k aktivaci události.</span><span class="sxs-lookup"><span data-stu-id="2035c-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="2035c-105">Tato metoda musí mít podpis, který odpovídá očekávání podle <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="2035c-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="2035c-106">Obslužná rutina události je volána pokaždé, když obsah <xref:System.Windows.Controls.TextBox> změní ovládacího prvku, uživatelem nebo prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="2035c-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="2035c-107">**Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> ovládacího prvku je vytvořen a zpočátku zobrazí s textem.</span><span class="sxs-lookup"><span data-stu-id="2035c-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2035c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2035c-108">Example</span></span>  
 <span data-ttu-id="2035c-109">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který definuje vaši <xref:System.Windows.Controls.TextBox> řídit, zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributu s hodnotou, která odpovídá názvu metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="2035c-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="2035c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2035c-110">Example</span></span>  
 <span data-ttu-id="2035c-111">Ve třídě použití modelu code-behind pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , která obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat změny vložit metodu volat pokaždé, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> dojde k aktivaci události.</span><span class="sxs-lookup"><span data-stu-id="2035c-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="2035c-112">Tato metoda musí mít podpis, který odpovídá očekávání podle <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="2035c-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="2035c-113">Obslužná rutina události je volána pokaždé, když obsah <xref:System.Windows.Controls.TextBox> změní ovládacího prvku, uživatelem nebo prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="2035c-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="2035c-114">**Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> ovládacího prvku je vytvořen a zpočátku zobrazí s textem.</span><span class="sxs-lookup"><span data-stu-id="2035c-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="2035c-115">Komentáře</span><span class="sxs-lookup"><span data-stu-id="2035c-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2035c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2035c-116">See also</span></span>
- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="2035c-117">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="2035c-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="2035c-118">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="2035c-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
