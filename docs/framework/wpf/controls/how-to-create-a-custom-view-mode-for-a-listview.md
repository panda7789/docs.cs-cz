---
title: 'Postupy: Vytvoření vlastního režimu zobrazení pro ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 239fb2e9a364bd0265ff7cf644ee296878280cf3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561692"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="e36f1-102">Postupy: Vytvoření vlastního režimu zobrazení pro ListView</span><span class="sxs-lookup"><span data-stu-id="e36f1-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="e36f1-103">Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Windows.Controls.ListView.View%2A> režim <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e36f1-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e36f1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e36f1-104">Example</span></span>  
 <span data-ttu-id="e36f1-105">Je nutné použít <xref:System.Windows.Controls.ViewBase> třídy při vytvoření vlastního zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e36f1-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="e36f1-106">Následující příklad ukazuje režim zobrazení, která je volána `PlainView`, který je odvozen z <xref:System.Windows.Controls.ViewBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="e36f1-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="e36f1-107">Chcete-li použít styl na vlastní zobrazení, použijte <xref:System.Windows.Style> třídy.</span><span class="sxs-lookup"><span data-stu-id="e36f1-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="e36f1-108">Následující příklad definuje <xref:System.Windows.Style> pro `PlainView` režim zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e36f1-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="e36f1-109">V předchozím příkladu je tímto stylem nastavena jako hodnota <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> vlastnost, která je definována pro `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="e36f1-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="e36f1-110">Chcete-li definovat rozložení dat vlastního režimu zobrazení, definujte <xref:System.Windows.DataTemplate> objektu.</span><span class="sxs-lookup"><span data-stu-id="e36f1-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="e36f1-111">Následující příklad definuje <xref:System.Windows.DataTemplate> , který slouží k zobrazení dat v `PlainView` režim zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e36f1-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="e36f1-112">Následující příklad ukazuje, jak definovat <xref:System.Windows.ResourceKey> pro `PlainView` režim zobrazení, která používá <xref:System.Windows.DataTemplate> , která je definována v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e36f1-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="e36f1-113">A <xref:System.Windows.Controls.ListView> ovládací prvek lze použít vlastní zobrazení, pokud jste nastavili <xref:System.Windows.Controls.ListView.View%2A> vlastnost klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="e36f1-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="e36f1-114">Následující příklad ukazuje, jak určit `PlainView` jako režim zobrazení <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="e36f1-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="e36f1-115">Úplnou ukázku najdete v tématu [ListView s ukázkou více zobrazení](https://go.microsoft.com/fwlink/?LinkID=160013).</span><span class="sxs-lookup"><span data-stu-id="e36f1-115">For the complete sample, see [ListView with Multiple Views Sample](https://go.microsoft.com/fwlink/?LinkID=160013).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36f1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e36f1-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="e36f1-117">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e36f1-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="e36f1-118">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="e36f1-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="e36f1-119">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="e36f1-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
