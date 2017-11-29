---
title: "Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2ecfc61c5b586dd3385890d73ded729a38fb41c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="0a735-102">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0a735-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>
<span data-ttu-id="0a735-103">Direktivy modulu runtime (. rd.xml) soubor je konfigurační soubor XML, který určuje, zda jsou k dispozici pro reflexi prvky určené programu.</span><span class="sxs-lookup"><span data-stu-id="0a735-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="0a735-104">Tady je příklad souboru direktivy modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="0a735-104">Here’s an example of a runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
<Application>  
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />  
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />  
  
  <Namespace Name="System.Collections.ObjectModel" >  
    <TypeInstantiation Name="ObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />  
    <TypeInstantiation Name="ReadOnlyObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />  
  </Namespace>  
</Application>  
</Directives>  
```  
  
## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="0a735-105">Struktura souboru direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0a735-105">The structure of a runtime directives file</span></span>  
 <span data-ttu-id="0a735-106">Direktivy modulu runtime souborů používá `http://schemas.microsoft.com/netfx/2013/01/metadata` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0a735-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>  
  
 <span data-ttu-id="0a735-107">Kořenový element [direktivy](../../../docs/framework/net-native/directives-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0a735-107">The root element is the [Directives](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span> <span data-ttu-id="0a735-108">Může obsahovat nula nebo více [knihovny](../../../docs/framework/net-native/library-element-net-native.md) prvky a nula nebo jedna [aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu, jak je znázorněno v následující strukturu.</span><span class="sxs-lookup"><span data-stu-id="0a735-108">It can contain zero or more [Library](../../../docs/framework/net-native/library-element-net-native.md) elements, and zero or one [Application](../../../docs/framework/net-native/application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="0a735-109">Atributy [aplikace](../../../docs/framework/net-native/application-element-net-native.md) element můžete definovat zásady reflexe modulu runtime celou aplikaci, nebo může sloužit jako kontejner pro podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="0a735-109">The attributes of the [Application](../../../docs/framework/net-native/application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="0a735-110">[Knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementu, na druhé straně je jednoduše kontejner.</span><span class="sxs-lookup"><span data-stu-id="0a735-110">The [Library](../../../docs/framework/net-native/library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="0a735-111">Podřízené objekty daného [aplikace](../../../docs/framework/net-native/application-element-net-native.md) a [knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementy definovat typy, metody, pole, vlastnosti a události, které jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="0a735-111">The children of the [Application](../../../docs/framework/net-native/application-element-net-native.md) and [Library](../../../docs/framework/net-native/library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>  
  
 <span data-ttu-id="0a735-112">Referenční informace, vyberte elementy z následující strukturu nebo najdete v části [elementy direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="0a735-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md).</span></span> <span data-ttu-id="0a735-113">V následující hierarchie se třemi tečkami označí rekurzivní struktury.</span><span class="sxs-lookup"><span data-stu-id="0a735-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="0a735-114">Informace v závorkách označuje, zda je daný element požadované nebo volitelné a pokud se používá, kolik instance (jeden nebo více) jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="0a735-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>  
  
 <span data-ttu-id="0a735-115">[Direktivy](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="0a735-115">[Directives](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span></span>  
 <span data-ttu-id="0a735-116">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="0a735-116">[Application](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span></span>  
 <span data-ttu-id="0a735-117">[Sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-117">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-119">.</span><span class="sxs-lookup"><span data-stu-id="0a735-119">.</span></span> <span data-ttu-id="0a735-120">.</span><span class="sxs-lookup"><span data-stu-id="0a735-120">.</span></span> <span data-ttu-id="0a735-121">.</span><span class="sxs-lookup"><span data-stu-id="0a735-121">.</span></span>  
 <span data-ttu-id="0a735-122">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-122">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-123">.</span><span class="sxs-lookup"><span data-stu-id="0a735-123">.</span></span> <span data-ttu-id="0a735-124">.</span><span class="sxs-lookup"><span data-stu-id="0a735-124">.</span></span> <span data-ttu-id="0a735-125">.</span><span class="sxs-lookup"><span data-stu-id="0a735-125">.</span></span>  
 <span data-ttu-id="0a735-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-127">.</span><span class="sxs-lookup"><span data-stu-id="0a735-127">.</span></span> <span data-ttu-id="0a735-128">.</span><span class="sxs-lookup"><span data-stu-id="0a735-128">.</span></span> <span data-ttu-id="0a735-129">.</span><span class="sxs-lookup"><span data-stu-id="0a735-129">.</span></span>  
 <span data-ttu-id="0a735-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-132">.</span><span class="sxs-lookup"><span data-stu-id="0a735-132">.</span></span> <span data-ttu-id="0a735-133">.</span><span class="sxs-lookup"><span data-stu-id="0a735-133">.</span></span> <span data-ttu-id="0a735-134">.</span><span class="sxs-lookup"><span data-stu-id="0a735-134">.</span></span>  
 <span data-ttu-id="0a735-135">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-135">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-136">.</span><span class="sxs-lookup"><span data-stu-id="0a735-136">.</span></span> <span data-ttu-id="0a735-137">.</span><span class="sxs-lookup"><span data-stu-id="0a735-137">.</span></span> <span data-ttu-id="0a735-138">.</span><span class="sxs-lookup"><span data-stu-id="0a735-138">.</span></span>  
 <span data-ttu-id="0a735-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-140">.</span><span class="sxs-lookup"><span data-stu-id="0a735-140">.</span></span> <span data-ttu-id="0a735-141">.</span><span class="sxs-lookup"><span data-stu-id="0a735-141">.</span></span> <span data-ttu-id="0a735-142">.</span><span class="sxs-lookup"><span data-stu-id="0a735-142">.</span></span>  
 <span data-ttu-id="0a735-143">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-143">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-144">[Podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy obsahující typu) [O:1]</span><span class="sxs-lookup"><span data-stu-id="0a735-144">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="0a735-145">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-145">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-146">.</span><span class="sxs-lookup"><span data-stu-id="0a735-146">.</span></span> <span data-ttu-id="0a735-147">.</span><span class="sxs-lookup"><span data-stu-id="0a735-147">.</span></span> <span data-ttu-id="0a735-148">.</span><span class="sxs-lookup"><span data-stu-id="0a735-148">.</span></span>  
 <span data-ttu-id="0a735-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-150">.</span><span class="sxs-lookup"><span data-stu-id="0a735-150">.</span></span> <span data-ttu-id="0a735-151">.</span><span class="sxs-lookup"><span data-stu-id="0a735-151">.</span></span> <span data-ttu-id="0a735-152">.</span><span class="sxs-lookup"><span data-stu-id="0a735-152">.</span></span>  
 <span data-ttu-id="0a735-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]</span><span class="sxs-lookup"><span data-stu-id="0a735-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="0a735-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-155">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-155">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-156">[Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-156">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="0a735-160">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-160">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-161">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-161">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-162">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-162">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-164">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-164">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-165">.</span><span class="sxs-lookup"><span data-stu-id="0a735-165">.</span></span> <span data-ttu-id="0a735-166">.</span><span class="sxs-lookup"><span data-stu-id="0a735-166">.</span></span> <span data-ttu-id="0a735-167">.</span><span class="sxs-lookup"><span data-stu-id="0a735-167">.</span></span>  
 <span data-ttu-id="0a735-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-169">.</span><span class="sxs-lookup"><span data-stu-id="0a735-169">.</span></span> <span data-ttu-id="0a735-170">.</span><span class="sxs-lookup"><span data-stu-id="0a735-170">.</span></span> <span data-ttu-id="0a735-171">.</span><span class="sxs-lookup"><span data-stu-id="0a735-171">.</span></span>  
 <span data-ttu-id="0a735-172">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-172">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-173">[Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-173">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="0a735-177">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-177">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-178">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-178">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-179">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-179">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-180">[Knihovna](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-180">[Library](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-181">[Sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-181">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-183">.</span><span class="sxs-lookup"><span data-stu-id="0a735-183">.</span></span> <span data-ttu-id="0a735-184">.</span><span class="sxs-lookup"><span data-stu-id="0a735-184">.</span></span> <span data-ttu-id="0a735-185">.</span><span class="sxs-lookup"><span data-stu-id="0a735-185">.</span></span>  
 <span data-ttu-id="0a735-186">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-186">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-187">.</span><span class="sxs-lookup"><span data-stu-id="0a735-187">.</span></span> <span data-ttu-id="0a735-188">.</span><span class="sxs-lookup"><span data-stu-id="0a735-188">.</span></span> <span data-ttu-id="0a735-189">.</span><span class="sxs-lookup"><span data-stu-id="0a735-189">.</span></span>  
 <span data-ttu-id="0a735-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-191">.</span><span class="sxs-lookup"><span data-stu-id="0a735-191">.</span></span> <span data-ttu-id="0a735-192">.</span><span class="sxs-lookup"><span data-stu-id="0a735-192">.</span></span> <span data-ttu-id="0a735-193">.</span><span class="sxs-lookup"><span data-stu-id="0a735-193">.</span></span>  
 <span data-ttu-id="0a735-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-196">.</span><span class="sxs-lookup"><span data-stu-id="0a735-196">.</span></span> <span data-ttu-id="0a735-197">.</span><span class="sxs-lookup"><span data-stu-id="0a735-197">.</span></span> <span data-ttu-id="0a735-198">.</span><span class="sxs-lookup"><span data-stu-id="0a735-198">.</span></span>  
 <span data-ttu-id="0a735-199">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-199">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-200">.</span><span class="sxs-lookup"><span data-stu-id="0a735-200">.</span></span> <span data-ttu-id="0a735-201">.</span><span class="sxs-lookup"><span data-stu-id="0a735-201">.</span></span> <span data-ttu-id="0a735-202">.</span><span class="sxs-lookup"><span data-stu-id="0a735-202">.</span></span>  
 <span data-ttu-id="0a735-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-204">.</span><span class="sxs-lookup"><span data-stu-id="0a735-204">.</span></span> <span data-ttu-id="0a735-205">.</span><span class="sxs-lookup"><span data-stu-id="0a735-205">.</span></span> <span data-ttu-id="0a735-206">.</span><span class="sxs-lookup"><span data-stu-id="0a735-206">.</span></span>  
 <span data-ttu-id="0a735-207">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-207">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-208">[Podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy obsahující typu) [O:1]</span><span class="sxs-lookup"><span data-stu-id="0a735-208">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="0a735-209">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-209">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-210">.</span><span class="sxs-lookup"><span data-stu-id="0a735-210">.</span></span> <span data-ttu-id="0a735-211">.</span><span class="sxs-lookup"><span data-stu-id="0a735-211">.</span></span> <span data-ttu-id="0a735-212">.</span><span class="sxs-lookup"><span data-stu-id="0a735-212">.</span></span>  
 <span data-ttu-id="0a735-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-214">.</span><span class="sxs-lookup"><span data-stu-id="0a735-214">.</span></span> <span data-ttu-id="0a735-215">.</span><span class="sxs-lookup"><span data-stu-id="0a735-215">.</span></span> <span data-ttu-id="0a735-216">.</span><span class="sxs-lookup"><span data-stu-id="0a735-216">.</span></span>  
 <span data-ttu-id="0a735-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]</span><span class="sxs-lookup"><span data-stu-id="0a735-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="0a735-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-219">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-219">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="0a735-221">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-221">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-222">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-222">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-223">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-223">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-225">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-225">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-226">.</span><span class="sxs-lookup"><span data-stu-id="0a735-226">.</span></span> <span data-ttu-id="0a735-227">.</span><span class="sxs-lookup"><span data-stu-id="0a735-227">.</span></span> <span data-ttu-id="0a735-228">.</span><span class="sxs-lookup"><span data-stu-id="0a735-228">.</span></span>  
 <span data-ttu-id="0a735-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="0a735-230">.</span><span class="sxs-lookup"><span data-stu-id="0a735-230">.</span></span> <span data-ttu-id="0a735-231">.</span><span class="sxs-lookup"><span data-stu-id="0a735-231">.</span></span> <span data-ttu-id="0a735-232">.</span><span class="sxs-lookup"><span data-stu-id="0a735-232">.</span></span>  
 <span data-ttu-id="0a735-233">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-233">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="0a735-235">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-235">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-236">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-236">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="0a735-237">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="0a735-237">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
  
 <span data-ttu-id="0a735-238">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) element může mít žádné atributy, nebo můžete mít atributy zásad popsané v [Runtime – direktiva a zásady části](#Directives).</span><span class="sxs-lookup"><span data-stu-id="0a735-238">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>  
  
 <span data-ttu-id="0a735-239">A [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element má jeden atribut, `Name`, který určuje název sestavení, bez jeho přípona souboru nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="0a735-239">A [Library](../../../docs/framework/net-native/library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="0a735-240">Například následující [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element se vztahuje na sestavení s názvem Extensions.dll.</span><span class="sxs-lookup"><span data-stu-id="0a735-240">For example, the following [Library](../../../docs/framework/net-native/library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <!-- Child elements go here -->    
  </Application>  
  <Library Name="Extensions">  
     <!-- Child elements go here -->    
  </Library>  
</Directives>  
```  
  
<a name="Directives"></a>   
## <a name="runtime-directives-and-policy"></a><span data-ttu-id="0a735-241">Direktivy modulu runtime a zásady</span><span class="sxs-lookup"><span data-stu-id="0a735-241">Runtime directives and policy</span></span>  
 <span data-ttu-id="0a735-242">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu samotnému a podřízených elementů [knihovny](../../../docs/framework/net-native/library-element-net-native.md) a [aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementy vyjádření zásad; to znamená, že definují způsob, ve kterém můžete použít aplikaci reflexe do programu elementu.</span><span class="sxs-lookup"><span data-stu-id="0a735-242">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element itself and the child elements of the [Library](../../../docs/framework/net-native/library-element-net-native.md) and [Application](../../../docs/framework/net-native/application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="0a735-243">Typ zásad je definován atribut elementu (například `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="0a735-243">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="0a735-244">Hodnota zásady je definován hodnotou atributu (například `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="0a735-244">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>  
  
 <span data-ttu-id="0a735-245">Žádné zásady určeného atribut elementu se vztahuje na všechny podřízené prvky, které nezadávejte hodnotu pro tuto zásadu.</span><span class="sxs-lookup"><span data-stu-id="0a735-245">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="0a735-246">Například, pokud je zadána zásadu [typ](../../../docs/framework/net-native/type-element-net-native.md) elementu, které zásady platí pro všechny obsažené typy a členy, pro které není explicitně zadané zásady.</span><span class="sxs-lookup"><span data-stu-id="0a735-246">For example, if a policy is specified by a [Type](../../../docs/framework/net-native/type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>  
  
 <span data-ttu-id="0a735-247">Zásady, které může být vyjádřená [aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md), a [typ](../../../docs/framework/net-native/type-element-net-native.md) elementy se liší od zásad, který může být vyjádřený pro jednotlivé členy (pomocí [metoda](../../../docs/framework/net-native/method-element-net-native.md), [vlastnost](../../../docs/framework/net-native/property-element-net-native.md), [Pole](../../../docs/framework/net-native/field-element-net-native.md), a [událostí](../../../docs/framework/net-native/event-element-net-native.md) elementy).</span><span class="sxs-lookup"><span data-stu-id="0a735-247">The policy that can be expressed by the [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](../../../docs/framework/net-native/method-element-net-native.md), [Property](../../../docs/framework/net-native/property-element-net-native.md), [Field](../../../docs/framework/net-native/field-element-net-native.md), and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements).</span></span>  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="0a735-248">Určení zásad pro sestavení, obory názvů a typy</span><span class="sxs-lookup"><span data-stu-id="0a735-248">Specifying policy for assemblies, namespaces, and types</span></span>  
 <span data-ttu-id="0a735-249">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md)a [ Typ](../../../docs/framework/net-native/type-element-net-native.md) elementy podporují tyto typy zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-249">The [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="0a735-250">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="0a735-250">`Activate`.</span></span> <span data-ttu-id="0a735-251">Ovládací prvky runtime přístup k konstruktory, chcete-li povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="0a735-251">Controls runtime access to constructors, to enable activation of instances.</span></span>  
  
-   <span data-ttu-id="0a735-252">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="0a735-252">`Browse`.</span></span> <span data-ttu-id="0a735-253">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0a735-253">Controls querying for information about program elements but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="0a735-254">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0a735-254">`Dynamic`.</span></span> <span data-ttu-id="0a735-255">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="0a735-255">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>  
  
-   <span data-ttu-id="0a735-256">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0a735-256">`Serialize`.</span></span> <span data-ttu-id="0a735-257">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a serializovat knihovny třetích stran, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="0a735-257">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>  
  
-   <span data-ttu-id="0a735-258">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="0a735-258">`DataContractSerializer`.</span></span> <span data-ttu-id="0a735-259">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0a735-259">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="0a735-260">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="0a735-260">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="0a735-261">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0a735-261">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="0a735-262">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="0a735-262">`XmlSerializer`.</span></span> <span data-ttu-id="0a735-263">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0a735-263">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="0a735-264">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="0a735-264">`MarshalObject`.</span></span> <span data-ttu-id="0a735-265">Ovládací prvky zásady pro zařazování odkazové typy WinRT a COM.</span><span class="sxs-lookup"><span data-stu-id="0a735-265">Controls policy for marshaling reference types to WinRT and COM.</span></span>  
  
-   <span data-ttu-id="0a735-266">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="0a735-266">`MarshalDelegate`.</span></span> <span data-ttu-id="0a735-267">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0a735-267">Controls policy for marshaling delegate types as function pointers to native code.</span></span>  
  
-   <span data-ttu-id="0a735-268">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="0a735-268">`MarshalStructure` .</span></span> <span data-ttu-id="0a735-269">Ovládací prvky zásady pro zařazování struktur nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0a735-269">Controls policy for marshaling structures to native code.</span></span>  
  
 <span data-ttu-id="0a735-270">Jsou nastavení související s těmito typy zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-270">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="0a735-271">`All`.</span><span class="sxs-lookup"><span data-stu-id="0a735-271">`All`.</span></span> <span data-ttu-id="0a735-272">Povolení zásad pro všechny typy a členy, kteří řetězu nástroj nedojde k odebrání.</span><span class="sxs-lookup"><span data-stu-id="0a735-272">Enable the policy for all types and members that the tool chain does not remove.</span></span>  
  
-   <span data-ttu-id="0a735-273">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="0a735-273">`Auto`.</span></span> <span data-ttu-id="0a735-274">Použije výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="0a735-274">Use the default behavior.</span></span> <span data-ttu-id="0a735-275">(Není zadávání zásad je stejné jako nastavení zásad na `Auto` Pokud tuto zásadu je přepsat, například nadřazeného elementu.)</span><span class="sxs-lookup"><span data-stu-id="0a735-275">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>  
  
-   <span data-ttu-id="0a735-276">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="0a735-276">`Excluded`.</span></span> <span data-ttu-id="0a735-277">Zakažte zásadu pro element programu.</span><span class="sxs-lookup"><span data-stu-id="0a735-277">Disable the policy for the program element.</span></span>  
  
-   <span data-ttu-id="0a735-278">`Public`.</span><span class="sxs-lookup"><span data-stu-id="0a735-278">`Public`.</span></span> <span data-ttu-id="0a735-279">Povolte zásady pro veřejné typy nebo členy, pokud řetězu nástroj zjistí, že člen není nutný a proto ji odstraní.</span><span class="sxs-lookup"><span data-stu-id="0a735-279">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="0a735-280">(V takovém případě je nutné použít `Required Public` zajistit, že člen se ukládají a má reflexe možnosti.)</span><span class="sxs-lookup"><span data-stu-id="0a735-280">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>  
  
-   <span data-ttu-id="0a735-281">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="0a735-281">`PublicAndInternal`.</span></span> <span data-ttu-id="0a735-282">Zásady pro veřejné a interní typy nebo členy povolte, pokud nástroj řetězu neodstraní.</span><span class="sxs-lookup"><span data-stu-id="0a735-282">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>  
  
-   <span data-ttu-id="0a735-283">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="0a735-283">`Required Public`.</span></span> <span data-ttu-id="0a735-284">Vyžadovat řetězu nástroj zachovat veřejných typů a členů, jestli se používají a povolíte zásady pro ně.</span><span class="sxs-lookup"><span data-stu-id="0a735-284">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="0a735-285">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="0a735-285">`Required PublicAndInternal`.</span></span> <span data-ttu-id="0a735-286">Vyžadovat řetězu nástroj aby veřejné a interní typy a členy, jestli se používají a povolíte zásady pro ně.</span><span class="sxs-lookup"><span data-stu-id="0a735-286">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="0a735-287">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="0a735-287">`Required All`.</span></span> <span data-ttu-id="0a735-288">Vyžadovat řetězu nástroj chránit všechny typy a členy, jestli se používají a povolíte zásady pro ně.</span><span class="sxs-lookup"><span data-stu-id="0a735-288">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>  
  
 <span data-ttu-id="0a735-289">Například následující soubor direktivy modulu runtime definuje zásady pro všechny typy a členy v sestavení DataClasses.dll.</span><span class="sxs-lookup"><span data-stu-id="0a735-289">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="0a735-290">Umožňuje reflexe pro serializaci všechny veřejné vlastnosti umožňuje procházení pro všechny typy a členy typu umožňuje aktivace pro všechny typy (z důvodu `Dynamic` atribut) a umožňuje reflexe pro všechny veřejné typy a členy.</span><span class="sxs-lookup"><span data-stu-id="0a735-290">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"   
                Browse="All" Activate="PublicAndInternal"   
                Dynamic="Public"  />  
   </Application>  
   <Library Name="UtilityLibrary">  
     <!-- Child elements go here -->    
   </Library>  
</Directives>  
```  
  
### <a name="specifying-policy-for-members"></a><span data-ttu-id="0a735-291">Určení zásad pro členy</span><span class="sxs-lookup"><span data-stu-id="0a735-291">Specifying policy for members</span></span>  
 <span data-ttu-id="0a735-292">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) a [pole](../../../docs/framework/net-native/field-element-net-native.md) elementy podporují tyto typy zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-292">The [Property](../../../docs/framework/net-native/property-element-net-native.md) and [Field](../../../docs/framework/net-native/field-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="0a735-293">`Browse`– Ovládací prvky dotazování na informace o tomto členu, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0a735-293">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="0a735-294">`Dynamic`-Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="0a735-294">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="0a735-295">Určuje také dotazování na informace o nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="0a735-295">Also controls querying for information about the containing type.</span></span>  
  
-   <span data-ttu-id="0a735-296">`Serialize`-Řídí runtime přístup k člen instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON povolit.</span><span class="sxs-lookup"><span data-stu-id="0a735-296">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="0a735-297">Tuto zásadu lze použít k konstruktory, polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="0a735-297">This policy can be applied to constructors, fields, and properties.</span></span>  
  
 <span data-ttu-id="0a735-298">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) a [událostí](../../../docs/framework/net-native/event-element-net-native.md) elementy podporují tyto typy zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-298">The [Method](../../../docs/framework/net-native/method-element-net-native.md) and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="0a735-299">`Browse`– Ovládací prvky dotazování na informace o tomto členu, ale neumožňuje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="0a735-299">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>  
  
-   <span data-ttu-id="0a735-300">`Dynamic`-Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="0a735-300">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="0a735-301">Určuje také dotazování na informace o nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="0a735-301">Also controls querying for information about the containing type.</span></span>  
  
 <span data-ttu-id="0a735-302">Jsou nastavení související s těmito typy zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-302">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="0a735-303">`Auto`-Použijte výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="0a735-303">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="0a735-304">(Není zadávání zásad je stejné jako nastavení zásad na `Auto` Pokud něco ho přepíše.)</span><span class="sxs-lookup"><span data-stu-id="0a735-304">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>  
  
-   <span data-ttu-id="0a735-305">`Excluded`-Nikdy obsahovat metadata pro člena.</span><span class="sxs-lookup"><span data-stu-id="0a735-305">`Excluded` - Never include metadata for the member.</span></span>  
  
-   <span data-ttu-id="0a735-306">`Included`-Povolte zásady, pokud nadřazený typ nachází ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="0a735-306">`Included` - Enable the policy if the parent type is present in the output.</span></span>  
  
-   <span data-ttu-id="0a735-307">`Required`-Vyžadují řetězu nástroj zachovat tento člen i když se zobrazí na nevyužitá a povolíte zásady pro ni.</span><span class="sxs-lookup"><span data-stu-id="0a735-307">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>  
  
## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="0a735-308">Sémantika souboru direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0a735-308">Runtime directives file semantics</span></span>  
 <span data-ttu-id="0a735-309">Zásady lze definovat současně pro elementy vyšší úrovně a nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="0a735-309">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="0a735-310">Například zásad lze definovat pro sestavení a některé typy obsažené v této sestavě.</span><span class="sxs-lookup"><span data-stu-id="0a735-310">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="0a735-311">Pokud není uvedeno konkrétní prvek nižší úrovně, dědí zásady svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="0a735-311">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="0a735-312">Například pokud `Assembly` nachází element ale `Type` elementy nejsou, zásady zadaný v `Assembly` element platí pro jednotlivé typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a735-312">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="0a735-313">Zásady pro stejného elementu programu můžete taky použít několik elementů.</span><span class="sxs-lookup"><span data-stu-id="0a735-313">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="0a735-314">Například samostatné [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) elementy může stejného elementu zásad definovat pro stejného sestavení jinak.</span><span class="sxs-lookup"><span data-stu-id="0a735-314">For example, separate [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="0a735-315">Následující části popisují, jak zásady pro konkrétní typ vyřešen v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="0a735-315">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>  
  
 <span data-ttu-id="0a735-316">A [typ](../../../docs/framework/net-native/type-element-net-native.md) nebo [metoda](../../../docs/framework/net-native/method-element-net-native.md) element obecný typ nebo metoda svých zásad platí pro všechny konkretizací, které nemají své vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="0a735-316">A [Type](../../../docs/framework/net-native/type-element-net-native.md) or [Method](../../../docs/framework/net-native/method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="0a735-317">Například `Type` element, který určuje zásady pro <xref:System.Collections.Generic.List%601> vztahuje na všechny zkonstruovaná instance daného obecného typu, pokud není přepsána pro konkrétní sestavený obecného typu (například `List<Int32>`) podle `TypeInstantiation` element.</span><span class="sxs-lookup"><span data-stu-id="0a735-317">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="0a735-318">Elementy, jinak hodnota definovat zásady pro element program s názvem.</span><span class="sxs-lookup"><span data-stu-id="0a735-318">Otherwise, elements define policy for the program element named.</span></span>  
  
 <span data-ttu-id="0a735-319">Pokud element je nejednoznačné, modul hledá shody a pokud najde přesnou shodu, použije ho.</span><span class="sxs-lookup"><span data-stu-id="0a735-319">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="0a735-320">Pokud najde více shod, budou existovat upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="0a735-320">If it finds multiple matches, there will be a warning or error.</span></span>  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="0a735-321">Pokud dva direktivy uplatňovat zásady na stejný element programu</span><span class="sxs-lookup"><span data-stu-id="0a735-321">If two directives apply policy to the same program element</span></span>  
 <span data-ttu-id="0a735-322">Pokud dva elementy v soubory direktivy modulu runtime jinou zkuste nastavit stejného typu zásady pro stejného elementu program (například sestavení nebo typ) na různé hodnoty, konflikt vyřešen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0a735-322">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>  
  
1.  <span data-ttu-id="0a735-323">Pokud `Excluded` element přítomen, vyšší prioritu.</span><span class="sxs-lookup"><span data-stu-id="0a735-323">If the `Excluded` element is present, it has precedence.</span></span>  
  
2.  <span data-ttu-id="0a735-324">`Required`má vyšší prioritu více není `Required`.</span><span class="sxs-lookup"><span data-stu-id="0a735-324">`Required` has precedence over not `Required`.</span></span>  
  
3.  <span data-ttu-id="0a735-325">`All`má vyšší prioritu než `PublicAndInternal`, který má vyšší prioritu než `Public`.</span><span class="sxs-lookup"><span data-stu-id="0a735-325">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>  
  
4.  <span data-ttu-id="0a735-326">Explicitní nastavení, má vyšší prioritu než `Auto`.</span><span class="sxs-lookup"><span data-stu-id="0a735-326">Any explicit setting has precedence over `Auto`.</span></span>  
  
 <span data-ttu-id="0a735-327">Například pokud projekt obsahuje následující dva soubory direktivy modulu runtime, zásady serializace pro DataClasses.dll je nastavené na obojí `Required Public` a `All`.</span><span class="sxs-lookup"><span data-stu-id="0a735-327">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="0a735-328">V takovém případě by možné přeložit jako zásady serializace `Required All`.</span><span class="sxs-lookup"><span data-stu-id="0a735-328">In this case, the serialization policy would be resolved as `Required All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"/>  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="All" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
 <span data-ttu-id="0a735-329">Ale pokud dva direktivy v souboru direktivy modulu runtime jeden zkuste nastavit stejný typ zásady pro stejného elementu programu, nástroj definice schématu XML zobrazí chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0a735-329">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="0a735-330">Pokud podřízenými a nadřazenými prvky použít stejný typ zásad</span><span class="sxs-lookup"><span data-stu-id="0a735-330">If child and parent elements apply the same policy type</span></span>  
 <span data-ttu-id="0a735-331">Podřízené elementy přepsat své nadřazené elementy, včetně `Excluded` nastavení.</span><span class="sxs-lookup"><span data-stu-id="0a735-331">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="0a735-332">Přepsání je hlavním důvodem by chcete určit `Auto`.</span><span class="sxs-lookup"><span data-stu-id="0a735-332">Overriding is the main reason you would want to specify `Auto`.</span></span>  
  
 <span data-ttu-id="0a735-333">V následujícím příkladu, nastavení pro všechno, co v zásad serializace `DataClasses` , není v `DataClasses.ViewModels` by `Required Public`a vše, co je v obou `DataClasses` a `DataClasses.ViewModels` by `All`.</span><span class="sxs-lookup"><span data-stu-id="0a735-333">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
   </Appliction>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="0a735-334">Pokud otevřete obecné typy a instancí elementy použít stejný typ zásad</span><span class="sxs-lookup"><span data-stu-id="0a735-334">If open generics and instantiated elements apply the same policy type</span></span>  
 <span data-ttu-id="0a735-335">V následujícím příkladu `Dictionary<int,int>` je přiřazen `Browse` zásady pouze v případě, že modul je další důvod, jí přidělit `Browse` zásad (které by jinak byly výchozí chování); každých vytváření instancí z <xref:System.Collections.Generic.Dictionary%602> budou mít všechny Procházet její členy.</span><span class="sxs-lookup"><span data-stu-id="0a735-335">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
      <Namespace Name="DataClasses.Generics" />  
      <Type Name="Dictionary" Browse="All" />  
      <TypeInstantiation Name="Dictionary"   
                         Arguments="System.Int32,System.Int32" Browse="Auto" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="how-policy-is-inferred"></a><span data-ttu-id="0a735-336">Jak odvodit zásad</span><span class="sxs-lookup"><span data-stu-id="0a735-336">How policy is inferred</span></span>  
 <span data-ttu-id="0a735-337">Každý typ zásad má jinou sadu pravidel, které určují, jak ovlivňuje přítomnosti tohoto typu zásad jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="0a735-337">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>  
  
#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="0a735-338">Účinku zásad procházení</span><span class="sxs-lookup"><span data-stu-id="0a735-338">The effect of Browse policy</span></span>  
 <span data-ttu-id="0a735-339">Použití `Browse` zásadu k typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-339">Applying the `Browse` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-340">Základní typ typu je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-340">The base type of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-341">Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-341">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-342">Pokud je typ s delegátem, `Invoke` je označené jako metodu na typ `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-342">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-343">Každé rozhraní typu je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-343">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-344">Typ každý atribut použitý typ je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-344">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-345">Pokud je obecný typ, je označené jako každý typ omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-345">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-346">Pokud je obecný typ, jsou označené jako typy, po které je vytvořena instance typu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-346">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="0a735-347">Použití `Browse` zásad na metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-347">Applying the `Browse` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-348">Každý typ parametru metody, je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-348">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-349">Návratový typ metody je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-349">The return type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-350">Obsahující typ metody je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-350">The containing type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-351">Pokud je metoda vytvořenou instanci obecné metody, je označené jako bez instancí obecná metoda `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-351">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-352">Typ každý atribut použitý metodu je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-352">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-353">Pokud je metoda Obecné, je označené jako každý typ omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-353">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-354">Pokud je metoda Obecné, jsou označené jako typy, po které je vytvořena instance metodu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-354">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="0a735-355">Použití `Browse` zásady pro pole zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-355">Applying the `Browse` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-356">Typ každý atribut použitých pro pole je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-356">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-357">Typ pole je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-357">The type of the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-358">Typ, do které patří pole je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-358">The type to which the field belongs is marked with the `Browse` policy.</span></span>  
  
#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="0a735-359">Účinek zásady dynamického</span><span class="sxs-lookup"><span data-stu-id="0a735-359">The effect of Dynamic policy</span></span>  
 <span data-ttu-id="0a735-360">Použití `Dynamic` zásadu k typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-360">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-361">Základní typ typu je označené jako `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-361">The base type of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-362">Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-362">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-363">Pokud je typ typem delegáta `Invoke` je označené jako metodu na typ `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-363">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-364">Každé rozhraní typu je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-364">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-365">Typ každý atribut použitý typ je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-365">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-366">Pokud je obecný typ, je označené jako každý typ omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-366">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-367">Pokud je obecný typ, jsou označené jako typy, po které je vytvořena instance typu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-367">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="0a735-368">Použití `Dynamic` zásad na metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-368">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-369">Každý typ parametru metody, je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-369">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-370">Návratový typ metody je označené jako `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-370">The return type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-371">Obsahující typ metody je označené jako `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-371">The containing type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-372">Pokud je metoda vytvořenou instanci obecné metody, je označené jako bez instancí obecná metoda `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-372">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-373">Typ každý atribut použitý metodu je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-373">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-374">Pokud je metoda Obecné, je označené jako každý typ omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-374">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-375">Pokud je metoda Obecné, jsou označené jako typy, po které je vytvořena instance metodu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-375">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-376">Můžete vyvolat metodu `MethodInfo.Invoke`, a že bude možné ve vytváření delegáta <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a735-376">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0a735-377">Použití `Dynamic` zásady pro pole zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-377">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-378">Typ každý atribut použitých pro pole je označené jako `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-378">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-379">Typ pole je označené jako `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-379">The type of the field is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-380">Typ, do které patří pole je označené jako `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-380">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>  
  
#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="0a735-381">Účinek Zásady aktivace</span><span class="sxs-lookup"><span data-stu-id="0a735-381">The effect of Activation policy</span></span>  
 <span data-ttu-id="0a735-382">Použití zásad aktivace typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-382">Applying the Activation policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-383">Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-383">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-384">Pokud je typ typem delegáta `Invoke` je označené jako metodu na typ `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-384">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-385">Konstruktory typu jsou označené jako `Activation` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-385">Constructors of the type are marked with the `Activation` policy.</span></span>  
  
 <span data-ttu-id="0a735-386">Použití `Activation` zásad na metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-386">Applying the `Activation` policy to a method involves the following policy change:</span></span>  
  
-   <span data-ttu-id="0a735-387">Může vyvolat konstruktor <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> a <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0a735-387">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0a735-388">Pro metody `Activation` zásada ovlivňuje pouze konstruktory.</span><span class="sxs-lookup"><span data-stu-id="0a735-388">For methods, the `Activation` policy affects constructors only.</span></span>  
  
 <span data-ttu-id="0a735-389">Použití `Activation` zásada pro pole nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="0a735-389">Applying the `Activation` policy to a field has no effect.</span></span>  
  
#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="0a735-390">Účinku zásad serializace</span><span class="sxs-lookup"><span data-stu-id="0a735-390">The effect of Serialize policy</span></span>  
 <span data-ttu-id="0a735-391">`Serialize` Zásad umožňuje použití běžné serializátorů prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="0a735-391">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="0a735-392">Nicméně, protože vzory přístupu k přesný odraz z jiných společností než Microsoft serializátorů nejsou známé společnosti Microsoft, nemusí být tato zásada zcela efektivní.</span><span class="sxs-lookup"><span data-stu-id="0a735-392">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>  
  
 <span data-ttu-id="0a735-393">Použití `Serialize` zásadu k typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-393">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-394">Základní typ typu je označené jako `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-394">The base type of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-395">Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-395">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="0a735-396">Pokud je typ typem delegáta `Invoke` je označené jako metodu na typ `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-396">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="0a735-397">Pokud je typ výčtu, je označené pole typu `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-397">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-398">Pokud typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` označena `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-398">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-399">Pokud je typ <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, nebo <xref:System.Collections.Generic.IReadOnlyList%601>, pak `T[]` a <xref:System.Collections.Generic.List%601> označené jako `Serialize` zásady, ale žádní členové typu rozhraní jsou označené `Serialize`zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-399">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-400">Pokud je typ <xref:System.Collections.Generic.List%601>, žádné členy typu jsou označené jako `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-400">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-401">Pokud je typ <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> označena `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-401">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="0a735-402">žádné členy typu jsou označené, ale `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-402">but no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-403">Pokud je typ <xref:System.Collections.Generic.Dictionary%602>, žádné členy typu jsou označené jako `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-403">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-404">Pokud typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` a `TValue` jsou označené `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-404">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-405">Každý konstruktor, každý přistupujícího objektu vlastnosti a každé pole je označené `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-405">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="0a735-406">Použití `Serialize` zásad na metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-406">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-407">Typ obsahující je označené jako `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-407">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-408">Návratový typ metody je označené jako `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-408">The return type of the method is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="0a735-409">Použití `Serialize` zásady pro pole zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="0a735-409">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="0a735-410">Typ obsahující je označené jako `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-410">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="0a735-411">Typ pole je označené jako `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="0a735-411">The type of the field is marked with the `Serialize` policy.</span></span>  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a><span data-ttu-id="0a735-412">Účinek zásady XmlSerializer, DataContractSerializer a DataContractJsonSerialier</span><span class="sxs-lookup"><span data-stu-id="0a735-412">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerialier policies</span></span>  
 <span data-ttu-id="0a735-413">Na rozdíl od `Serialize` zásadu, která je určena na základě reflexe serializátorů, `XmlSerializer`, `DataContractSerializer`, a `DataContractJsonSerializer` zásady slouží k povolení sadu serializátorů, které jsou známé [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu.</span><span class="sxs-lookup"><span data-stu-id="0a735-413">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the `XmlSerializer`, `DataContractSerializer`, and `DataContractJsonSerializer` policies are used to enable a set of serializers that are known to the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="0a735-414">Tyto serializátorů nejsou implementované pomocí reflexe, ale sadu typů, které může být serializovány v době běhu je určen podobným způsobem jako typy, které jsou reflectable.</span><span class="sxs-lookup"><span data-stu-id="0a735-414">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>  
  
 <span data-ttu-id="0a735-415">Použití jednu z těchto zásad na typ umožňuje typ k serializaci s odpovídající serializátor.</span><span class="sxs-lookup"><span data-stu-id="0a735-415">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="0a735-416">Všechny typy, které pro Serializační stroj můžete určit staticky potřebují serializace bude také být serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="0a735-416">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>  
  
 <span data-ttu-id="0a735-417">Tyto zásady mají vliv na metody nebo pole.</span><span class="sxs-lookup"><span data-stu-id="0a735-417">These policies have no effect on methods or fields.</span></span>  
  
 <span data-ttu-id="0a735-418">Další informace najdete v části "Rozdíly v Serializátorů" v [migrace vaše aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="0a735-418">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a735-419">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a735-419">See Also</span></span>  
 [<span data-ttu-id="0a735-420">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0a735-420">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="0a735-421">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="0a735-421">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)
