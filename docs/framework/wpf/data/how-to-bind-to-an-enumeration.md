---
title: "Postupy: Připojení k vyčíslení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72439cdc1c1017378a5b6b3f6b4bf41a9eee2537
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="0485d-102">Postupy: Připojení k vyčíslení</span><span class="sxs-lookup"><span data-stu-id="0485d-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="0485d-103">Tento příklad ukazuje, jak vytvořit vazbu na výčet vazbou metodě GetValues ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0485d-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0485d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0485d-104">Example</span></span>  
 <span data-ttu-id="0485d-105">V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazí seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby.</span><span class="sxs-lookup"><span data-stu-id="0485d-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="0485d-106"><xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> jsou svázané s tak, že můžete změnit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnota vlastnosti <xref:System.Windows.Controls.Button> výběrem hodnoty v <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="0485d-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="0485d-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="0485d-107">See Also</span></span>  
 [<span data-ttu-id="0485d-108">Vytvoření vazby k metodě</span><span class="sxs-lookup"><span data-stu-id="0485d-108">Bind to a Method</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [<span data-ttu-id="0485d-109">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="0485d-109">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="0485d-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="0485d-110">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
