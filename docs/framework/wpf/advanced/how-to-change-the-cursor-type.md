---
title: "Postupy: Změna typu kurzoru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41cd8c9cd647c7efbc4e6cf13517ed638245e51c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="c1fc1-102">Postupy: Změna typu kurzoru</span><span class="sxs-lookup"><span data-stu-id="c1fc1-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="c1fc1-103">Tento příklad ukazuje, jak změnit <xref:System.Windows.Input.Cursor> ukazatele myši pro konkrétní element a pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c1fc1-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="c1fc1-104">V tomto příkladu se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru a souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="c1fc1-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1fc1-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1fc1-105">Example</span></span>  
 <span data-ttu-id="c1fc1-106">Vytvoření uživatelského rozhraní, která se skládá z <xref:System.Windows.Controls.ComboBox> vyberte požadovanou <xref:System.Windows.Input.Cursor>, pár <xref:System.Windows.Controls.RadioButton> objekty, které chcete zjistit, zda změna kurzoru platí pro pouze jeden element či platí v celé aplikaci a <xref:System.Windows.Controls.Border> což je nový kurzor se použije pro element.</span><span class="sxs-lookup"><span data-stu-id="c1fc1-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="c1fc1-107">Následující kód za vytvoří <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obslužná rutina události, která je volána, když typ kurzoru se změnilo v <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="c1fc1-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="c1fc1-108">Příkaz switch filtry na název kurzoru a nastaví <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> který s názvem *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="c1fc1-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="c1fc1-109">Pokud změnu kurzor je nastavený na "Celou aplikaci", <xref:System.Windows.Input.Mouse.OverrideCursor%2A> je nastavena na <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1fc1-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="c1fc1-110">Vynutí kurzor změnit pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c1fc1-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="c1fc1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1fc1-111">See Also</span></span>  
 [<span data-ttu-id="c1fc1-112">Vstupní – přehled</span><span class="sxs-lookup"><span data-stu-id="c1fc1-112">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
