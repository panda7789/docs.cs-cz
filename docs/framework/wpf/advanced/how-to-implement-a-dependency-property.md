---
title: "Postupy: Implementace vlastnosti závislosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d63e66b2458fa4ff21a227bdc2898d97e5eb30f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="a8cd7-102">Postupy: Implementace vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="a8cd7-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="a8cd7-103">Tento příklad ukazuje, jak zálohovat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost s <xref:System.Windows.DependencyProperty> pole, proto definování vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="a8cd7-104">Když definovat vlastní vlastnosti a mají podporovat mnoho aspektů [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcí, včetně styly, vazby dat, dědičnosti, animace a výchozí hodnoty, měli byste implementovat jako vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8cd7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8cd7-105">Example</span></span>  
 <span data-ttu-id="a8cd7-106">Následující příklad poprvé registruje vlastnost závislosti voláním <xref:System.Windows.DependencyProperty.Register%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="a8cd7-107">Název pole identifikátor, který použijete k uložení názvu a vlastnosti vlastnost závislosti musí být <xref:System.Windows.DependencyProperty.Name%2A> jste zvolili pro vlastnost závislosti v rámci <xref:System.Windows.DependencyProperty.Register%2A> volání, která se připojí pomocí řetězcového literálu `Property`.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="a8cd7-108">Například Pokud zaregistrujete vlastnost závislosti s <xref:System.Windows.DependencyProperty.Name%2A> z `Location`, pak musí mít název pole identifikátor, který určíte pro vlastnost závislosti `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="a8cd7-109">V tomto příkladu, název vlastnosti závislosti a jeho [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přistupujícího objektu je `State`; je pole identifikátor `StateProperty`; je typ vlastnosti <xref:System.Boolean>; a typ, který registruje vlastnost závislosti je `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="a8cd7-110">Pokud nedodržíte postupujte podle tohoto vzoru pro pojmenovávání, Designer nemusí správně sestavy vaší vlastností a některé aspekty vlastnost systému styl aplikace nemusí chovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="a8cd7-111">Můžete také zadat výchozí metadata pro vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="a8cd7-112">Tento příklad zaregistruje výchozí hodnota `State` vlastnost závislosti být `false`.</span><span class="sxs-lookup"><span data-stu-id="a8cd7-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="a8cd7-113">Další informace o tom, a důvod, proč k implementaci vlastnost závislosti, oproti právě zálohování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost s soukromé pole, najdete v části [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a8cd7-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8cd7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8cd7-114">See Also</span></span>  
 [<span data-ttu-id="a8cd7-115">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="a8cd7-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="a8cd7-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a8cd7-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
