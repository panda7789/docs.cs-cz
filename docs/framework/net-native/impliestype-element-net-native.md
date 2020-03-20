---
title: <ImpliesType>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181007"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="a0c6a-102">\<ImplikaceTyp> element (nativní.NET)</span><span class="sxs-lookup"><span data-stu-id="a0c6a-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="a0c6a-103">Platí zásady pro typ, pokud tato zásada byla použita pro obsahující typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0c6a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0c6a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0c6a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a0c6a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0c6a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0c6a-107">Attributes</span></span>  
  
|<span data-ttu-id="a0c6a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a0c6a-108">Attribute</span></span>|<span data-ttu-id="a0c6a-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="a0c6a-109">Attribute type</span></span>|<span data-ttu-id="a0c6a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a0c6a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="a0c6a-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="a0c6a-111">General</span></span>|<span data-ttu-id="a0c6a-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-112">Required attribute.</span></span> <span data-ttu-id="a0c6a-113">Určuje název typu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="a0c6a-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a0c6a-114">Reflection</span></span>|<span data-ttu-id="a0c6a-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-115">Optional attribute.</span></span> <span data-ttu-id="a0c6a-116">Řídí přístup za běhu k konstruktorům, aby bylo možné aktivovat instance.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="a0c6a-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a0c6a-117">Reflection</span></span>|<span data-ttu-id="a0c6a-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-118">Optional attribute.</span></span> <span data-ttu-id="a0c6a-119">Řídí dotazování na informace o prvcích programu, ale neumožňuje žádný přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="a0c6a-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a0c6a-120">Reflection</span></span>|<span data-ttu-id="a0c6a-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-121">Optional attribute.</span></span> <span data-ttu-id="a0c6a-122">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, aby bylo možné povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="a0c6a-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="a0c6a-123">Serialization</span></span>|<span data-ttu-id="a0c6a-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-124">Optional attribute.</span></span> <span data-ttu-id="a0c6a-125">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby instance typu mohly být serializovány a deserializovány knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="a0c6a-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="a0c6a-126">Serialization</span></span>|<span data-ttu-id="a0c6a-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-127">Optional attribute.</span></span> <span data-ttu-id="a0c6a-128">Řídí zásady serializace, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> která používá třídu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="a0c6a-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="a0c6a-129">Serialization</span></span>|<span data-ttu-id="a0c6a-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-130">Optional attribute.</span></span> <span data-ttu-id="a0c6a-131">Řídí zásady pro serializaci JSON, který používá třídu. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a0c6a-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="a0c6a-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="a0c6a-132">Serialization</span></span>|<span data-ttu-id="a0c6a-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-133">Optional attribute.</span></span> <span data-ttu-id="a0c6a-134">Řídí zásady serializace XML, která používá třídu. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a0c6a-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="a0c6a-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="a0c6a-135">Interop</span></span>|<span data-ttu-id="a0c6a-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-136">Optional attribute.</span></span> <span data-ttu-id="a0c6a-137">Řídí zásady pro zařazování typů odkazů na prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="a0c6a-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="a0c6a-138">Interop</span></span>|<span data-ttu-id="a0c6a-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-139">Optional attribute.</span></span> <span data-ttu-id="a0c6a-140">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="a0c6a-141">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="a0c6a-141">Interop</span></span>|<span data-ttu-id="a0c6a-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-142">Optional attribute.</span></span> <span data-ttu-id="a0c6a-143">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a0c6a-144">Atribut Název</span><span class="sxs-lookup"><span data-stu-id="a0c6a-144">Name attribute</span></span>  
  
|<span data-ttu-id="a0c6a-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a0c6a-145">Value</span></span>|<span data-ttu-id="a0c6a-146">Popis</span><span class="sxs-lookup"><span data-stu-id="a0c6a-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0c6a-147">*Type_name*</span><span class="sxs-lookup"><span data-stu-id="a0c6a-147">*type_name*</span></span>|<span data-ttu-id="a0c6a-148">Název typu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-148">The type name.</span></span> <span data-ttu-id="a0c6a-149">Pokud je typ `<ImpliesType>` reprezentované tímto prvkem umístěn `<Type>` ve stejném oboru názvů jako jeho obsahující prvek, *type_name* může obsahovat název typu bez jeho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="a0c6a-150">V opačném případě *musí type_name* obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="a0c6a-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="a0c6a-151">All other attributes</span></span>  
  
