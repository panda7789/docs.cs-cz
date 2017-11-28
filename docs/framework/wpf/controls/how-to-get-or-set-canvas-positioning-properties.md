---
title: "Postupy: Načtení nebo nastavení vlastnosti umístění plátna"
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
helpviewer_keywords: Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b2f20754c8425149f73f10af773604539125adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>Postupy: Načtení nebo nastavení vlastnosti umístění plátna
Tento příklad ukazuje, jak používat umísťovací metody třídy <xref:System.Windows.Controls.Canvas> element na pozici podřízené obsah. Tento příklad používá obsah <xref:System.Windows.Controls.ListBoxItem> představují umístění hodnoty a převede hodnoty instancí <xref:System.Double>, který je požadovaný argument pro umístění. Hodnoty jsou pak převést zpět na řetězce a zobrazí jako text v <xref:System.Windows.Controls.TextBlock> element pomocí <xref:System.Windows.Controls.Canvas.GetLeft%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Windows.Controls.ListBox> element, který má jedenáct volitelný <xref:System.Windows.Controls.ListBoxItem> elementy. <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Aktivačních událostí `ChangeLeft` vlastní metodu, která definuje následující kód bloku.  
  
 Každý <xref:System.Windows.Controls.ListBoxItem> představuje <xref:System.Double> hodnotu, která je jeden z argumentů, <xref:System.Windows.Controls.Canvas.SetLeft%2A> metodu <xref:System.Windows.Controls.Canvas> přijímá. Aby bylo možné používat <xref:System.Windows.Controls.ListBoxItem> představující instanci <xref:System.Double>, je nutné nejprve převést <xref:System.Windows.Controls.ListBoxItem> do správného datového typu.  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 Když uživatel změní <xref:System.Windows.Controls.ListBox> výběr, vyvolá `ChangeLeft` vlastní metoda. Tato metoda předá <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.LengthConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Double> (Všimněte si, že tato hodnota již byl převeden na <xref:System.String> pomocí <xref:System.Windows.Controls.Control.ToString%2A> Metoda). Tato hodnota je předána zpět <xref:System.Windows.Controls.Canvas.SetLeft%2A> a <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody <xref:System.Windows.Controls.Canvas> Chcete-li změnit umístění `text1` objektu.  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)
