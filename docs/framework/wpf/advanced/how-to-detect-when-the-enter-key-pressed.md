---
title: 'Postupy: Detekce stisknuté klávesy Enter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: 1de11cd30d1990dcd2bc927a69b60c66c721addb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Postupy: Detekce stisknuté klávesy Enter
Tento příklad ukazuje, jak zjistit, kdy <xref:System.Windows.Input.Key.Enter> není stisknuta klávesa na klávesnici.  
  
 V tomto příkladu se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a soubor kódu.  
  
## <a name="example"></a>Příklad  
 Když uživatel stiskne <xref:System.Windows.Input.Key.Enter> klíče v <xref:System.Windows.Controls.TextBox>, vstup v textovém poli se zobrazí v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.KeyDown> obslužné rutiny události.  Pokud je klíč, který je stisknutí <xref:System.Windows.Input.Key.Enter> klíče, zobrazí se zpráva v <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
