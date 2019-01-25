---
title: 'Postupy: Vytvoření objektu StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 20e2b21b10129c096398606501768a7ace0617fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674229"
---
# <a name="how-to-create-a-stackpanel"></a>Postupy: Vytvoření objektu StackPanel
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Příklad  
 A <xref:System.Windows.Controls.StackPanel> umožňuje zásobníku prvky v zadaném směru. Pomocí vlastností, které jsou definovány na <xref:System.Windows.Controls.StackPanel>, obsah byl zajištěn tok obě svisle, což je výchozí nastavení, nebo vodorovně.  
  
 Následující příklad svisle zásobníků pět <xref:System.Windows.Controls.TextBlock> ovládací prvky, každý s jiným <xref:System.Windows.Controls.Border> a <xref:System.Windows.Controls.Border.Background%2A>, s použitím <xref:System.Windows.Controls.StackPanel>. Podřízené prvky, které nemají zadán <xref:System.Windows.FrameworkElement.Width%2A> roztáhnout tak, aby vyplnil nadřazené okno; nicméně jsou podřízené prvky, které mají zadanou <xref:System.Windows.FrameworkElement.Width%2A>, je umístěn okna na střed.  
  
 Výchozí směr zásobníku <xref:System.Windows.Controls.StackPanel> je svislý. K řízení toku obsahu v <xref:System.Windows.Controls.StackPanel>, použijte <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost. Vodorovné zarovnání můžete řídit pomocí <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost.  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.StackPanel>
- [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
