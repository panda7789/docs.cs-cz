---
title: 'Postupy: Zpracování směrované události'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: 42f5f247e775fbf0bd323fc693a74d6149c87bb3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368191"
---
# <a name="how-to-handle-a-routed-event"></a>Postupy: Zpracování směrované události
Tento příklad ukazuje, jak šíření pracovní událostí a jak napsat obslužnou rutinu, která dokáže zpracovávat data směrované události.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], prvky jsou uspořádány ve stromové struktuře element jazyka. Při zpracování událostí, které se původně vyvolána podřízené elementy ve stromu elementů se můžete zúčastnit nadřazeného elementu. To je možné z důvodu směrování událostí.  
  
 Směrované události obvykle odpovídat jednomu ze dvou strategie směrování, šíření a tunelové propojení. Tento příklad se zaměřuje na šíření událostí a používá <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> událost, která ukazuje, jak směrování funguje.  
  
 Následující příklad vytvoří dva <xref:System.Windows.Controls.Button> ovládací prvky a používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atribut syntaxe se připojit k běžné nadřazený prvek, který v tomto příkladu je obslužná rutina události <xref:System.Windows.Controls.StackPanel>. Místo připojování jednotlivé obslužné rutiny pro každou <xref:System.Windows.Controls.Button> podřízený element v příkladu syntaxe atributu připojit obslužná rutina události <xref:System.Windows.Controls.StackPanel> nadřazeného elementu. Tento vzor zpracování událostí ukazuje způsob použití směrování událostí jako postup pro omezení počtu prvků kde je obslužná rutina připojená. Šíření událostí pro každou <xref:System.Windows.Controls.Button> trasy prostřednictvím nadřazeného elementu.  
  
 Všimněte si, že v nadřazené <xref:System.Windows.Controls.StackPanel> elementu, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> název události, zadaný jako atribut je částečně kvalifikované pojmenováním <xref:System.Windows.Controls.Button> třídy. <xref:System.Windows.Controls.Button> Třída je <xref:System.Windows.Controls.Primitives.ButtonBase> odvozenou třídu, která má <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí ve výpisu. Tato technika částečné kvalifikace pro obslužnou rutinu události připojení je nutné v případě, že událost, která se zpracovává neexistuje u členů výpis elementu, kde je obslužná rutina směrované události připojen.  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 Následující příklad popisovače <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  Příklad sestavy, které elementy zpracovává události a který element vyvolává událost. Obslužná rutina události je provedena, když uživatel klikne na tlačítko buď tlačítko.  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.RoutedEvent>
- [Přehled vstupu](input-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Témata s postupy](events-how-to-topics.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
