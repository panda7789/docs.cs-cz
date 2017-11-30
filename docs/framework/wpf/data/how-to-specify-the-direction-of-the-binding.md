---
title: "Postupy: Určení směru připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdcda02a61f0114bfbbe5d5c411cb397cddcf683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="32879-102">Postupy: Určení směru připojení</span><span class="sxs-lookup"><span data-stu-id="32879-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="32879-103">Tento příklad ukazuje, jak určit, zda vazby aktualizuje pouze vazby pro vlastnost target (cíl), vlastnost vazby zdroj (zdroj) nebo vlastnost target i vlastnost zdroje.</span><span class="sxs-lookup"><span data-stu-id="32879-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32879-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="32879-104">Example</span></span>  
 <span data-ttu-id="32879-105">Můžete použít <xref:System.Windows.Data.Binding.Mode%2A> vlastnosti k určení směru vazby.</span><span class="sxs-lookup"><span data-stu-id="32879-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="32879-106">V následujícím seznamu výčtu jsou uvedené dostupné možnosti pro vazbu aktualizace:</span><span class="sxs-lookup"><span data-stu-id="32879-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="32879-107"><xref:System.Windows.Data.BindingMode.TwoWay>Při každé změně vlastnost Cílová nebo zdrojová vlastnost aktualizuje vlastnost target nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="32879-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="32879-108"><xref:System.Windows.Data.BindingMode.OneWay>Vlastnost target aktualizuje jenom v případě, že změny vlastností zdroje.</span><span class="sxs-lookup"><span data-stu-id="32879-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="32879-109"><xref:System.Windows.Data.BindingMode.OneTime>aktualizuje vlastnost target pouze při spuštění aplikace, nebo když <xref:System.Windows.FrameworkElement.DataContext%2A> zde nevyskytlo změnu.</span><span class="sxs-lookup"><span data-stu-id="32879-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="32879-110"><xref:System.Windows.Data.BindingMode.OneWayToSource>Aktualizuje vlastnosti zdroj při vlastnost target.</span><span class="sxs-lookup"><span data-stu-id="32879-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="32879-111"><xref:System.Windows.Data.BindingMode.Default>způsobí, že výchozí <xref:System.Windows.Data.Binding.Mode%2A> hodnotu vlastnost target, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="32879-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="32879-112">Další informace najdete v tématu <xref:System.Windows.Data.BindingMode> výčtu.</span><span class="sxs-lookup"><span data-stu-id="32879-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="32879-113">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Data.Binding.Mode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="32879-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="32879-114">Ke zjištění změny zdrojů (platí pro <xref:System.Windows.Data.BindingMode.OneWay> a <xref:System.Windows.Data.BindingMode.TwoWay> vazby), zdroj musí implementovat, jako vhodný mechanismus oznámení změn vhodný vlastnost <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="32879-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="32879-115">V tématu [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) příklad <xref:System.ComponentModel.INotifyPropertyChanged> implementace.</span><span class="sxs-lookup"><span data-stu-id="32879-115">See [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="32879-116">Pro <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby, můžete řídit načasování aktualizací zdroje podle nastavení <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="32879-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="32879-117">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="32879-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32879-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="32879-118">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="32879-119">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="32879-119">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="32879-120">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="32879-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
