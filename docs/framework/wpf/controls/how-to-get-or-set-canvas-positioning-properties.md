---
title: 'Postupy: Načtení nebo nastavení vlastnosti umístění plátna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 294b49d427a67da849ce930cf29a48f1735bf135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551977"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a><span data-ttu-id="6099b-102">Postupy: Načtení nebo nastavení vlastnosti umístění plátna</span><span class="sxs-lookup"><span data-stu-id="6099b-102">How to: Get or Set Canvas Positioning Properties</span></span>
<span data-ttu-id="6099b-103">Tento příklad ukazuje, jak používat umísťovací metody třídy <xref:System.Windows.Controls.Canvas> element na pozici podřízené obsah.</span><span class="sxs-lookup"><span data-stu-id="6099b-103">This example shows how to use the positioning methods of the <xref:System.Windows.Controls.Canvas> element to position child content.</span></span> <span data-ttu-id="6099b-104">Tento příklad používá obsah <xref:System.Windows.Controls.ListBoxItem> představují umístění hodnoty a převede hodnoty instancí <xref:System.Double>, který je požadovaný argument pro umístění.</span><span class="sxs-lookup"><span data-stu-id="6099b-104">This example uses content in a <xref:System.Windows.Controls.ListBoxItem> to represent positioning values and converts the values into instances of <xref:System.Double>, which is a required argument for positioning.</span></span> <span data-ttu-id="6099b-105">Hodnoty jsou pak převést zpět na řetězce a zobrazí jako text v <xref:System.Windows.Controls.TextBlock> element pomocí <xref:System.Windows.Controls.Canvas.GetLeft%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6099b-105">The values are then converted back into strings and displayed as text in a <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.Canvas.GetLeft%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6099b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6099b-106">Example</span></span>  
 <span data-ttu-id="6099b-107">Následující příklad vytvoří <xref:System.Windows.Controls.ListBox> element, který má jedenáct volitelný <xref:System.Windows.Controls.ListBoxItem> elementy.</span><span class="sxs-lookup"><span data-stu-id="6099b-107">The following example creates a <xref:System.Windows.Controls.ListBox> element that has eleven selectable <xref:System.Windows.Controls.ListBoxItem> elements.</span></span> <span data-ttu-id="6099b-108"><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Aktivačních událostí `ChangeLeft` vlastní metodu, která definuje následující kód bloku.</span><span class="sxs-lookup"><span data-stu-id="6099b-108">The <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event triggers the `ChangeLeft` custom method, which the subsequent code block defines.</span></span>  
  
 <span data-ttu-id="6099b-109">Každý <xref:System.Windows.Controls.ListBoxItem> představuje <xref:System.Double> hodnotu, která je jeden z argumentů, <xref:System.Windows.Controls.Canvas.SetLeft%2A> metodu <xref:System.Windows.Controls.Canvas> přijímá.</span><span class="sxs-lookup"><span data-stu-id="6099b-109">Each <xref:System.Windows.Controls.ListBoxItem> represents a <xref:System.Double> value, which is one of the arguments that the <xref:System.Windows.Controls.Canvas.SetLeft%2A> method of <xref:System.Windows.Controls.Canvas> accepts.</span></span> <span data-ttu-id="6099b-110">Aby bylo možné používat <xref:System.Windows.Controls.ListBoxItem> představující instanci <xref:System.Double>, je nutné nejprve převést <xref:System.Windows.Controls.ListBoxItem> do správného datového typu.</span><span class="sxs-lookup"><span data-stu-id="6099b-110">In order to use a <xref:System.Windows.Controls.ListBoxItem> to represent an instance of <xref:System.Double>, you must first convert the <xref:System.Windows.Controls.ListBoxItem> to the correct data type.</span></span>  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="6099b-111">Když uživatel změní <xref:System.Windows.Controls.ListBox> výběr, vyvolá `ChangeLeft` vlastní metoda.</span><span class="sxs-lookup"><span data-stu-id="6099b-111">When a user changes the <xref:System.Windows.Controls.ListBox> selection, it invokes the `ChangeLeft` custom method.</span></span> <span data-ttu-id="6099b-112">Tato metoda předá <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.LengthConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Double> (Všimněte si, že tato hodnota již byl převeden na <xref:System.String> pomocí <xref:System.Windows.Controls.Control.ToString%2A> Metoda).</span><span class="sxs-lookup"><span data-stu-id="6099b-112">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.LengthConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double> (notice that this value has already been converted to a <xref:System.String> by using the <xref:System.Windows.Controls.Control.ToString%2A> method).</span></span> <span data-ttu-id="6099b-113">Tato hodnota je předána zpět <xref:System.Windows.Controls.Canvas.SetLeft%2A> a <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody <xref:System.Windows.Controls.Canvas> Chcete-li změnit umístění `text1` objektu.</span><span class="sxs-lookup"><span data-stu-id="6099b-113">This value is then passed back to the <xref:System.Windows.Controls.Canvas.SetLeft%2A> and <xref:System.Windows.Controls.Canvas.GetLeft%2A> methods of <xref:System.Windows.Controls.Canvas> in order to change the position of the `text1` object.</span></span>  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6099b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6099b-114">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [<span data-ttu-id="6099b-115">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="6099b-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
