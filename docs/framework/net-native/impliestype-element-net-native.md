---
title: <ImpliesType> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1739c2a5e15d4c120d487c849819b6439afabade
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288012"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="0332f-102">\<ImpliesType > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0332f-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="0332f-103">Použije zásady na typ, pokud tyto zásady se nastavily pro nadřazený typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="0332f-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0332f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0332f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0332f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0332f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0332f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0332f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0332f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0332f-107">Attributes</span></span>  
  
|<span data-ttu-id="0332f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0332f-108">Attribute</span></span>|<span data-ttu-id="0332f-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="0332f-109">Attribute type</span></span>|<span data-ttu-id="0332f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0332f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0332f-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="0332f-111">General</span></span>|<span data-ttu-id="0332f-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-112">Required attribute.</span></span> <span data-ttu-id="0332f-113">Určuje název typu.</span><span class="sxs-lookup"><span data-stu-id="0332f-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="0332f-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0332f-114">Reflection</span></span>|<span data-ttu-id="0332f-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-115">Optional attribute.</span></span> <span data-ttu-id="0332f-116">Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="0332f-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="0332f-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0332f-117">Reflection</span></span>|<span data-ttu-id="0332f-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-118">Optional attribute.</span></span> <span data-ttu-id="0332f-119">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0332f-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="0332f-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0332f-120">Reflection</span></span>|<span data-ttu-id="0332f-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-121">Optional attribute.</span></span> <span data-ttu-id="0332f-122">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="0332f-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="0332f-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="0332f-123">Serialization</span></span>|<span data-ttu-id="0332f-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-124">Optional attribute.</span></span> <span data-ttu-id="0332f-125">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="0332f-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="0332f-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="0332f-126">Serialization</span></span>|<span data-ttu-id="0332f-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-127">Optional attribute.</span></span> <span data-ttu-id="0332f-128">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0332f-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="0332f-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="0332f-129">Serialization</span></span>|<span data-ttu-id="0332f-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-130">Optional attribute.</span></span> <span data-ttu-id="0332f-131">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0332f-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="0332f-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="0332f-132">Serialization</span></span>|<span data-ttu-id="0332f-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-133">Optional attribute.</span></span> <span data-ttu-id="0332f-134">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0332f-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="0332f-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="0332f-135">Interop</span></span>|<span data-ttu-id="0332f-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-136">Optional attribute.</span></span> <span data-ttu-id="0332f-137">Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0332f-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="0332f-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="0332f-138">Interop</span></span>|<span data-ttu-id="0332f-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-139">Optional attribute.</span></span> <span data-ttu-id="0332f-140">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0332f-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="0332f-141">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="0332f-141">Interop</span></span>|<span data-ttu-id="0332f-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0332f-142">Optional attribute.</span></span> <span data-ttu-id="0332f-143">Určuje zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0332f-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0332f-144">Název atributu</span><span class="sxs-lookup"><span data-stu-id="0332f-144">Name attribute</span></span>  
  
|<span data-ttu-id="0332f-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0332f-145">Value</span></span>|<span data-ttu-id="0332f-146">Popis</span><span class="sxs-lookup"><span data-stu-id="0332f-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0332f-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="0332f-147">*type_name*</span></span>|<span data-ttu-id="0332f-148">Název typu.</span><span class="sxs-lookup"><span data-stu-id="0332f-148">The type name.</span></span> <span data-ttu-id="0332f-149">Pokud typ reprezentovaný tímto objektem `<ImpliesType>` prvek nachází v oboru názvů stejný jako jeho obsahující `<Type>` elementu *type_name* může obsahovat název typu bez svůj obor názvů.</span><span class="sxs-lookup"><span data-stu-id="0332f-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="0332f-150">V opačném případě *type_name* musí obsahovat plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="0332f-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0332f-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="0332f-151">All other attributes</span></span>  
  
