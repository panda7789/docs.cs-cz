---
title: 'Postupy: Registrace přidružené vlastnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 4c678a64b62b8f4db24cf39ffbafac52e56c9982
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768677"
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="ea54b-102">Postupy: Registrace přidružené vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ea54b-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="ea54b-103">Tento příklad ukazuje, jak registrace připojené vlastnosti a zadejte veřejnou přistupující objekty tak, aby vlastnost můžete použít v obou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kódu.</span><span class="sxs-lookup"><span data-stu-id="ea54b-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="ea54b-104">Připojené vlastnosti jsou koncept syntaxi definované [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea54b-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="ea54b-105">Většina přidružené vlastnosti pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy jsou také implementovány jako vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="ea54b-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="ea54b-106">Vlastnosti závislostí lze použít na jakémkoli <xref:System.Windows.DependencyObject> typy.</span><span class="sxs-lookup"><span data-stu-id="ea54b-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea54b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea54b-107">Example</span></span>  
 <span data-ttu-id="ea54b-108">Následující příklad ukazuje, jak registrace připojené vlastnosti jako vlastnost závislosti, s použitím <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ea54b-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="ea54b-109">Třída zprostředkovatele má možnost poskytnout výchozí metadat pro vlastnost, která lze použít při vlastnost se používá na jiné třídy, pokud tuto třídu přepisuje metadata.</span><span class="sxs-lookup"><span data-stu-id="ea54b-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="ea54b-110">V tomto příkladu, výchozí hodnota `IsBubbleSource` je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="ea54b-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="ea54b-111">Třída zprostředkovatele pro připojené vlastnosti (i když není registrován jako vlastnost závislosti) musí poskytnout statické get a set přistupující objekty, které podle konvence `Set` *[AttachedPropertyName]* a `Get` *[AttachedPropertyName]*.</span><span class="sxs-lookup"><span data-stu-id="ea54b-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="ea54b-112">Tyto přístupové objekty jsou vyžadovány tak, aby jednající [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky dokáže rozpoznat vlastnost jako atribut v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a vyřešení příslušných typů.</span><span class="sxs-lookup"><span data-stu-id="ea54b-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="ea54b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea54b-113">See also</span></span>

- <xref:System.Windows.DependencyProperty>
- [<span data-ttu-id="ea54b-114">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="ea54b-114">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="ea54b-115">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="ea54b-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="ea54b-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ea54b-116">How-to Topics</span></span>](properties-how-to-topics.md)
