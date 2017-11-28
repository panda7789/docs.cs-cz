---
title: "Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 503683de875b8853e219139800eef2a5417a1574
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="d1dff-102">Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView</span><span class="sxs-lookup"><span data-stu-id="d1dff-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="d1dff-103">Tento příklad ukazuje, jak změnit vzhled taženou <xref:System.Windows.Controls.GridViewColumnHeader> když uživatel změní pozici sloupce.</span><span class="sxs-lookup"><span data-stu-id="d1dff-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1dff-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1dff-104">Example</span></span>  
 <span data-ttu-id="d1dff-105">Když přetáhněte záhlaví sloupce na jiné místo v <xref:System.Windows.Controls.ListView> používající <xref:System.Windows.Controls.GridView> sloupec pro režim zobrazení, se přesune do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="d1dff-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="d1dff-106">Při přetahování na záhlaví sloupce, zobrazí se plovoucí kopie záhlaví kromě původní hlavičku.</span><span class="sxs-lookup"><span data-stu-id="d1dff-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="d1dff-107">V záhlaví sloupce <xref:System.Windows.Controls.GridView> je reprezentována <xref:System.Windows.Controls.GridViewColumnHeader> objektu.</span><span class="sxs-lookup"><span data-stu-id="d1dff-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="d1dff-108">Chcete-li přizpůsobit vzhled plovoucí a původní hlavičky, můžete nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> změnit <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="d1dff-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="d1dff-109">Tyto <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> se použijí při <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> hodnota vlastnosti je `true` a <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> hodnota vlastnosti je <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="d1dff-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="d1dff-110">Když uživatel tlačítka myši a obsahuje, zatímco myši pozastaví na <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> hodnotu vlastnosti změny `true`.</span><span class="sxs-lookup"><span data-stu-id="d1dff-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="d1dff-111">Podobně když uživatel zahájí operaci přetažení <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> změny vlastností do <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="d1dff-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="d1dff-112">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> změnit <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.Background%2A> barvy původní a plovoucí hlaviček, když uživatel nastavuje tažením sloupce do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="d1dff-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="d1dff-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1dff-113">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="d1dff-114">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="d1dff-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="d1dff-115">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="d1dff-115">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="d1dff-116">Rutina GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="d1dff-116">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
