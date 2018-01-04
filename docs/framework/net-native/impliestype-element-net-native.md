---
title: Element &lt;ImpliesType&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36620e8a8f6cb96b11f951ee5477e6edad9c925a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltimpliestypegt-element-net-native"></a><span data-ttu-id="5adcf-102">Element &lt;ImpliesType&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="5adcf-102">&lt;ImpliesType&gt; Element (.NET Native)</span></span>
<span data-ttu-id="5adcf-103">Platí zásady pro typu, v případě, že zásada obsahující typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="5adcf-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5adcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5adcf-104">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
             Browse="policy_type"  
             Dynamic="policy_type"  
             Serialize="policy_type"   
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5adcf-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5adcf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5adcf-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5adcf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5adcf-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="5adcf-107">Attributes</span></span>  
  
|<span data-ttu-id="5adcf-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="5adcf-108">Attribute</span></span>|<span data-ttu-id="5adcf-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="5adcf-109">Attribute type</span></span>|<span data-ttu-id="5adcf-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5adcf-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="5adcf-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="5adcf-111">General</span></span>|<span data-ttu-id="5adcf-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-112">Required attribute.</span></span> <span data-ttu-id="5adcf-113">Určuje název typu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="5adcf-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5adcf-114">Reflection</span></span>|<span data-ttu-id="5adcf-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-115">Optional attribute.</span></span> <span data-ttu-id="5adcf-116">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="5adcf-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="5adcf-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5adcf-117">Reflection</span></span>|<span data-ttu-id="5adcf-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-118">Optional attribute.</span></span> <span data-ttu-id="5adcf-119">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5adcf-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="5adcf-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5adcf-120">Reflection</span></span>|<span data-ttu-id="5adcf-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-121">Optional attribute.</span></span> <span data-ttu-id="5adcf-122">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="5adcf-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="5adcf-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="5adcf-123">Serialization</span></span>|<span data-ttu-id="5adcf-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-124">Optional attribute.</span></span> <span data-ttu-id="5adcf-125">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="5adcf-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="5adcf-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="5adcf-126">Serialization</span></span>|<span data-ttu-id="5adcf-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-127">Optional attribute.</span></span> <span data-ttu-id="5adcf-128">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="5adcf-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="5adcf-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="5adcf-129">Serialization</span></span>|<span data-ttu-id="5adcf-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-130">Optional attribute.</span></span> <span data-ttu-id="5adcf-131">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="5adcf-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="5adcf-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="5adcf-132">Serialization</span></span>|<span data-ttu-id="5adcf-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-133">Optional attribute.</span></span> <span data-ttu-id="5adcf-134">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="5adcf-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="5adcf-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="5adcf-135">Interop</span></span>|<span data-ttu-id="5adcf-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-136">Optional attribute.</span></span> <span data-ttu-id="5adcf-137">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="5adcf-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="5adcf-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="5adcf-138">Interop</span></span>|<span data-ttu-id="5adcf-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-139">Optional attribute.</span></span> <span data-ttu-id="5adcf-140">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="5adcf-141">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="5adcf-141">Interop</span></span>|<span data-ttu-id="5adcf-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5adcf-142">Optional attribute.</span></span> <span data-ttu-id="5adcf-143">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="5adcf-144">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="5adcf-144">Name attribute</span></span>  
  
|<span data-ttu-id="5adcf-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5adcf-145">Value</span></span>|<span data-ttu-id="5adcf-146">Popis</span><span class="sxs-lookup"><span data-stu-id="5adcf-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5adcf-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="5adcf-147">*type_name*</span></span>|<span data-ttu-id="5adcf-148">Název typu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-148">The type name.</span></span> <span data-ttu-id="5adcf-149">Pokud typ reprezentovaný tímto objektem `<ImpliesType>` prvek nachází v oboru názvů stejné jako jeho obsahující `<Type>` elementu *type_name* může zahrnovat název typu bez jeho obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5adcf-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="5adcf-150">V opačném *type_name* musí obsahovat typ plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="5adcf-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="5adcf-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="5adcf-151">All other attributes</span></span>  
  
