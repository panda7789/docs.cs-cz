---
title: 'Postupy: Určení směru připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 6e617b2fdb6150aa8d5d6960f7aab58198c8b240
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550146"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Postupy: Určení směru připojení
Tento příklad ukazuje, jak určit, zda vazba aktualizuje pouze vazby pro vlastnost target (cíl), vlastnost vazby source (zdroj), nebo vlastnost target i vlastnost source.  
  
## <a name="example"></a>Příklad  
 Můžete použít <xref:System.Windows.Data.Binding.Mode%2A> vlastnosti k určení směru připojení. Následující seznam výčtu uvádí dostupné možnosti pro aktualizace vazeb:  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> aktualizuje cílovou vlastnost nebo vlastnost pokaždé, když se změní vlastnost target nebo vlastnost source.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> Aktualizuje vlastnosti cílového pouze v případě, že se změní vlastnost source.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> Aktualizuje vlastnosti cílového pouze při spuštění aplikace, nebo když <xref:System.Windows.FrameworkElement.DataContext%2A> při změně.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> Při změně vlastnosti cílového, aktualizuje vlastnost source.  
  
-   <xref:System.Windows.Data.BindingMode.Default> způsobí, že výchozí <xref:System.Windows.Data.Binding.Mode%2A> hodnotu vlastnost target, který se má použít.  
  
 Další informace najdete v tématu <xref:System.Windows.Data.BindingMode> výčtu.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Data.Binding.Mode%2A> vlastnost.  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Chcete-li zjistit změny zdrojového (platí pro <xref:System.Windows.Data.BindingMode.OneWay> a <xref:System.Windows.Data.BindingMode.TwoWay> vazby), zdroj musí implementovat mechanismus oznámení změn vhodné vlastnosti, jako <xref:System.ComponentModel.INotifyPropertyChanged>. Zobrazit [implementace oznámení změn vlastností](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) příklad <xref:System.ComponentModel.INotifyPropertyChanged> implementace.  
  
 Pro <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby, časování aktualizací zdroje můžete řídit tak, že nastavíte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Data.Binding>
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
