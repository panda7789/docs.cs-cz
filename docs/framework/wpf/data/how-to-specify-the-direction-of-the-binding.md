---
title: 'Postupy: Určení směru vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 4334ed178e7f2ed90928db6b434eb8c9fee77bf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206431"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="078b4-102">Postupy: Určení směru vazby</span><span class="sxs-lookup"><span data-stu-id="078b4-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="078b4-103">Tento příklad ukazuje, jak určit, zda vazba aktualizuje pouze vazby pro vlastnost target (cíl), vlastnost vazby source (zdroj), nebo vlastnost target i vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="078b4-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="078b4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="078b4-104">Example</span></span>  
 <span data-ttu-id="078b4-105">Můžete použít <xref:System.Windows.Data.Binding.Mode%2A> vlastnosti k určení směru připojení.</span><span class="sxs-lookup"><span data-stu-id="078b4-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="078b4-106">Následující seznam výčtu uvádí dostupné možnosti pro aktualizace vazeb:</span><span class="sxs-lookup"><span data-stu-id="078b4-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="078b4-107"><xref:System.Windows.Data.BindingMode.TwoWay> aktualizuje cílovou vlastnost nebo vlastnost pokaždé, když se změní vlastnost target nebo vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="078b4-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="078b4-108"><xref:System.Windows.Data.BindingMode.OneWay> Aktualizuje vlastnosti cílového pouze v případě, že se změní vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="078b4-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="078b4-109"><xref:System.Windows.Data.BindingMode.OneTime> Aktualizuje vlastnosti cílového pouze při spuštění aplikace, nebo když <xref:System.Windows.FrameworkElement.DataContext%2A> při změně.</span><span class="sxs-lookup"><span data-stu-id="078b4-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="078b4-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> Při změně vlastnosti cílového, aktualizuje vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="078b4-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="078b4-111"><xref:System.Windows.Data.BindingMode.Default> způsobí, že výchozí <xref:System.Windows.Data.Binding.Mode%2A> hodnotu vlastnost target, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="078b4-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="078b4-112">Další informace najdete v tématu <xref:System.Windows.Data.BindingMode> výčtu.</span><span class="sxs-lookup"><span data-stu-id="078b4-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="078b4-113">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Data.Binding.Mode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="078b4-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="078b4-114">Chcete-li zjistit změny zdrojového (platí pro <xref:System.Windows.Data.BindingMode.OneWay> a <xref:System.Windows.Data.BindingMode.TwoWay> vazby), zdroj musí implementovat mechanismus oznámení změn vhodné vlastnosti, jako <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="078b4-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="078b4-115">Zobrazit [implementace oznámení změn vlastností](how-to-implement-property-change-notification.md) příklad <xref:System.ComponentModel.INotifyPropertyChanged> implementace.</span><span class="sxs-lookup"><span data-stu-id="078b4-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="078b4-116">Pro <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby, časování aktualizací zdroje můžete řídit tak, že nastavíte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="078b4-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="078b4-117">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="078b4-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078b4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="078b4-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="078b4-119">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="078b4-119">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="078b4-120">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="078b4-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
