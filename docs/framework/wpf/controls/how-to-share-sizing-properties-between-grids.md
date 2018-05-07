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
ms.openlocfilehash: a85c0c36ef99e6501afddaca7f26acd2928da1ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-share-sizing-properties-between-grids"></a>Postupy: Sdílení vlastností změny velikosti mezi mřížkami
Tento příklad ukazuje, jak sdílet data velikosti sloupců a řádků mezi <xref:System.Windows.Controls.Grid> elementy, aby bylo možné zachovat dimenzování konzistentní.  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí dva <xref:System.Windows.Controls.Grid> elementy jako podřízené prvky nadřazený <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Připojené vlastnost <xref:System.Windows.Controls.Grid> je definovaný v nadřazené <xref:System.Windows.Controls.DockPanel>.  
  
 V příkladu manipuluje hodnotu vlastnosti s použitím dvou <xref:System.Windows.Controls.Button> elementy; každý element představuje jeden z hodnot vlastnost typu Boolean. Když <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> je hodnota vlastnosti nastavena `true`, každý sloupec nebo řádek člen <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> sdílí informace o nastavení velikosti, bez ohledu na obsah sloupce či řádku.  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 Následující příklad kódu zpracovává metody, tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolá událost. V příkladu je zapsán výsledky těchto volání metody <xref:System.Windows.Controls.TextBlock> prvky, které používá související získat metody pro výstup nové hodnoty vlastností jako řetězce.  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
