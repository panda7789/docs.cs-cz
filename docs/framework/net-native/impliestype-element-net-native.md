---
title: <ImpliesType>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10fa3a0ac04038bb686311a4d86c99442c0fcf26
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049666"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="a66c2-102">\<Element > ImpliesType (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="a66c2-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="a66c2-103">Použije zásady na typ, pokud byly tyto zásady použity na obsahující typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a66c2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a66c2-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a66c2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a66c2-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a66c2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a66c2-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a66c2-107">Attributes</span></span>  
  
|<span data-ttu-id="a66c2-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a66c2-108">Attribute</span></span>|<span data-ttu-id="a66c2-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="a66c2-109">Attribute type</span></span>|<span data-ttu-id="a66c2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a66c2-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="a66c2-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="a66c2-111">General</span></span>|<span data-ttu-id="a66c2-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-112">Required attribute.</span></span> <span data-ttu-id="a66c2-113">Určuje název typu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="a66c2-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a66c2-114">Reflection</span></span>|<span data-ttu-id="a66c2-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-115">Optional attribute.</span></span> <span data-ttu-id="a66c2-116">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="a66c2-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="a66c2-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a66c2-117">Reflection</span></span>|<span data-ttu-id="a66c2-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-118">Optional attribute.</span></span> <span data-ttu-id="a66c2-119">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="a66c2-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a66c2-120">Reflection</span></span>|<span data-ttu-id="a66c2-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-121">Optional attribute.</span></span> <span data-ttu-id="a66c2-122">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="a66c2-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="a66c2-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="a66c2-123">Serialization</span></span>|<span data-ttu-id="a66c2-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-124">Optional attribute.</span></span> <span data-ttu-id="a66c2-125">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="a66c2-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="a66c2-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="a66c2-126">Serialization</span></span>|<span data-ttu-id="a66c2-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-127">Optional attribute.</span></span> <span data-ttu-id="a66c2-128">Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="a66c2-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="a66c2-129">Serialization</span></span>|<span data-ttu-id="a66c2-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-130">Optional attribute.</span></span> <span data-ttu-id="a66c2-131">Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="a66c2-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="a66c2-132">Serialization</span></span>|<span data-ttu-id="a66c2-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-133">Optional attribute.</span></span> <span data-ttu-id="a66c2-134">Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="a66c2-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="a66c2-135">Interop</span></span>|<span data-ttu-id="a66c2-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-136">Optional attribute.</span></span> <span data-ttu-id="a66c2-137">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="a66c2-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="a66c2-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="a66c2-138">Interop</span></span>|<span data-ttu-id="a66c2-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-139">Optional attribute.</span></span> <span data-ttu-id="a66c2-140">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="a66c2-141">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="a66c2-141">Interop</span></span>|<span data-ttu-id="a66c2-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a66c2-142">Optional attribute.</span></span> <span data-ttu-id="a66c2-143">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a66c2-144">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="a66c2-144">Name attribute</span></span>  
  
|<span data-ttu-id="a66c2-145">Value</span><span class="sxs-lookup"><span data-stu-id="a66c2-145">Value</span></span>|<span data-ttu-id="a66c2-146">Popis</span><span class="sxs-lookup"><span data-stu-id="a66c2-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a66c2-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="a66c2-147">*type_name*</span></span>|<span data-ttu-id="a66c2-148">Název typu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-148">The type name.</span></span> <span data-ttu-id="a66c2-149">Pokud je typ reprezentovaný tímto `<ImpliesType>` prvkem umístěný ve stejném oboru názvů jako element, který `<Type>` obsahuje, *TYPE_NAME* může obsahovat název typu bez jeho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a66c2-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="a66c2-150">Jinak musí *TYPE_NAME* obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="a66c2-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="a66c2-151">All other attributes</span></span>  
  
