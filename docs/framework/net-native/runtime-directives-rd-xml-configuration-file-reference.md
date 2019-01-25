---
title: Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fed8097c472be487256840f289c1d8252d978a93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637101"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="2680b-102">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="2680b-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>
<span data-ttu-id="2680b-103">Direktivy modulu runtime (. rd.xml) soubor je konfigurační soubor XML, který určuje, zda jsou k dispozici pro účely reflexe prvky určené programu.</span><span class="sxs-lookup"><span data-stu-id="2680b-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="2680b-104">Tady je příklad souboru direktiv modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="2680b-104">Here’s an example of a runtime directives file:</span></span>  
  
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
  
## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="2680b-105">Struktura souboru direktiv modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2680b-105">The structure of a runtime directives file</span></span>  
 <span data-ttu-id="2680b-106">Direktivy modulu runtime souboru používá `http://schemas.microsoft.com/netfx/2013/01/metadata` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2680b-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>  
  
 <span data-ttu-id="2680b-107">Kořenový prvek je [direktivy](../../../docs/framework/net-native/directives-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="2680b-107">The root element is the [Directives](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span> <span data-ttu-id="2680b-108">Může obsahovat nula nebo více [knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementy a nula nebo jedna [aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu, jak je znázorněno v následující strukturu.</span><span class="sxs-lookup"><span data-stu-id="2680b-108">It can contain zero or more [Library](../../../docs/framework/net-native/library-element-net-native.md) elements, and zero or one [Application](../../../docs/framework/net-native/application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="2680b-109">Atributy [aplikace](../../../docs/framework/net-native/application-element-net-native.md) element můžete definovat zásady reflexe modulu runtime celou aplikaci, nebo může sloužit jako kontejner pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="2680b-109">The attributes of the [Application](../../../docs/framework/net-native/application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="2680b-110">[Knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementu, na druhé straně je prostě kontejner.</span><span class="sxs-lookup"><span data-stu-id="2680b-110">The [Library](../../../docs/framework/net-native/library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="2680b-111">Podřízené objekty daného [aplikace](../../../docs/framework/net-native/application-element-net-native.md) a [knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementy definovat typy, metody, pole, vlastnosti a události, které jsou k dispozici pro účely reflexe.</span><span class="sxs-lookup"><span data-stu-id="2680b-111">The children of the [Application](../../../docs/framework/net-native/application-element-net-native.md) and [Library](../../../docs/framework/net-native/library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>  
  
 <span data-ttu-id="2680b-112">Referenční informace, zvolte prvky z následující strukturu nebo naleznete v tématu [elementy direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="2680b-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md).</span></span> <span data-ttu-id="2680b-113">V následující hierarchie označí se třemi tečkami rekurzivní strukturou.</span><span class="sxs-lookup"><span data-stu-id="2680b-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="2680b-114">Informace v závorkách označují, jestli tento element je nepovinné nebo povinné, a pokud se používá, kolik instancí (jeden nebo více) jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="2680b-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>  
  
 <span data-ttu-id="2680b-115">[Direktivy](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="2680b-115">[Directives](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span></span>  
 <span data-ttu-id="2680b-116">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="2680b-116">[Application](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span></span>  
 <span data-ttu-id="2680b-117">[Sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-117">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-119">.</span><span class="sxs-lookup"><span data-stu-id="2680b-119">.</span></span> <span data-ttu-id="2680b-120">.</span><span class="sxs-lookup"><span data-stu-id="2680b-120">.</span></span> <span data-ttu-id="2680b-121">.</span><span class="sxs-lookup"><span data-stu-id="2680b-121">.</span></span>  
 <span data-ttu-id="2680b-122">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-122">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-123">.</span><span class="sxs-lookup"><span data-stu-id="2680b-123">.</span></span> <span data-ttu-id="2680b-124">.</span><span class="sxs-lookup"><span data-stu-id="2680b-124">.</span></span> <span data-ttu-id="2680b-125">.</span><span class="sxs-lookup"><span data-stu-id="2680b-125">.</span></span>  
 <span data-ttu-id="2680b-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-127">.</span><span class="sxs-lookup"><span data-stu-id="2680b-127">.</span></span> <span data-ttu-id="2680b-128">.</span><span class="sxs-lookup"><span data-stu-id="2680b-128">.</span></span> <span data-ttu-id="2680b-129">.</span><span class="sxs-lookup"><span data-stu-id="2680b-129">.</span></span>  
 <span data-ttu-id="2680b-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-132">.</span><span class="sxs-lookup"><span data-stu-id="2680b-132">.</span></span> <span data-ttu-id="2680b-133">.</span><span class="sxs-lookup"><span data-stu-id="2680b-133">.</span></span> <span data-ttu-id="2680b-134">.</span><span class="sxs-lookup"><span data-stu-id="2680b-134">.</span></span>  
 <span data-ttu-id="2680b-135">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-135">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-136">.</span><span class="sxs-lookup"><span data-stu-id="2680b-136">.</span></span> <span data-ttu-id="2680b-137">.</span><span class="sxs-lookup"><span data-stu-id="2680b-137">.</span></span> <span data-ttu-id="2680b-138">.</span><span class="sxs-lookup"><span data-stu-id="2680b-138">.</span></span>  
 <span data-ttu-id="2680b-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-140">.</span><span class="sxs-lookup"><span data-stu-id="2680b-140">.</span></span> <span data-ttu-id="2680b-141">.</span><span class="sxs-lookup"><span data-stu-id="2680b-141">.</span></span> <span data-ttu-id="2680b-142">.</span><span class="sxs-lookup"><span data-stu-id="2680b-142">.</span></span>  
 <span data-ttu-id="2680b-143">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-143">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-144">[Podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy nadřazeného typu) [O:1]</span><span class="sxs-lookup"><span data-stu-id="2680b-144">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="2680b-145">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-145">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-146">.</span><span class="sxs-lookup"><span data-stu-id="2680b-146">.</span></span> <span data-ttu-id="2680b-147">.</span><span class="sxs-lookup"><span data-stu-id="2680b-147">.</span></span> <span data-ttu-id="2680b-148">.</span><span class="sxs-lookup"><span data-stu-id="2680b-148">.</span></span>  
 <span data-ttu-id="2680b-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-150">.</span><span class="sxs-lookup"><span data-stu-id="2680b-150">.</span></span> <span data-ttu-id="2680b-151">.</span><span class="sxs-lookup"><span data-stu-id="2680b-151">.</span></span> <span data-ttu-id="2680b-152">.</span><span class="sxs-lookup"><span data-stu-id="2680b-152">.</span></span>  
 <span data-ttu-id="2680b-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atributem) [O:1]</span><span class="sxs-lookup"><span data-stu-id="2680b-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="2680b-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-155">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-155">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-156">[Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-156">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (vytvořený obecnou metodu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="2680b-160">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-160">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-161">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-161">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-162">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-162">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-164">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-164">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-165">.</span><span class="sxs-lookup"><span data-stu-id="2680b-165">.</span></span> <span data-ttu-id="2680b-166">.</span><span class="sxs-lookup"><span data-stu-id="2680b-166">.</span></span> <span data-ttu-id="2680b-167">.</span><span class="sxs-lookup"><span data-stu-id="2680b-167">.</span></span>  
 <span data-ttu-id="2680b-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-169">.</span><span class="sxs-lookup"><span data-stu-id="2680b-169">.</span></span> <span data-ttu-id="2680b-170">.</span><span class="sxs-lookup"><span data-stu-id="2680b-170">.</span></span> <span data-ttu-id="2680b-171">.</span><span class="sxs-lookup"><span data-stu-id="2680b-171">.</span></span>  
 <span data-ttu-id="2680b-172">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-172">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-173">[Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-173">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (vytvořený obecnou metodu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="2680b-177">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-177">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-178">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-178">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-179">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-179">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-180">[Knihovna](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-180">[Library](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-181">[Sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-181">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-183">.</span><span class="sxs-lookup"><span data-stu-id="2680b-183">.</span></span> <span data-ttu-id="2680b-184">.</span><span class="sxs-lookup"><span data-stu-id="2680b-184">.</span></span> <span data-ttu-id="2680b-185">.</span><span class="sxs-lookup"><span data-stu-id="2680b-185">.</span></span>  
 <span data-ttu-id="2680b-186">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-186">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-187">.</span><span class="sxs-lookup"><span data-stu-id="2680b-187">.</span></span> <span data-ttu-id="2680b-188">.</span><span class="sxs-lookup"><span data-stu-id="2680b-188">.</span></span> <span data-ttu-id="2680b-189">.</span><span class="sxs-lookup"><span data-stu-id="2680b-189">.</span></span>  
 <span data-ttu-id="2680b-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-191">.</span><span class="sxs-lookup"><span data-stu-id="2680b-191">.</span></span> <span data-ttu-id="2680b-192">.</span><span class="sxs-lookup"><span data-stu-id="2680b-192">.</span></span> <span data-ttu-id="2680b-193">.</span><span class="sxs-lookup"><span data-stu-id="2680b-193">.</span></span>  
 <span data-ttu-id="2680b-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-196">.</span><span class="sxs-lookup"><span data-stu-id="2680b-196">.</span></span> <span data-ttu-id="2680b-197">.</span><span class="sxs-lookup"><span data-stu-id="2680b-197">.</span></span> <span data-ttu-id="2680b-198">.</span><span class="sxs-lookup"><span data-stu-id="2680b-198">.</span></span>  
 <span data-ttu-id="2680b-199">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-199">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-200">.</span><span class="sxs-lookup"><span data-stu-id="2680b-200">.</span></span> <span data-ttu-id="2680b-201">.</span><span class="sxs-lookup"><span data-stu-id="2680b-201">.</span></span> <span data-ttu-id="2680b-202">.</span><span class="sxs-lookup"><span data-stu-id="2680b-202">.</span></span>  
 <span data-ttu-id="2680b-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-204">.</span><span class="sxs-lookup"><span data-stu-id="2680b-204">.</span></span> <span data-ttu-id="2680b-205">.</span><span class="sxs-lookup"><span data-stu-id="2680b-205">.</span></span> <span data-ttu-id="2680b-206">.</span><span class="sxs-lookup"><span data-stu-id="2680b-206">.</span></span>  
 <span data-ttu-id="2680b-207">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-207">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-208">[Podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy nadřazeného typu) [O:1]</span><span class="sxs-lookup"><span data-stu-id="2680b-208">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="2680b-209">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-209">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-210">.</span><span class="sxs-lookup"><span data-stu-id="2680b-210">.</span></span> <span data-ttu-id="2680b-211">.</span><span class="sxs-lookup"><span data-stu-id="2680b-211">.</span></span> <span data-ttu-id="2680b-212">.</span><span class="sxs-lookup"><span data-stu-id="2680b-212">.</span></span>  
 <span data-ttu-id="2680b-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-214">.</span><span class="sxs-lookup"><span data-stu-id="2680b-214">.</span></span> <span data-ttu-id="2680b-215">.</span><span class="sxs-lookup"><span data-stu-id="2680b-215">.</span></span> <span data-ttu-id="2680b-216">.</span><span class="sxs-lookup"><span data-stu-id="2680b-216">.</span></span>  
 <span data-ttu-id="2680b-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atributem) [O:1]</span><span class="sxs-lookup"><span data-stu-id="2680b-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="2680b-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-219">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-219">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (vytvořený obecnou metodu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="2680b-221">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-221">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-222">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-222">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-223">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-223">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-225">[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-225">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-226">.</span><span class="sxs-lookup"><span data-stu-id="2680b-226">.</span></span> <span data-ttu-id="2680b-227">.</span><span class="sxs-lookup"><span data-stu-id="2680b-227">.</span></span> <span data-ttu-id="2680b-228">.</span><span class="sxs-lookup"><span data-stu-id="2680b-228">.</span></span>  
 <span data-ttu-id="2680b-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="2680b-230">.</span><span class="sxs-lookup"><span data-stu-id="2680b-230">.</span></span> <span data-ttu-id="2680b-231">.</span><span class="sxs-lookup"><span data-stu-id="2680b-231">.</span></span> <span data-ttu-id="2680b-232">.</span><span class="sxs-lookup"><span data-stu-id="2680b-232">.</span></span>  
 <span data-ttu-id="2680b-233">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-233">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (vytvořený obecnou metodu) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="2680b-235">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-235">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-236">[Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-236">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="2680b-237">[Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="2680b-237">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
  
 <span data-ttu-id="2680b-238">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) prvek může mít žádné atributy, nebo může mít atributy zásad popsané v [Runtime směrnice a zásady části](#Directives).</span><span class="sxs-lookup"><span data-stu-id="2680b-238">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>  
  
 <span data-ttu-id="2680b-239">A [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element má jeden atribut `Name`, který určuje název knihovny nebo bez jeho přípona souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="2680b-239">A [Library](../../../docs/framework/net-native/library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="2680b-240">Například následující [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element se vztahuje na sestavení s názvem Extensions.dll.</span><span class="sxs-lookup"><span data-stu-id="2680b-240">For example, the following [Library](../../../docs/framework/net-native/library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>  
  
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
## <a name="runtime-directives-and-policy"></a><span data-ttu-id="2680b-241">Direktivy modulu runtime a zásady</span><span class="sxs-lookup"><span data-stu-id="2680b-241">Runtime directives and policy</span></span>  
 <span data-ttu-id="2680b-242">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu samotného a podřízených elementů [knihovny](../../../docs/framework/net-native/library-element-net-native.md) a [aplikace](../../../docs/framework/net-native/application-element-net-native.md) prvky vyjádření zásad; to znamená, že definují způsob, ve kterém můžete použít aplikaci reflexe pro prvek programu.</span><span class="sxs-lookup"><span data-stu-id="2680b-242">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element itself and the child elements of the [Library](../../../docs/framework/net-native/library-element-net-native.md) and [Application](../../../docs/framework/net-native/application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="2680b-243">Typ zásad je definován atribut prvku (například `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="2680b-243">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="2680b-244">Hodnota zásad je definována hodnota atributu (například `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="2680b-244">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>  
  
 <span data-ttu-id="2680b-245">Všechny zásady určené atribut elementu se vztahuje na všechny podřízené prvky, které nechcete zadat hodnotu pro tuto zásadu.</span><span class="sxs-lookup"><span data-stu-id="2680b-245">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="2680b-246">Například, pokud je zásada určená [typ](../../../docs/framework/net-native/type-element-net-native.md) elementu, které zásady platí pro všechny typy a členy, u kterých není explicitně zadán zásadu.</span><span class="sxs-lookup"><span data-stu-id="2680b-246">For example, if a policy is specified by a [Type](../../../docs/framework/net-native/type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>  
  
 <span data-ttu-id="2680b-247">Zásady, které lze vyjádřit pomocí [aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md), a [typ](../../../docs/framework/net-native/type-element-net-native.md) prvky se liší od zásad, který může být vyjádřena pro jednotlivé členy (podle [metoda](../../../docs/framework/net-native/method-element-net-native.md), [vlastnost](../../../docs/framework/net-native/property-element-net-native.md), [Pole](../../../docs/framework/net-native/field-element-net-native.md), a [události](../../../docs/framework/net-native/event-element-net-native.md) elementy).</span><span class="sxs-lookup"><span data-stu-id="2680b-247">The policy that can be expressed by the [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](../../../docs/framework/net-native/method-element-net-native.md), [Property](../../../docs/framework/net-native/property-element-net-native.md), [Field](../../../docs/framework/net-native/field-element-net-native.md), and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements).</span></span>  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="2680b-248">Určení zásad pro sestavení, oborů názvů a typy</span><span class="sxs-lookup"><span data-stu-id="2680b-248">Specifying policy for assemblies, namespaces, and types</span></span>  
 <span data-ttu-id="2680b-249">[Aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md)a [ Typ](../../../docs/framework/net-native/type-element-net-native.md) prvky podporu následujících typů zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-249">The [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="2680b-250">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="2680b-250">`Activate`.</span></span> <span data-ttu-id="2680b-251">Řídí přístup runtime konstruktorů, umožňuje aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="2680b-251">Controls runtime access to constructors, to enable activation of instances.</span></span>  
  
-   <span data-ttu-id="2680b-252">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="2680b-252">`Browse`.</span></span> <span data-ttu-id="2680b-253">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2680b-253">Controls querying for information about program elements but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="2680b-254">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="2680b-254">`Dynamic`.</span></span> <span data-ttu-id="2680b-255">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="2680b-255">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>  
  
-   <span data-ttu-id="2680b-256">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="2680b-256">`Serialize`.</span></span> <span data-ttu-id="2680b-257">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu být serializován a serializováno modulem knihovny třetích stran, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="2680b-257">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>  
  
-   <span data-ttu-id="2680b-258">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="2680b-258">`DataContractSerializer`.</span></span> <span data-ttu-id="2680b-259">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="2680b-259">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="2680b-260">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="2680b-260">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="2680b-261">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="2680b-261">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="2680b-262">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="2680b-262">`XmlSerializer`.</span></span> <span data-ttu-id="2680b-263">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="2680b-263">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="2680b-264">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="2680b-264">`MarshalObject`.</span></span> <span data-ttu-id="2680b-265">Určuje zásady pro zařazování typy odkazů ve WinRT a COM.</span><span class="sxs-lookup"><span data-stu-id="2680b-265">Controls policy for marshaling reference types to WinRT and COM.</span></span>  
  
-   <span data-ttu-id="2680b-266">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="2680b-266">`MarshalDelegate`.</span></span> <span data-ttu-id="2680b-267">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="2680b-267">Controls policy for marshaling delegate types as function pointers to native code.</span></span>  
  
-   <span data-ttu-id="2680b-268">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="2680b-268">`MarshalStructure` .</span></span> <span data-ttu-id="2680b-269">Určuje zásady pro zařazování struktur do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="2680b-269">Controls policy for marshaling structures to native code.</span></span>  
  
 <span data-ttu-id="2680b-270">Nastavení související s těmito typy zásad jsou:</span><span class="sxs-lookup"><span data-stu-id="2680b-270">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="2680b-271">`All`.</span><span class="sxs-lookup"><span data-stu-id="2680b-271">`All`.</span></span> <span data-ttu-id="2680b-272">Povolte zásady pro všechny typy a členy, které řetězce nástrojů se neodeberou.</span><span class="sxs-lookup"><span data-stu-id="2680b-272">Enable the policy for all types and members that the tool chain does not remove.</span></span>  
  
-   <span data-ttu-id="2680b-273">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="2680b-273">`Auto`.</span></span> <span data-ttu-id="2680b-274">Použije výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="2680b-274">Use the default behavior.</span></span> <span data-ttu-id="2680b-275">(Zásady bez zadání je ekvivalentní k nastavení této zásady na `Auto` Pokud tuto zásadu je přepsána, například nadřazeného elementu.)</span><span class="sxs-lookup"><span data-stu-id="2680b-275">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>  
  
-   <span data-ttu-id="2680b-276">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="2680b-276">`Excluded`.</span></span> <span data-ttu-id="2680b-277">Zásada pro ovládací prvek programu.</span><span class="sxs-lookup"><span data-stu-id="2680b-277">Disable the policy for the program element.</span></span>  
  
-   <span data-ttu-id="2680b-278">`Public`.</span><span class="sxs-lookup"><span data-stu-id="2680b-278">`Public`.</span></span> <span data-ttu-id="2680b-279">Povolte zásady pro veřejné typy nebo členy, pokud řetězec nástrojů zjistí, že člen není nutný a proto ji odebere.</span><span class="sxs-lookup"><span data-stu-id="2680b-279">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="2680b-280">(V druhém případě je nutné použít `Required Public` zajistíte, že člen je uložen a má schopnosti reflexe.)</span><span class="sxs-lookup"><span data-stu-id="2680b-280">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>  
  
-   <span data-ttu-id="2680b-281">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="2680b-281">`PublicAndInternal`.</span></span> <span data-ttu-id="2680b-282">Povolte zásady pro veřejné a vnitřní typy nebo členy, pokud řetězec nástrojů neodebere.</span><span class="sxs-lookup"><span data-stu-id="2680b-282">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>  
  
-   <span data-ttu-id="2680b-283">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="2680b-283">`Required Public`.</span></span> <span data-ttu-id="2680b-284">Vyžadovat řetězce nástrojů se veřejné typy a členy, které určuje, jestli se používají a povolte zásady pro ně.</span><span class="sxs-lookup"><span data-stu-id="2680b-284">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="2680b-285">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="2680b-285">`Required PublicAndInternal`.</span></span> <span data-ttu-id="2680b-286">Vyžadovat řetězce nástrojů se veřejné a vnitřní typy a členy, které určuje, jestli se používají a povolte zásady pro ně.</span><span class="sxs-lookup"><span data-stu-id="2680b-286">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="2680b-287">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="2680b-287">`Required All`.</span></span> <span data-ttu-id="2680b-288">Vyžadují řetězce nástrojů zachovat všechny typy a členy, které určuje, jestli se používají a povolte zásady pro ně.</span><span class="sxs-lookup"><span data-stu-id="2680b-288">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>  
  
 <span data-ttu-id="2680b-289">Například následující soubor direktiv modulu runtime definuje zásady pro všechny typy a členy v sestavení DataClasses.dll.</span><span class="sxs-lookup"><span data-stu-id="2680b-289">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="2680b-290">Umožňuje reflexe pro serializaci všechny veřejné vlastnosti, umožňuje procházení pro všechny typy a členy typu, umožňuje aktivaci pro všechny typy (z důvodu `Dynamic` atribut) a umožňuje reflexe pro všechny veřejné typy a členy.</span><span class="sxs-lookup"><span data-stu-id="2680b-290">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>  
  
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
  
### <a name="specifying-policy-for-members"></a><span data-ttu-id="2680b-291">Určení zásad pro členy</span><span class="sxs-lookup"><span data-stu-id="2680b-291">Specifying policy for members</span></span>  
 <span data-ttu-id="2680b-292">[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) a [pole](../../../docs/framework/net-native/field-element-net-native.md) prvky podporu následujících typů zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-292">The [Property](../../../docs/framework/net-native/property-element-net-native.md) and [Field](../../../docs/framework/net-native/field-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="2680b-293">`Browse` – Ovládací prvky dotazování na informace o tomto členu, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2680b-293">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="2680b-294">`Dynamic` -Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="2680b-294">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="2680b-295">Určuje také dotazování na informace o nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="2680b-295">Also controls querying for information about the containing type.</span></span>  
  
-   <span data-ttu-id="2680b-296">`Serialize` -Určuje runtime přístup k členu instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON povolit.</span><span class="sxs-lookup"><span data-stu-id="2680b-296">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="2680b-297">Tuto zásadu lze použít pro konstruktory, polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="2680b-297">This policy can be applied to constructors, fields, and properties.</span></span>  
  
 <span data-ttu-id="2680b-298">[Metoda](../../../docs/framework/net-native/method-element-net-native.md) a [události](../../../docs/framework/net-native/event-element-net-native.md) prvky podporu následujících typů zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-298">The [Method](../../../docs/framework/net-native/method-element-net-native.md) and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="2680b-299">`Browse` – Ovládací prvky dotazování na informace o tomto členu, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2680b-299">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>  
  
-   <span data-ttu-id="2680b-300">`Dynamic` -Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="2680b-300">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="2680b-301">Určuje také dotazování na informace o nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="2680b-301">Also controls querying for information about the containing type.</span></span>  
  
 <span data-ttu-id="2680b-302">Nastavení související s těmito typy zásad jsou:</span><span class="sxs-lookup"><span data-stu-id="2680b-302">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="2680b-303">`Auto` – Použijte výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="2680b-303">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="2680b-304">(Zásady bez zadání je ekvivalentní k nastavení této zásady na `Auto` Pokud něco ji přepisuje.)</span><span class="sxs-lookup"><span data-stu-id="2680b-304">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>  
  
-   <span data-ttu-id="2680b-305">`Excluded` -Nikdy Nezahrnovat metadata pro tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="2680b-305">`Excluded` - Never include metadata for the member.</span></span>  
  
-   <span data-ttu-id="2680b-306">`Included` -Zásadu povolte, pokud je k dispozici ve výstupu nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="2680b-306">`Included` - Enable the policy if the parent type is present in the output.</span></span>  
  
-   <span data-ttu-id="2680b-307">`Required` -Vyžaduje řetězec nástrojů zachovat tento člen se zobrazí i v případě nevyužitá a povolte zásady pro něj.</span><span class="sxs-lookup"><span data-stu-id="2680b-307">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>  
  
## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="2680b-308">Sémantika souboru direktiv modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2680b-308">Runtime directives file semantics</span></span>  
 <span data-ttu-id="2680b-309">Zásady lze definovat současně pro elementy vyšší úrovně a nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="2680b-309">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="2680b-310">Zásady lze například definovat pro sestavení a pro některé typy obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="2680b-310">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="2680b-311">Pokud není zastoupen konkrétní element nižší úrovně, zdědí zásada svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="2680b-311">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="2680b-312">Například pokud `Assembly` element je k dispozici, ale `Type` prvky nejsou, zásady zadaná v `Assembly` element platí pro jednotlivé typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="2680b-312">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="2680b-313">Více prvků lze také použít zásady stejný ovládací prvek programu.</span><span class="sxs-lookup"><span data-stu-id="2680b-313">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="2680b-314">Například samostatné [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) elementy definovat stejný element zásad pro stejného sestavení odlišně.</span><span class="sxs-lookup"><span data-stu-id="2680b-314">For example, separate [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="2680b-315">Následující části popisují, jak zásady pro konkrétní typ vyřeší v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="2680b-315">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>  
  
 <span data-ttu-id="2680b-316">A [typ](../../../docs/framework/net-native/type-element-net-native.md) nebo [metoda](../../../docs/framework/net-native/method-element-net-native.md) element obecného typu nebo metody své zásady platí pro všechny instance, nesmí být svými vlastními zásadami.</span><span class="sxs-lookup"><span data-stu-id="2680b-316">A [Type](../../../docs/framework/net-native/type-element-net-native.md) or [Method](../../../docs/framework/net-native/method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="2680b-317">Například `Type` prvek, který určuje zásady pro <xref:System.Collections.Generic.List%601> nepřepíšete pro konkrétní Konstruovaný obecný typ se vztahuje na všechny instance Konstruovaný obecný typ, (, jako `List<Int32>`) podle `TypeInstantiation` elementu.</span><span class="sxs-lookup"><span data-stu-id="2680b-317">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="2680b-318">V opačném případě elementy definovat zásady pro ovládací prvek programu s názvem.</span><span class="sxs-lookup"><span data-stu-id="2680b-318">Otherwise, elements define policy for the program element named.</span></span>  
  
 <span data-ttu-id="2680b-319">Pokud element je nejednoznačný, modul hledá shody a pokud se najde přesná shoda, použije ji.</span><span class="sxs-lookup"><span data-stu-id="2680b-319">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="2680b-320">Pokud se najde více shod, bude upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="2680b-320">If it finds multiple matches, there will be a warning or error.</span></span>  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="2680b-321">Pokud dvě direktivy uplatňovat zásady na stejný ovládací prvek programu</span><span class="sxs-lookup"><span data-stu-id="2680b-321">If two directives apply policy to the same program element</span></span>  
 <span data-ttu-id="2680b-322">Pokud dva prvky v různých běhových direktivy souborů došlo k pokusu o nastavení stejného typu zásady pro stejný ovládací prvek programu (například sestavení nebo typ) na různé hodnoty, je konflikt vyřešen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2680b-322">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>  
  
1.  <span data-ttu-id="2680b-323">Pokud `Excluded` element je k dispozici, má přednost.</span><span class="sxs-lookup"><span data-stu-id="2680b-323">If the `Excluded` element is present, it has precedence.</span></span>  
  
2.  <span data-ttu-id="2680b-324">`Required` má vyšší prioritu více not `Required`.</span><span class="sxs-lookup"><span data-stu-id="2680b-324">`Required` has precedence over not `Required`.</span></span>  
  
3.  <span data-ttu-id="2680b-325">`All` má vyšší prioritu než `PublicAndInternal`, který má vyšší prioritu než `Public`.</span><span class="sxs-lookup"><span data-stu-id="2680b-325">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>  
  
4.  <span data-ttu-id="2680b-326">Žádné explicitní nastavení má vyšší prioritu než `Auto`.</span><span class="sxs-lookup"><span data-stu-id="2680b-326">Any explicit setting has precedence over `Auto`.</span></span>  
  
 <span data-ttu-id="2680b-327">Například, pokud jeden projekt obsahuje následující dva soubory direktivy modulu runtime, serializace pro DataClasses.dll je zásada nastavená na obojí `Required Public` a `All`.</span><span class="sxs-lookup"><span data-stu-id="2680b-327">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="2680b-328">V takovém případě bude vyřešeno jako zásady serializace `Required All`.</span><span class="sxs-lookup"><span data-stu-id="2680b-328">In this case, the serialization policy would be resolved as `Required All`.</span></span>  
  
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
  
 <span data-ttu-id="2680b-329">Pokud dvě direktivy v souboru direktivy jeden modul runtime došlo k pokusu o nastavení stejného typu zásady pro stejný ovládací prvek programu, ale nástroj definici schématu XML zobrazí chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="2680b-329">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="2680b-330">Když použijete podřízenými a nadřazenými prvky stejného typu zásad</span><span class="sxs-lookup"><span data-stu-id="2680b-330">If child and parent elements apply the same policy type</span></span>  
 <span data-ttu-id="2680b-331">Podřízené prvky přepsat jejich nadřazených prvků, včetně `Excluded` nastavení.</span><span class="sxs-lookup"><span data-stu-id="2680b-331">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="2680b-332">Přepsání je hlavní důvod, proč byste měli určit `Auto`.</span><span class="sxs-lookup"><span data-stu-id="2680b-332">Overriding is the main reason you would want to specify `Auto`.</span></span>  
  
 <span data-ttu-id="2680b-333">V následujícím příkladu, nastavení pro všechno, co v zásady serializace `DataClasses` , který není v `DataClasses.ViewModels` by `Required Public`a vše, co je v obou `DataClasses` a `DataClasses.ViewModels` by `All`.</span><span class="sxs-lookup"><span data-stu-id="2680b-333">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>  
  
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
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="2680b-334">Pokud otevřete obecné typy a instance prvky použití stejného typu zásad</span><span class="sxs-lookup"><span data-stu-id="2680b-334">If open generics and instantiated elements apply the same policy type</span></span>  
 <span data-ttu-id="2680b-335">V následujícím příkladu `Dictionary<int,int>` je přiřazen `Browse` zásad jenom v případě, že modul je dalším důvodem pro ni `Browse` zásady (které by jinak byly výchozí chování); všechny další instance <xref:System.Collections.Generic.Dictionary%602> budou mít všechny jejích členů nelze procházet.</span><span class="sxs-lookup"><span data-stu-id="2680b-335">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>  
  
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
  
### <a name="how-policy-is-inferred"></a><span data-ttu-id="2680b-336">Jak odvodit zásad</span><span class="sxs-lookup"><span data-stu-id="2680b-336">How policy is inferred</span></span>  
 <span data-ttu-id="2680b-337">Každý typ zásad má jinou sadu pravidel, které určují, jak ovlivňuje jiných objektů, které přítomnosti tohoto typu zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-337">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>  
  
#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="2680b-338">Účinek zásady procházení</span><span class="sxs-lookup"><span data-stu-id="2680b-338">The effect of Browse policy</span></span>  
 <span data-ttu-id="2680b-339">Použití `Browse` zásadu k typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-339">Applying the `Browse` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-340">Je označené základní typ typu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-340">The base type of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-341">Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-341">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-342">Pokud je typ delegáta `Invoke` metoda v typu je označena `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-342">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-343">Každé rozhraní typ je označen `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-343">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-344">Typ každého atributu použitý pro typ je označen pomocí `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-344">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-345">Pokud je typ obecný, je označené každého typu omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-345">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-346">Pokud je typ obecný, typy, po které je vytvořena instance typu jsou označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-346">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="2680b-347">Použití `Browse` zásad na metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-347">Applying the `Browse` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-348">Každý typ parametru metody, je označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-348">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-349">Návratový typ metody je označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-349">The return type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-350">Nadřazený typ metody je označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-350">The containing type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-351">Pokud je metoda vytvořenou instanci obecné metody, nevytvořeným instancím obecná metoda je označena `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-351">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-352">Typ každý atribut do metody je označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-352">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-353">Pokud je obecná metoda, je označené každého typu omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-353">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-354">Pokud metody je obecný, typy, po které je vytvořena instance metoda jsou označeny `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-354">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="2680b-355">Použití `Browse` zásad pole zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-355">Applying the `Browse` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-356">Typ každý atribut použit na pole je označeno `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-356">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-357">Typ pole je označeno `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-357">The type of the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-358">Typ, ke kterému patří toto pole je označeno `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-358">The type to which the field belongs is marked with the `Browse` policy.</span></span>  
  
#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="2680b-359">Účinek zásady dynamického</span><span class="sxs-lookup"><span data-stu-id="2680b-359">The effect of Dynamic policy</span></span>  
 <span data-ttu-id="2680b-360">Použití `Dynamic` zásadu k typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-360">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-361">Je označené základní typ typu `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-361">The base type of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-362">Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-362">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-363">Pokud typ je typ delegátu, `Invoke` metoda v typu je označena `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-363">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-364">Každé rozhraní typ je označen `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-364">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-365">Typ každého atributu použitý pro typ je označen pomocí `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-365">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-366">Pokud je typ obecný, je označené každého typu omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-366">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-367">Pokud je typ obecný, typy, po které je vytvořena instance typu jsou označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-367">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="2680b-368">Použití `Dynamic` zásad na metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-368">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-369">Každý typ parametru metody, je označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-369">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-370">Návratový typ metody je označené `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-370">The return type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-371">Nadřazený typ metody je označené `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-371">The containing type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-372">Pokud je metoda vytvořenou instanci obecné metody, nevytvořeným instancím obecná metoda je označena `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-372">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-373">Typ každý atribut do metody je označené `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-373">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-374">Pokud je obecná metoda, je označené každého typu omezení `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-374">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-375">Pokud metody je obecný, typy, po které je vytvořena instance metoda jsou označeny `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-375">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-376">Metodu lze vyvolat pomocí `MethodInfo.Invoke`, a vytvoření delegáta je možné podle <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2680b-376">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2680b-377">Použití `Dynamic` zásad pole zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-377">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-378">Typ každý atribut použit na pole je označeno `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-378">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-379">Typ pole je označeno `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-379">The type of the field is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-380">Typ, ke kterému patří toto pole je označeno `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-380">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>  
  
#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="2680b-381">Účinek Zásady aktivace</span><span class="sxs-lookup"><span data-stu-id="2680b-381">The effect of Activation policy</span></span>  
 <span data-ttu-id="2680b-382">Použití zásady aktivace do typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-382">Applying the Activation policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-383">Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-383">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-384">Pokud typ je typ delegátu, `Invoke` metoda v typu je označena `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-384">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-385">Konstruktory typu jsou označené `Activation` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-385">Constructors of the type are marked with the `Activation` policy.</span></span>  
  
 <span data-ttu-id="2680b-386">Použití `Activation` zásad na metodu zahrnuje následující změnu zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-386">Applying the `Activation` policy to a method involves the following policy change:</span></span>  
  
-   <span data-ttu-id="2680b-387">Konstruktor jde vyvolat <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> a <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2680b-387">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="2680b-388">Pro metody `Activation` zásada ovlivňuje pouze konstruktory.</span><span class="sxs-lookup"><span data-stu-id="2680b-388">For methods, the `Activation` policy affects constructors only.</span></span>  
  
 <span data-ttu-id="2680b-389">Použití `Activation` zásad na pole nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="2680b-389">Applying the `Activation` policy to a field has no effect.</span></span>  
  
#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="2680b-390">Účinek zásady serializace</span><span class="sxs-lookup"><span data-stu-id="2680b-390">The effect of Serialize policy</span></span>  
 <span data-ttu-id="2680b-391">`Serialize` Zásad umožňuje použít běžné serializátory založenými na reflexi.</span><span class="sxs-lookup"><span data-stu-id="2680b-391">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="2680b-392">Ale vzhledem k tomu, že se mají Microsoftu známé vzorce přístupů k přesný odraz serializátory od jiných výrobců, tyto zásady nemusí být zcela efektivní.</span><span class="sxs-lookup"><span data-stu-id="2680b-392">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>  
  
 <span data-ttu-id="2680b-393">Použití `Serialize` zásadu k typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-393">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-394">Je označené základní typ typu `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-394">The base type of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-395">Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Browse` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-395">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="2680b-396">Pokud typ je typ delegátu, `Invoke` metoda v typu je označena `Dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-396">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="2680b-397">Pokud je typ výčtu, je označené pole typu `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-397">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-398">Pokud tento typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` je označené `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-398">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-399">Pokud je typ <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, nebo <xref:System.Collections.Generic.IReadOnlyList%601>, pak `T[]` a <xref:System.Collections.Generic.List%601> označené `Serialize` zásad., ale žádné členy typu rozhraní jsou označené `Serialize`zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-399">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-400">Pokud je typ <xref:System.Collections.Generic.List%601>, jsou označeny žádné členy typu `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-400">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-401">Pokud je typ <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> je označené `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-401">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="2680b-402">ale jsou označené žádné členy typu `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-402">but no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-403">Pokud je typ <xref:System.Collections.Generic.Dictionary%602>, jsou označeny žádné členy typu `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-403">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-404">Pokud tento typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` a `TValue` jsou označené `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-404">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-405">Každý konstruktoru, každý přistupující objekt vlastnosti a každé pole je označeno `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-405">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="2680b-406">Použití `Serialize` zásad na metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-406">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-407">Nadřazený typ je označen `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-407">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-408">Návratový typ metody je označené `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-408">The return type of the method is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="2680b-409">Použití `Serialize` zásad pole zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="2680b-409">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="2680b-410">Nadřazený typ je označen `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-410">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="2680b-411">Typ pole je označeno `Serialize` zásad.</span><span class="sxs-lookup"><span data-stu-id="2680b-411">The type of the field is marked with the `Serialize` policy.</span></span>  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a><span data-ttu-id="2680b-412">Účinek zásady XmlSerializer, Třída DataContractSerializer a DataContractJsonSerialier</span><span class="sxs-lookup"><span data-stu-id="2680b-412">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerialier policies</span></span>  
 <span data-ttu-id="2680b-413">Na rozdíl od `Serialize` zásad, která je určena pro serializátory založenými na reflexi, `XmlSerializer`, `DataContractSerializer`, a `DataContractJsonSerializer` zásady slouží k povolení sadu serializátory, které jsou známé [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce.</span><span class="sxs-lookup"><span data-stu-id="2680b-413">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the `XmlSerializer`, `DataContractSerializer`, and `DataContractJsonSerializer` policies are used to enable a set of serializers that are known to the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="2680b-414">Tyto serializátory nejsou implementované pomocí reflexe, ale sadu typů, které lze serializovat v době běhu je určen podobným způsobem jako typy, které jsou reflektovatelné.</span><span class="sxs-lookup"><span data-stu-id="2680b-414">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>  
  
 <span data-ttu-id="2680b-415">Použít některou z těchto zásad do typu umožňuje, aby typ k serializaci pomocí serializátoru odpovídající.</span><span class="sxs-lookup"><span data-stu-id="2680b-415">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="2680b-416">Navíc všechny typy, které potřebují serializace staticky určit Serializační stroj se také být serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="2680b-416">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>  
  
 <span data-ttu-id="2680b-417">Tyto zásady nemají žádný vliv na metody nebo pole.</span><span class="sxs-lookup"><span data-stu-id="2680b-417">These policies have no effect on methods or fields.</span></span>  
  
 <span data-ttu-id="2680b-418">Další informace najdete v části "Rozdíly v Serializátory" v [migrace Windows Store aplikace pro .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="2680b-418">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2680b-419">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2680b-419">See also</span></span>
- [<span data-ttu-id="2680b-420">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2680b-420">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="2680b-421">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="2680b-421">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)
