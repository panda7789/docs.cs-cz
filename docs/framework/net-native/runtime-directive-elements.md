---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128173"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="3a3f3-102">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3a3f3-102">Runtime Directive Elements</span></span>
<span data-ttu-id="3a3f3-103">Formát souboru direktiv modulu runtime (RD. XML) podporuje následující elementy direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="3a3f3-104">Hierarchickou reprezentaci naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="3a3f3-105">\<> aplikace</span><span class="sxs-lookup"><span data-stu-id="3a3f3-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="3a3f3-106">Aplikuje zásady odrazu modulu runtime na všechny typy používané aplikací a slouží jako kontejner pro typy celé aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="3a3f3-107">Toto je podřízený prvek [direktiv\<](directives-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="3a3f3-108">\<> sestavení</span><span class="sxs-lookup"><span data-stu-id="3a3f3-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="3a3f3-109">Použije zásady modulu runtime pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="3a3f3-110">Toto je podřízený prvek [\<aplikace >](application-element-net-native.md) a\<prvky [> knihovny](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="3a3f3-111">\<AttributeImplies ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="3a3f3-112">Pokud je v něm obsažená direktiva [typu\<](type-element-net-native.md) je atribut, aplikuje zásady modulu runtime na prvky kódu, na které se tento atribut aplikuje.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="3a3f3-113">Direktivy \<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="3a3f3-114">Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="3a3f3-115">Jeho podřízené prvky jsou [\<aplikační >](application-element-net-native.md) a [\<knihovny >](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="3a3f3-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="3a3f3-116">> události \<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="3a3f3-117">Aplikuje zásady modulu runtime na událost.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="3a3f3-118">Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="3a3f3-119">\<pole ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="3a3f3-120">Aplikuje na pole zásady modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="3a3f3-121">Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="3a3f3-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="3a3f3-123">Aplikuje zásady modulu runtime na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="3a3f3-124">\<ImpliesType ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="3a3f3-125">Aplikuje zásadu modulu runtime na typ, pokud byla tato zásada použita na obsahující typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="3a3f3-126">> knihovny \<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="3a3f3-127">Použije zásady modulu runtime pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="3a3f3-128">Toto je podřízený prvek [\<aplikace >](application-element-net-native.md) a\<prvky [> knihovny](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="3a3f3-129">Metoda\<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="3a3f3-130">Aplikuje zásady modulu runtime na metodu.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="3a3f3-131">Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="3a3f3-132">\<MethodInstantiation ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="3a3f3-133">Aplikuje zásady modulu runtime na vytvořenou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="3a3f3-134">Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="3a3f3-135">Obor názvů \<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="3a3f3-136">Použije zásady modulu runtime pro všechny typy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="3a3f3-137">Parametr \<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="3a3f3-138">Aplikuje zásady modulu runtime na typ argumentu předaného metodě.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="3a3f3-139">Vlastnost \<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="3a3f3-140">Aplikuje zásady modulu runtime na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="3a3f3-141">Toto je podřízený [typ\<](type-element-net-native.md) a [\<prvky > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3a3f3-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="3a3f3-142">\<podtypy ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="3a3f3-143">Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="3a3f3-144">Typ\<</span><span class="sxs-lookup"><span data-stu-id="3a3f3-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="3a3f3-145">Použije zásady modulu runtime na typ.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="3a3f3-146">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="3a3f3-147">Použije zásady modulu runtime na konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="3a3f3-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="3a3f3-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="3a3f3-149">Aplikuje zásady modulu runtime na typ reprezentovaný argumentem <xref:System.Type> předaným metodě.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a3f3-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a3f3-150">See also</span></span>

- [<span data-ttu-id="3a3f3-151">Referenční dokumentace ke konfiguračnímu souboru Rd. XML</span><span class="sxs-lookup"><span data-stu-id="3a3f3-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
