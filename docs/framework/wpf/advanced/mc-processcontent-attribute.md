---
title: mc:ProcessContent – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 59097959ff4b3efaba4e4ee63d308eb21f91529d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187045"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="fa779-102">mc:ProcessContent – atribut</span><span class="sxs-lookup"><span data-stu-id="fa779-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="fa779-103">Určuje, které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky by měl mít pořád obsahu zpracovaných příslušné nadřazené elementy i v případě, že bezprostřední nadřazený element může ignorovat. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru kvůli určení [mc: ignorable – atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="fa779-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="fa779-104">`mc:ProcessContent` Atribut podporuje kompatibility značek pro vlastní obor názvů mapování a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.</span><span class="sxs-lookup"><span data-stu-id="fa779-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="fa779-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="fa779-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="fa779-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="fa779-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa779-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="fa779-107">*ignorablePrefix*</span></span>|<span data-ttu-id="fa779-108">Libovolný platnou předponu řetězec podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="fa779-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="fa779-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="fa779-109">*ignorableUri*</span></span>|<span data-ttu-id="fa779-110">Libovolný platný identifikátor URI pro určení oboru názvů, podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="fa779-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="fa779-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="fa779-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="fa779-112">Element, který lze ignorovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace, pokud nadřazený typ není možné přeložit.</span><span class="sxs-lookup"><span data-stu-id="fa779-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="fa779-113">*[obsah]*</span><span class="sxs-lookup"><span data-stu-id="fa779-113">*[content]*</span></span>|<span data-ttu-id="fa779-114">*ThisElementCanBeIgnored* označen jako ignorable.</span><span class="sxs-lookup"><span data-stu-id="fa779-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="fa779-115">Pokud procesor ignoruje tento prvek *[obsah]* zpracovává *objekt*.</span><span class="sxs-lookup"><span data-stu-id="fa779-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa779-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa779-116">Remarks</span></span>  
 <span data-ttu-id="fa779-117">Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor bude ignorovat obsah v rámci elementu ignorované.</span><span class="sxs-lookup"><span data-stu-id="fa779-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="fa779-118">Můžete zadat konkrétní elementu podle `mc:ProcessContent`a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor bude pokračovat ve zpracování obsahu v rámci elementu ignorované.</span><span class="sxs-lookup"><span data-stu-id="fa779-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="fa779-119">To by obvykle použijí, pokud obsah je vnořená v rámci několik značek, nejméně jeden z nich je možné ignorovat, a nejméně jeden z nich není ignorable.</span><span class="sxs-lookup"><span data-stu-id="fa779-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="fa779-120">Několik předpon je možné zadat atribut, pomocí oddělovače. místo, například: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="fa779-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="fa779-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Obor názvů definuje další prvky a atributy, které nejsou uvedené v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa779-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="fa779-122">Další informace najdete v tématu [specifikace kompatibility značek XML](https://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="fa779-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa779-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa779-123">See Also</span></span>  
 [<span data-ttu-id="fa779-124">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="fa779-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="fa779-125">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="fa779-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
