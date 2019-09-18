---
title: Elementy direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049273"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="08e83-102">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="08e83-102">Runtime Directive Elements</span></span>
<span data-ttu-id="08e83-103">Formát souboru direktiv modulu runtime (RD. XML) podporuje následující elementy direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="08e83-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="08e83-104">Hierarchickou reprezentaci naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="08e83-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="08e83-105">\<> Aplikace</span><span class="sxs-lookup"><span data-stu-id="08e83-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="08e83-106">Aplikuje zásady odrazu modulu runtime na všechny typy používané aplikací a slouží jako kontejner pro typy celé aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="08e83-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="08e83-107">Toto je podřízený [ \<prvek direktiv >](directives-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="08e83-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="08e83-108">\<> Sestavení</span><span class="sxs-lookup"><span data-stu-id="08e83-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="08e83-109">Použije zásady modulu runtime pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="08e83-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="08e83-110">Toto je podřízený objekt [ \<aplikace >](application-element-net-native.md) a [ \<> prvků knihovny](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="08e83-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="08e83-111">\<AttributeImplies ></span><span class="sxs-lookup"><span data-stu-id="08e83-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="08e83-112">Pokud je jeho nadřazeným [ \<typem](type-element-net-native.md) direktiva > atribut, aplikuje zásady modulu runtime na prvky kódu, na které se tento atribut aplikuje.</span><span class="sxs-lookup"><span data-stu-id="08e83-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="08e83-113">\<> Direktiv</span><span class="sxs-lookup"><span data-stu-id="08e83-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="08e83-114">Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="08e83-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="08e83-115">Jeho podřízené prvky jsou [ \<aplikace >](application-element-net-native.md) a [ \<> knihovny](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="08e83-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="08e83-116">\<> Události</span><span class="sxs-lookup"><span data-stu-id="08e83-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="08e83-117">Aplikuje zásady modulu runtime na událost.</span><span class="sxs-lookup"><span data-stu-id="08e83-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="08e83-118">Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.</span><span class="sxs-lookup"><span data-stu-id="08e83-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="08e83-119">\<> Pole</span><span class="sxs-lookup"><span data-stu-id="08e83-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="08e83-120">Aplikuje na pole zásady modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="08e83-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="08e83-121">Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.</span><span class="sxs-lookup"><span data-stu-id="08e83-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="08e83-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="08e83-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="08e83-123">Aplikuje zásady modulu runtime na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="08e83-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="08e83-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="08e83-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="08e83-125">Aplikuje zásadu modulu runtime na typ, pokud byla tato zásada použita na obsahující typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="08e83-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="08e83-126">\<Library></span><span class="sxs-lookup"><span data-stu-id="08e83-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="08e83-127">Použije zásady modulu runtime pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="08e83-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="08e83-128">Toto je podřízený objekt [ \<aplikace >](application-element-net-native.md) a [ \<> prvků knihovny](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="08e83-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="08e83-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="08e83-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="08e83-130">Aplikuje zásady modulu runtime na metodu.</span><span class="sxs-lookup"><span data-stu-id="08e83-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="08e83-131">Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.</span><span class="sxs-lookup"><span data-stu-id="08e83-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="08e83-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="08e83-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="08e83-133">Aplikuje zásady modulu runtime na vytvořenou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="08e83-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="08e83-134">Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.</span><span class="sxs-lookup"><span data-stu-id="08e83-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="08e83-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="08e83-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="08e83-136">Použije zásady modulu runtime pro všechny typy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="08e83-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="08e83-137">\<> Parametru</span><span class="sxs-lookup"><span data-stu-id="08e83-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="08e83-138">Aplikuje zásady modulu runtime na typ argumentu předaného metodě.</span><span class="sxs-lookup"><span data-stu-id="08e83-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="08e83-139">\<> Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="08e83-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="08e83-140">Aplikuje zásady modulu runtime na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="08e83-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="08e83-141">Toto je podřízený objekt [ \<typu >](type-element-net-native.md) a [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) prvky.</span><span class="sxs-lookup"><span data-stu-id="08e83-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="08e83-142">\<> Podtypů</span><span class="sxs-lookup"><span data-stu-id="08e83-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="08e83-143">Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="08e83-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="08e83-144">\<Zadejte ></span><span class="sxs-lookup"><span data-stu-id="08e83-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="08e83-145">Použije zásady modulu runtime na typ.</span><span class="sxs-lookup"><span data-stu-id="08e83-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="08e83-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="08e83-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="08e83-147">Použije zásady modulu runtime na konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="08e83-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="08e83-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="08e83-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="08e83-149">Aplikuje zásady modulu runtime na typ reprezentovaný <xref:System.Type> argumentem předaným metodě.</span><span class="sxs-lookup"><span data-stu-id="08e83-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e83-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08e83-150">See also</span></span>

- [<span data-ttu-id="08e83-151">Referenční dokumentace ke konfiguračnímu souboru Rd. XML</span><span class="sxs-lookup"><span data-stu-id="08e83-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
