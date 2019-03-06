---
title: 'Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 442fff7a36a48d5df7ba9e07426e50f602cb93e8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357492"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="76cbf-102">Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView</span><span class="sxs-lookup"><span data-stu-id="76cbf-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="76cbf-103">Tento příklad ukazuje, jak změnit vzhled Přetahované <xref:System.Windows.Controls.GridViewColumnHeader> když uživatel změní pozici sloupce.</span><span class="sxs-lookup"><span data-stu-id="76cbf-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76cbf-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="76cbf-104">Example</span></span>  
 <span data-ttu-id="76cbf-105">Při přetažení záhlaví sloupce do jiného umístění v <xref:System.Windows.Controls.ListView> , která používá <xref:System.Windows.Controls.GridView> sloupec pro režim zobrazení, se přesune do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="76cbf-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="76cbf-106">Při přetahování na záhlaví sloupce, se zobrazí kromě originální kopii záhlaví s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="76cbf-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="76cbf-107">V záhlaví sloupce <xref:System.Windows.Controls.GridView> je reprezentována <xref:System.Windows.Controls.GridViewColumnHeader> objektu.</span><span class="sxs-lookup"><span data-stu-id="76cbf-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="76cbf-108">Chcete-li přizpůsobit vzhled s plovoucí desetinnou čárkou a původní záhlaví, můžete nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> upravit <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="76cbf-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="76cbf-109">Tyto <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> se použije, když <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> hodnota vlastnosti je `true` a <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> hodnota vlastnosti je <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="76cbf-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="76cbf-110">Když uživatel stiskne tlačítko myši a obsahuje při pozastavení ukazatele myši na <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> změní hodnota vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="76cbf-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="76cbf-111">Podobně, když uživatel začne operace přetažení <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> vlastnost se změní na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="76cbf-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="76cbf-112">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> změnit <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.Background%2A> barvy s plovoucí desetinnou čárkou a původní záhlaví, když uživatel přetáhne sloupce do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="76cbf-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="76cbf-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76cbf-113">See also</span></span>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="76cbf-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="76cbf-114">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="76cbf-115">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="76cbf-115">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="76cbf-116">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="76cbf-116">GridView Overview</span></span>](gridview-overview.md)
