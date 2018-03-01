---
title: "Postupy: Použití šablon na styl ListView používající GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9abc19ca14cf512deff898f5f20d23870b8b7847
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="80f42-102">Postupy: Použití šablon na styl ListView používající GridView</span><span class="sxs-lookup"><span data-stu-id="80f42-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="80f42-103">Tento příklad ukazuje způsob použití <xref:System.Windows.DataTemplate> a <xref:System.Windows.Style> objekty, které chcete určit vzhled <xref:System.Windows.Controls.ListView> ovládací prvek, který používá <xref:System.Windows.Controls.GridView> režimu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="80f42-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80f42-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="80f42-104">Example</span></span>  
 <span data-ttu-id="80f42-105">Následující příklady zobrazují <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty, které přizpůsobení vzhledu záhlaví sloupce <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="80f42-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="80f42-106">Následující příklad ukazuje, jak použít <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty, které chcete nastavit <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> vlastnosti <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="80f42-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="80f42-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Vlastnost definuje obsah buňky sloupců.</span><span class="sxs-lookup"><span data-stu-id="80f42-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="80f42-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> jsou pouze dvě několik vlastností, které můžete použít k přizpůsobení vzhledu záhlaví sloupců pro <xref:System.Windows.Controls.GridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80f42-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="80f42-109">Další informace najdete v tématu [GridView styly záhlaví sloupců a Přehled šablon](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="80f42-109">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="80f42-110">Následující příklad ukazuje, jak definovat <xref:System.Windows.DataTemplate> , přizpůsobení vzhledu buněk v <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="80f42-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="80f42-111">Následující příklad ukazuje, jak použít <xref:System.Windows.DataTemplate> definovat obsah <xref:System.Windows.Controls.GridViewColumn> buňky.</span><span class="sxs-lookup"><span data-stu-id="80f42-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="80f42-112">Tato šablona se používá namísto <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnosti, které se zobrazí v předchozí <xref:System.Windows.Controls.GridViewColumn> příklad.</span><span class="sxs-lookup"><span data-stu-id="80f42-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="80f42-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="80f42-113">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="80f42-114">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="80f42-114">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="80f42-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="80f42-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="80f42-116">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="80f42-116">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
