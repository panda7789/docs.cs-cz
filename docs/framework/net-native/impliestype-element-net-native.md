---
title: Element &lt;ImpliesType&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97b3e63ceb4b121c3e71e33a00fdf725258039c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395587"
---
# <a name="ltimpliestypegt-element-net-native"></a><span data-ttu-id="3467b-102">Element &lt;ImpliesType&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3467b-102">&lt;ImpliesType&gt; Element (.NET Native)</span></span>
<span data-ttu-id="3467b-103">Platí zásady pro typu, v případě, že zásada obsahující typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="3467b-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3467b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3467b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3467b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3467b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3467b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3467b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3467b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3467b-107">Attributes</span></span>  
  
|<span data-ttu-id="3467b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3467b-108">Attribute</span></span>|<span data-ttu-id="3467b-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="3467b-109">Attribute type</span></span>|<span data-ttu-id="3467b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3467b-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3467b-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="3467b-111">General</span></span>|<span data-ttu-id="3467b-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-112">Required attribute.</span></span> <span data-ttu-id="3467b-113">Určuje název typu.</span><span class="sxs-lookup"><span data-stu-id="3467b-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="3467b-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3467b-114">Reflection</span></span>|<span data-ttu-id="3467b-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-115">Optional attribute.</span></span> <span data-ttu-id="3467b-116">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="3467b-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="3467b-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3467b-117">Reflection</span></span>|<span data-ttu-id="3467b-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-118">Optional attribute.</span></span> <span data-ttu-id="3467b-119">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3467b-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="3467b-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3467b-120">Reflection</span></span>|<span data-ttu-id="3467b-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-121">Optional attribute.</span></span> <span data-ttu-id="3467b-122">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="3467b-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="3467b-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="3467b-123">Serialization</span></span>|<span data-ttu-id="3467b-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-124">Optional attribute.</span></span> <span data-ttu-id="3467b-125">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="3467b-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="3467b-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="3467b-126">Serialization</span></span>|<span data-ttu-id="3467b-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-127">Optional attribute.</span></span> <span data-ttu-id="3467b-128">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="3467b-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="3467b-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="3467b-129">Serialization</span></span>|<span data-ttu-id="3467b-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-130">Optional attribute.</span></span> <span data-ttu-id="3467b-131">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="3467b-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="3467b-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="3467b-132">Serialization</span></span>|<span data-ttu-id="3467b-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-133">Optional attribute.</span></span> <span data-ttu-id="3467b-134">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="3467b-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="3467b-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="3467b-135">Interop</span></span>|<span data-ttu-id="3467b-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-136">Optional attribute.</span></span> <span data-ttu-id="3467b-137">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="3467b-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="3467b-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="3467b-138">Interop</span></span>|<span data-ttu-id="3467b-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-139">Optional attribute.</span></span> <span data-ttu-id="3467b-140">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3467b-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="3467b-141">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="3467b-141">Interop</span></span>|<span data-ttu-id="3467b-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3467b-142">Optional attribute.</span></span> <span data-ttu-id="3467b-143">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3467b-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3467b-144">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="3467b-144">Name attribute</span></span>  
  
|<span data-ttu-id="3467b-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3467b-145">Value</span></span>|<span data-ttu-id="3467b-146">Popis</span><span class="sxs-lookup"><span data-stu-id="3467b-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3467b-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="3467b-147">*type_name*</span></span>|<span data-ttu-id="3467b-148">Název typu.</span><span class="sxs-lookup"><span data-stu-id="3467b-148">The type name.</span></span> <span data-ttu-id="3467b-149">Pokud typ reprezentovaný tímto objektem `<ImpliesType>` prvek nachází v oboru názvů stejné jako jeho obsahující `<Type>` elementu *type_name* může zahrnovat název typu bez jeho obor názvů.</span><span class="sxs-lookup"><span data-stu-id="3467b-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="3467b-150">V opačném *type_name* musí obsahovat typ plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="3467b-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3467b-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="3467b-151">All other attributes</span></span>  
  