|<span data-ttu-id="5adcf-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5adcf-152">Value</span></span>|<span data-ttu-id="5adcf-153">Popis</span><span class="sxs-lookup"><span data-stu-id="5adcf-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5adcf-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="5adcf-154">*policy_setting*</span></span>|<span data-ttu-id="5adcf-155">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="5adcf-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="5adcf-156">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="5adcf-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="5adcf-157">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5adcf-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5adcf-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5adcf-158">Child Elements</span></span>  
 <span data-ttu-id="5adcf-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="5adcf-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5adcf-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5adcf-160">Parent Elements</span></span>  
  
|<span data-ttu-id="5adcf-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="5adcf-161">Element</span></span>|<span data-ttu-id="5adcf-162">Popis</span><span class="sxs-lookup"><span data-stu-id="5adcf-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5adcf-163">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="5adcf-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="5adcf-164">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="5adcf-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="5adcf-165">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="5adcf-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="5adcf-166">Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="5adcf-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="5adcf-167">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="5adcf-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="5adcf-168">Reflexe zásada se vztahuje na metodu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5adcf-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5adcf-169">Remarks</span></span>  
 <span data-ttu-id="5adcf-170">`<ImpliesType>` Element je primárně určený pro použití knihovny.</span><span class="sxs-lookup"><span data-stu-id="5adcf-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="5adcf-171">Zaměřuje se na následující scénář:</span><span class="sxs-lookup"><span data-stu-id="5adcf-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="5adcf-172">Pokud rutinu, která potřebuje, aby odpovídala v jeden typ, nutně vyžaduje, aby odpovídala v druhého typu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="5adcf-173">Metadata pro předpokládané instance druhý typ není k dispozici, protože statické analysis není označení, že je nezbytné.</span><span class="sxs-lookup"><span data-stu-id="5adcf-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="5adcf-174">Existují dva typy nejčastěji, jsou obecné konkretizací s argumenty sdílené typu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="5adcf-175">`<ImpliesType>` Element byla definována za předpokladu, že potřebu reflexe v typu zadaném pomocí svého nadřízeného elementu znamená potřebu reflexe v typu zadaném pomocí `<ImpliesType>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="5adcf-176">Například následující direktivy reflexe použít dva typy `Explicit<T>` a `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="5adcf-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="5adcf-177">Tato direktiva nemá žádný vliv, pokud vytváření instancí z `Explicit` má definovanou `Dynamic` nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="5adcf-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="5adcf-178">Například, pokud je to tento případ pro `Explicit<Int32>`, `Implicit<Int32>` je vytvořena s jeho veřejné členy root, a jejich metadat je přístupné pro dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="5adcf-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="5adcf-179">Následuje příklad reálného, který se vztahuje na alespoň jeden serializátor.</span><span class="sxs-lookup"><span data-stu-id="5adcf-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="5adcf-180">Direktivy zaznamenat požadavky, které odráží na něco zadán jako `IList<` *něco* `>` také zahrnuje odrážející na odpovídajícím `List<` *něco* `>` typu bez nutnosti jakékoli poznámky jednotlivých aplikací.</span><span class="sxs-lookup"><span data-stu-id="5adcf-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="5adcf-181">`<ImpliesType>` Element se může zobrazit i v rámci `<Method>` elementu, protože v některých případech vytváření instancí obecná metoda znamená odrážející při vytváření instance typu.</span><span class="sxs-lookup"><span data-stu-id="5adcf-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="5adcf-182">Představte si například obecná metoda `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` , danou knihovnu bude přistupovat dynamicky spolu s příslušnými <xref:System.Collections.Generic.List%601> a <xref:System.Array> typy.</span><span class="sxs-lookup"><span data-stu-id="5adcf-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="5adcf-183">To může být vyjádřený jako:</span><span class="sxs-lookup"><span data-stu-id="5adcf-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5adcf-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="5adcf-184">See Also</span></span>  
 [<span data-ttu-id="5adcf-185">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5adcf-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="5adcf-186">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5adcf-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="5adcf-187">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5adcf-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
