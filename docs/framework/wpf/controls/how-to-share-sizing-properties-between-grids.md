---
title: 'Postupy: Sdílení vlastností změny velikosti mezi mřížkami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: d5ab2ac612d55c8cbc34ae6d7d9d63b9f8aa23e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190337"
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="b08ab-102">Postupy: Sdílení vlastností změny velikosti mezi mřížkami</span><span class="sxs-lookup"><span data-stu-id="b08ab-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="b08ab-103">Tento příklad ukazuje, jak ke sdílení dat pro změnu velikosti sloupců a řádků mezi <xref:System.Windows.Controls.Grid> prvky, aby bylo možné zachovat změny velikosti konzistentní vzhledem k aplikacím.</span><span class="sxs-lookup"><span data-stu-id="b08ab-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b08ab-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b08ab-104">Example</span></span>  
 <span data-ttu-id="b08ab-105">Následující příklad uvádí dvě <xref:System.Windows.Controls.Grid> prvky jako podřízené prvky nadřazeného <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="b08ab-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="b08ab-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Připojené vlastnosti <xref:System.Windows.Controls.Grid> je definován v nadřazené <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="b08ab-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="b08ab-107">V příkladu zpracovává hodnoty vlastnosti pomocí dvou <xref:System.Windows.Controls.Button> elementy; každý element představuje jednu z hodnot logická vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b08ab-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="b08ab-108">Když <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> je hodnota vlastnosti nastavena `true`, každý sloupec nebo řádek člen <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> sdílí informace o nastavení velikosti, bez ohledu na obsah řádku nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="b08ab-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="b08ab-109">...</span><span class="sxs-lookup"><span data-stu-id="b08ab-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="b08ab-110">Následující příklad použití modelu code-behind zpracovává metody, která tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="b08ab-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="b08ab-111">Tento příklad zapíše výsledky volání těchto metod na <xref:System.Windows.Controls.TextBlock> prvky, které týkající se použití metody get na výstup nové hodnoty vlastnosti jako řetězce.</span><span class="sxs-lookup"><span data-stu-id="b08ab-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b08ab-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b08ab-112">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [<span data-ttu-id="b08ab-113">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="b08ab-113">Panels Overview</span></span>](panels-overview.md)
