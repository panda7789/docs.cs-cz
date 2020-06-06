---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128173"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="04b31-102">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="04b31-102">Runtime Directive Elements</span></span>
<span data-ttu-id="04b31-103">Formát souboru direktiv modulu runtime (RD. XML) podporuje následující elementy direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="04b31-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="04b31-104">Hierarchickou reprezentaci naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="04b31-105">Aplikuje zásady odrazu modulu runtime na všechny typy používané aplikací a slouží jako kontejner pro typy celé aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="04b31-105">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="04b31-106">Toto je podřízený [\<Directives>](directives-element-net-native.md) prvek elementu.</span><span class="sxs-lookup"><span data-stu-id="04b31-106">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="04b31-107">Použije zásady modulu runtime pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="04b31-107">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="04b31-108">Toto je podřízený prvek [\<Application>](application-element-net-native.md) a [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-108">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="04b31-109">Pokud [\<Type>](type-element-net-native.md) je direktiva obsahující direktiva atributem, aplikace aplikuje zásady modulu runtime na prvky kódu, na které se tento atribut aplikuje.</span><span class="sxs-lookup"><span data-stu-id="04b31-109">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="04b31-110">Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04b31-110">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="04b31-111">Jeho podřízené prvky jsou [\<Application>](application-element-net-native.md) a [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-111">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="04b31-112">Aplikuje zásady modulu runtime na událost.</span><span class="sxs-lookup"><span data-stu-id="04b31-112">Applies runtime policy to an event.</span></span> <span data-ttu-id="04b31-113">Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-113">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="04b31-114">Aplikuje na pole zásady modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="04b31-114">Applies runtime policy to a field.</span></span> <span data-ttu-id="04b31-115">Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-115">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="04b31-116">Aplikuje zásady modulu runtime na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="04b31-116">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="04b31-117">Aplikuje zásadu modulu runtime na typ, pokud byla tato zásada použita na obsahující typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="04b31-117">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="04b31-118">Použije zásady modulu runtime pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="04b31-118">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="04b31-119">Toto je podřízený prvek [\<Application>](application-element-net-native.md) a [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-119">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="04b31-120">Aplikuje zásady modulu runtime na metodu.</span><span class="sxs-lookup"><span data-stu-id="04b31-120">Applies runtime policy to a method.</span></span> <span data-ttu-id="04b31-121">Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="04b31-122">Aplikuje zásady modulu runtime na vytvořenou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="04b31-122">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="04b31-123">Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-123">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="04b31-124">Použije zásady modulu runtime pro všechny typy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="04b31-124">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="04b31-125">Aplikuje zásady modulu runtime na typ argumentu předaného metodě.</span><span class="sxs-lookup"><span data-stu-id="04b31-125">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="04b31-126">Aplikuje zásady modulu runtime na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="04b31-126">Applies runtime policy to a property.</span></span> <span data-ttu-id="04b31-127">Toto je podřízený prvek [\<Type>](type-element-net-native.md) a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04b31-127">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="04b31-128">Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="04b31-128">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="04b31-129">Použije zásady modulu runtime na typ.</span><span class="sxs-lookup"><span data-stu-id="04b31-129">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="04b31-130">Použije zásady modulu runtime na konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="04b31-130">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="04b31-131">Aplikuje zásady modulu runtime na typ reprezentovaný <xref:System.Type> argumentem předaným metodě.</span><span class="sxs-lookup"><span data-stu-id="04b31-131">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b31-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="04b31-132">See also</span></span>

- [<span data-ttu-id="04b31-133">Referenční dokumentace ke konfiguračnímu souboru Rd. XML</span><span class="sxs-lookup"><span data-stu-id="04b31-133">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
