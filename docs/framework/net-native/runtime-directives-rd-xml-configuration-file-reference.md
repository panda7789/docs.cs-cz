---
title: Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: f4c51dc269775d14d395cb464b3787cc987e086d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128131"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="e9906-102">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e9906-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="e9906-103">Soubor direktiv modulu runtime (. Rd. XML) je konfigurační soubor XML, který určuje, zda jsou určené prvky programu k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="e9906-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="e9906-104">Tady je příklad souboru direktiv modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="e9906-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="e9906-105">Struktura souboru direktiv modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e9906-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="e9906-106">Soubor direktiv modulu runtime používá `http://schemas.microsoft.com/netfx/2013/01/metadata` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e9906-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="e9906-107">Kořenový element je element [direktivy](directives-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="e9906-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="e9906-108">Může obsahovat nula nebo více prvků [knihovny](library-element-net-native.md) a nula nebo jeden prvek [aplikace](application-element-net-native.md) , jak je znázorněno v následující struktuře.</span><span class="sxs-lookup"><span data-stu-id="e9906-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="e9906-109">Atributy prvku [aplikace](application-element-net-native.md) mohou definovat zásady reflexe modulu runtime v rámci aplikace nebo mohou sloužit jako kontejner pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9906-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="e9906-110">Element [Library (knihovna](library-element-net-native.md) ) je na druhé straně jednoduchý kontejner.</span><span class="sxs-lookup"><span data-stu-id="e9906-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="e9906-111">Podřízené položky prvků [aplikace](application-element-net-native.md) a [knihovny](library-element-net-native.md) definují typy, metody, pole, vlastnosti a události, které jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="e9906-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="e9906-112">Pro referenční informace vyberte prvky z následující struktury nebo si prohlédněte [elementy direktivy modulu runtime](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="e9906-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="e9906-113">V následující hierarchii se tři tečky označí rekurzivní strukturu.</span><span class="sxs-lookup"><span data-stu-id="e9906-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="e9906-114">Informace v závorkách označují, zda je tento prvek volitelný nebo vyžadovaný, a pokud je použit, kolik instancí (jedna nebo mnoho) je povoleno.</span><span class="sxs-lookup"><span data-stu-id="e9906-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

