---
title: 'Postupy: Použití šablon na styl ListView používající GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: baef8bdee73d8493ba406f5eef1e3e3676680704
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355763"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="cde7f-102">Postupy: Použití šablon na styl ListView používající GridView</span><span class="sxs-lookup"><span data-stu-id="cde7f-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="cde7f-103">Tento příklad ukazuje způsob použití <xref:System.Windows.DataTemplate> a <xref:System.Windows.Style> objekty k určení vzhledu <xref:System.Windows.Controls.ListView> ovládací prvek, který se používá <xref:System.Windows.Controls.GridView> režim zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cde7f-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cde7f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cde7f-104">Example</span></span>  
 <span data-ttu-id="cde7f-105">Následující příklady ukazují <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty, které přizpůsobit vzhled pro záhlaví sloupce <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="cde7f-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="cde7f-106">Následující příklad ukazuje, jak pomocí nich <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty nastavit <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> vlastnosti <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="cde7f-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="cde7f-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Vlastnost definuje obsah buňky sloupce.</span><span class="sxs-lookup"><span data-stu-id="cde7f-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="cde7f-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> jsou jenom dvě několik vlastností, které můžete použít k přizpůsobení vzhledu záhlaví sloupce <xref:System.Windows.Controls.GridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cde7f-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="cde7f-109">Další informace najdete v tématu [GridView styly záhlaví sloupců a Přehled šablon](gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cde7f-109">For more information, see [GridView Column Header Styles and Templates Overview](gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="cde7f-110">Následující příklad ukazuje, jak definovat <xref:System.Windows.DataTemplate> , který přizpůsobí vzhledu buněk v <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="cde7f-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="cde7f-111">Následující příklad ukazuje, jak pomocí tohoto <xref:System.Windows.DataTemplate> definovat obsah <xref:System.Windows.Controls.GridViewColumn> buňky.</span><span class="sxs-lookup"><span data-stu-id="cde7f-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="cde7f-112">Tato šablona se používá namísto <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnost, která se zobrazí v předchozím <xref:System.Windows.Controls.GridViewColumn> příklad.</span><span class="sxs-lookup"><span data-stu-id="cde7f-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="cde7f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cde7f-113">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="cde7f-114">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="cde7f-114">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="cde7f-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="cde7f-115">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="cde7f-116">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="cde7f-116">ListView Overview</span></span>](listview-overview.md)
