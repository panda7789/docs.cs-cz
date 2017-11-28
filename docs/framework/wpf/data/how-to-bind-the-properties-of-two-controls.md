---
title: "Postupy: Svázání vlastností dvou ovládacích prvků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff3da19d33e747ec514de9cd24fa08ccd6ab13bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="5b8d3-102">Postupy: Svázání vlastností dvou ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="5b8d3-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="5b8d3-103">Tento příklad ukazuje, jak pro vazbu s jinou pomocí vlastnost jeden vytvořenou instanci ovládacího prvku <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5b8d3-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b8d3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b8d3-104">Example</span></span>  
 <span data-ttu-id="5b8d3-105">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Canvas> k <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="5b8d3-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="5b8d3-106">Při tomto příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5b8d3-106">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="5b8d3-107">![Na plátno se zeleným pozadím](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="5b8d3-107">![A canvas with a green background](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="5b8d3-108">**Poznámka:** vlastnost target vazba (v tomto příkladu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost) musí být vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="5b8d3-108">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="5b8d3-109">Další informace najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5b8d3-109">For more information, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8d3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b8d3-110">See Also</span></span>  
 [<span data-ttu-id="5b8d3-111">Zadejte zdroj vazby</span><span class="sxs-lookup"><span data-stu-id="5b8d3-111">Specify the Binding Source</span></span>](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [<span data-ttu-id="5b8d3-112">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="5b8d3-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
