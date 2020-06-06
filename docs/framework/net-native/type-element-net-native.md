---
title: <Type>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: 4e88b49b82513079ddcf6f0bafe02d44235a406a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73091857"
---
# <a name="type-element-net-native"></a><span data-ttu-id="3053b-102">\<Type>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3053b-102">\<Type> Element (.NET Native)</span></span>

<span data-ttu-id="3053b-103">Aplikuje zásady modulu runtime na konkrétní typ, jako je třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="3053b-103">Applies runtime policy to a particular type, such as a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="3053b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3053b-104">Syntax</span></span>

```xml
<Type Name="type_name"
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

## <a name="attributes-and-elements"></a><span data-ttu-id="3053b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3053b-105">Attributes and Elements</span></span>

<span data-ttu-id="3053b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3053b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3053b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3053b-107">Attributes</span></span>

|<span data-ttu-id="3053b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3053b-108">Attribute</span></span>|<span data-ttu-id="3053b-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="3053b-109">Attribute type</span></span>|<span data-ttu-id="3053b-110">Description</span><span class="sxs-lookup"><span data-stu-id="3053b-110">Description</span></span>|
|---------------|--------------------|-----------------|
|`Name`|<span data-ttu-id="3053b-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="3053b-111">General</span></span>|<span data-ttu-id="3053b-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-112">Required attribute.</span></span> <span data-ttu-id="3053b-113">Určuje název typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-113">Specifies the type name.</span></span>|
|`Activate`|<span data-ttu-id="3053b-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3053b-114">Reflection</span></span>|<span data-ttu-id="3053b-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-115">Optional attribute.</span></span> <span data-ttu-id="3053b-116">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="3053b-116">Controls runtime access to constructors to enable activation of instances.</span></span>|
|`Browse`|<span data-ttu-id="3053b-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3053b-117">Reflection</span></span>|<span data-ttu-id="3053b-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-118">Optional attribute.</span></span> <span data-ttu-id="3053b-119">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="3053b-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|
|`Dynamic`|<span data-ttu-id="3053b-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3053b-120">Reflection</span></span>|<span data-ttu-id="3053b-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-121">Optional attribute.</span></span> <span data-ttu-id="3053b-122">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="3053b-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|
|`Serialize`|<span data-ttu-id="3053b-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="3053b-123">Serialization</span></span>|<span data-ttu-id="3053b-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-124">Optional attribute.</span></span> <span data-ttu-id="3053b-125">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="3053b-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|
|`DataContractSerializer`|<span data-ttu-id="3053b-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="3053b-126">Serialization</span></span>|<span data-ttu-id="3053b-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-127">Optional attribute.</span></span> <span data-ttu-id="3053b-128">Řídí zásady pro serializaci, která používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="3053b-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|
|`DataContractJsonSerializer`|<span data-ttu-id="3053b-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="3053b-129">Serialization</span></span>|<span data-ttu-id="3053b-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-130">Optional attribute.</span></span> <span data-ttu-id="3053b-131">Řídí zásady pro serializaci JSON, které používají <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="3053b-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|
|`XmlSerializer`|<span data-ttu-id="3053b-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="3053b-132">Serialization</span></span>|<span data-ttu-id="3053b-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-133">Optional attribute.</span></span> <span data-ttu-id="3053b-134">Řídí zásady pro serializaci XML, které používají <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="3053b-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|
|`MarshalObject`|<span data-ttu-id="3053b-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="3053b-135">Interop</span></span>|<span data-ttu-id="3053b-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-136">Optional attribute.</span></span> <span data-ttu-id="3053b-137">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="3053b-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|
|`MarshalDelegate`|<span data-ttu-id="3053b-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="3053b-138">Interop</span></span>|<span data-ttu-id="3053b-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-139">Optional attribute.</span></span> <span data-ttu-id="3053b-140">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3053b-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|
|`MarshalStructure`|<span data-ttu-id="3053b-141">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="3053b-141">Interop</span></span>|<span data-ttu-id="3053b-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3053b-142">Optional attribute.</span></span> <span data-ttu-id="3053b-143">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3053b-143">Controls policy for marshaling value types to native code.</span></span>|

## <a name="name-attribute"></a><span data-ttu-id="3053b-144">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="3053b-144">Name attribute</span></span>

|<span data-ttu-id="3053b-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3053b-145">Value</span></span>|<span data-ttu-id="3053b-146">Description</span><span class="sxs-lookup"><span data-stu-id="3053b-146">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="3053b-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="3053b-147">*type_name*</span></span>|<span data-ttu-id="3053b-148">Název typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-148">The type name.</span></span> <span data-ttu-id="3053b-149">Pokud `<Type>` je tento prvek podřízeným [\<Namespace>](namespace-element-net-native.md) elementem nebo jiným `<Type>` prvkem, *TYPE_NAME* může obsahovat název typu bez jeho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3053b-149">If this `<Type>` element is the child of either a [\<Namespace>](namespace-element-net-native.md) element or another `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="3053b-150">Jinak *TYPE_NAME* musí zahrnovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|

