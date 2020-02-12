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
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124296"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="2c1e1-102">Postupy: Změna velikosti plátna použitím jezdce</span><span class="sxs-lookup"><span data-stu-id="2c1e1-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="2c1e1-103">Tento příklad ukazuje, jak použít ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb> pro změnu velikosti ovládacího prvku <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c1e1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c1e1-104">Example</span></span>  
 <span data-ttu-id="2c1e1-105">Ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb> poskytuje funkce přetažení, které lze použít k přesunutí nebo změně velikosti ovládacích prvků monitorováním <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> událostí <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="2c1e1-106">Uživatel zahájí operaci přetažení stisknutím levého tlačítka myši, když je ukazatel myši pozastaven na ovládacím prvku <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="2c1e1-107">Operace přetažení bude pokračovat, dokud nebude stisknuto levé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="2c1e1-108">Během operace přetažení může <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> probíhat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="2c1e1-109">Pokaždé, když k tomu dojde, třída <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> poskytuje změnu pozice, která odpovídá změně pozice myši.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="2c1e1-110">Když uživatel uvolní levé tlačítko myši, operace přetažení se dokončí.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="2c1e1-111">Operace přetažení poskytuje pouze nové souřadnice; nemění automaticky umístění <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="2c1e1-112">Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb> ovládací prvek, který je podřízeným prvkem <xref:System.Windows.Controls.Canvas> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="2c1e1-113">Obslužná rutina události pro událost <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> poskytuje logiku pro přesunutí <xref:System.Windows.Controls.Primitives.Thumb> a změnu velikosti <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2c1e1-114">Obslužné rutiny události pro událost <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> a <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> mění barvu <xref:System.Windows.Controls.Primitives.Thumb> během operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="2c1e1-115">Následující příklad definuje <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="2c1e1-116">Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> obslužnou rutinu události, která přesouvá <xref:System.Windows.Controls.Primitives.Thumb> a mění velikost <xref:System.Windows.Controls.Canvas> v reakci na pohyb myši.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="2c1e1-117">Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="2c1e1-118">Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.</span><span class="sxs-lookup"><span data-stu-id="2c1e1-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="2c1e1-119">Úplnou ukázku najdete v tématu [Ukázka funkcionality přetažení jezdce](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span><span class="sxs-lookup"><span data-stu-id="2c1e1-119">For the complete sample, see [Thumb Drag Functionality Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1e1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c1e1-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