|<span data-ttu-id="3467b-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3467b-152">Value</span></span>|<span data-ttu-id="3467b-153">Popis</span><span class="sxs-lookup"><span data-stu-id="3467b-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3467b-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3467b-154">*policy_setting*</span></span>|<span data-ttu-id="3467b-155">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="3467b-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="3467b-156">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="3467b-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="3467b-157">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3467b-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3467b-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3467b-158">Child Elements</span></span>  
 <span data-ttu-id="3467b-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="3467b-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3467b-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3467b-160">Parent Elements</span></span>  
  
|<span data-ttu-id="3467b-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="3467b-161">Element</span></span>|<span data-ttu-id="3467b-162">Popis</span><span class="sxs-lookup"><span data-stu-id="3467b-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3467b-163">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="3467b-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="3467b-164">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="3467b-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="3467b-165">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="3467b-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="3467b-166">Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="3467b-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="3467b-167">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="3467b-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="3467b-168">Reflexe zásada se vztahuje na metodu.</span><span class="sxs-lookup"><span data-stu-id="3467b-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3467b-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3467b-169">Remarks</span></span>  
 <span data-ttu-id="3467b-170">`<ImpliesType>` Element je primárně určený pro použití knihovny.</span><span class="sxs-lookup"><span data-stu-id="3467b-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="3467b-171">Zaměřuje se na následující scénář:</span><span class="sxs-lookup"><span data-stu-id="3467b-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="3467b-172">Pokud rutinu, která potřebuje, aby odpovídala v jeden typ, nutně vyžaduje, aby odpovídala v druhého typu.</span><span class="sxs-lookup"><span data-stu-id="3467b-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="3467b-173">Metadata pro předpokládané instance druhý typ není k dispozici, protože statické analysis není označení, že je nezbytné.</span><span class="sxs-lookup"><span data-stu-id="3467b-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="3467b-174">Existují dva typy nejčastěji, jsou obecné konkretizací s argumenty sdílené typu.</span><span class="sxs-lookup"><span data-stu-id="3467b-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="3467b-175">`<ImpliesType>` Element byla definována za předpokladu, že potřebu reflexe v typu zadaném pomocí svého nadřízeného elementu znamená potřebu reflexe v typu zadaném pomocí `<ImpliesType>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3467b-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="3467b-176">Například následující direktivy reflexe použít dva typy `Explicit<T>` a `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="3467b-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="3467b-177">Tato direktiva nemá žádný vliv, pokud vytváření instancí z `Explicit` má definovanou `Dynamic` nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="3467b-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="3467b-178">Například, pokud je to tento případ pro `Explicit<Int32>`, `Implicit<Int32>` je vytvořena s jeho veřejné členy root, a jejich metadat je přístupné pro dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="3467b-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="3467b-179">Následuje příklad reálného, který se vztahuje na alespoň jeden serializátor.</span><span class="sxs-lookup"><span data-stu-id="3467b-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="3467b-180">Direktivy zaznamenat požadavky, které odráží na něco zadán jako `IList<` *něco* `>` také zahrnuje odrážející na odpovídajícím `List<` *něco* `>` typu bez nutnosti jakékoli poznámky jednotlivých aplikací.</span><span class="sxs-lookup"><span data-stu-id="3467b-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="3467b-181">`<ImpliesType>` Element se může zobrazit i v rámci `<Method>` elementu, protože v některých případech vytváření instancí obecná metoda znamená odrážející při vytváření instance typu.</span><span class="sxs-lookup"><span data-stu-id="3467b-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="3467b-182">Představte si například obecná metoda `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` , danou knihovnu bude přistupovat dynamicky spolu s příslušnými <xref:System.Collections.Generic.List%601> a <xref:System.Array> typy.</span><span class="sxs-lookup"><span data-stu-id="3467b-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="3467b-183">To může být vyjádřený jako:</span><span class="sxs-lookup"><span data-stu-id="3467b-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3467b-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="3467b-184">See Also</span></span>  
 [<span data-ttu-id="3467b-185">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3467b-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="3467b-186">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3467b-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="3467b-187">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3467b-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