|<span data-ttu-id="0332f-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0332f-152">Value</span></span>|<span data-ttu-id="0332f-153">Popis</span><span class="sxs-lookup"><span data-stu-id="0332f-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0332f-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0332f-154">*policy_setting*</span></span>|<span data-ttu-id="0332f-155">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="0332f-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="0332f-156">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="0332f-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="0332f-157">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0332f-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0332f-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0332f-158">Child Elements</span></span>  
 <span data-ttu-id="0332f-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="0332f-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0332f-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0332f-160">Parent Elements</span></span>  
  
|<span data-ttu-id="0332f-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="0332f-161">Element</span></span>|<span data-ttu-id="0332f-162">Popis</span><span class="sxs-lookup"><span data-stu-id="0332f-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0332f-163">\<Type></span><span class="sxs-lookup"><span data-stu-id="0332f-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="0332f-164">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0332f-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="0332f-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="0332f-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="0332f-166">Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0332f-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="0332f-167">\<Method></span><span class="sxs-lookup"><span data-stu-id="0332f-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="0332f-168">Použije zásady reflexe pro metodu.</span><span class="sxs-lookup"><span data-stu-id="0332f-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0332f-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0332f-169">Remarks</span></span>  
 <span data-ttu-id="0332f-170">`<ImpliesType>` Element je primárně určena pro použití knihovny.</span><span class="sxs-lookup"><span data-stu-id="0332f-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="0332f-171">To řeší následující scénář:</span><span class="sxs-lookup"><span data-stu-id="0332f-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="0332f-172">Pokud rutiny potřebuje tak, aby odrážely na jeden typ, nutně musí tak, aby odrážely u druhého typu.</span><span class="sxs-lookup"><span data-stu-id="0332f-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="0332f-173">Metadata pro implicitní vytvoření instance typu druhý není k dispozici, jinak, protože statické analýzy neukazuje, že je nutné.</span><span class="sxs-lookup"><span data-stu-id="0332f-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="0332f-174">Nejčastěji jsou tyto dva typy obecných instancí s argumenty sdíleného typu.</span><span class="sxs-lookup"><span data-stu-id="0332f-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="0332f-175">`<ImpliesType>` Byl definován prvek za předpokladu, že potřebujete reflexe na typu určeného jeho nadřazený element znamená potřebu reflexe na typ určený `<ImpliesType>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0332f-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="0332f-176">Například následující direktivy reflection platí i pro dva typy `Explicit<T>` a `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="0332f-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="0332f-177">Tato direktiva nemá žádný vliv, pokud instance `Explicit` má definované `Dynamic` nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="0332f-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="0332f-178">Například, pokud je to tento případ pro `Explicit<Int32>`, `Implicit<Int32>` je vytvořena instance s jeho veřejné členy root, a jejich metadat je přístupné pro dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="0332f-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="0332f-179">Následuje příklad reálného světa, který platí pro jeden serializátor.</span><span class="sxs-lookup"><span data-stu-id="0332f-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="0332f-180">Direktivy zaznamenání požadavku, že něco reflexi typu `IList<` *něco* `>` zahrnuje také reflexi u odpovídajícího `List<` *něco* `>` typ nevyžaduje žádnou poznámku jednotlivých aplikací.</span><span class="sxs-lookup"><span data-stu-id="0332f-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="0332f-181">`<ImpliesType>` Element se může zobrazit i v rámci `<Method>` element, protože v některých případech vytváření instancí obecné metody zahrnuje vytvoření instance typu reflexi.</span><span class="sxs-lookup"><span data-stu-id="0332f-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="0332f-182">Představte si například obecné metody `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` , který danou knihovnu bude mít přístup k dynamicky spolu s přidruženou <xref:System.Collections.Generic.List%601> a <xref:System.Array> typy.</span><span class="sxs-lookup"><span data-stu-id="0332f-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="0332f-183">Tento rozdíl lze vyjádřit jako:</span><span class="sxs-lookup"><span data-stu-id="0332f-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0332f-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0332f-184">See also</span></span>
- [<span data-ttu-id="0332f-185">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0332f-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0332f-186">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0332f-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="0332f-187">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0332f-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