<span data-ttu-id="e9906-115">[Direktivy](directives-element-net-native.md) [1:1] [aplikace](application-element-net-native.md) [0:1] [sestavení](assembly-element-net-native.md) [0: M] [obor názvů](namespace-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="e9906-115">[Directives](directives-element-net-native.md) [1:1] [Application](application-element-net-native.md) [0:1] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-116">.</span><span class="sxs-lookup"><span data-stu-id="e9906-116">.</span></span> <span data-ttu-id="e9906-117">.</span><span class="sxs-lookup"><span data-stu-id="e9906-117">.</span></span>
<span data-ttu-id="e9906-118">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-118">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-119">.</span><span class="sxs-lookup"><span data-stu-id="e9906-119">.</span></span> <span data-ttu-id="e9906-120">.</span><span class="sxs-lookup"><span data-stu-id="e9906-120">.</span></span>
<span data-ttu-id="e9906-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-122">.</span><span class="sxs-lookup"><span data-stu-id="e9906-122">.</span></span> <span data-ttu-id="e9906-123">.</span><span class="sxs-lookup"><span data-stu-id="e9906-123">.</span></span>
<span data-ttu-id="e9906-124">[Obor názvů](namespace-element-net-native.md) [0: m] [obor názvů](namespace-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="e9906-124">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-125">.</span><span class="sxs-lookup"><span data-stu-id="e9906-125">.</span></span> <span data-ttu-id="e9906-126">.</span><span class="sxs-lookup"><span data-stu-id="e9906-126">.</span></span>
<span data-ttu-id="e9906-127">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-127">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-128">.</span><span class="sxs-lookup"><span data-stu-id="e9906-128">.</span></span> <span data-ttu-id="e9906-129">.</span><span class="sxs-lookup"><span data-stu-id="e9906-129">.</span></span>
<span data-ttu-id="e9906-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-131">.</span><span class="sxs-lookup"><span data-stu-id="e9906-131">.</span></span> <span data-ttu-id="e9906-132">.</span><span class="sxs-lookup"><span data-stu-id="e9906-132">.</span></span>
<span data-ttu-id="e9906-133">[Typ](type-element-net-native.md) [0: m] [podtypy](subtypes-element-net-native.md) (podtřídy obsahujícího typu) [O:1] [typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-133">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-134">.</span><span class="sxs-lookup"><span data-stu-id="e9906-134">.</span></span> <span data-ttu-id="e9906-135">.</span><span class="sxs-lookup"><span data-stu-id="e9906-135">.</span></span>
<span data-ttu-id="e9906-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-137">.</span><span class="sxs-lookup"><span data-stu-id="e9906-137">.</span></span> <span data-ttu-id="e9906-138">.</span><span class="sxs-lookup"><span data-stu-id="e9906-138">.</span></span>
<span data-ttu-id="e9906-139">[AttributeImplies](attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: m] [Metoda](method-element-net-native.md) [0: M] [parametr](parameter-element-net-native.md) [0: m] [TypeParameter](typeparameter-element-net-native.md) [0: m] [GenericParameter](genericparameter-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) ( konstruované obecné metody) [0: M] [vlastnost](property-element-net-native.md) [[0: m] [](field-element-net-native.md) 0: m] [událost](event-element-net-native.md) [0: m] [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: m] [typ](type-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="e9906-139">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-140">.</span><span class="sxs-lookup"><span data-stu-id="e9906-140">.</span></span> <span data-ttu-id="e9906-141">.</span><span class="sxs-lookup"><span data-stu-id="e9906-141">.</span></span>
<span data-ttu-id="e9906-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-143">.</span><span class="sxs-lookup"><span data-stu-id="e9906-143">.</span></span> <span data-ttu-id="e9906-144">.</span><span class="sxs-lookup"><span data-stu-id="e9906-144">.</span></span>
<span data-ttu-id="e9906-145">[Metoda](method-element-net-native.md) [0: m] [parametr](parameter-element-net-native.md) [0: m] [TypeParameter](typeparameter-element-net-native.md) [0: M] [GenericParameter](genericparameter-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: m] [Property](property-element-net-native.md) [0: M] [pole](field-element-net-native.md) [0: m] [událost](event-element-net-native.md) [0: m] [ Knihovna](library-element-net-native.md) [0: m] [sestavení](assembly-element-net-native.md) [0: m] [obor názvů](namespace-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="e9906-145">[Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [Library](library-element-net-native.md) [0:M] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-146">.</span><span class="sxs-lookup"><span data-stu-id="e9906-146">.</span></span> <span data-ttu-id="e9906-147">.</span><span class="sxs-lookup"><span data-stu-id="e9906-147">.</span></span>
<span data-ttu-id="e9906-148">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-148">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-149">.</span><span class="sxs-lookup"><span data-stu-id="e9906-149">.</span></span> <span data-ttu-id="e9906-150">.</span><span class="sxs-lookup"><span data-stu-id="e9906-150">.</span></span>
<span data-ttu-id="e9906-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-152">.</span><span class="sxs-lookup"><span data-stu-id="e9906-152">.</span></span> <span data-ttu-id="e9906-153">.</span><span class="sxs-lookup"><span data-stu-id="e9906-153">.</span></span>
<span data-ttu-id="e9906-154">[Obor názvů](namespace-element-net-native.md) [0: m] [obor názvů](namespace-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="e9906-154">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-155">.</span><span class="sxs-lookup"><span data-stu-id="e9906-155">.</span></span> <span data-ttu-id="e9906-156">.</span><span class="sxs-lookup"><span data-stu-id="e9906-156">.</span></span>
<span data-ttu-id="e9906-157">[Zadejte](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-158">.</span><span class="sxs-lookup"><span data-stu-id="e9906-158">.</span></span> <span data-ttu-id="e9906-159">.</span><span class="sxs-lookup"><span data-stu-id="e9906-159">.</span></span>
<span data-ttu-id="e9906-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-161">.</span><span class="sxs-lookup"><span data-stu-id="e9906-161">.</span></span> <span data-ttu-id="e9906-162">.</span><span class="sxs-lookup"><span data-stu-id="e9906-162">.</span></span>
<span data-ttu-id="e9906-163">[Typ](type-element-net-native.md) [0: m] [podtypy](subtypes-element-net-native.md) (podtřídy obsahujícího typu) [O:1] [typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-163">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-164">.</span><span class="sxs-lookup"><span data-stu-id="e9906-164">.</span></span> <span data-ttu-id="e9906-165">.</span><span class="sxs-lookup"><span data-stu-id="e9906-165">.</span></span>
<span data-ttu-id="e9906-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-167">.</span><span class="sxs-lookup"><span data-stu-id="e9906-167">.</span></span> <span data-ttu-id="e9906-168">.</span><span class="sxs-lookup"><span data-stu-id="e9906-168">.</span></span>
<span data-ttu-id="e9906-169">[AttributeImplies](attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: m] [Metoda](method-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) (vytvořená obecná metoda) [0: m] [vlastnost](property-element-net-native.md) [0: m] [0: [m]](field-element-net-native.md) [Event](event-element-net-native.md) [0 : M] [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: m] [typ](type-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="e9906-169">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="e9906-170">.</span><span class="sxs-lookup"><span data-stu-id="e9906-170">.</span></span> <span data-ttu-id="e9906-171">.</span><span class="sxs-lookup"><span data-stu-id="e9906-171">.</span></span>
<span data-ttu-id="e9906-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M].</span><span class="sxs-lookup"><span data-stu-id="e9906-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="e9906-173">.</span><span class="sxs-lookup"><span data-stu-id="e9906-173">.</span></span> <span data-ttu-id="e9906-174">.</span><span class="sxs-lookup"><span data-stu-id="e9906-174">.</span></span>
<span data-ttu-id="e9906-175">[Metoda](method-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: m] [vlastnost](property-element-net-native.md) [0: M] [pole](field-element-net-native.md) [0: m] [událost](event-element-net-native.md) [0: m]</span><span class="sxs-lookup"><span data-stu-id="e9906-175">[Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="e9906-176">Element [aplikace](application-element-net-native.md) nemůže mít žádné atributy, nebo může mít atributy zásad popsané v [části direktiva a zásady modulu runtime](#Directives).</span><span class="sxs-lookup"><span data-stu-id="e9906-176">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="e9906-177">Element [knihovny](library-element-net-native.md) má jeden atribut `Name`, který určuje název knihovny nebo sestavení bez přípony souboru.</span><span class="sxs-lookup"><span data-stu-id="e9906-177">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="e9906-178">Například následující prvek [knihovny](library-element-net-native.md) se vztahuje na sestavení s názvem Extensions. dll.</span><span class="sxs-lookup"><span data-stu-id="e9906-178">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="e9906-179">Direktivy a zásady modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e9906-179">Runtime directives and policy</span></span>

<span data-ttu-id="e9906-180">Samotný prvek [aplikace](application-element-net-native.md) a podřízené prvky [knihovny](library-element-net-native.md) a prvků [aplikace](application-element-net-native.md) expresní zásady; To znamená, že definují způsob, jakým může aplikace použít reflexi u prvku programu.</span><span class="sxs-lookup"><span data-stu-id="e9906-180">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="e9906-181">Typ zásady je definován atributem elementu (například `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="e9906-181">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="e9906-182">Hodnota zásady je definována hodnotou atributu (například `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="e9906-182">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="e9906-183">Všechny zásady určené atributem elementu se vztahují na všechny podřízené prvky, které neurčují hodnotu pro tuto zásadu.</span><span class="sxs-lookup"><span data-stu-id="e9906-183">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="e9906-184">Například pokud je zásada určena prvkem [typu](type-element-net-native.md) , tato zásada platí pro všechny obsažené typy a členy, pro které není explicitně určena zásada.</span><span class="sxs-lookup"><span data-stu-id="e9906-184">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="e9906-185">Zásady, které může vyjádřit [aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) , se liší od zásad, které je možné vyjádřit pro jednotlivé členy ( [Metody](method-element-net-native.md), [vlastnosti](property-element-net-native.md), [pole](field-element-net-native.md)a prvky [události](event-element-net-native.md) ).</span><span class="sxs-lookup"><span data-stu-id="e9906-185">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="e9906-186">Určení zásad pro sestavení, obory názvů a typy</span><span class="sxs-lookup"><span data-stu-id="e9906-186">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="e9906-187">[Aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) podporují následující typy zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-187">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="e9906-188">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="e9906-188">`Activate`.</span></span> <span data-ttu-id="e9906-189">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="e9906-189">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="e9906-190">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-190">`Browse`.</span></span> <span data-ttu-id="e9906-191">Řídí dotazování pro informace o prvcích programu, ale neumožňuje přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e9906-191">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="e9906-192">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-192">`Dynamic`.</span></span> <span data-ttu-id="e9906-193">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="e9906-193">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="e9906-194">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-194">`Serialize`.</span></span> <span data-ttu-id="e9906-195">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a serializovat pomocí knihoven třetích stran, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="e9906-195">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="e9906-196">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="e9906-196">`DataContractSerializer`.</span></span> <span data-ttu-id="e9906-197">Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9906-197">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="e9906-198">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="e9906-198">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="e9906-199">Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9906-199">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="e9906-200">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="e9906-200">`XmlSerializer`.</span></span> <span data-ttu-id="e9906-201">Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9906-201">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="e9906-202">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="e9906-202">`MarshalObject`.</span></span> <span data-ttu-id="e9906-203">Řídí zásady pro zařazování typů odkazů do WinRT a COM.</span><span class="sxs-lookup"><span data-stu-id="e9906-203">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="e9906-204">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="e9906-204">`MarshalDelegate`.</span></span> <span data-ttu-id="e9906-205">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e9906-205">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="e9906-206">`MarshalStructure`.</span><span class="sxs-lookup"><span data-stu-id="e9906-206">`MarshalStructure` .</span></span> <span data-ttu-id="e9906-207">Řídí zásady pro zařazování struktur do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e9906-207">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="e9906-208">Nastavení přidružená k těmto typům zásad jsou:</span><span class="sxs-lookup"><span data-stu-id="e9906-208">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="e9906-209">`All`.</span><span class="sxs-lookup"><span data-stu-id="e9906-209">`All`.</span></span> <span data-ttu-id="e9906-210">Povolte zásadu pro všechny typy a členy, které řetěz nástroje neodebere.</span><span class="sxs-lookup"><span data-stu-id="e9906-210">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="e9906-211">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="e9906-211">`Auto`.</span></span> <span data-ttu-id="e9906-212">Použijte výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="e9906-212">Use the default behavior.</span></span> <span data-ttu-id="e9906-213">(Není-li určena zásada, je ekvivalentní nastavení této zásady na `Auto`, pokud tato zásada není přepsána, například nadřazeným prvkem.)</span><span class="sxs-lookup"><span data-stu-id="e9906-213">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="e9906-214">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="e9906-214">`Excluded`.</span></span> <span data-ttu-id="e9906-215">Zakáže zásady pro prvek programu.</span><span class="sxs-lookup"><span data-stu-id="e9906-215">Disable the policy for the program element.</span></span>

- <span data-ttu-id="e9906-216">`Public`.</span><span class="sxs-lookup"><span data-stu-id="e9906-216">`Public`.</span></span> <span data-ttu-id="e9906-217">Povolte zásadu pro veřejné typy nebo členy, pokud řetěz nástrojů nezjistí, že je člen zbytečný a proto jej odebere.</span><span class="sxs-lookup"><span data-stu-id="e9906-217">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="e9906-218">(V druhém případě je nutné použít `Required Public` k zajištění toho, že člen je udržován a má možnosti reflexe.)</span><span class="sxs-lookup"><span data-stu-id="e9906-218">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="e9906-219">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="e9906-219">`PublicAndInternal`.</span></span> <span data-ttu-id="e9906-220">Povolte zásady pro veřejné a interní typy nebo členy, pokud je řetěz nástrojů neodebere.</span><span class="sxs-lookup"><span data-stu-id="e9906-220">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="e9906-221">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="e9906-221">`Required Public`.</span></span> <span data-ttu-id="e9906-222">Vyžaduje, aby řetěz nástrojů zachoval veřejné typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.</span><span class="sxs-lookup"><span data-stu-id="e9906-222">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="e9906-223">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="e9906-223">`Required PublicAndInternal`.</span></span> <span data-ttu-id="e9906-224">Vyžaduje, aby řetěz nástrojů zachoval veřejné i interní typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.</span><span class="sxs-lookup"><span data-stu-id="e9906-224">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="e9906-225">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="e9906-225">`Required All`.</span></span> <span data-ttu-id="e9906-226">Vyžaduje, aby řetězec nástroje zachoval všechny typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.</span><span class="sxs-lookup"><span data-stu-id="e9906-226">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="e9906-227">Například následující direktivy modulu runtime definují zásadu pro všechny typy a členy v souboru DataClasses. dll sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9906-227">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="e9906-228">Umožňuje reflexi pro serializaci všech veřejných vlastností, umožňuje procházení pro všechny typy a členy typu, umožňuje aktivaci pro všechny typy (z důvodu `Dynamic` atributu) a povoluje reflexi pro všechny veřejné typy a členy.</span><span class="sxs-lookup"><span data-stu-id="e9906-228">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="e9906-229">Určení zásad pro členy</span><span class="sxs-lookup"><span data-stu-id="e9906-229">Specifying policy for members</span></span>

<span data-ttu-id="e9906-230">Prvky [Property](property-element-net-native.md) a [Field](field-element-net-native.md) podporují následující typy zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-230">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="e9906-231">`Browse` – řídí dotazování pro informace o tomto členu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="e9906-231">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="e9906-232">`Dynamic` – řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="e9906-232">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="e9906-233">Také ovládá dotazování na informace o nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="e9906-233">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="e9906-234">`Serialize` – řídí přístup k členu za běhu, aby se mohly instance typů serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="e9906-234">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="e9906-235">Tuto zásadu lze použít na konstruktory, pole a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e9906-235">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="e9906-236">[Metoda](method-element-net-native.md) a prvky [události](event-element-net-native.md) podporují následující typy zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-236">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="e9906-237">`Browse` – řídí dotazování pro informace o tomto členu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="e9906-237">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="e9906-238">`Dynamic` – řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="e9906-238">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="e9906-239">Také ovládá dotazování na informace o nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="e9906-239">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="e9906-240">Nastavení přidružená k těmto typům zásad jsou:</span><span class="sxs-lookup"><span data-stu-id="e9906-240">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="e9906-241">`Auto` – použije výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="e9906-241">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="e9906-242">(Pokud se nezadá zásada, bude se jednat o nastavení této zásady, aby se `Auto`, pokud je něco nepřepisuje.)</span><span class="sxs-lookup"><span data-stu-id="e9906-242">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="e9906-243">`Excluded` – nikdy Nezahrnovat metadata pro člena.</span><span class="sxs-lookup"><span data-stu-id="e9906-243">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="e9906-244">`Included` – povolí zásadu, pokud se ve výstupu nachází nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="e9906-244">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="e9906-245">`Required` – vyžaduje, aby řetěz nástrojů zachoval tento člen, i když se zdá být nepoužitý, a pro něj povolí zásady.</span><span class="sxs-lookup"><span data-stu-id="e9906-245">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="e9906-246">Sémantika souboru direktiv modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e9906-246">Runtime directives file semantics</span></span>

<span data-ttu-id="e9906-247">Zásady lze definovat současně pro elementy vyšší úrovně i na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="e9906-247">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="e9906-248">Například zásada může být definována pro sestavení a pro některé typy obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9906-248">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="e9906-249">Pokud není určitý element na nižší úrovni reprezentován, zdědí zásady jeho nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="e9906-249">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="e9906-250">Například pokud `Assembly` element je přítomen, ale `Type` prvky nejsou, zásada zadaná v prvku `Assembly` se vztahuje na každý typ v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9906-250">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="e9906-251">U stejného prvku programu lze také použít více prvků.</span><span class="sxs-lookup"><span data-stu-id="e9906-251">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="e9906-252">Například samostatné prvky [sestavení](assembly-element-net-native.md) mohou definovat stejný prvek zásad pro stejné sestavení odlišně.</span><span class="sxs-lookup"><span data-stu-id="e9906-252">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="e9906-253">V následujících částech se dozvíte, jak se v těchto případech vyřeší zásada pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="e9906-253">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="e9906-254">[Typ](type-element-net-native.md) nebo prvek [metody](method-element-net-native.md) obecného typu nebo metody aplikuje zásady na všechny instance, které nemají vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="e9906-254">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="e9906-255">Například element `Type`, který určuje zásadu pro <xref:System.Collections.Generic.List%601>, se vztahuje na všechny vytvořené instance tohoto obecného typu, pokud není přepsán pro konkrétní konstruovaný typ (například `List<Int32>`) pomocí elementu `TypeInstantiation`.</span><span class="sxs-lookup"><span data-stu-id="e9906-255">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="e9906-256">V opačném případě elementy definují zásady pro prvek program s názvem.</span><span class="sxs-lookup"><span data-stu-id="e9906-256">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="e9906-257">Pokud je prvek dvojznačný, modul hledá shody a pokud najde přesnou shodu, bude ho používat.</span><span class="sxs-lookup"><span data-stu-id="e9906-257">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="e9906-258">Pokud najde více shod, dojde k upozornění nebo chybě.</span><span class="sxs-lookup"><span data-stu-id="e9906-258">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="e9906-259">Pokud dvě direktivy používají zásady na stejný prvek programu</span><span class="sxs-lookup"><span data-stu-id="e9906-259">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="e9906-260">Pokud se dva prvky v různých souborech běhových direktiv pokusí nastavit stejný typ zásad pro stejný prvek programu (například sestavení nebo typ) na jiné hodnoty, konflikt je vyřešen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e9906-260">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="e9906-261">Pokud `Excluded` element je přítomen, má přednost.</span><span class="sxs-lookup"><span data-stu-id="e9906-261">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="e9906-262">`Required` má přednost před ne`Required`m.</span><span class="sxs-lookup"><span data-stu-id="e9906-262">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="e9906-263">`All` má přednost před `PublicAndInternal`, která má přednost před `Public`.</span><span class="sxs-lookup"><span data-stu-id="e9906-263">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="e9906-264">Jakékoli explicitní nastavení má přednost před `Auto`.</span><span class="sxs-lookup"><span data-stu-id="e9906-264">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="e9906-265">Například pokud jeden projekt obsahuje následující dva soubory běhových direktiv, zásada serializace pro DataClasses. dll je nastavena na `Required Public` i `All`.</span><span class="sxs-lookup"><span data-stu-id="e9906-265">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="e9906-266">V takovém případě by zásada serializace byla vyřešena jako `Required All`.</span><span class="sxs-lookup"><span data-stu-id="e9906-266">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="e9906-267">Nicméně pokud se dvě direktivy v jednom souboru direktiv modulu runtime pokusí nastavit stejný typ zásad pro stejný prvek programu, nástroj definice schématu XML zobrazí chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="e9906-267">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="e9906-268">Pokud podřízené a nadřazené prvky použijí stejný typ zásad</span><span class="sxs-lookup"><span data-stu-id="e9906-268">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="e9906-269">Podřízené prvky přepíšou své nadřazené prvky, včetně nastavení `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="e9906-269">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="e9906-270">Přepsání je hlavní důvod, proč byste chtěli zadat `Auto`.</span><span class="sxs-lookup"><span data-stu-id="e9906-270">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="e9906-271">V následujícím příkladu je nastavení zásad serializace pro vše v `DataClasses`, které není v `DataClasses.ViewModels`, `Required Public`a vše, co je v `DataClasses` i `DataClasses.ViewModels`, by `All`.</span><span class="sxs-lookup"><span data-stu-id="e9906-271">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="e9906-272">Pokud jsou otevřené generické prvky a instance se stejnými typy, použijte stejný typ zásad</span><span class="sxs-lookup"><span data-stu-id="e9906-272">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="e9906-273">V následujícím příkladu je `Dictionary<int,int>` přiřazena zásada `Browse` pouze v případě, že má motor jiný důvod k tomu, aby se mu přidělila zásada `Browse` (která by jinak představovala výchozí chování); všechny ostatní instance <xref:System.Collections.Generic.Dictionary%602> budou procházet všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="e9906-273">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="e9906-274">Způsob odvození zásad</span><span class="sxs-lookup"><span data-stu-id="e9906-274">How policy is inferred</span></span>

<span data-ttu-id="e9906-275">Každý typ zásad má jinou sadu pravidel, která určují, jak bude mít přítomnost tohoto typu zásad vliv na jiné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="e9906-275">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="e9906-276">Účinek zásad procházení</span><span class="sxs-lookup"><span data-stu-id="e9906-276">The effect of Browse policy</span></span>

<span data-ttu-id="e9906-277">Použití zásad `Browse` na typ zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-277">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-278">Základní typ tohoto typu je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-278">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-279">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-279">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-280">Pokud je typ delegát, je metoda `Invoke` v typu označena zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-280">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-281">Každé rozhraní typu je označeno zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-281">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-282">Typ každého atributu, který je použit pro typ, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-282">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-283">Pokud je typ obecný, je každý typ omezení označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-283">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-284">Pokud je typ obecný, typy, jejichž instance jsou vytvořeny, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-284">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="e9906-285">Použití zásad `Browse` pro metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-285">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-286">Každý typ parametru metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-286">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-287">Návratový typ metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-287">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-288">Nadřazený typ metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-288">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-289">Pokud je metoda instancí generické metody, je obecná metoda uninstance označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-289">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-290">Typ každého atributu, který je použit pro metodu, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-290">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-291">Pokud je metoda obecná, každý typ omezení je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-291">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-292">Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-292">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="e9906-293">Použití zásad `Browse` u pole zahrnuje tyto změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-293">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-294">Typ každého atributu, který se používá pro pole, je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-294">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-295">Typ pole je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-295">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-296">Typ, ke kterému pole patří, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-296">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="e9906-297">Účinek dynamických zásad</span><span class="sxs-lookup"><span data-stu-id="e9906-297">The effect of Dynamic policy</span></span>

<span data-ttu-id="e9906-298">Použití zásad `Dynamic` na typ zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-298">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-299">Základní typ tohoto typu je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-299">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-300">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-300">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-301">Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-301">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-302">Každé rozhraní typu je označeno zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-302">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-303">Typ každého atributu, který je použit pro typ, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-303">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-304">Pokud je typ obecný, je každý typ omezení označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-304">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-305">Pokud je typ obecný, typy, jejichž instance jsou vytvořeny, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-305">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="e9906-306">Použití zásad `Dynamic` pro metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-306">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-307">Každý typ parametru metody je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-307">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-308">Návratový typ metody je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-308">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-309">Nadřazený typ metody je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-309">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-310">Pokud je metoda instancí generické metody, je obecná metoda uninstance označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-310">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-311">Typ každého atributu, který je použit pro metodu, je označen zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-311">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-312">Pokud je metoda obecná, každý typ omezení je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-312">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-313">Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-313">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-314">Metodu lze vyvolat pomocí `MethodInfo.Invoke`a je možné vytvořit delegáta pomocí <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9906-314">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e9906-315">Použití zásad `Dynamic` u pole zahrnuje tyto změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-315">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-316">Typ každého atributu, který se používá pro pole, je označený zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-316">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-317">Typ pole je označený zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-317">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-318">Typ, ke kterému pole patří, je označen zásadou `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-318">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="e9906-319">Účinek zásad aktivace</span><span class="sxs-lookup"><span data-stu-id="e9906-319">The effect of Activation policy</span></span>

<span data-ttu-id="e9906-320">Použití zásad aktivace u typu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-320">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-321">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-322">Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-322">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-323">Konstruktory typu jsou označené zásadou `Activation`.</span><span class="sxs-lookup"><span data-stu-id="e9906-323">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="e9906-324">Použití zásad `Activation` pro metodu zahrnuje následující změnu zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-324">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="e9906-325">Konstruktor může být vyvolán metodami <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> a <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9906-325">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e9906-326">Pro metody má zásada `Activation` vliv pouze na konstruktory.</span><span class="sxs-lookup"><span data-stu-id="e9906-326">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="e9906-327">Použití zásad `Activation` pro pole nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="e9906-327">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="e9906-328">Účinek zásad serializace</span><span class="sxs-lookup"><span data-stu-id="e9906-328">The effect of Serialize policy</span></span>

<span data-ttu-id="e9906-329">Zásady `Serialize` umožňují použití běžných serializátorů založených na reflexi.</span><span class="sxs-lookup"><span data-stu-id="e9906-329">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="e9906-330">Vzhledem k tomu, že společnost Microsoft nezná přesné vzory přístupu k reflexi serializátorů od jiných společností než Microsoftu, tato zásada nemusí být zcela účinná.</span><span class="sxs-lookup"><span data-stu-id="e9906-330">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="e9906-331">Použití zásad `Serialize` na typ zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-331">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-332">Základní typ tohoto typu je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-332">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-333">Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.</span><span class="sxs-lookup"><span data-stu-id="e9906-333">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="e9906-334">Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="e9906-334">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="e9906-335">Pokud je typ výčet, pole typu je označeno zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-335">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-336">Pokud typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` je označen zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-336">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-337">Pokud je typ <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>nebo <xref:System.Collections.Generic.IReadOnlyList%601>, pak `T[]` a <xref:System.Collections.Generic.List%601> označené zásadou pro `Serialize`. nejsou ale žádné členy typu rozhraní označené zásadami pro `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-337">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-338">Pokud je typ <xref:System.Collections.Generic.List%601>, žádné členy typu nejsou označeny zásadami `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-338">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-339">Pokud je typ <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-339">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="e9906-340">ale žádní členové typu nejsou označeni pomocí zásad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-340">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-341">Pokud je typ <xref:System.Collections.Generic.Dictionary%602>, žádné členy typu nejsou označeny zásadami `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-341">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-342">Pokud typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` a `TValue` jsou označeny zásadami `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-342">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-343">Každý konstruktor, každý přistupující objekt vlastnosti a každé pole je označeno zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-343">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="e9906-344">Použití zásad `Serialize` pro metodu zahrnuje následující změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-344">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-345">Nadřazený typ je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-345">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-346">Návratový typ metody je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-346">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="e9906-347">Použití zásad `Serialize` u pole zahrnuje tyto změny zásad:</span><span class="sxs-lookup"><span data-stu-id="e9906-347">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="e9906-348">Nadřazený typ je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-348">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="e9906-349">Typ pole je označený zásadou `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="e9906-349">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="e9906-350">Vliv zásad XmlSerializer, DataContractSerializer a DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="e9906-350">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="e9906-351">Na rozdíl od `Serialize` zásady, která je určena pro serializátory založené na reflexi, jsou použity zásady <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k povolení sady serializátorů, které jsou známé jako řetězec nástroje .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e9906-351">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="e9906-352">Tyto serializátory nejsou implementovány pomocí reflexe, ale sada typů, které lze serializovat za běhu, je určena podobným způsobem jako typy, které jsou reflektované.</span><span class="sxs-lookup"><span data-stu-id="e9906-352">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="e9906-353">Použití jedné z těchto zásad na typ umožňuje serializovat typ pomocí odpovídajícího serializátoru.</span><span class="sxs-lookup"><span data-stu-id="e9906-353">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="e9906-354">Všechny typy, které může modul serializace staticky určit jako nutnost serializace, budou také serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="e9906-354">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="e9906-355">Tyto zásady nemají žádný vliv na metody nebo pole.</span><span class="sxs-lookup"><span data-stu-id="e9906-355">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="e9906-356">Další informace najdete v části "rozdíly v Serializacích" v tématu [migrace aplikace pro Windows Store na .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="e9906-356">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9906-357">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9906-357">See also</span></span>

- [<span data-ttu-id="e9906-358">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e9906-358">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e9906-359">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="e9906-359">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
