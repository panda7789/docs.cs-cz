---
title: 'Postupy: Implementace vlastnosti závislosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 90eb15d3cc0d9a6c1d07879b0166da4d45d786be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727323"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="8ab12-102">Postupy: Implementace vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="8ab12-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="8ab12-103">Tento příklad ukazuje, jak zálohovat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost s <xref:System.Windows.DependencyProperty> pole, proto definování vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="8ab12-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="8ab12-104">Při definování vlastní vlastnosti a nechcete, aby podporují mnoho aspektů [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkce, včetně styly, vazby dat, dědičnost, animace a výchozí hodnoty, měli byste implementovat jako vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="8ab12-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab12-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ab12-105">Example</span></span>  
 <span data-ttu-id="8ab12-106">Následující příklad nejprve registruje vlastnost závislosti voláním <xref:System.Windows.DependencyProperty.Register%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8ab12-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="8ab12-107">Název pole identifikátor, který použijete k uložení názvu a vlastnosti vlastnost závislosti musí být <xref:System.Windows.DependencyProperty.Name%2A> jste zvolili pro vlastnost závislosti v rámci <xref:System.Windows.DependencyProperty.Register%2A> volání připojí pomocí řetězcového literálu `Property`.</span><span class="sxs-lookup"><span data-stu-id="8ab12-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="8ab12-108">Například když si zaregistrujete pomocí vlastnosti závislosti <xref:System.Windows.DependencyProperty.Name%2A> z `Location`, pak musí mít název na identifikátor pole, které definujete pro vlastnost závislosti `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="8ab12-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="8ab12-109">V tomto příkladu, název vlastnosti závislostí a jeho [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přístupový objekt není `State`; je pole identifikátor `StateProperty`; typ vlastnosti je <xref:System.Boolean>; a typ, který registruje vlastnost závislosti je `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="8ab12-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="8ab12-110">Pokud chcete řídit tímto vzorem pojmenování, návrháři nemusí správně sestavu vaše vlastnost, a některé aspekty aplikaci ve stylu systému vlastnost nemusí chovat dle očekávání.</span><span class="sxs-lookup"><span data-stu-id="8ab12-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="8ab12-111">Můžete také určit výchozí metadat pro vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="8ab12-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="8ab12-112">Tento příklad registruje výchozí hodnota `State` vlastnost závislosti bude `false`.</span><span class="sxs-lookup"><span data-stu-id="8ab12-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="8ab12-113">Další informace o tom, a proto implementace vlastnosti závislosti, na rozdíl od jenom zálohování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost s privátní pole, naleznete v tématu [přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ab12-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab12-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ab12-114">See also</span></span>
- [<span data-ttu-id="8ab12-115">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="8ab12-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="8ab12-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8ab12-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
