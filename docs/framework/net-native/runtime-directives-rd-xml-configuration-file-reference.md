---
title: Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738405"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="3b8b4-102">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3b8b4-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="3b8b4-103">Soubor direktiv modulu runtime (. Rd. XML) je konfigurační soubor XML, který určuje, zda jsou určené prvky programu k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="3b8b4-104">Tady je příklad souboru direktiv modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="3b8b4-105">Struktura souboru direktiv modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3b8b4-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="3b8b4-106">Soubor direktiv modulu runtime používá `http://schemas.microsoft.com/netfx/2013/01/metadata` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="3b8b4-107">Kořenový element je element [direktivy](directives-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3b8b4-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="3b8b4-108">Může obsahovat nula nebo více prvků [knihovny](library-element-net-native.md) a nula nebo jeden prvek [aplikace](application-element-net-native.md) , jak je znázorněno v následující struktuře.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="3b8b4-109">Atributy prvku [aplikace](application-element-net-native.md) mohou definovat zásady reflexe modulu runtime v rámci aplikace nebo mohou sloužit jako kontejner pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="3b8b4-110">Element [Library (knihovna](library-element-net-native.md) ) je na druhé straně jednoduchý kontejner.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="3b8b4-111">Podřízené položky prvků [aplikace](application-element-net-native.md) a [knihovny](library-element-net-native.md) definují typy, metody, pole, vlastnosti a události, které jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="3b8b4-112">Pro referenční informace vyberte prvky z následující struktury nebo si prohlédněte [elementy direktivy modulu runtime](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="3b8b4-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="3b8b4-113">V následující hierarchii se tři tečky označí rekurzivní strukturu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="3b8b4-114">Informace v závorkách označují, zda je tento prvek volitelný nebo vyžadovaný, a pokud je použit, kolik instancí (jedna nebo mnoho) je povoleno.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="3b8b4-115">[Direktivy](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-115">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="3b8b4-116">[Aplikace](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-116">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="3b8b4-117">[Sestavení](assembly-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-117">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-118">[Obor názvů](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-118">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-119">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-119">.</span></span> <span data-ttu-id="3b8b4-120">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-120">.</span></span>
      - <span data-ttu-id="3b8b4-121">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-121">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-122">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-122">.</span></span> <span data-ttu-id="3b8b4-123">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-123">.</span></span>
      - <span data-ttu-id="3b8b4-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-125">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-125">.</span></span> <span data-ttu-id="3b8b4-126">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-126">.</span></span>
    - <span data-ttu-id="3b8b4-127">[Obor názvů](namespace-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-127">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-128">[Obor názvů](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-128">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-129">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-129">.</span></span> <span data-ttu-id="3b8b4-130">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-130">.</span></span>
      - <span data-ttu-id="3b8b4-131">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-131">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-132">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-132">.</span></span> <span data-ttu-id="3b8b4-133">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-133">.</span></span>
      - <span data-ttu-id="3b8b4-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-135">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-135">.</span></span> <span data-ttu-id="3b8b4-136">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-136">.</span></span>
    - <span data-ttu-id="3b8b4-137">[Typ](type-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-137">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-138">[Podtypy](subtypes-element-net-native.md) (podtřídy obsahujícího typu) [O:1]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-138">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="3b8b4-139">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-139">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-140">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-140">.</span></span> <span data-ttu-id="3b8b4-141">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-141">.</span></span>
      - <span data-ttu-id="3b8b4-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-143">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-143">.</span></span> <span data-ttu-id="3b8b4-144">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-144">.</span></span>
      - <span data-ttu-id="3b8b4-145">[AttributeImplies](attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-145">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="3b8b4-146">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-147">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-147">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="3b8b4-148">[Parametr](parameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-148">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="3b8b4-149">[TypeParameter](typeparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="3b8b4-150">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-152">[Vlastnost](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-152">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-153">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-153">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-154">[Událost](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-154">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="3b8b4-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-156">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-156">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-157">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-157">.</span></span> <span data-ttu-id="3b8b4-158">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-158">.</span></span>
      - <span data-ttu-id="3b8b4-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-160">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-160">.</span></span> <span data-ttu-id="3b8b4-161">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-161">.</span></span>
      - <span data-ttu-id="3b8b4-162">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-162">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="3b8b4-163">[Parametr](parameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-163">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="3b8b4-164">[TypeParameter](typeparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="3b8b4-165">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-167">[Vlastnost](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-167">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-168">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-168">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-169">[Událost](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-169">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="3b8b4-170">[Knihovna](library-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-170">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="3b8b4-171">[Sestavení](assembly-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-171">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-172">[Obor názvů](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-172">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-173">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-173">.</span></span> <span data-ttu-id="3b8b4-174">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-174">.</span></span>
      - <span data-ttu-id="3b8b4-175">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-175">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-176">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-176">.</span></span> <span data-ttu-id="3b8b4-177">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-177">.</span></span>
      - <span data-ttu-id="3b8b4-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-179">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-179">.</span></span> <span data-ttu-id="3b8b4-180">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-180">.</span></span>
    - <span data-ttu-id="3b8b4-181">[Obor názvů](namespace-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-181">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-182">[Obor názvů](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-182">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-183">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-183">.</span></span> <span data-ttu-id="3b8b4-184">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-184">.</span></span>
      - <span data-ttu-id="3b8b4-185">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-185">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-186">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-186">.</span></span> <span data-ttu-id="3b8b4-187">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-187">.</span></span>
      - <span data-ttu-id="3b8b4-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-189">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-189">.</span></span> <span data-ttu-id="3b8b4-190">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-190">.</span></span>
    - <span data-ttu-id="3b8b4-191">[Typ](type-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-191">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-192">[Podtypy](subtypes-element-net-native.md) (podtřídy obsahujícího typu) [O:1]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-192">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="3b8b4-193">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-193">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-194">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-194">.</span></span> <span data-ttu-id="3b8b4-195">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-195">.</span></span>
      - <span data-ttu-id="3b8b4-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-197">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-197">.</span></span> <span data-ttu-id="3b8b4-198">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-198">.</span></span>
      - <span data-ttu-id="3b8b4-199">[AttributeImplies](attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-199">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="3b8b4-200">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-201">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-201">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-203">[Vlastnost](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-203">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-204">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-204">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-205">[Událost](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-205">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="3b8b4-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-207">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-207">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3b8b4-208">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-208">.</span></span> <span data-ttu-id="3b8b4-209">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-209">.</span></span>
      - <span data-ttu-id="3b8b4-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3b8b4-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3b8b4-211">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-211">.</span></span> <span data-ttu-id="3b8b4-212">.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-212">.</span></span>
      - <span data-ttu-id="3b8b4-213">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-213">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-215">[Vlastnost](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-215">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-216">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-216">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="3b8b4-217">[Událost](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3b8b4-217">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="3b8b4-218">Element [aplikace](application-element-net-native.md) nemůže mít žádné atributy, nebo může mít atributy zásad popsané v [části direktiva a zásady modulu runtime](#Directives).</span><span class="sxs-lookup"><span data-stu-id="3b8b4-218">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="3b8b4-219">Element [knihovny](library-element-net-native.md) má jeden atribut `Name`, který určuje název knihovny nebo sestavení bez přípony souboru.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-219">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="3b8b4-220">Například následující prvek [knihovny](library-element-net-native.md) se vztahuje na sestavení s názvem Extensions. dll.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-220">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="3b8b4-221">Direktivy a zásady modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3b8b4-221">Runtime directives and policy</span></span>

<span data-ttu-id="3b8b4-222">Samotný prvek [aplikace](application-element-net-native.md) a podřízené prvky [knihovny](library-element-net-native.md) a prvků [aplikace](application-element-net-native.md) expresní zásady; To znamená, že definují způsob, jakým může aplikace použít reflexi u prvku programu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-222">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="3b8b4-223">Typ zásady je definován atributem elementu (například `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="3b8b4-223">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="3b8b4-224">Hodnota zásady je definována hodnotou atributu (například `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="3b8b4-224">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="3b8b4-225">Všechny zásady určené atributem elementu se vztahují na všechny podřízené prvky, které neurčují hodnotu pro tuto zásadu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-225">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="3b8b4-226">Například pokud je zásada určena prvkem [typu](type-element-net-native.md) , tato zásada platí pro všechny obsažené typy a členy, pro které není explicitně určena zásada.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-226">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="3b8b4-227">Zásady, které může vyjádřit [aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) , se liší od zásad, které je možné vyjádřit pro jednotlivé členy ( [metodou](method-element-net-native.md), [vlastností](property-element-net-native.md), [polem](field-element-net-native.md)a [událostmi](event-element-net-native.md) ).</span><span class="sxs-lookup"><span data-stu-id="3b8b4-227">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="3b8b4-228">Určení zásad pro sestavení, obory názvů a typy</span><span class="sxs-lookup"><span data-stu-id="3b8b4-228">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="3b8b4-229">[Aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) podporují následující typy zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-229">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="3b8b4-230">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-230">`Activate`.</span></span> <span data-ttu-id="3b8b4-231">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-231">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="3b8b4-232">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-232">`Browse`.</span></span> <span data-ttu-id="3b8b4-233">Řídí dotazování pro informace o prvcích programu, ale neumožňuje přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-233">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="3b8b4-234">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-234">`Dynamic`.</span></span> <span data-ttu-id="3b8b4-235">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-235">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="3b8b4-236">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-236">`Serialize`.</span></span> <span data-ttu-id="3b8b4-237">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a serializovat pomocí knihoven třetích stran, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-237">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="3b8b4-238">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-238">`DataContractSerializer`.</span></span> <span data-ttu-id="3b8b4-239">Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-239">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="3b8b4-240">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-240">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="3b8b4-241">Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-241">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="3b8b4-242">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-242">`XmlSerializer`.</span></span> <span data-ttu-id="3b8b4-243">Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-243">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="3b8b4-244">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-244">`MarshalObject`.</span></span> <span data-ttu-id="3b8b4-245">Řídí zásady pro zařazování typů odkazů do WinRT a COM.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-245">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="3b8b4-246">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-246">`MarshalDelegate`.</span></span> <span data-ttu-id="3b8b4-247">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-247">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="3b8b4-248">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="3b8b4-248">`MarshalStructure` .</span></span> <span data-ttu-id="3b8b4-249">Řídí zásady pro zařazování struktur do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-249">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="3b8b4-250">Nastavení přidružená k těmto typům zásad jsou:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-250">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="3b8b4-251">`All`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-251">`All`.</span></span> <span data-ttu-id="3b8b4-252">Povolte zásadu pro všechny typy a členy, které řetěz nástroje neodebere.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-252">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="3b8b4-253">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-253">`Auto`.</span></span> <span data-ttu-id="3b8b4-254">Použijte výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-254">Use the default behavior.</span></span> <span data-ttu-id="3b8b4-255">(Není-li určena zásada, je ekvivalentní nastavení této zásady na `Auto`, pokud tato zásada není přepsána, například nadřazeným prvkem.)</span><span class="sxs-lookup"><span data-stu-id="3b8b4-255">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="3b8b4-256">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-256">`Excluded`.</span></span> <span data-ttu-id="3b8b4-257">Zakáže zásady pro prvek programu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-257">Disable the policy for the program element.</span></span>

- <span data-ttu-id="3b8b4-258">`Public`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-258">`Public`.</span></span> <span data-ttu-id="3b8b4-259">Povolte zásadu pro veřejné typy nebo členy, pokud řetěz nástrojů nezjistí, že je člen zbytečný a proto jej odebere.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-259">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="3b8b4-260">(V druhém případě je nutné použít `Required Public` k zajištění toho, že člen je udržován a má možnosti reflexe.)</span><span class="sxs-lookup"><span data-stu-id="3b8b4-260">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="3b8b4-261">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-261">`PublicAndInternal`.</span></span> <span data-ttu-id="3b8b4-262">Povolte zásady pro veřejné a interní typy nebo členy, pokud je řetěz nástrojů neodebere.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-262">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="3b8b4-263">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-263">`Required Public`.</span></span> <span data-ttu-id="3b8b4-264">Vyžaduje, aby řetěz nástrojů zachoval veřejné typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-264">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="3b8b4-265">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-265">`Required PublicAndInternal`.</span></span> <span data-ttu-id="3b8b4-266">Vyžaduje, aby řetěz nástrojů zachoval veřejné i interní typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-266">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="3b8b4-267">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-267">`Required All`.</span></span> <span data-ttu-id="3b8b4-268">Vyžaduje, aby řetězec nástroje zachoval všechny typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-268">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="3b8b4-269">Například následující direktivy modulu runtime definují zásadu pro všechny typy a členy v souboru DataClasses. dll sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-269">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="3b8b4-270">Umožňuje reflexi pro serializaci všech veřejných vlastností, umožňuje procházení pro všechny typy a členy typu, umožňuje aktivaci pro všechny typy (z důvodu `Dynamic` atributu) a povoluje reflexi pro všechny veřejné typy a členy.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-270">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="3b8b4-271">Určení zásad pro členy</span><span class="sxs-lookup"><span data-stu-id="3b8b4-271">Specifying policy for members</span></span>

<span data-ttu-id="3b8b4-272">Prvky [Property](property-element-net-native.md) a [Field](field-element-net-native.md) podporují následující typy zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-272">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="3b8b4-273">`Browse` – řídí dotazování pro informace o tomto členu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-273">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="3b8b4-274">`Dynamic` – řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-274">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="3b8b4-275">Také ovládá dotazování na informace o nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-275">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="3b8b4-276">`Serialize` – řídí přístup k členu za běhu, aby se mohly instance typů serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-276">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="3b8b4-277">Tuto zásadu lze použít na konstruktory, pole a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-277">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="3b8b4-278">[Metoda](method-element-net-native.md) a prvky [události](event-element-net-native.md) podporují následující typy zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-278">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="3b8b4-279">`Browse` – řídí dotazování pro informace o tomto členu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-279">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="3b8b4-280">`Dynamic` – řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-280">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="3b8b4-281">Také ovládá dotazování na informace o nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-281">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="3b8b4-282">Nastavení přidružená k těmto typům zásad jsou:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-282">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="3b8b4-283">`Auto` – použije výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-283">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="3b8b4-284">(Pokud se nezadá zásada, bude se jednat o nastavení této zásady, aby se `Auto`, pokud je něco nepřepisuje.)</span><span class="sxs-lookup"><span data-stu-id="3b8b4-284">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="3b8b4-285">`Excluded` – nikdy Nezahrnovat metadata pro člena.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-285">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="3b8b4-286">`Included` – povolí zásadu, pokud se ve výstupu nachází nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-286">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="3b8b4-287">`Required` – vyžaduje, aby řetěz nástrojů zachoval tento člen, i když se zdá být nepoužitý, a pro něj povolí zásady.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-287">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="3b8b4-288">Sémantika souboru direktiv modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3b8b4-288">Runtime directives file semantics</span></span>

<span data-ttu-id="3b8b4-289">Zásady lze definovat současně pro elementy vyšší úrovně i na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-289">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="3b8b4-290">Například zásada může být definována pro sestavení a pro některé typy obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-290">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="3b8b4-291">Pokud není určitý element na nižší úrovni reprezentován, zdědí zásady jeho nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-291">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="3b8b4-292">Například pokud `Assembly` element je přítomen, ale `Type` prvky nejsou, zásada zadaná v prvku `Assembly` se vztahuje na každý typ v sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-292">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="3b8b4-293">U stejného prvku programu lze také použít více prvků.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-293">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="3b8b4-294">Například samostatné prvky [sestavení](assembly-element-net-native.md) mohou definovat stejný prvek zásad pro stejné sestavení odlišně.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-294">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="3b8b4-295">V následujících částech se dozvíte, jak se v těchto případech vyřeší zásada pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-295">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="3b8b4-296">[Typ](type-element-net-native.md) nebo prvek [metody](method-element-net-native.md) obecného typu nebo metody aplikuje zásady na všechny instance, které nemají vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-296">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="3b8b4-297">Například element `Type`, který určuje zásadu pro <xref:System.Collections.Generic.List%601>, se vztahuje na všechny vytvořené instance tohoto obecného typu, pokud není přepsán pro konkrétní konstruovaný typ (například `List<Int32>`) pomocí elementu `TypeInstantiation`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-297">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="3b8b4-298">V opačném případě elementy definují zásady pro prvek program s názvem.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-298">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="3b8b4-299">Pokud je prvek dvojznačný, modul hledá shody a pokud najde přesnou shodu, bude ho používat.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-299">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="3b8b4-300">Pokud najde více shod, dojde k upozornění nebo chybě.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-300">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="3b8b4-301">Pokud dvě direktivy používají zásady na stejný prvek programu</span><span class="sxs-lookup"><span data-stu-id="3b8b4-301">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="3b8b4-302">Pokud se dva prvky v různých souborech běhových direktiv pokusí nastavit stejný typ zásad pro stejný prvek programu (například sestavení nebo typ) na jiné hodnoty, konflikt je vyřešen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-302">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="3b8b4-303">Pokud `Excluded` element je přítomen, má přednost.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-303">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="3b8b4-304">`Required` má přednost před ne`Required`m.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-304">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="3b8b4-305">`All` má přednost před `PublicAndInternal`, která má přednost před `Public`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-305">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="3b8b4-306">Jakékoli explicitní nastavení má přednost před `Auto`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-306">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="3b8b4-307">Například pokud jeden projekt obsahuje následující dva soubory běhových direktiv, zásada serializace pro DataClasses. dll je nastavena na `Required Public` i `All`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-307">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="3b8b4-308">V takovém případě by zásada serializace byla vyřešena jako `Required All`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-308">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="3b8b4-309">Nicméně pokud se dvě direktivy v jednom souboru direktiv modulu runtime pokusí nastavit stejný typ zásad pro stejný prvek programu, nástroj definice schématu XML zobrazí chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-309">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="3b8b4-310">Pokud podřízené a nadřazené prvky použijí stejný typ zásad</span><span class="sxs-lookup"><span data-stu-id="3b8b4-310">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="3b8b4-311">Podřízené prvky přepíšou své nadřazené prvky, včetně nastavení `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-311">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="3b8b4-312">Přepsání je hlavní důvod, proč byste chtěli zadat `Auto`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-312">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="3b8b4-313">V následujícím příkladu je nastavení zásad serializace pro vše v `DataClasses`, které není v `DataClasses.ViewModels`, `Required Public`a vše, co je v `DataClasses` i `DataClasses.ViewModels`, by `All`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-313">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="3b8b4-314">Pokud jsou otevřené generické prvky a instance se stejnými typy, použijte stejný typ zásad</span><span class="sxs-lookup"><span data-stu-id="3b8b4-314">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="3b8b4-315">V následujícím příkladu je `Dictionary<int,int>` přiřazena zásada `Browse` pouze v případě, že má motor jiný důvod k tomu, aby se mu přidělila zásada `Browse` (která by jinak představovala výchozí chování); všechny ostatní instance <xref:System.Collections.Generic.Dictionary%602> budou procházet všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-315">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="3b8b4-316">Způsob odvození zásad</span><span class="sxs-lookup"><span data-stu-id="3b8b4-316">How policy is inferred</span></span>

<span data-ttu-id="3b8b4-317">Každý typ zásad má jinou sadu pravidel, která určují, jak bude mít přítomnost tohoto typu zásad vliv na jiné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-317">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="3b8b4-318">Účinek zásad procházení</span><span class="sxs-lookup"><span data-stu-id="3b8b4-318">The effect of Browse policy</span></span>

<span data-ttu-id="3b8b4-319">Použití zásad `Browse` na typ zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-319">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-320">Základní typ tohoto typu je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-320">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-321">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-322">Pokud je typ delegát, je metoda `Invoke` v typu označena zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-322">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-323">Každé rozhraní typu je označeno zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-323">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-324">Typ každého atributu, který je použit pro typ, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-324">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-325">Pokud je typ obecný, je každý typ omezení označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-325">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-326">Pokud je typ obecný, typy, jejichž instance jsou vytvořeny, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-326">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="3b8b4-327">Použití zásad `Browse` pro metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-327">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-328">Každý typ parametru metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-328">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-329">Návratový typ metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-329">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-330">Nadřazený typ metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-330">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-331">Pokud je metoda instancí generické metody, je obecná metoda uninstance označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-331">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-332">Typ každého atributu, který je použit pro metodu, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-332">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-333">Pokud je metoda obecná, každý typ omezení je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-333">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-334">Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-334">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="3b8b4-335">Použití zásad `Browse` u pole zahrnuje tyto změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-335">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-336">Typ každého atributu, který se používá pro pole, je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-336">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-337">Typ pole je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-337">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-338">Typ, ke kterému pole patří, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-338">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="3b8b4-339">Účinek dynamických zásad</span><span class="sxs-lookup"><span data-stu-id="3b8b4-339">The effect of Dynamic policy</span></span>

<span data-ttu-id="3b8b4-340">Použití zásad `Dynamic` na typ zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-340">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-341">Základní typ tohoto typu je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-341">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-342">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-342">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-343">Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-343">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-344">Každé rozhraní typu je označeno zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-344">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-345">Typ každého atributu, který je použit pro typ, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-345">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-346">Pokud je typ obecný, je každý typ omezení označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-346">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-347">Pokud je typ obecný, typy, jejichž instance jsou vytvořeny, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-347">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="3b8b4-348">Použití zásad `Dynamic` pro metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-348">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-349">Každý typ parametru metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-349">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-350">Návratový typ metody je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-350">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-351">Nadřazený typ metody je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-351">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-352">Pokud je metoda instancí generické metody, je obecná metoda uninstance označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-352">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-353">Typ každého atributu, který je použit pro metodu, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-353">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-354">Pokud je metoda obecná, každý typ omezení je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-354">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-355">Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-355">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-356">Metodu lze vyvolat pomocí `MethodInfo.Invoke`a je možné vytvořit delegáta pomocí <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-356">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3b8b4-357">Použití zásad `Dynamic` u pole zahrnuje tyto změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-357">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-358">Typ každého atributu, který se používá pro pole, je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-358">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-359">Typ pole je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-359">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-360">Typ, ke kterému pole patří, je označen zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-360">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="3b8b4-361">Účinek zásad aktivace</span><span class="sxs-lookup"><span data-stu-id="3b8b4-361">The effect of Activation policy</span></span>

<span data-ttu-id="3b8b4-362">Použití zásad aktivace u typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-362">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-363">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-363">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-364">Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-364">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-365">Konstruktory typu jsou označené zásadou `Activation`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-365">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="3b8b4-366">Použití zásad `Activation` pro metodu zahrnuje následující změnu zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-366">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="3b8b4-367">Konstruktor může být vyvolán metodami <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> a <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-367">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="3b8b4-368">Pro metody má zásada `Activation` vliv pouze na konstruktory.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-368">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="3b8b4-369">Použití zásad `Activation` pro pole nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-369">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="3b8b4-370">Účinek zásad serializace</span><span class="sxs-lookup"><span data-stu-id="3b8b4-370">The effect of Serialize policy</span></span>

<span data-ttu-id="3b8b4-371">Zásady `Serialize` umožňují použití běžných serializátorů založených na reflexi.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-371">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="3b8b4-372">Vzhledem k tomu, že společnost Microsoft nezná přesné vzory přístupu k reflexi serializátorů od jiných společností než Microsoftu, tato zásada nemusí být zcela účinná.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-372">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="3b8b4-373">Použití zásad `Serialize` na typ zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-373">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-374">Základní typ tohoto typu je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-374">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-375">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-375">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3b8b4-376">Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-376">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3b8b4-377">Pokud je typ výčet, pole typu je označeno zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-377">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-378">Pokud typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` je označen zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-378">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-379">Pokud je typ <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>nebo <xref:System.Collections.Generic.IReadOnlyList%601>, pak `T[]` a <xref:System.Collections.Generic.List%601> označené zásadou pro `Serialize`. nejsou ale žádné členy typu rozhraní označené zásadami pro `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-379">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-380">Pokud je typ <xref:System.Collections.Generic.List%601>, žádné členy typu nejsou označeny zásadami `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-380">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-381">Pokud je typ <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-381">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="3b8b4-382">ale žádní členové typu nejsou označeni pomocí zásad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-382">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-383">Pokud je typ <xref:System.Collections.Generic.Dictionary%602>, žádné členy typu nejsou označeny zásadami `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-383">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-384">Pokud typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` a `TValue` jsou označeny zásadami `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-384">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-385">Každý konstruktor, každý přistupující objekt vlastnosti a každé pole je označeno zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-385">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="3b8b4-386">Použití zásad `Serialize` pro metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-386">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-387">Nadřazený typ je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-387">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-388">Návratový typ metody je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-388">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="3b8b4-389">Použití zásad `Serialize` u pole zahrnuje tyto změny zásad:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-389">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="3b8b4-390">Nadřazený typ je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-390">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3b8b4-391">Typ pole je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-391">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="3b8b4-392">Vliv zásad XmlSerializer, DataContractSerializer a DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="3b8b4-392">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="3b8b4-393">Na rozdíl od `Serialize` zásady, která je určena pro serializátory založené na reflexi, jsou použity zásady <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k povolení sady serializátorů, které jsou známé jako řetězec nástroje .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-393">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="3b8b4-394">Tyto serializátory nejsou implementovány pomocí reflexe, ale sada typů, které lze serializovat za běhu, je určena podobným způsobem jako typy, které jsou reflektované.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-394">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="3b8b4-395">Použití jedné z těchto zásad na typ umožňuje serializovat typ pomocí odpovídajícího serializátoru.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-395">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="3b8b4-396">Všechny typy, které může modul serializace staticky určit jako nutnost serializace, budou také serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-396">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="3b8b4-397">Tyto zásady nemají žádný vliv na metody nebo pole.</span><span class="sxs-lookup"><span data-stu-id="3b8b4-397">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="3b8b4-398">Další informace najdete v části "rozdíly v Serializacích" v tématu [migrace aplikace pro Windows Store na .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="3b8b4-398">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3b8b4-399">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b8b4-399">See also</span></span>

- [<span data-ttu-id="3b8b4-400">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3b8b4-400">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="3b8b4-401">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="3b8b4-401">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