## <a name="all-other-attributes"></a><span data-ttu-id="3053b-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="3053b-151">All other attributes</span></span>

|<span data-ttu-id="3053b-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3053b-152">Value</span></span>|<span data-ttu-id="3053b-153">Description</span><span class="sxs-lookup"><span data-stu-id="3053b-153">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="3053b-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3053b-154">*policy_setting*</span></span>|<span data-ttu-id="3053b-155">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="3053b-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="3053b-156">Možné hodnoty jsou `All` , `Auto` , `Excluded` , `Public` , `PublicAndInternal` , `Required Public` , a `Required PublicAndInternal` `Required All` .</span><span class="sxs-lookup"><span data-stu-id="3053b-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="3053b-157">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3053b-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3053b-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3053b-158">Child Elements</span></span>

|<span data-ttu-id="3053b-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="3053b-159">Element</span></span>|<span data-ttu-id="3053b-160">Description</span><span class="sxs-lookup"><span data-stu-id="3053b-160">Description</span></span>|
|-------------|-----------------|
|[\<AttributeImplies>](attributeimplies-element-net-native.md)|<span data-ttu-id="3053b-161">Pokud je nadřazeným typem atribut, definuje zásady modulu runtime pro prvky kódu, na které je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="3053b-161">If the containing type is an attribute, defines runtime policy for code elements to which the attribute is applied.</span></span>|
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="3053b-162">Aplikuje zásadu odrazu na událost, která patří k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-162">Applies reflection policy to an event belonging to this type.</span></span>|
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="3053b-163">Aplikuje zásadu odrazu na pole patřící do tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-163">Applies reflection policy to a field belonging to this type.</span></span>|
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="3053b-164">Použije zásady na typ parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-164">Applies policy to the parameter type of a generic type.</span></span>|
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="3053b-165">Použije zásady na typ, pokud byly tyto zásady použity na typ reprezentovaný nadřazeným `<Type>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="3053b-165">Applies policy to a type, if that policy has been applied to the type represented by the containing `<Type>` element.</span></span>|
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="3053b-166">Aplikuje zásadu odrazu na metodu, která patří tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-166">Applies reflection policy to a method belonging to this type.</span></span>|
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="3053b-167">Aplikuje zásady odrazu na vytvořenou obecnou metodu, která patří k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-167">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="3053b-168">Aplikuje zásadu odrazu na vlastnost patřící tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-168">Applies reflection policy to a property belonging to this type.</span></span>|
|[\<Subtypes>](subtypes-element-net-native.md)|<span data-ttu-id="3053b-169">Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="3053b-169">Applies runtime policy to all classes inherited from the containing type.</span></span>|
|`<Type>`|<span data-ttu-id="3053b-170">Aplikuje zásadu odrazu na vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="3053b-170">Applies reflection policy to a nested type.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="3053b-171">Aplikuje zásadu odrazu na konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="3053b-171">Applies reflection policy to a constructed generic type.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3053b-172">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3053b-172">Parent Elements</span></span>

|<span data-ttu-id="3053b-173">Prvek</span><span class="sxs-lookup"><span data-stu-id="3053b-173">Element</span></span>|<span data-ttu-id="3053b-174">Description</span><span class="sxs-lookup"><span data-stu-id="3053b-174">Description</span></span>|
|-------------|-----------------|
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="3053b-175">Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3053b-175">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="3053b-176">Aplikuje zásady odrazu na všechny typy v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="3053b-176">Applies reflection policy to all the types in a specified assembly.</span></span>|
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="3053b-177">Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3053b-177">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="3053b-178">Aplikuje zásady odrazu na všechny typy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3053b-178">Applies reflection policy to all the types in a namespace.</span></span>|
|`<Type>`|<span data-ttu-id="3053b-179">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="3053b-179">Applies reflection policy to a type and all its members.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="3053b-180">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="3053b-180">Applies reflection policy to a constructed generic type and all its members.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3053b-181">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3053b-181">Remarks</span></span>

<span data-ttu-id="3053b-182">Atributy reflexe, serializace a interoperability jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="3053b-182">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="3053b-183">Pokud není žádné, `<Type>` element slouží jako kontejner, jehož podřízené typy definují zásady pro jednotlivé členy.</span><span class="sxs-lookup"><span data-stu-id="3053b-183">If none are present, the `<Type>` element serves as a container whose child types define policy for individual members.</span></span>

<span data-ttu-id="3053b-184">Pokud `<Type>` je prvek podřízený prvku [\<Assembly>](assembly-element-net-native.md) , [\<Namespace>](namespace-element-net-native.md) , `<Type>` nebo [\<TypeInstantiation>](typeinstantiation-element-net-native.md) , přepíše nastavení zásad definované nadřazeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="3053b-184">If a `<Type>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), `<Type>`, or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element, it overrides the policy settings defined by the parent element.</span></span>