|<span data-ttu-id="a0c6a-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a0c6a-152">Value</span></span>|<span data-ttu-id="a0c6a-153">Popis</span><span class="sxs-lookup"><span data-stu-id="a0c6a-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0c6a-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a0c6a-154">*policy_setting*</span></span>|<span data-ttu-id="a0c6a-155">Nastavení, které se má použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="a0c6a-156">Možné hodnoty `All` `Auto`jsou `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , a .</span><span class="sxs-lookup"><span data-stu-id="a0c6a-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="a0c6a-157">Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a0c6a-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0c6a-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0c6a-158">Child Elements</span></span>  
 <span data-ttu-id="a0c6a-159">Žádné.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0c6a-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0c6a-160">Parent Elements</span></span>  
  
|<span data-ttu-id="a0c6a-161">Element</span><span class="sxs-lookup"><span data-stu-id="a0c6a-161">Element</span></span>|<span data-ttu-id="a0c6a-162">Popis</span><span class="sxs-lookup"><span data-stu-id="a0c6a-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0c6a-163">\<Typ></span><span class="sxs-lookup"><span data-stu-id="a0c6a-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="a0c6a-164">Použije zásady reflexe na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="a0c6a-165">\<TypRychlé></span><span class="sxs-lookup"><span data-stu-id="a0c6a-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="a0c6a-166">Použije zásady reflexe na vytvořený obecný typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="a0c6a-167">\<>metody</span><span class="sxs-lookup"><span data-stu-id="a0c6a-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="a0c6a-168">Použije zásady reflexe na metodu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0c6a-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0c6a-169">Remarks</span></span>  
 <span data-ttu-id="a0c6a-170">Prvek `<ImpliesType>` je primárně určen pro použití v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="a0c6a-171">Řeší následující scénář:</span><span class="sxs-lookup"><span data-stu-id="a0c6a-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="a0c6a-172">Pokud rutina potřebuje přemýšlet o jednom typu, musí nutně odrážet na druhý typ.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="a0c6a-173">Metadata pro implikované konkretizace druhého typu je jinak nedostupná, protože statická analýza neznamená, že je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="a0c6a-174">Nejčastěji dva typy jsou obecné instance s argumenty sdíleného typu.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="a0c6a-175">Prvek `<ImpliesType>` byl definován s předpokladem, že potřeba reflexe na typ určený jeho nadřazený prvek znamená potřebu reflexe na typ určený elementem. `<ImpliesType>`</span><span class="sxs-lookup"><span data-stu-id="a0c6a-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="a0c6a-176">Například následující direktivy reflexe `Explicit<T>` `Implicit<T>`platí pro dva typy a .</span><span class="sxs-lookup"><span data-stu-id="a0c6a-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="a0c6a-177">Tato směrnice nemá žádný účinek, `Explicit` pokud `Dynamic` konstanční má definované nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="a0c6a-178">Například pokud tomu tak je `Explicit<Int32>` `Implicit<Int32>` pro , je vytvořena instance s jeho veřejné členy zakořeněné a jejich metadata je přístupná pro dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="a0c6a-179">Následuje příklad reálného světa, který platí pro alespoň jeden serializátor.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="a0c6a-180">Direktivy zachycují požadavek, že `IList<`reflexe na něco zadali jako *něco* `>` také zahrnuje reflexi na odpovídající `List<` *něco* `>` typu bez nutnosti jakékoli poznámky pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="a0c6a-181">Prvek `<ImpliesType>` může také zobrazit `<Method>` v rámci prvku, protože v některých případech vytváření instancí obecné metody znamená reflexi na typ instanování.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="a0c6a-182">Představte si například `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` obecnou metodu, ke které bude <xref:System.Collections.Generic.List%601> <xref:System.Array> daná knihovna dynamicky přistupovat spolu s přidruženými a typy.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="a0c6a-183">To lze vyjádřit takto:</span><span class="sxs-lookup"><span data-stu-id="a0c6a-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0c6a-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c6a-184">See also</span></span>

- [<span data-ttu-id="a0c6a-185">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a0c6a-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a0c6a-186">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a0c6a-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="a0c6a-187">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a0c6a-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
