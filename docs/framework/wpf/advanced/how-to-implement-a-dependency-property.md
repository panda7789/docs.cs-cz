---
title: 'Postupy: Implementace vlastnosti závislosti'
description: Definujte vlastnost závislosti v Windows Presentation Foundation tím, že zadáte zálohu vlastnosti modulu CLR (Common Language Runtime) s polem DependencyProperty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 673f653a9b02627efcccdfe08c4812ca0834217c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165092"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="0a732-103">Postupy: Implementace vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="0a732-103">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="0a732-104">Tento příklad ukazuje, jak zálohovat vlastnost modulu CLR (Common Language Runtime) s <xref:System.Windows.DependencyProperty> polem a definovat tak vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="0a732-104">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="0a732-105">Pokud definujete vlastní vlastnosti a chcete, aby podporovaly spoustu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcí, včetně stylů, datových vazeb, dědičnosti, animace a výchozích hodnot, měli byste je implementovat jako vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="0a732-105">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a732-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a732-106">Example</span></span>  
 <span data-ttu-id="0a732-107">V následujícím příkladu je nejprve registrována vlastnost závislosti voláním <xref:System.Windows.DependencyProperty.Register%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0a732-107">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="0a732-108">Název pole identifikátor, který použijete k uložení názvu a vlastností závislosti, musí být <xref:System.Windows.DependencyProperty.Name%2A> zvolen pro vlastnost závislosti jako součást <xref:System.Windows.DependencyProperty.Register%2A> volání, která je připojena pomocí řetězcového literálu `Property` .</span><span class="sxs-lookup"><span data-stu-id="0a732-108">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="0a732-109">Pokud například zaregistrujete vlastnost závislosti s parametrem <xref:System.Windows.DependencyProperty.Name%2A> `Location` , musí být pole identifikátor, které definujete pro vlastnost Dependency, pojmenováno `LocationProperty` .</span><span class="sxs-lookup"><span data-stu-id="0a732-109">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="0a732-110">V tomto příkladu je název vlastnosti závislosti a jejího přístupového objektu CLR `State` ; pole identifikátoru je `StateProperty` ; typ vlastnosti je <xref:System.Boolean> ; a typ, který zaregistruje vlastnost závislosti, je `MyStateControl` .</span><span class="sxs-lookup"><span data-stu-id="0a732-110">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="0a732-111">Pokud se nedaří postupovat podle tohoto vzoru pojmenování, Návrháři nemusí správně nahlásit vlastnost a některé aspekty aplikace stylu systému vlastností se nemusí chovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="0a732-111">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="0a732-112">Můžete také zadat výchozí metadata pro vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="0a732-112">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="0a732-113">Tento příklad registruje výchozí hodnotu `State` vlastnosti závislosti, která má být `false` .</span><span class="sxs-lookup"><span data-stu-id="0a732-113">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="0a732-114">Další informace o tom, jak a proč implementovat vlastnost závislosti, na rozdíl od pouhého zálohování vlastnosti CLR s privátním polem, najdete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0a732-114">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a732-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a732-115">See also</span></span>

- [<span data-ttu-id="0a732-116">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="0a732-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="0a732-117">– postupy</span><span class="sxs-lookup"><span data-stu-id="0a732-117">How-to Topics</span></span>](properties-how-to-topics.md)
