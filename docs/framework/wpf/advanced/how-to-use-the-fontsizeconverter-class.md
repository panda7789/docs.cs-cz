---
title: 'Postupy: Použití třídy FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Postupy: Použití třídy FontSizeConverter
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.FontSizeConverter> a použít ho chcete-li změnit velikost písma.  
  
 V příkladu definuje vlastní metodu s názvem `changeSize` , převede obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Double>a novější do <xref:System.String>. Tato metoda předá <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.FontSizeConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Double>. Tato hodnota se potom předá zpět jako hodnota <xref:System.Windows.Controls.TextBlock.FontSize%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.  
  
 Tento příklad také definuje druhý vlastní metodu, která je volána `changeFamily`. Tato metoda převede <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> k <xref:System.String>a pak předá tuto hodnotu <xref:System.Windows.Controls.TextBlock.FontFamily%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.  
  
 Tento příklad nespouští.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FontSizeConverter>
