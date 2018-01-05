---
title: "Postupy: Registrace připojené vlastnosti"
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
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c727eee7b56473808fec06ea42044fc742f7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="07bcc-102">Postupy: Registrace připojené vlastnosti</span><span class="sxs-lookup"><span data-stu-id="07bcc-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="07bcc-103">Tento příklad ukazuje způsob registrace přidružená vlastnost a poskytovat veřejné přístupových objektů, takže můžete použít vlastnost v obou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kód.</span><span class="sxs-lookup"><span data-stu-id="07bcc-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="07bcc-104">Přidružené vlastnosti jsou definované pomocí syntaxe koncept [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07bcc-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="07bcc-105">Většina přidružené vlastnosti pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy jsou implementované také jako vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="07bcc-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="07bcc-106">Můžete použít na všech vlastností závislostí <xref:System.Windows.DependencyObject> typy.</span><span class="sxs-lookup"><span data-stu-id="07bcc-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07bcc-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="07bcc-107">Example</span></span>  
 <span data-ttu-id="07bcc-108">Následující příklad ukazuje, jak zaregistrovat přidružená vlastnost jako vlastnost závislosti, s použitím <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="07bcc-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="07bcc-109">Třída zprostředkovatele má možnost poskytnout výchozí metadata pro vlastnost, která lze použít při vlastnost se používá na jiné třídy, pokud přepsání třídy metadat.</span><span class="sxs-lookup"><span data-stu-id="07bcc-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="07bcc-110">V tomto příkladu, výchozí hodnota `IsBubbleSource` je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="07bcc-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="07bcc-111">Třída zprostředkovatele (i když není registrován jako vlastnost závislosti) připojené vlastnosti musíte zadat statické get a sadu přístupových objektů, které následují zásady vytváření názvů `Set` *[AttachedPropertyName]* a `Get` *[AttachedPropertyName]*.</span><span class="sxs-lookup"><span data-stu-id="07bcc-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="07bcc-112">Tyto přístupové objekty jsou potřeba, aby funguje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky poznáte vlastnost jako atribut v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a vyřešení příslušných typů.</span><span class="sxs-lookup"><span data-stu-id="07bcc-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="07bcc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="07bcc-113">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="07bcc-114">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="07bcc-114">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="07bcc-115">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="07bcc-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="07bcc-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="07bcc-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