|<span data-ttu-id="a66c2-152">Value</span><span class="sxs-lookup"><span data-stu-id="a66c2-152">Value</span></span>|<span data-ttu-id="a66c2-153">Popis</span><span class="sxs-lookup"><span data-stu-id="a66c2-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a66c2-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a66c2-154">*policy_setting*</span></span>|<span data-ttu-id="a66c2-155">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="a66c2-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="a66c2-156">Možné hodnoty jsou `All`, `Auto`, `Excluded` ,`PublicAndInternal`,, ,`Required PublicAndInternal`a. `Required Public` `Public` `Required All`</span><span class="sxs-lookup"><span data-stu-id="a66c2-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="a66c2-157">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a66c2-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a66c2-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a66c2-158">Child Elements</span></span>  
 <span data-ttu-id="a66c2-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="a66c2-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a66c2-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a66c2-160">Parent Elements</span></span>  
  
|<span data-ttu-id="a66c2-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="a66c2-161">Element</span></span>|<span data-ttu-id="a66c2-162">Popis</span><span class="sxs-lookup"><span data-stu-id="a66c2-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a66c2-163">\<Zadejte ></span><span class="sxs-lookup"><span data-stu-id="a66c2-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="a66c2-164">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="a66c2-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="a66c2-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="a66c2-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="a66c2-166">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="a66c2-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="a66c2-167">\<Method></span><span class="sxs-lookup"><span data-stu-id="a66c2-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="a66c2-168">Aplikuje zásadu reflexe na metodu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a66c2-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a66c2-169">Remarks</span></span>  
 <span data-ttu-id="a66c2-170">`<ImpliesType>` Element je primárně určen pro použití v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="a66c2-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="a66c2-171">Řeší následující scénář:</span><span class="sxs-lookup"><span data-stu-id="a66c2-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="a66c2-172">Pokud rutina potřebuje reflektovat na jeden typ, musí být nutně odpovídat druhému typu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="a66c2-173">Metadata pro implicitní instanci druhého typu jsou jinak nedostupná, protože statická analýza neindikuje, že je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="a66c2-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="a66c2-174">Nejčastěji jsou tyto dva typy obecné instance s argumenty sdíleného typu.</span><span class="sxs-lookup"><span data-stu-id="a66c2-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="a66c2-175">Element byl definován s předpokladem, že nutnost reflexe u typu určeného jeho nadřazeným elementem implikuje nutnost reflexe u typu určeného `<ImpliesType>` elementem. `<ImpliesType>`</span><span class="sxs-lookup"><span data-stu-id="a66c2-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="a66c2-176">Například následující direktivy reflexe platí pro dva typy, `Explicit<T>` a `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="a66c2-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="a66c2-177">Tato direktiva nemá žádný vliv, pokud vytvoření instance `Explicit` má definované `Dynamic` nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="a66c2-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="a66c2-178">Například pokud se jedná o případ `Explicit<Int32>`, `Implicit<Int32>` je vytvořena instance s jeho veřejnými členy rootd a jejich metadata jsou k dispozici pro dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="a66c2-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="a66c2-179">Následuje příklad reálného světa, který se vztahuje alespoň na jeden serializátor.</span><span class="sxs-lookup"><span data-stu-id="a66c2-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="a66c2-180">Direktivy zachytí požadavek, který reflektuje na něco napsaného `IList<`jako *něco* `>` zahrnuje také reflektování `List<`na odpovídající typ *něčeho* `>` , aniž by to vyžadovalo. Anotace jednotlivých aplikací.</span><span class="sxs-lookup"><span data-stu-id="a66c2-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="a66c2-181">Element se může také objevit `<Method>` v rámci elementu, protože v některých případech instance obecné metody implikuje odrážející typ instance. `<ImpliesType>`</span><span class="sxs-lookup"><span data-stu-id="a66c2-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="a66c2-182">Představte si například obecnou `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` metodu, kterou bude mít daná knihovna k dynamickému přístupu <xref:System.Collections.Generic.List%601> společně <xref:System.Array> s přidruženými typy a.</span><span class="sxs-lookup"><span data-stu-id="a66c2-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="a66c2-183">Tato možnost může být vyjádřena takto:</span><span class="sxs-lookup"><span data-stu-id="a66c2-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a66c2-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a66c2-184">See also</span></span>

- [<span data-ttu-id="a66c2-185">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a66c2-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a66c2-186">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a66c2-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="a66c2-187">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a66c2-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
