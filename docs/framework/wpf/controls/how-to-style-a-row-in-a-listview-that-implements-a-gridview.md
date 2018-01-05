---
title: "Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e37d70fe1cb6aefb1404424c1a8f5339e0badf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="9e003-102">Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView</span><span class="sxs-lookup"><span data-stu-id="9e003-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="9e003-103">Tento příklad ukazuje, jak k úpravě stylu řádku <xref:System.Windows.Controls.ListView> ovládací prvek, který implementuje <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> režimu.</span><span class="sxs-lookup"><span data-stu-id="9e003-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e003-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e003-104">Example</span></span>  
 <span data-ttu-id="9e003-105">Můžete styl řádku <xref:System.Windows.Controls.ListView> ovládací prvek pro nastavení <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> na <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9e003-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="9e003-106">Nastavení stylu pro jeho položky, které jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="9e003-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="9e003-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odkazy <xref:System.Windows.Controls.ControlTemplate> objekty, které se používají k zobrazení obsahu řádek.</span><span class="sxs-lookup"><span data-stu-id="9e003-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="9e003-108">Je kompletní ukázka v následujících příkladech se extrahují z, zobrazí kolekce skladbu informací, které jsou uloženy v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] databáze.</span><span class="sxs-lookup"><span data-stu-id="9e003-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="9e003-109">Skladeb v databázi obsahuje pole, hodnocení a hodnotu tohoto pole určuje způsob zobrazení řádek skladbu informace.</span><span class="sxs-lookup"><span data-stu-id="9e003-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="9e003-110">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListViewItem> objekty, které představují skladeb v kolekci skladbu.</span><span class="sxs-lookup"><span data-stu-id="9e003-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="9e003-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odkazy <xref:System.Windows.Controls.ControlTemplate> objekty, které určují, jak zobrazit řádek skladbu informace.</span><span class="sxs-lookup"><span data-stu-id="9e003-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="9e003-112">Následující příklad ukazuje <xref:System.Windows.Controls.ControlTemplate> doplňuje textový řetězec `"Strongly Recommended"` na řádek.</span><span class="sxs-lookup"><span data-stu-id="9e003-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="9e003-113">Tato šablona odkazuje <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> a zobrazí, když na skladbu hodnocení má hodnotu 5 (5).</span><span class="sxs-lookup"><span data-stu-id="9e003-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="9e003-114"><xref:System.Windows.Controls.ControlTemplate> Zahrnuje <xref:System.Windows.Controls.GridViewRowPresenter> objekt, který nastaví rozložení obsahu řádku ve sloupcích podle definice <xref:System.Windows.Controls.GridView> režimu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9e003-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="9e003-115">V následujícím příkladu definuje <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="9e003-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="9e003-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e003-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="9e003-117">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="9e003-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="9e003-118">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="9e003-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="9e003-119">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9e003-119">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
