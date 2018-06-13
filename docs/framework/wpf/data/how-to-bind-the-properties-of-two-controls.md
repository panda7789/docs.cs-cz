---
title: 'Postupy: Svázání vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 02e71bfcc41fc3d256ea95381ed27d36b289b8f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555578"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="c8f40-102">Postupy: Svázání vlastností dvou ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="c8f40-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="c8f40-103">Tento příklad ukazuje, jak pro vazbu s jinou pomocí vlastnost jeden vytvořenou instanci ovládacího prvku <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c8f40-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8f40-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8f40-104">Example</span></span>  
 <span data-ttu-id="c8f40-105">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Canvas> k <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="c8f40-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="c8f40-106">Vlastnost <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="c8f40-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="c8f40-107">Při tomto příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="c8f40-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="c8f40-108">![Na plátno se zeleným pozadím](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="c8f40-108">![A canvas with a green background](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="c8f40-109">**Poznámka:** vlastnost target vazba (v tomto příkladu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost) musí být vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="c8f40-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="c8f40-110">Další informace najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c8f40-110">For more information, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f40-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8f40-111">See Also</span></span>  
 [<span data-ttu-id="c8f40-112">Určení zdroje vazby</span><span class="sxs-lookup"><span data-stu-id="c8f40-112">Specify the Binding Source</span></span>](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [<span data-ttu-id="c8f40-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c8f40-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
