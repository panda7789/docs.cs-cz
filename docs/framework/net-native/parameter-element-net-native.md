---
title: <Parameter> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c18919a6c48c251138a3d5e88079d3383979ef1a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266400"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="aa989-102">\<Parametr > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="aa989-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="aa989-103">Použije zásady reflexe pro daný typ argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="aa989-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa989-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa989-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa989-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aa989-105">Attributes and Elements</span></span>  
 <span data-ttu-id="aa989-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aa989-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa989-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="aa989-107">Attributes</span></span>  
  
|<span data-ttu-id="aa989-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="aa989-108">Attribute</span></span>|<span data-ttu-id="aa989-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="aa989-109">Attribute type</span></span>|<span data-ttu-id="aa989-110">Popis</span><span class="sxs-lookup"><span data-stu-id="aa989-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="aa989-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="aa989-111">General</span></span>|<span data-ttu-id="aa989-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-112">Required attribute.</span></span> <span data-ttu-id="aa989-113">Název parametru.</span><span class="sxs-lookup"><span data-stu-id="aa989-113">The parameter name.</span></span> <span data-ttu-id="aa989-114">Například pro podpis metody `String.CompareTo(Object value)`, hodnota `Name` atribut je "value".</span><span class="sxs-lookup"><span data-stu-id="aa989-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="aa989-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="aa989-115">Reflection</span></span>|<span data-ttu-id="aa989-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-116">Optional attribute.</span></span> <span data-ttu-id="aa989-117">Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="aa989-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="aa989-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="aa989-118">Reflection</span></span>|<span data-ttu-id="aa989-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-119">Optional attribute.</span></span> <span data-ttu-id="aa989-120">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="aa989-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="aa989-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="aa989-121">Reflection</span></span>|<span data-ttu-id="aa989-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-122">Optional attribute.</span></span> <span data-ttu-id="aa989-123">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="aa989-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="aa989-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="aa989-124">Serialization</span></span>|<span data-ttu-id="aa989-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-125">Optional attribute.</span></span> <span data-ttu-id="aa989-126">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="aa989-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="aa989-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="aa989-127">Serialization</span></span>|<span data-ttu-id="aa989-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-128">Optional attribute.</span></span> <span data-ttu-id="aa989-129">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="aa989-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="aa989-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="aa989-130">Serialization</span></span>|<span data-ttu-id="aa989-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-131">Optional attribute.</span></span> <span data-ttu-id="aa989-132">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="aa989-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="aa989-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="aa989-133">Serialization</span></span>|<span data-ttu-id="aa989-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-134">Optional attribute.</span></span> <span data-ttu-id="aa989-135">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="aa989-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="aa989-136">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="aa989-136">Interop</span></span>|<span data-ttu-id="aa989-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-137">Optional attribute.</span></span> <span data-ttu-id="aa989-138">Určuje zásady pro zařazování typy odkazů ve WinRT a COM.</span><span class="sxs-lookup"><span data-stu-id="aa989-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="aa989-139">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="aa989-139">Interop</span></span>|<span data-ttu-id="aa989-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-140">Optional attribute.</span></span> <span data-ttu-id="aa989-141">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="aa989-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="aa989-142">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="aa989-142">Interop</span></span>|<span data-ttu-id="aa989-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa989-143">Optional attribute.</span></span> <span data-ttu-id="aa989-144">Určuje zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="aa989-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="aa989-145">Název atributu</span><span class="sxs-lookup"><span data-stu-id="aa989-145">Name attribute</span></span>  
  
|<span data-ttu-id="aa989-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aa989-146">Value</span></span>|<span data-ttu-id="aa989-147">Popis</span><span class="sxs-lookup"><span data-stu-id="aa989-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa989-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="aa989-148">*parameter_name*</span></span>|<span data-ttu-id="aa989-149">Název parametru metody, pro které zásada platí.</span><span class="sxs-lookup"><span data-stu-id="aa989-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="aa989-150">Například pro podpis metody `String.CompareTo(Object value)`, hodnota `Name` atribut je "value".</span><span class="sxs-lookup"><span data-stu-id="aa989-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="aa989-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="aa989-151">All other attributes</span></span>  
  
|<span data-ttu-id="aa989-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aa989-152">Value</span></span>|<span data-ttu-id="aa989-153">Popis</span><span class="sxs-lookup"><span data-stu-id="aa989-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa989-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="aa989-154">*policy_setting*</span></span>|<span data-ttu-id="aa989-155">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="aa989-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="aa989-156">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="aa989-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="aa989-157">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="aa989-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa989-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aa989-158">Child Elements</span></span>  
 <span data-ttu-id="aa989-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="aa989-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa989-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aa989-160">Parent Elements</span></span>  
  
|<span data-ttu-id="aa989-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa989-161">Element</span></span>|<span data-ttu-id="aa989-162">Popis</span><span class="sxs-lookup"><span data-stu-id="aa989-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa989-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="aa989-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="aa989-164">Použije zásady reflexe runtime konstruktoru nebo metody.</span><span class="sxs-lookup"><span data-stu-id="aa989-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa989-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa989-165">Remarks</span></span>  
 <span data-ttu-id="aa989-166">`<Parameter>` Element je podřízeným prvkem [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) elementu a se používá k aplikování zásad na konkrétní metody parametr.</span><span class="sxs-lookup"><span data-stu-id="aa989-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="aa989-167">Je zadán parametr konkrétní metody podle názvu, nikoli podle typu.</span><span class="sxs-lookup"><span data-stu-id="aa989-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="aa989-168">Nejméně jeden atribut, který představuje typ zásad, jako například `Activate` nebo `Dynamic`, musí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="aa989-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa989-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa989-169">See also</span></span>
- [<span data-ttu-id="aa989-170">\<Metoda > – Element</span><span class="sxs-lookup"><span data-stu-id="aa989-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="aa989-171">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="aa989-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="aa989-172">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="aa989-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="aa989-173">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="aa989-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
