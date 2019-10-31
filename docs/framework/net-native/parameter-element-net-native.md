---
title: <Parameter> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: c6dfc347d44a794ee8496c45ca879f9daab12b22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128202"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="5da17-102">> element \<parametru (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="5da17-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="5da17-103">Aplikuje zásadu odrazu na typ argumentu předaného metodě.</span><span class="sxs-lookup"><span data-stu-id="5da17-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5da17-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5da17-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5da17-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5da17-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5da17-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5da17-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="5da17-107">Attributes</span></span>  
  
|<span data-ttu-id="5da17-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="5da17-108">Attribute</span></span>|<span data-ttu-id="5da17-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="5da17-109">Attribute type</span></span>|<span data-ttu-id="5da17-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5da17-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="5da17-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="5da17-111">General</span></span>|<span data-ttu-id="5da17-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-112">Required attribute.</span></span> <span data-ttu-id="5da17-113">Název parametru.</span><span class="sxs-lookup"><span data-stu-id="5da17-113">The parameter name.</span></span> <span data-ttu-id="5da17-114">Například pro signaturu metody `String.CompareTo(Object value)`hodnota atributu `Name` je "value".</span><span class="sxs-lookup"><span data-stu-id="5da17-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="5da17-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5da17-115">Reflection</span></span>|<span data-ttu-id="5da17-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-116">Optional attribute.</span></span> <span data-ttu-id="5da17-117">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="5da17-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="5da17-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5da17-118">Reflection</span></span>|<span data-ttu-id="5da17-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-119">Optional attribute.</span></span> <span data-ttu-id="5da17-120">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="5da17-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="5da17-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5da17-121">Reflection</span></span>|<span data-ttu-id="5da17-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-122">Optional attribute.</span></span> <span data-ttu-id="5da17-123">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="5da17-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="5da17-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="5da17-124">Serialization</span></span>|<span data-ttu-id="5da17-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-125">Optional attribute.</span></span> <span data-ttu-id="5da17-126">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="5da17-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="5da17-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="5da17-127">Serialization</span></span>|<span data-ttu-id="5da17-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-128">Optional attribute.</span></span> <span data-ttu-id="5da17-129">Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5da17-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="5da17-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="5da17-130">Serialization</span></span>|<span data-ttu-id="5da17-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-131">Optional attribute.</span></span> <span data-ttu-id="5da17-132">Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5da17-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="5da17-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="5da17-133">Serialization</span></span>|<span data-ttu-id="5da17-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-134">Optional attribute.</span></span> <span data-ttu-id="5da17-135">Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5da17-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="5da17-136">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="5da17-136">Interop</span></span>|<span data-ttu-id="5da17-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-137">Optional attribute.</span></span> <span data-ttu-id="5da17-138">Řídí zásady pro zařazování typů odkazů do WinRT a COM.</span><span class="sxs-lookup"><span data-stu-id="5da17-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="5da17-139">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="5da17-139">Interop</span></span>|<span data-ttu-id="5da17-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-140">Optional attribute.</span></span> <span data-ttu-id="5da17-141">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="5da17-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="5da17-142">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="5da17-142">Interop</span></span>|<span data-ttu-id="5da17-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5da17-143">Optional attribute.</span></span> <span data-ttu-id="5da17-144">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="5da17-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="5da17-145">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="5da17-145">Name attribute</span></span>  
  
|<span data-ttu-id="5da17-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5da17-146">Value</span></span>|<span data-ttu-id="5da17-147">Popis</span><span class="sxs-lookup"><span data-stu-id="5da17-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5da17-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="5da17-148">*parameter_name*</span></span>|<span data-ttu-id="5da17-149">Název parametru metody, na který se zásada aplikuje.</span><span class="sxs-lookup"><span data-stu-id="5da17-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="5da17-150">Například pro signaturu metody `String.CompareTo(Object value)`hodnota atributu `Name` je "value".</span><span class="sxs-lookup"><span data-stu-id="5da17-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="5da17-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="5da17-151">All other attributes</span></span>  
  
|<span data-ttu-id="5da17-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5da17-152">Value</span></span>|<span data-ttu-id="5da17-153">Popis</span><span class="sxs-lookup"><span data-stu-id="5da17-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5da17-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="5da17-154">*policy_setting*</span></span>|<span data-ttu-id="5da17-155">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="5da17-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="5da17-156">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="5da17-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="5da17-157">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5da17-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5da17-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5da17-158">Child Elements</span></span>  
 <span data-ttu-id="5da17-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="5da17-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5da17-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5da17-160">Parent Elements</span></span>  
  
|<span data-ttu-id="5da17-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="5da17-161">Element</span></span>|<span data-ttu-id="5da17-162">Popis</span><span class="sxs-lookup"><span data-stu-id="5da17-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5da17-163">Metoda\<</span><span class="sxs-lookup"><span data-stu-id="5da17-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="5da17-164">Aplikuje zásady reflexe za běhu na konstruktor nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="5da17-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5da17-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5da17-165">Remarks</span></span>  
 <span data-ttu-id="5da17-166">Element `<Parameter>` je podřízený prvku [\<metody >](method-element-net-native.md) a používá se k aplikování zásad na konkrétní parametr metody.</span><span class="sxs-lookup"><span data-stu-id="5da17-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="5da17-167">Konkrétní parametr metody je určen podle názvu, nikoli podle typu.</span><span class="sxs-lookup"><span data-stu-id="5da17-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="5da17-168">Musí být přítomen alespoň jeden atribut, který představuje typ zásady, například `Activate` nebo `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="5da17-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da17-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5da17-169">See also</span></span>

- [<span data-ttu-id="5da17-170">\<> – element metody</span><span class="sxs-lookup"><span data-stu-id="5da17-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="5da17-171">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5da17-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="5da17-172">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5da17-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="5da17-173">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5da17-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