<span data-ttu-id="3053b-185">`<Type>`Element obecného typu aplikuje zásady na všechny instance, které nemají vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="3053b-185">A `<Type>` element of a generic type applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="3053b-186">Zásady konstruovaných obecných typů jsou definovány [\<TypeInstantiation>](typeinstantiation-element-net-native.md) prvkem.</span><span class="sxs-lookup"><span data-stu-id="3053b-186">The policy of constructed generic types is defined by the [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>

<span data-ttu-id="3053b-187">Je-li typ obecný typ, jeho název je upraven symbolem čárky akcent ( \` ) následovaným jeho počtem obecných parametrů.</span><span class="sxs-lookup"><span data-stu-id="3053b-187">If the type is a generic type, its name is decorated by a grave accent symbol (\`) followed by its number of generic parameters.</span></span> <span data-ttu-id="3053b-188">Například `Name` atribut `<Type>` prvku pro <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídu se zobrazí jako ``Name="System.Collections.Generic.List`1"`` .</span><span class="sxs-lookup"><span data-stu-id="3053b-188">For example, the `Name` attribute of a `<Type>` element for the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class appears as ``Name="System.Collections.Generic.List`1"``.</span></span>

## <a name="example"></a><span data-ttu-id="3053b-189">Příklad</span><span class="sxs-lookup"><span data-stu-id="3053b-189">Example</span></span>

<span data-ttu-id="3053b-190">Následující příklad používá reflexi k zobrazení informací o polích, vlastnostech a metodách <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="3053b-190">The following example uses reflection to display information about the fields, properties, and methods of the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3053b-191">Proměnná `b` v příkladu je <xref:Windows.UI.Xaml.Controls.TextBlock> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3053b-191">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span> <span data-ttu-id="3053b-192">Vzhledem k tomu, že příklad jednoduše načte informace o typu, je dostupnost metadat řízena `Browse` nastavením zásad.</span><span class="sxs-lookup"><span data-stu-id="3053b-192">Because the example simply retrieves type information, the availability of metadata is controlled by the `Browse` policy setting.</span></span>

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <span data-ttu-id="3053b-193">Vzhledem k tomu, že metadata pro <xref:System.Collections.Generic.List%601> třídu nejsou automaticky obsažena v řetězu nástroje .NET Native, v příkladu se nezobrazí požadované informace o členu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3053b-193">Because metadata for the <xref:System.Collections.Generic.List%601> class isn't automatically included by the .NET Native tool chain, the example fails to display the requested member information at run time.</span></span> <span data-ttu-id="3053b-194">Chcete-li poskytnout potřebná metadata, přidejte následující `<Type>` prvek do souboru direktiv modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3053b-194">To provide the necessary metadata, add the following `<Type>` element to the runtime directives file.</span></span> <span data-ttu-id="3053b-195">Všimněte si, že vzhledem k tomu, že jsme poskytli nadřazený [<element oboru názvů \> ](namespace-element-net-native.md) , nemusíme v elementu zadat plně kvalifikovaný název typu `<Type>` .</span><span class="sxs-lookup"><span data-stu-id="3053b-195">Note that, because we've provided a parent [<Namespace\>](namespace-element-net-native.md) element, we don't have to provide a fully qualified type name in the `<Type>` element.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a><span data-ttu-id="3053b-196">Příklad</span><span class="sxs-lookup"><span data-stu-id="3053b-196">Example</span></span>
 <span data-ttu-id="3053b-197">Následující příklad používá reflexi k načtení <xref:System.Reflection.PropertyInfo> objektu, který představuje <xref:System.String.Chars%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3053b-197">The following example uses reflection to retrieve a <xref:System.Reflection.PropertyInfo> object that represents the <xref:System.String.Chars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3053b-198">Pak použije <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodu k načtení hodnoty sedmého znaku v řetězci a k zobrazení všech znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="3053b-198">It then uses the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method to retrieve the value of the seventh character in a string, and to display all the characters in the string.</span></span> <span data-ttu-id="3053b-199">Proměnná `b` v příkladu je <xref:Windows.UI.Xaml.Controls.TextBlock> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3053b-199">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <span data-ttu-id="3053b-200">Vzhledem k tomu, že metadata pro <xref:System.String> objekt nejsou k dispozici, volání <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody vyvolá <xref:System.NullReferenceException> výjimku za běhu při kompilování s řetězem nástrojů .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3053b-200">Because metadata for the <xref:System.String> object isn't available, the call to the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method throws a <xref:System.NullReferenceException> exception at run time when compiled with the .NET Native tool chain.</span></span> <span data-ttu-id="3053b-201">Chcete-li vyloučit výjimku a poskytnout potřebná metadata, přidejte `<Type>` do souboru direktiv modulu runtime následující element:</span><span class="sxs-lookup"><span data-stu-id="3053b-201">To eliminate the exception and provide the necessary metadata, add the following `<Type>` element to the runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a><span data-ttu-id="3053b-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="3053b-202">See also</span></span>

- [<span data-ttu-id="3053b-203">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3053b-203">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3053b-204">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3053b-204">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="3053b-205">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3053b-205">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
