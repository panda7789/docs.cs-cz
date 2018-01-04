---
title: "Postupy: Přidání typu vlastníka pro vlastnost závislosti"
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
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93934c8f84a7257445b530e27896342bdd73aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="aca46-102">Postupy: Přidání typu vlastníka pro vlastnost závislosti</span><span class="sxs-lookup"><span data-stu-id="aca46-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="aca46-103">Tento příklad ukazuje, jak přidat třídu jako vlastníka vlastnosti závislosti registrován pro jiného typu.</span><span class="sxs-lookup"><span data-stu-id="aca46-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="aca46-104">Tímto způsobem, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky a vlastnost systému jsou obě rozpoznat třída jako vlastníka další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aca46-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="aca46-105">Přidání jako vlastník volitelně umožňuje přidání třídy zajistit metadata specifická pro typ.</span><span class="sxs-lookup"><span data-stu-id="aca46-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="aca46-106">V následujícím příkladu `StateProperty` vlastnost registrován `MyStateControl` třídy.</span><span class="sxs-lookup"><span data-stu-id="aca46-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="aca46-107">Třída `UnrelatedStateControl` přidá sám sebe jako vlastníkem `StateProperty` pomocí <xref:System.Windows.DependencyProperty.AddOwner%2A> metodu, konkrétně pomocí podpisu, který umožňuje novými metadaty pro vlastnost závislosti uložených na přidání typu.</span><span class="sxs-lookup"><span data-stu-id="aca46-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="aca46-108">Všimněte si, že by měl poskytovat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] přístupových objektů pro vlastnost podobně jako v příkladu znázorněno [implementovat vlastnost závislosti](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) příklad, jakož i znovu vystavit identifikátor vlastnosti závislosti na třídě, který chcete přidat jako vlastník.</span><span class="sxs-lookup"><span data-stu-id="aca46-108">Notice that you should provide [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accessors for the property similar to the example shown in the [Implement a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="aca46-109">Bez obálky, vlastnost závislosti by i nadále fungovat z perspektivy programový přístup pomocí <xref:System.Windows.DependencyObject.GetValue%2A> nebo <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="aca46-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="aca46-110">Obvykle budete chtít paralelní s tímto chováním vlastnosti systému, ale [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obálky vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aca46-110">But you typically want to parallel this property-system behavior with the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrappers.</span></span> <span data-ttu-id="aca46-111">Obálky usnadňují nastavit vlastnost závislosti prostřednictvím kódu programu a umožňují, a nastavte vlastnosti jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy.</span><span class="sxs-lookup"><span data-stu-id="aca46-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="aca46-112">Chcete-li zjistit, jak lze přepsat výchozí metadata, přečtěte si téma [přepsat Metadata pro vlastnost závislosti](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span><span class="sxs-lookup"><span data-stu-id="aca46-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aca46-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="aca46-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="aca46-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="aca46-114">See Also</span></span>  
 [<span data-ttu-id="aca46-115">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="aca46-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="aca46-116">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="aca46-116">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
