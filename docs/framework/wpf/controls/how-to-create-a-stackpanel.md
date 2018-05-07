---
title: 'Postupy: Vytvoření objektu StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 30f24d8dba7c09271a5957822439af6b64e05aca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-stackpanel"></a>Postupy: Vytvoření objektu StackPanel
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Příklad  
 A <xref:System.Windows.Controls.StackPanel> umožňuje zásobníku elementů v zadaném směru. Pomocí vlastností, které jsou definovány na <xref:System.Windows.Controls.StackPanel>, obsah může obtékat i svisle, což je výchozí nastavení, nebo vodorovně.  
  
 Následující příklad svisle balíků pět <xref:System.Windows.Controls.TextBlock> prvky, každý s jiným <xref:System.Windows.Controls.Border> a <xref:System.Windows.Controls.Border.Background%2A>, pomocí <xref:System.Windows.Controls.StackPanel>. Podřízené elementy, které mají není zadána žádná <xref:System.Windows.FrameworkElement.Width%2A> roztáhnou tak, aby vyplnil celou nadřazeného okna; však podřízené elementy jejichž zadané <xref:System.Windows.FrameworkElement.Width%2A>, na střed v rámci okna.  
  
 Výchozí směr zásobníku v <xref:System.Windows.Controls.StackPanel> je svislý. K řízení toku obsahu v <xref:System.Windows.Controls.StackPanel>, použijte <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost. Vodorovné zarovnání můžete řídit pomocí <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.StackPanel>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
