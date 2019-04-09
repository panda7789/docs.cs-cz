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
# <a name="how-to-share-sizing-properties-between-grids"></a>Postupy: Sdílení vlastností změny velikosti mezi mřížkami
Tento příklad ukazuje, jak ke sdílení dat pro změnu velikosti sloupců a řádků mezi <xref:System.Windows.Controls.Grid> prvky, aby bylo možné zachovat změny velikosti konzistentní vzhledem k aplikacím.  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí dvě <xref:System.Windows.Controls.Grid> prvky jako podřízené prvky nadřazeného <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Připojené vlastnosti <xref:System.Windows.Controls.Grid> je definován v nadřazené <xref:System.Windows.Controls.DockPanel>.  
  
 V příkladu zpracovává hodnoty vlastnosti pomocí dvou <xref:System.Windows.Controls.Button> elementy; každý element představuje jednu z hodnot logická vlastnost. Když <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> je hodnota vlastnosti nastavena `true`, každý sloupec nebo řádek člen <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> sdílí informace o nastavení velikosti, bez ohledu na obsah řádku nebo sloupce.  
  
 [!code-xaml[gridIssharedsizescopeProp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 Následující příklad použití modelu code-behind zpracovává metody, která tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolává události. Tento příklad zapíše výsledky volání těchto metod na <xref:System.Windows.Controls.TextBlock> prvky, které týkající se použití metody get na výstup nové hodnoty vlastnosti jako řetězce.  
  
 [!code-csharp[gridIssharedsizescopeProp#3](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [Přehled panelů](panels-overview.md)
