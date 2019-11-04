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
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="fd25e-102">Postupy: určení směru vazby</span><span class="sxs-lookup"><span data-stu-id="fd25e-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="fd25e-103">Tento příklad ukazuje, jak určit, zda vazba aktualizuje pouze cílovou vlastnost (cílovou) vazby, vlastnost zdroje vazby (zdroj) nebo jak vlastnost target, tak vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="fd25e-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd25e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd25e-104">Example</span></span>  
 <span data-ttu-id="fd25e-105">Vlastnost <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> slouží k určení směru vazby.</span><span class="sxs-lookup"><span data-stu-id="fd25e-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="fd25e-106">K dispozici jsou následující možnosti pro aktualizace vazeb:</span><span class="sxs-lookup"><span data-stu-id="fd25e-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="fd25e-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> aktualizuje cílovou vlastnost nebo vlastnost vždy, když se změní buď vlastnost target, nebo vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="fd25e-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="fd25e-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> aktualizuje cílovou vlastnost pouze v případě, že se změní vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="fd25e-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="fd25e-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> aktualizuje cílovou vlastnost pouze v případě, že se aplikace spustí nebo když se <xref:System.Windows.FrameworkElement.DataContext%2A> dopadne na změnu.</span><span class="sxs-lookup"><span data-stu-id="fd25e-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="fd25e-110">Když se změní cílová vlastnost, <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> aktualizuje vlastnost source.</span><span class="sxs-lookup"><span data-stu-id="fd25e-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="fd25e-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> způsobí, že bude použita výchozí hodnota <xref:System.Windows.Data.Binding.Mode%2A> cílovou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fd25e-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="fd25e-112">Další informace najdete v <xref:System.Windows.Data.BindingMode> výčtu.</span><span class="sxs-lookup"><span data-stu-id="fd25e-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="fd25e-113">Následující příklad ukazuje, jak nastavit vlastnost <xref:System.Windows.Data.Binding.Mode%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd25e-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="fd25e-114">Aby bylo možné zjistit změny ve zdroji (platí pro vazby <xref:System.Windows.Data.BindingMode.OneWay> a <xref:System.Windows.Data.BindingMode.TwoWay>), musí zdroj implementovat vhodný mechanismus pro oznamování změn vlastností, jako je například <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="fd25e-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="fd25e-115">Příklad implementace <xref:System.ComponentModel.INotifyPropertyChanged> v tématu [implementace oznámení o změně vlastností](how-to-implement-property-change-notification.md) .</span><span class="sxs-lookup"><span data-stu-id="fd25e-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="fd25e-116">V případě vazeb <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> můžete určit načasování zdrojových aktualizací nastavením vlastnosti <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd25e-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="fd25e-117">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd25e-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd25e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd25e-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="fd25e-119">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="fd25e-119">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="fd25e-120">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="fd25e-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
