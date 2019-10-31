---
title: <ImpliesType> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 2f0ce1a1587e190627212cba07db298c12f4b30e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128394"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="6babf-102">\<element > ImpliesType (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6babf-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="6babf-103">Použije zásady na typ, pokud byly tyto zásady použity na obsahující typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="6babf-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6babf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6babf-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6babf-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6babf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6babf-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6babf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6babf-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="6babf-107">Attributes</span></span>  
  
|<span data-ttu-id="6babf-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="6babf-108">Attribute</span></span>|<span data-ttu-id="6babf-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="6babf-109">Attribute type</span></span>|<span data-ttu-id="6babf-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6babf-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6babf-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="6babf-111">General</span></span>|<span data-ttu-id="6babf-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-112">Required attribute.</span></span> <span data-ttu-id="6babf-113">Určuje název typu.</span><span class="sxs-lookup"><span data-stu-id="6babf-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="6babf-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6babf-114">Reflection</span></span>|<span data-ttu-id="6babf-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-115">Optional attribute.</span></span> <span data-ttu-id="6babf-116">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="6babf-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6babf-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6babf-117">Reflection</span></span>|<span data-ttu-id="6babf-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-118">Optional attribute.</span></span> <span data-ttu-id="6babf-119">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="6babf-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6babf-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6babf-120">Reflection</span></span>|<span data-ttu-id="6babf-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-121">Optional attribute.</span></span> <span data-ttu-id="6babf-122">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="6babf-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6babf-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="6babf-123">Serialization</span></span>|<span data-ttu-id="6babf-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-124">Optional attribute.</span></span> <span data-ttu-id="6babf-125">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="6babf-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6babf-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="6babf-126">Serialization</span></span>|<span data-ttu-id="6babf-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-127">Optional attribute.</span></span> <span data-ttu-id="6babf-128">Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6babf-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6babf-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="6babf-129">Serialization</span></span>|<span data-ttu-id="6babf-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-130">Optional attribute.</span></span> <span data-ttu-id="6babf-131">Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6babf-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6babf-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="6babf-132">Serialization</span></span>|<span data-ttu-id="6babf-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-133">Optional attribute.</span></span> <span data-ttu-id="6babf-134">Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6babf-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6babf-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="6babf-135">Interop</span></span>|<span data-ttu-id="6babf-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-136">Optional attribute.</span></span> <span data-ttu-id="6babf-137">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="6babf-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6babf-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="6babf-138">Interop</span></span>|<span data-ttu-id="6babf-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-139">Optional attribute.</span></span> <span data-ttu-id="6babf-140">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6babf-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6babf-141">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="6babf-141">Interop</span></span>|<span data-ttu-id="6babf-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6babf-142">Optional attribute.</span></span> <span data-ttu-id="6babf-143">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6babf-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6babf-144">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="6babf-144">Name attribute</span></span>  
  
|<span data-ttu-id="6babf-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6babf-145">Value</span></span>|<span data-ttu-id="6babf-146">Popis</span><span class="sxs-lookup"><span data-stu-id="6babf-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6babf-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="6babf-147">*type_name*</span></span>|<span data-ttu-id="6babf-148">Název typu.</span><span class="sxs-lookup"><span data-stu-id="6babf-148">The type name.</span></span> <span data-ttu-id="6babf-149">Pokud je typ reprezentovaný tímto `<ImpliesType>` element umístěn ve stejném oboru názvů jako jeho element obsahující `<Type>`, *TYPE_NAME* může obsahovat název typu bez jeho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6babf-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="6babf-150">Jinak musí *TYPE_NAME* obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="6babf-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6babf-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="6babf-151">All other attributes</span></span>  
  
|<span data-ttu-id="6babf-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6babf-152">Value</span></span>|<span data-ttu-id="6babf-153">Popis</span><span class="sxs-lookup"><span data-stu-id="6babf-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6babf-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6babf-154">*policy_setting*</span></span>|<span data-ttu-id="6babf-155">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="6babf-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="6babf-156">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="6babf-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6babf-157">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6babf-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6babf-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6babf-158">Child Elements</span></span>  
 <span data-ttu-id="6babf-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="6babf-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6babf-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6babf-160">Parent Elements</span></span>  
  
|<span data-ttu-id="6babf-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="6babf-161">Element</span></span>|<span data-ttu-id="6babf-162">Popis</span><span class="sxs-lookup"><span data-stu-id="6babf-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6babf-163">Typ\<</span><span class="sxs-lookup"><span data-stu-id="6babf-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="6babf-164">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="6babf-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="6babf-165">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="6babf-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="6babf-166">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="6babf-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="6babf-167">Metoda\<</span><span class="sxs-lookup"><span data-stu-id="6babf-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="6babf-168">Aplikuje zásadu reflexe na metodu.</span><span class="sxs-lookup"><span data-stu-id="6babf-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6babf-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6babf-169">Remarks</span></span>  
 <span data-ttu-id="6babf-170">Element `<ImpliesType>` je primárně určen pro použití v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="6babf-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="6babf-171">Řeší následující scénář:</span><span class="sxs-lookup"><span data-stu-id="6babf-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="6babf-172">Pokud rutina potřebuje reflektovat na jeden typ, musí být nutně odpovídat druhému typu.</span><span class="sxs-lookup"><span data-stu-id="6babf-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="6babf-173">Metadata pro implicitní instanci druhého typu jsou jinak nedostupná, protože statická analýza neindikuje, že je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="6babf-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="6babf-174">Nejčastěji jsou tyto dva typy obecné instance s argumenty sdíleného typu.</span><span class="sxs-lookup"><span data-stu-id="6babf-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="6babf-175">`<ImpliesType>` element byl definován s předpokladem, že nutnost reflexe u typu určeného jeho nadřazeným elementem implikuje nutnost reflexe u typu určeného `<ImpliesType>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="6babf-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="6babf-176">Například následující direktivy reflexe platí pro dva typy `Explicit<T>` a `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="6babf-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="6babf-177">Tato direktiva nemá žádný vliv, pokud vytvoření instance `Explicit` nemá definované nastavení zásad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="6babf-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="6babf-178">Pokud se například jedná o případ `Explicit<Int32>`, `Implicit<Int32>` se vytvoří instance se svými veřejnými členy rooted a jejich metadata jsou k dispozici pro dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="6babf-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="6babf-179">Následuje příklad reálného světa, který se vztahuje alespoň na jeden serializátor.</span><span class="sxs-lookup"><span data-stu-id="6babf-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="6babf-180">Direktivy zachytí požadavek, který se odráží na něco, co je `IList<`*něco*`>` zahrnuje také reflektování na odpovídající *`List<`typ*`>`, aniž by to vyžadovalo jednotlivé aplikace. poznámky.</span><span class="sxs-lookup"><span data-stu-id="6babf-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="6babf-181">Element `<ImpliesType>` se může také zobrazit v elementu `<Method>`, protože v některých případech instance obecné metody implikuje odrážející typ instance.</span><span class="sxs-lookup"><span data-stu-id="6babf-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="6babf-182">Představte si například obecnou metodu `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)`, že daná knihovna bude dynamicky přistupovat společně s přidruženými <xref:System.Collections.Generic.List%601> a <xref:System.Array> typy.</span><span class="sxs-lookup"><span data-stu-id="6babf-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="6babf-183">Tato možnost může být vyjádřena takto:</span><span class="sxs-lookup"><span data-stu-id="6babf-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6babf-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6babf-184">See also</span></span>

- [<span data-ttu-id="6babf-185">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6babf-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6babf-186">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6babf-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="6babf-187">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6babf-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
