---
title: "Postupy: Sdílení vlastností změny velikosti mezi mřížkami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0e3be0a0b550f6fbbc9876709094d4a23abe1a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="f9a26-102">Postupy: Sdílení vlastností změny velikosti mezi mřížkami</span><span class="sxs-lookup"><span data-stu-id="f9a26-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="f9a26-103">Tento příklad ukazuje, jak sdílet data velikosti sloupců a řádků mezi <xref:System.Windows.Controls.Grid> elementy, aby bylo možné zachovat dimenzování konzistentní.</span><span class="sxs-lookup"><span data-stu-id="f9a26-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9a26-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9a26-104">Example</span></span>  
 <span data-ttu-id="f9a26-105">Následující příklad uvádí dva <xref:System.Windows.Controls.Grid> elementy jako podřízené prvky nadřazený <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="f9a26-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="f9a26-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Připojené vlastnost <xref:System.Windows.Controls.Grid> je definovaný v nadřazené <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="f9a26-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="f9a26-107">V příkladu manipuluje hodnotu vlastnosti s použitím dvou <xref:System.Windows.Controls.Button> elementy; každý element představuje jeden z hodnot vlastnost typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="f9a26-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="f9a26-108">Když <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> je hodnota vlastnosti nastavena `true`, každý sloupec nebo řádek člen <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> sdílí informace o nastavení velikosti, bez ohledu na obsah sloupce či řádku.</span><span class="sxs-lookup"><span data-stu-id="f9a26-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="f9a26-109">...</span><span class="sxs-lookup"><span data-stu-id="f9a26-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="f9a26-110">Následující příklad kódu zpracovává metody, tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="f9a26-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="f9a26-111">V příkladu je zapsán výsledky těchto volání metody <xref:System.Windows.Controls.TextBlock> prvky, které používá související získat metody pro výstup nové hodnoty vlastností jako řetězce.</span><span class="sxs-lookup"><span data-stu-id="f9a26-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f9a26-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9a26-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [<span data-ttu-id="f9a26-113">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="f9a26-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
