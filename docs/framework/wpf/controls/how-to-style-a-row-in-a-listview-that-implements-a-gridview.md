---
title: 'Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 0c8806c399959fdc1466e0839ba469881718092b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361626"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="0fca7-102">Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView</span><span class="sxs-lookup"><span data-stu-id="0fca7-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="0fca7-103">Tento příklad ukazuje, jak nastavení stylu řádku v <xref:System.Windows.Controls.ListView> ovládací prvek, který implementuje <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> režimu.</span><span class="sxs-lookup"><span data-stu-id="0fca7-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fca7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fca7-104">Example</span></span>  
 <span data-ttu-id="0fca7-105">Můžete stylu řádku v <xref:System.Windows.Controls.ListView> ovládacího prvku tak, že nastavíte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> na <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0fca7-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="0fca7-106">Nastavit styl pro jeho položky, které jsou reprezentovány ve formě <xref:System.Windows.Controls.ListViewItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="0fca7-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="0fca7-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odkazy <xref:System.Windows.Controls.ControlTemplate> objekty, které se používají k zobrazení obsahu řádku.</span><span class="sxs-lookup"><span data-stu-id="0fca7-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="0fca7-108">Úplnou ukázku, která v následujících příkladech se extrahují z, zobrazí kolekci skladby informací uložených v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] databáze.</span><span class="sxs-lookup"><span data-stu-id="0fca7-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="0fca7-109">Skladeb v databázi obsahuje pole, hodnocení a hodnotou tohoto pole určuje způsob zobrazení řádku skladby informace.</span><span class="sxs-lookup"><span data-stu-id="0fca7-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="0fca7-110">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListViewItem> objekty, které představují skladeb v kolekci skladby.</span><span class="sxs-lookup"><span data-stu-id="0fca7-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="0fca7-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odkazy <xref:System.Windows.Controls.ControlTemplate> objekty, které určují, jak zobrazit řádek skladby informace.</span><span class="sxs-lookup"><span data-stu-id="0fca7-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="0fca7-112">Následující příklad ukazuje <xref:System.Windows.Controls.ControlTemplate> , který přidá textový řetězec `"Strongly Recommended"` na řádek.</span><span class="sxs-lookup"><span data-stu-id="0fca7-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="0fca7-113">Tato šablona odkazuje <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> a zobrazí, když skladby hodnocení má hodnotu 5 (pět).</span><span class="sxs-lookup"><span data-stu-id="0fca7-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="0fca7-114"><xref:System.Windows.Controls.ControlTemplate> Zahrnuje <xref:System.Windows.Controls.GridViewRowPresenter> objekt, který nastaví rozložení obsahu řádku ve sloupcích podle definice <xref:System.Windows.Controls.GridView> režim zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0fca7-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="0fca7-115">Následující příklad definuje <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="0fca7-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="0fca7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fca7-116">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="0fca7-117">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="0fca7-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="0fca7-118">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="0fca7-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="0fca7-119">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="0fca7-119">Styling and Templating</span></span>](styling-and-templating.md)
