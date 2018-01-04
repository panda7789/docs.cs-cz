---
title: Elementy direktivy modulu runtime
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2566c5ebe8c94610c8f7e258da7c77adb86a49f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="ac622-102">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ac622-102">Runtime Directive Elements</span></span>
<span data-ttu-id="ac622-103">Formát souboru runtime (rd.xml) direktivy podporuje následující elementy direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ac622-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="ac622-104">V tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) pro znázornění hierarchické.</span><span class="sxs-lookup"><span data-stu-id="ac622-104">See [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="ac622-105">\<Aplikace ></span><span class="sxs-lookup"><span data-stu-id="ac622-105">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 <span data-ttu-id="ac622-106">Platí zásady reflexe modulu runtime pro všechny typy používané aplikace a slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.</span><span class="sxs-lookup"><span data-stu-id="ac622-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="ac622-107">Toto je podřízený [ \<direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="ac622-107">This is a child of the [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="ac622-108">\<Sestavení ></span><span class="sxs-lookup"><span data-stu-id="ac622-108">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 <span data-ttu-id="ac622-109">Runnntime zásad platí pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac622-109">Applies runnntime policy to all the types in an assembly.</span></span> <span data-ttu-id="ac622-110">Toto je podřízený [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="ac622-110">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="ac622-111">\<AttributeImplies ></span><span class="sxs-lookup"><span data-stu-id="ac622-111">\<AttributeImplies></span></span>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 <span data-ttu-id="ac622-112">Pokud jeho obsahující [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) – direktiva je atributem, platí zásady modulu runtime pro elementy kódu, pro které platí tento atribut.</span><span class="sxs-lookup"><span data-stu-id="ac622-112">If its containing [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="ac622-113">\<Direktivy jazyka ></span><span class="sxs-lookup"><span data-stu-id="ac622-113">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 <span data-ttu-id="ac622-114">Kořenový element v každém souboru direktivy modulu runtime pro [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac622-114">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="ac622-115">Její podřízené elementy jsou [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="ac622-115">Its child elements are [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="ac622-116">\<Událost ></span><span class="sxs-lookup"><span data-stu-id="ac622-116">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)  
 <span data-ttu-id="ac622-117">Platí zásady modulu runtime pro událost.</span><span class="sxs-lookup"><span data-stu-id="ac622-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="ac622-118">Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="ac622-118">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="ac622-119">\<Pole ></span><span class="sxs-lookup"><span data-stu-id="ac622-119">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)  
 <span data-ttu-id="ac622-120">Platí zásady modulu runtime pro pole.</span><span class="sxs-lookup"><span data-stu-id="ac622-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="ac622-121">Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="ac622-121">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="ac622-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="ac622-122">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 <span data-ttu-id="ac622-123">Zásady modulu runtime se vztahuje na typ parametru obecný typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="ac622-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="ac622-124">\<ImpliesType ></span><span class="sxs-lookup"><span data-stu-id="ac622-124">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 <span data-ttu-id="ac622-125">Platí zásady modulu runtime pro typu, v případě, že zásada obsahující typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="ac622-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="ac622-126">\<Knihovna ></span><span class="sxs-lookup"><span data-stu-id="ac622-126">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 <span data-ttu-id="ac622-127">Modul runtime zásad platí pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac622-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="ac622-128">Toto je podřízený [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) a [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="ac622-128">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="ac622-129">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="ac622-129">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 <span data-ttu-id="ac622-130">Platí zásady modulu runtime pro metodu.</span><span class="sxs-lookup"><span data-stu-id="ac622-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="ac622-131">Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="ac622-131">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="ac622-132">\<MethodInstantiation ></span><span class="sxs-lookup"><span data-stu-id="ac622-132">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 <span data-ttu-id="ac622-133">Sestavené obecné metody se týká zásady modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ac622-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="ac622-134">Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="ac622-134">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="ac622-135">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="ac622-135">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 <span data-ttu-id="ac622-136">Modul runtime zásad platí pro všechny typy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ac622-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="ac622-137">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="ac622-137">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 <span data-ttu-id="ac622-138">Zásady modulu runtime se vztahuje na typ argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="ac622-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="ac622-139">\<Vlastnost ></span><span class="sxs-lookup"><span data-stu-id="ac622-139">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)  
 <span data-ttu-id="ac622-140">Vlastnost se týká zásady modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ac622-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="ac622-141">Toto je podřízený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) a [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="ac622-141">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="ac622-142">\<Subtypes ></span><span class="sxs-lookup"><span data-stu-id="ac622-142">\<Subtypes></span></span>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 <span data-ttu-id="ac622-143">Modul runtime zásad platí pro všechny třídy dědí z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="ac622-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="ac622-144">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="ac622-144">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 <span data-ttu-id="ac622-145">Platí pro typ zásady modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ac622-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="ac622-146">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="ac622-146">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 <span data-ttu-id="ac622-147">Platí zásady modulu runtime pro vytvořený obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ac622-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="ac622-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="ac622-148">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 <span data-ttu-id="ac622-149">Zásady modulu runtime se vztahuje na typ zastoupený <xref:System.Type> argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="ac622-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac622-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac622-150">See Also</span></span>  
 [<span data-ttu-id="ac622-151">Odkaz na soubor RD.XML konfigurace</span><span class="sxs-lookup"><span data-stu-id="ac622-151">rd.xml Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
