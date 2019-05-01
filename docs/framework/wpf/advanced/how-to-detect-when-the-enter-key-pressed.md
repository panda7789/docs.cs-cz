---
title: 'Postupy: Rozpoznat, kdy stisknuté klávesy Enter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a99da5804bbc31897198b9b6d9e21da9f17dfe26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051413"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Postupy: Rozpoznat, kdy stisknuté klávesy Enter
Tento příklad ukazuje, jak zjistit, kdy <xref:System.Windows.Input.Key.Enter> stisknutí klávesy na klávesnici.  
  
 Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu na pozadí.  
  
## <a name="example"></a>Příklad  
 Když uživatel stiskne klávesu <xref:System.Windows.Input.Key.Enter> klíče v <xref:System.Windows.Controls.TextBox>, vstup v textovém poli se zobrazí v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.KeyDown> obslužné rutiny události.  Pokud je klíč, která byla stisknuta <xref:System.Windows.Input.Key.Enter> klíče, zobrazí se zpráva v <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vstupu](input-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
