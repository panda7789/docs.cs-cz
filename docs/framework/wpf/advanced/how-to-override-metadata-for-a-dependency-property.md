---
title: "Postupy: Přetížení metadat pro vlastnost závislosti"
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
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e7cb01c81b5fb24830cbe0cc39befbadaf4405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a><span data-ttu-id="08d83-102">Postupy: Přetížení metadat pro vlastnost závislosti</span><span class="sxs-lookup"><span data-stu-id="08d83-102">How to: Override Metadata for a Dependency Property</span></span>
<span data-ttu-id="08d83-103">Tento příklad ukazuje, jak lze přepsat výchozí metadat vlastností závislostí, který přichází z zděděná třída, voláním <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metoda a poskytuje metadata pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="08d83-103">This example shows how to override default dependency property metadata that comes from an inherited class, by calling the <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> method and providing type-specific metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08d83-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="08d83-104">Example</span></span>  
 <span data-ttu-id="08d83-105">Definováním jeho <xref:System.Windows.PropertyMetadata>, třídu můžete definovat chování, vlastnost závislosti, například jeho výchozí hodnotu a vlastnost systému zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="08d83-105">By defining its <xref:System.Windows.PropertyMetadata>, a class can define the dependency property's behaviors, such as its default value and property system callbacks.</span></span> <span data-ttu-id="08d83-106">Mnoho závislostí vlastnosti třídy již máte výchozí metadata navázat součástí jejich procesu registrace.</span><span class="sxs-lookup"><span data-stu-id="08d83-106">Many dependency property classes already have default metadata established as part of their registration process.</span></span> <span data-ttu-id="08d83-107">Jedná se o vlastnostech závislostí, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08d83-107">This includes the dependency properties that are part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].</span></span> <span data-ttu-id="08d83-108">Třídu, která dědí vlastnost závislosti prostřednictvím jeho dědičnosti tříd můžete přepsat původní metadata, tak, aby charakteristiky vlastnosti, která může být změněna pomocí metadat bude shodovat s požadavky na žádné konkrétní podtřídy.</span><span class="sxs-lookup"><span data-stu-id="08d83-108">A class that inherits the dependency property through its class inheritance can override the original metadata so that the characteristics of the property that can be altered through metadata will match any subclass-specific requirements.</span></span>  
  
 <span data-ttu-id="08d83-109">Přepsání metadata na vlastnost závislosti je třeba provést před tuto vlastnost je uskutečnění používá vlastnost systémem (Tato hodnota rovná čas, které jsou vytvářeny instance určité instance objektů, které registrují vlastnost).</span><span class="sxs-lookup"><span data-stu-id="08d83-109">Overriding metadata on a dependency property must be done prior to that property being placed in use by the property system (this equates to the time that specific instances of objects that register the property are instantiated).</span></span> <span data-ttu-id="08d83-110">Volání <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> musí provést v rámci statické konstruktory typu, který poskytuje sám sebe jako `forType` parametr <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="08d83-110">Calls to <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> must be performed within the static constructors of the type that provides itself as the `forType` parameter of <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.</span></span> <span data-ttu-id="08d83-111">Pokud se pokusíte změnit metadata po existovat instance typu vlastníka, to nevydá výjimky, ale způsobí nekonzistentní chování systému vlastnost.</span><span class="sxs-lookup"><span data-stu-id="08d83-111">If you attempt to change metadata once instances of the owner type exist, this will not raise exceptions, but will result in inconsistent behaviors in the property system.</span></span> <span data-ttu-id="08d83-112">Navíc metadata lze pouze přepsat jednou podle typu.</span><span class="sxs-lookup"><span data-stu-id="08d83-112">Also, metadata can only be overridden once per type.</span></span> <span data-ttu-id="08d83-113">Následné pokusy o přepsání metadata stejného typu, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="08d83-113">Subsequent attempts to override metadata on the same type will raise an exception.</span></span>  
  
 <span data-ttu-id="08d83-114">V následujícím příkladu, vlastní třídu `MyAdvancedStateControl` přepsání zadaná pro metadata `StateProperty` podle `MyAdvancedStateControl` s novými metadaty vlastnost.</span><span class="sxs-lookup"><span data-stu-id="08d83-114">In the following example, the custom class `MyAdvancedStateControl` overrides the metadata provided for `StateProperty` by `MyAdvancedStateControl` with new property metadata.</span></span> <span data-ttu-id="08d83-115">Například výchozí hodnota `StateProperty` je nyní `true` Pokud je vlastnost dotazován na nově vytvořený `MyAdvancedStateControl` instance.</span><span class="sxs-lookup"><span data-stu-id="08d83-115">For instance, the default value of the `StateProperty` is now `true` when the property is queried on a newly constructed `MyAdvancedStateControl` instance.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="08d83-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="08d83-116">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="08d83-117">Přehled vlastností závislostí</span><span class="sxs-lookup"><span data-stu-id="08d83-117">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="08d83-118">Vlastnosti vlastní závislosti</span><span class="sxs-lookup"><span data-stu-id="08d83-118">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="08d83-119">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="08d83-119">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
