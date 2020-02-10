---
title: mc:ProcessContent – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: bcf55668bdc70902e346c401549a88f6ccb9072e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095122"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="1c82d-102">mc:ProcessContent – atribut</span><span class="sxs-lookup"><span data-stu-id="1c82d-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="1c82d-103">Určuje, které prvky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mají stále obsah zpracovaný relevantními nadřazenými prvky, a to i v případě, že je přímý nadřazený prvek možné ignorovat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ým procesorem z důvodu určení [atributu MC: ignorováno](mc-ignorable-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="1c82d-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="1c82d-104">Atribut `mc:ProcessContent` podporuje kompatibilitu značek pro vlastní mapování oboru názvů a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správu verzí.</span><span class="sxs-lookup"><span data-stu-id="1c82d-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1c82d-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="1c82d-105">XAML Attribute Usage</span></span>  
  
```xaml  
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
  
## <a name="xaml-values"></a><span data-ttu-id="1c82d-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="1c82d-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c82d-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="1c82d-107">*ignorablePrefix*</span></span>|<span data-ttu-id="1c82d-108">Libovolný platný řetězec předpony podle specifikace XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="1c82d-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="1c82d-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="1c82d-109">*ignorableUri*</span></span>|<span data-ttu-id="1c82d-110">Libovolný platný identifikátor URI pro určení oboru názvů podle specifikace XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="1c82d-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="1c82d-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="1c82d-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="1c82d-112">Element, který může být ignorován pomocí implementace [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] procesoru, pokud nelze přeložit nadřízený typ.</span><span class="sxs-lookup"><span data-stu-id="1c82d-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="1c82d-113">*sušin*</span><span class="sxs-lookup"><span data-stu-id="1c82d-113">*[content]*</span></span>|<span data-ttu-id="1c82d-114">*ThisElementCanBeIgnored* je označeno jako ignorovatelné.</span><span class="sxs-lookup"><span data-stu-id="1c82d-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="1c82d-115">Pokud procesor tento prvek ignoruje, je objekt *[Content]* zpracován pomocí *objektu*.</span><span class="sxs-lookup"><span data-stu-id="1c82d-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c82d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c82d-116">Remarks</span></span>  
 <span data-ttu-id="1c82d-117">Ve výchozím nastavení bude procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorovat obsah v rámci ignorovaného prvku.</span><span class="sxs-lookup"><span data-stu-id="1c82d-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="1c82d-118">Můžete určit konkrétní prvek pomocí `mc:ProcessContent`a procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bude pokračovat ve zpracování obsahu v rámci ignorovaného prvku.</span><span class="sxs-lookup"><span data-stu-id="1c82d-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="1c82d-119">Tato část by se obvykle použila v případě, že je obsah vnořen do několika značek, nejméně jeden z nich je ignorován a nejméně jeden z nich nelze ignorovat.</span><span class="sxs-lookup"><span data-stu-id="1c82d-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="1c82d-120">V atributu lze zadat více předpon pomocí oddělovače mezer, například: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="1c82d-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="1c82d-121">Obor názvů `http://schemas.openxmlformats.org/markup-compatibility/2006` definuje další prvky a atributy, které nejsou zdokumentovány v této oblasti sady SDK.</span><span class="sxs-lookup"><span data-stu-id="1c82d-121">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="1c82d-122">Další informace najdete v tématu [specifikace kompatibility značek XML](https://docs.microsoft.com/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="1c82d-122">For more information, see [XML Markup Compatibility Specification](https://docs.microsoft.com/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c82d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c82d-123">See also</span></span>

- [<span data-ttu-id="1c82d-124">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="1c82d-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="1c82d-125">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1c82d-125">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
