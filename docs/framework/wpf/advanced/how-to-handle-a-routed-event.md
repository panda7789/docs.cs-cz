---
title: "Postupy: Zpracování směrované události"
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
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83f59f2df9311f30995b18529a733a5569c85ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-a-routed-event"></a>Postupy: Zpracování směrované události
Tento příklad ukazuje, jak probublávání události práci a jak napsat obslužnou rutinu, která dokáže zpracovat data směrované události.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elementy jsou uspořádány do stromové struktury k elementu. Zpracování událostí, které jsou původně aktivováno podřízené elementy ve stromové struktuře element účastnit nadřazeného elementu. To je možné díky směrování událostí.  
  
 Směrované události podle obvykle jednu ze dvou směrování strategií, šíření nebo tunelové propojení. Tento příklad se zaměřuje na probublávání události a používá <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> událostí zobrazíte funguje jak směrování.  
  
 Následující příklad vytvoří dvě <xref:System.Windows.Controls.Button> ovládací prvky a používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe k připojení obslužné rutiny události pro běžné nadřazený element, který v tomto příkladu je atribut <xref:System.Windows.Controls.StackPanel>. Místo připojení jednotlivé obslužné rutiny pro každou <xref:System.Windows.Controls.Button> podřízený element v příkladu používá syntaxi atribut připojit obslužná rutina události <xref:System.Windows.Controls.StackPanel> nadřazeného elementu. Tento vzor zpracování událostí ukazuje, jak používat událostí směrování jako technika snižuje počet elementů, kde je připojen obslužnou rutinu. Všechny probublávání události pro každou <xref:System.Windows.Controls.Button> směrovat přes nadřazeného elementu.  
  
 Všimněte si, že v nadřazené <xref:System.Windows.Controls.StackPanel> elementu, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> název události zadaný jako atribut je částečně kvalifikovaný pojmenováním <xref:System.Windows.Controls.Button> třídy. <xref:System.Windows.Controls.Button> Třída je <xref:System.Windows.Controls.Primitives.ButtonBase> odvozené třídy, který má <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost v její členy výpis. Tato technika částečné kvalifikace pro připojení obslužné rutiny události je nezbytný, pokud událost, která se právě zpracovává neexistuje v členy výpis elementu, kde je obslužná rutina směrované události připojen.  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 Následující příklad popisovače <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  V příkladu sestavy, který element zpracovává události a které elementy vyvolá událost. Obslužné rutiny události se spustí, když uživatel klikne buď tlačítko.  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.RoutedEvent>  
 [Vstupní – přehled](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled směrované události](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [Syntaxe jazyka XAML podrobně](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
