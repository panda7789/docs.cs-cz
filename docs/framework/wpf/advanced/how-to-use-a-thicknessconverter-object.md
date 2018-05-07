---
title: 'Postupy: Použití objektu ThicknessConverter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: 119c4397dee76429e776378ee89fa49747dbfce4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-thicknessconverter-object"></a>Postupy: Použití objektu ThicknessConverter
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.ThicknessConverter> a použít ho k změňte tloušťku ohraničení.  
  
 V příkladu definuje vlastní metodu s názvem `changeThickness`; tato metoda převede první obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Windows.Thickness>a později převede obsah do <xref:System.String>. Tato metoda předá <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.ThicknessConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Windows.Thickness>. Tato hodnota se potom předá zpět jako hodnota <xref:System.Windows.Controls.Border.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.  
  
 Tento příklad nespouští.  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [Postupy: změnit Margin – vlastnost](http://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [Postupy: převod ListBoxItem na nový datový typ.](http://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
