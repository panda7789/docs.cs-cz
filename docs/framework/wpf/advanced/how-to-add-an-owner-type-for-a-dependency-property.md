---
title: 'Postupy: Přidání typu vlastníka pro vlastnost závislosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401131"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="b933d-102">Postupy: Přidání typu vlastníka pro vlastnost závislosti</span><span class="sxs-lookup"><span data-stu-id="b933d-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="b933d-103">Tento příklad ukazuje, jak přidat třídu jako vlastníka vlastnosti závislosti registrované pro jiný typ.</span><span class="sxs-lookup"><span data-stu-id="b933d-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="b933d-104">Tímto způsobem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokáže čtenář a systém vlastností rozpoznat třídu jako dalšího vlastníka vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b933d-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="b933d-105">Přidání jako vlastníka můžete volitelně povolit přidání třídy pro zadání metadat specifických pro typ.</span><span class="sxs-lookup"><span data-stu-id="b933d-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="b933d-106">V následujícím příkladu `StateProperty` je vlastnost zaregistrována `MyStateControl` třídou.</span><span class="sxs-lookup"><span data-stu-id="b933d-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="b933d-107">Třída `UnrelatedStateControl` přidá sebe samu jako vlastníka `StateProperty` pomocí <xref:System.Windows.DependencyProperty.AddOwner%2A> metody, konkrétně pomocí signatury, která umožňuje nová metadata pro vlastnost závislosti, protože existuje v přidávaném typu.</span><span class="sxs-lookup"><span data-stu-id="b933d-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="b933d-108">Všimněte si, že byste měli poskytnout přístupové objekty modulu CLR (Common Language Runtime) pro vlastnost podobně jako v příkladu, který je uveden v příkladu [implementace vlastnosti závislosti](how-to-implement-a-dependency-property.md) , a také znovu vystavit identifikátor vlastnosti závislosti pro třídu, která je přidávána jako vlastník.</span><span class="sxs-lookup"><span data-stu-id="b933d-108">Notice that you should provide common language runtime (CLR) accessors for the property similar to the example shown in the [Implement a Dependency Property](how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="b933d-109">Bez obálky může vlastnost Dependency i nadále pracovat z perspektivy programového přístupu pomocí <xref:System.Windows.DependencyObject.GetValue%2A> nebo. <xref:System.Windows.DependencyObject.SetValue%2A></span><span class="sxs-lookup"><span data-stu-id="b933d-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="b933d-110">Ale obvykle chcete, aby toto chování systému vlastností bylo paralelně paralelní s obálkami vlastností CLR.</span><span class="sxs-lookup"><span data-stu-id="b933d-110">But you typically want to parallel this property-system behavior with the CLR property wrappers.</span></span> <span data-ttu-id="b933d-111">Obálky usnadňují nastavení vlastnosti závislosti programově a umožňují nastavit vlastnosti jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy.</span><span class="sxs-lookup"><span data-stu-id="b933d-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="b933d-112">Chcete-li zjistit, jak přepsat výchozí metadata, přečtěte si téma [přepis metadat pro vlastnost závislosti](how-to-override-metadata-for-a-dependency-property.md).</span><span class="sxs-lookup"><span data-stu-id="b933d-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b933d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b933d-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="b933d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b933d-114">See also</span></span>

- [<span data-ttu-id="b933d-115">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="b933d-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="b933d-116">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="b933d-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
