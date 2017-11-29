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
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)
