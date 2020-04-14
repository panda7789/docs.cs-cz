---
title: 'Postupy: Vytvoření vlastního režimu zobrazení pro ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243216"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="21d02-102">Postup: Vytvoření vlastního režimu zobrazení pro listview</span><span class="sxs-lookup"><span data-stu-id="21d02-102">How to: Create a custom view mode for a ListView</span></span>

<span data-ttu-id="21d02-103">Tento příklad ukazuje, jak <xref:System.Windows.Controls.ListView.View%2A> vytvořit <xref:System.Windows.Controls.ListView> vlastní režim pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="21d02-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21d02-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="21d02-104">Example</span></span>  
 <span data-ttu-id="21d02-105">Třídu je <xref:System.Windows.Controls.ViewBase> nutné použít při vytváření <xref:System.Windows.Controls.ListView> vlastního zobrazení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21d02-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="21d02-106">Následující příklad ukazuje režim `PlainView` zobrazení s názvem je <xref:System.Windows.Controls.ViewBase> odvozen od třídy.</span><span class="sxs-lookup"><span data-stu-id="21d02-106">The following example shows a view mode called `PlainView` that's derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="21d02-107">Chcete-li použít styl na vlastní <xref:System.Windows.Style> zobrazení, použijte třídu.</span><span class="sxs-lookup"><span data-stu-id="21d02-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="21d02-108">Následující příklad definuje <xref:System.Windows.Style> pro `PlainView` režim zobrazení.</span><span class="sxs-lookup"><span data-stu-id="21d02-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="21d02-109">V předchozím příkladu je tento styl nastaven <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> jako hodnota vlastnosti, která je definována pro `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="21d02-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that's defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="21d02-110">Chcete-li definovat rozložení dat ve vlastním <xref:System.Windows.DataTemplate> režimu zobrazení, definujte objekt.</span><span class="sxs-lookup"><span data-stu-id="21d02-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="21d02-111">Následující příklad definuje <xref:System.Windows.DataTemplate> a, který lze použít `PlainView` k zobrazení dat v režimu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="21d02-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="21d02-112">Následující příklad ukazuje, jak <xref:System.Windows.ResourceKey> definovat `PlainView` pro režim <xref:System.Windows.DataTemplate> zobrazení, který používá, který je definován v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="21d02-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="21d02-113">Ovládací <xref:System.Windows.Controls.ListView> prvek můžete použít vlastní zobrazení, pokud nastavíte <xref:System.Windows.Controls.ListView.View%2A> vlastnost na klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="21d02-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="21d02-114">Následující příklad ukazuje, `PlainView` jak určit jako <xref:System.Windows.Controls.ListView>režim zobrazení pro .</span><span class="sxs-lookup"><span data-stu-id="21d02-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="21d02-115">Úplnou ukázku naleznete v [tématu ListView s více zobrazeními (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) nebo [ListView s více zobrazeními (Visual Basic).](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)</span><span class="sxs-lookup"><span data-stu-id="21d02-115">For the complete sample, see [ListView with Multiple Views (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d02-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="21d02-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="21d02-117">– postupy</span><span class="sxs-lookup"><span data-stu-id="21d02-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="21d02-118">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="21d02-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="21d02-119">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="21d02-119">GridView Overview</span></span>](gridview-overview.md)
