---
title: 'Postupy: Určení směru připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459090"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Postupy: určení směru vazby

Tento příklad ukazuje, jak určit, zda vazba aktualizuje pouze cílovou vlastnost (cílovou) vazby, vlastnost zdroje vazby (zdroj) nebo jak vlastnost target, tak vlastnost source.  
  
## <a name="example"></a>Příklad  
 Vlastnost <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> slouží k určení směru vazby. K dispozici jsou následující možnosti pro aktualizace vazeb:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> aktualizuje cílovou vlastnost nebo vlastnost vždy, když se změní buď vlastnost target, nebo vlastnost source.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> aktualizuje cílovou vlastnost pouze v případě, že se změní vlastnost source.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> aktualizuje cílovou vlastnost pouze v případě, že se aplikace spustí nebo když se <xref:System.Windows.FrameworkElement.DataContext%2A> dopadne na změnu.  
  
- Když se změní cílová vlastnost, <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> aktualizuje vlastnost source.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> způsobí, že bude použita výchozí hodnota <xref:System.Windows.Data.Binding.Mode%2A> cílovou vlastnost.  
  
 Další informace najdete v <xref:System.Windows.Data.BindingMode> výčtu.  
  
 Následující příklad ukazuje, jak nastavit vlastnost <xref:System.Windows.Data.Binding.Mode%2A>.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Aby bylo možné zjistit změny ve zdroji (platí pro vazby <xref:System.Windows.Data.BindingMode.OneWay> a <xref:System.Windows.Data.BindingMode.TwoWay>), musí zdroj implementovat vhodný mechanismus pro oznamování změn vlastností, jako je například <xref:System.ComponentModel.INotifyPropertyChanged>. Příklad implementace <xref:System.ComponentModel.INotifyPropertyChanged> v tématu [implementace oznámení o změně vlastností](how-to-implement-property-change-notification.md) .  
  
 V případě vazeb <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> můžete určit načasování zdrojových aktualizací nastavením vlastnosti <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
