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
ms.openlocfilehash: ebfb8642a01f6d602f4e5ffa58fde6a8ee0b4e1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001478"
---
# <a name="how-to-use-a-thicknessconverter-object"></a>Postupy: Použití objektu ThicknessConverter
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.ThicknessConverter> a použít ho ke změně tloušťky ohraničení.  
  
 Příklad definuje vlastní metodu nazvanou `changeThickness`; tato metoda nejprve převede obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Windows.Thickness>a později převede obsah do <xref:System.String>. Tato metoda předává <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.ThicknessConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do instance <xref:System.Windows.Thickness>. Tato hodnota je pak předán zpět jako hodnotu <xref:System.Windows.Controls.Border.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.  
  
 V tomto příkladu se nespustí.  
  
 [!code-csharp[ThicknessConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- [Postupy: Změnit vlastnosti okraj](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))
- [Postupy: Převést ListBoxItem na nový datový typ.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))
- [Přehled panelu](../controls/panels-overview.md)
