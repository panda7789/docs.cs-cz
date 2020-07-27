---
title: 'Postupy: Změna typu kurzoru'
description: Změní kurzor ukazatele myši u prvku a pro aplikaci v Windows Presentation Foundation. Tento příklad se skládá z XAML a souboru kódu na pozadí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165969"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="230d9-104">Postupy: Změna typu kurzoru</span><span class="sxs-lookup"><span data-stu-id="230d9-104">How to: Change the Cursor Type</span></span>
<span data-ttu-id="230d9-105">Tento příklad ukazuje, jak změnit <xref:System.Windows.Input.Cursor> ukazatel myši pro určitý element a pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="230d9-105">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="230d9-106">Tento příklad se skládá ze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru a souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="230d9-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="230d9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="230d9-107">Example</span></span>  
 <span data-ttu-id="230d9-108">Uživatelské rozhraní je vytvořeno, což se skládá z a <xref:System.Windows.Controls.ComboBox> vybrat požadovanou <xref:System.Windows.Input.Cursor> dvojici <xref:System.Windows.Controls.RadioButton> objektů k určení, zda se Změna kurzoru vztahuje pouze na jeden prvek nebo platí pro celou aplikaci, a <xref:System.Windows.Controls.Border> prvek, který je prvkem, na který je nový kurzor aplikován.</span><span class="sxs-lookup"><span data-stu-id="230d9-108">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="230d9-109">Následující kód vytvoří <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obslužnou rutinu události, která je volána při změně typu kurzoru v <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="230d9-109">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="230d9-110">Příkaz přepíná filtry na název kurzoru a nastavuje vlastnost s <xref:System.Windows.FrameworkElement.Cursor%2A> <xref:System.Windows.Controls.Border> názvem *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="230d9-110">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="230d9-111">Pokud je Změna kurzoru nastavena na "celá aplikace", <xref:System.Windows.Input.Mouse.OverrideCursor%2A> vlastnost je nastavena na <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="230d9-111">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="230d9-112">To vynutí změnu kurzoru pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="230d9-112">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="230d9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="230d9-113">See also</span></span>

- [<span data-ttu-id="230d9-114">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="230d9-114">Input Overview</span></span>](input-overview.md)
