---
title: 'Postupy: Změna velikosti plátna použitím jezdce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: c3e7176b0578c8fdc5f4331ad8f3b464f3a88b51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555061"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="6821b-102">Postupy: Změna velikosti plátna použitím jezdce</span><span class="sxs-lookup"><span data-stu-id="6821b-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="6821b-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Controls.Primitives.Thumb> řízení ke změně velikosti <xref:System.Windows.Controls.Canvas> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6821b-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6821b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6821b-104">Example</span></span>  
 <span data-ttu-id="6821b-105"><xref:System.Windows.Controls.Primitives.Thumb> Řízení poskytuje přetažení funkce, které slouží k přesunutí nebo změna velikosti ovládacích prvků pomocí monitorování <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> události <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="6821b-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="6821b-106">Uživatel začne operaci přetažení stisknutím levé tlačítko myši, když ukazatel myši je pozastaven na <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6821b-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="6821b-107">Operaci přetažení pokračuje tak dlouho, dokud zůstává levé tlačítko myši stisknuté.</span><span class="sxs-lookup"><span data-stu-id="6821b-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="6821b-108">Během operace tažení <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> může dojít, více než jednou.</span><span class="sxs-lookup"><span data-stu-id="6821b-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="6821b-109">Pokaždé, když k ní dojde, <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> třída poskytuje změnu v hodnotě pozice, který odpovídá změnu v pozici myši.</span><span class="sxs-lookup"><span data-stu-id="6821b-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="6821b-110">Když uživatel uvolní levé tlačítko myši, dokončení operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="6821b-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="6821b-111">Operaci přetažení pouze poskytuje nové souřadnice; není automaticky přemístit <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="6821b-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="6821b-112">Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb> prvek, který je o podřízený prvek <xref:System.Windows.Controls.Canvas> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6821b-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="6821b-113">Obslužné rutiny události pro jeho <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> událostí obsahuje logiku pro přesun <xref:System.Windows.Controls.Primitives.Thumb> a změňte velikost <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="6821b-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="6821b-114">Obslužné rutiny událostí <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> událostí Změna barvy <xref:System.Windows.Controls.Primitives.Thumb> během operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="6821b-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="6821b-115">V následujícím příkladu je definován <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="6821b-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="6821b-116">Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> obslužné rutiny události, která přemísťuje <xref:System.Windows.Controls.Primitives.Thumb> a změní <xref:System.Windows.Controls.Canvas> v reakci na pohybu myši.</span><span class="sxs-lookup"><span data-stu-id="6821b-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="6821b-117">Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6821b-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="6821b-118">Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6821b-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="6821b-119">Kompletní příklad, najdete v části [jezdec přetažení funkce ukázka](http://go.microsoft.com/fwlink/?LinkID=160042).</span><span class="sxs-lookup"><span data-stu-id="6821b-119">For the complete sample, see [Thumb Drag Functionality Sample](http://go.microsoft.com/fwlink/?LinkID=160042).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6821b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6821b-120">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
