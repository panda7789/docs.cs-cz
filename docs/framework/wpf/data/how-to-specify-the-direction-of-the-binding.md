---
title: 'Postupy: Určení směru vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817906"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Postupy: Zadat směr vazby

Tento příklad ukazuje, jak určit, zda vazba aktualizuje pouze cílovou vlastnost (cílovou) vazby, vlastnost zdroje vazby (zdroj) nebo jak vlastnost target, tak vlastnost source.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> Vlastnost slouží k určení směru vazby. K dispozici jsou následující možnosti pro aktualizace vazeb:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>aktualizuje cílovou vlastnost nebo vlastnost vždy, když se změní buď vlastnost target, nebo vlastnost source.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>aktualizuje cílovou vlastnost pouze v případě, že se změní vlastnost source.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>aktualizuje cílovou vlastnost pouze v případě, že se aplikace spustí nebo <xref:System.Windows.FrameworkElement.DataContext%2A> dojde ke změně.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>aktualizuje zdrojovou vlastnost, když se změní cílová vlastnost.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>způsobí použití výchozí <xref:System.Windows.Data.Binding.Mode%2A> hodnoty cílová vlastnost.  
  
 Další informace najdete v tématu <xref:System.Windows.Data.BindingMode> výčet.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Data.Binding.Mode%2A> vlastnost.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Aby bylo možné zjistit změny ve zdroji <xref:System.Windows.Data.BindingMode.OneWay> ( <xref:System.Windows.Data.BindingMode.TwoWay> platí pro vazby a), musí zdroj implementovat vhodný mechanismus pro oznamování změn <xref:System.ComponentModel.INotifyPropertyChanged>vlastností, jako je například. Příklad<xref:System.ComponentModel.INotifyPropertyChanged> implementace naleznete v tématu [implementace oznámení o změně vlastností](how-to-implement-property-change-notification.md) .  
  
 Pro <xref:System.Windows.Data.BindingMode.TwoWay> vazby <xref:System.Windows.Data.BindingMode.OneWayToSource> nebo můžete řídit načasování <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> zdrojových aktualizací nastavením vlastnosti. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding>
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
