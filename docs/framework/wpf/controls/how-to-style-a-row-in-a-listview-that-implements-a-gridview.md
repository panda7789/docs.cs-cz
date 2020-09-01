---
title: 'Postupy: nastavení stylu řádku v zobrazení ListView s použitím prvku GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271942"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="1be28-102">Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView</span><span class="sxs-lookup"><span data-stu-id="1be28-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="1be28-103">Tento příklad ukazuje, jak stylovat řádek v <xref:System.Windows.Controls.ListView> ovládacím prvku, který používá <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> režim.</span><span class="sxs-lookup"><span data-stu-id="1be28-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1be28-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1be28-104">Example</span></span>  
 <span data-ttu-id="1be28-105">Můžete nastavit styl řádku v <xref:System.Windows.Controls.ListView> ovládacím prvku nastavením <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1be28-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="1be28-106">Nastavte styl pro položky, které jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="1be28-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="1be28-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>Odkazuje na <xref:System.Windows.Controls.ControlTemplate> objekty, které se používají k zobrazení obsahu řádku.</span><span class="sxs-lookup"><span data-stu-id="1be28-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="1be28-108">Kompletní ukázka, z níž jsou extrahovány následující příklady, zobrazuje kolekci informací o skladbách, které jsou uloženy v databázi XML.</span><span class="sxs-lookup"><span data-stu-id="1be28-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an XML database.</span></span> <span data-ttu-id="1be28-109">Každá skladba v databázi má pole hodnocení a hodnota tohoto pole určuje, jak se má zobrazit řádek informací o skladbě.</span><span class="sxs-lookup"><span data-stu-id="1be28-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="1be28-110">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListViewItem> objekty, které reprezentují skladby v kolekci song.</span><span class="sxs-lookup"><span data-stu-id="1be28-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="1be28-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>Odkazuje na <xref:System.Windows.Controls.ControlTemplate> objekty, které určují, jak se má zobrazit řádek informací o skladbě.</span><span class="sxs-lookup"><span data-stu-id="1be28-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="1be28-112">Následující příklad ukazuje <xref:System.Windows.Controls.ControlTemplate> , který přidá textový řetězec `"Strongly Recommended"` na řádek.</span><span class="sxs-lookup"><span data-stu-id="1be28-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="1be28-113">Na tuto šablonu odkazuje v <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> a se zobrazí, když má hodnocení skladby hodnotu 5 (pět).</span><span class="sxs-lookup"><span data-stu-id="1be28-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="1be28-114"><xref:System.Windows.Controls.ControlTemplate>Obsahuje <xref:System.Windows.Controls.GridViewRowPresenter> objekt, který rozloží obsah řádku ve sloupcích definovaných <xref:System.Windows.Controls.GridView> režimem zobrazení.</span><span class="sxs-lookup"><span data-stu-id="1be28-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="1be28-115">Následující příklad definuje <xref:System.Windows.Controls.GridView> .</span><span class="sxs-lookup"><span data-stu-id="1be28-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="1be28-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1be28-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="1be28-117">– postupy</span><span class="sxs-lookup"><span data-stu-id="1be28-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="1be28-118">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="1be28-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="1be28-119">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1be28-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
