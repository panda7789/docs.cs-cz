---
title: Element &lt;GenericParameter&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 601118d2dcc42f9e35da0e24c782b218efd7a025
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltgenericparametergt-element-net-native"></a><span data-ttu-id="519c1-102">Element &lt;GenericParameter&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="519c1-102">&lt;GenericParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="519c1-103">Zásada se vztahuje na typ parametru obecný typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="519c1-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="519c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="519c1-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="519c1-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="519c1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="519c1-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="519c1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="519c1-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="519c1-107">Attributes</span></span>  
  
|<span data-ttu-id="519c1-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="519c1-108">Attribute</span></span>|<span data-ttu-id="519c1-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="519c1-109">Attribute type</span></span>|<span data-ttu-id="519c1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="519c1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="519c1-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="519c1-111">General</span></span>|<span data-ttu-id="519c1-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-112">Required attribute.</span></span> <span data-ttu-id="519c1-113">Název obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="519c1-113">The name of the generic parameter.</span></span> <span data-ttu-id="519c1-114">Například pro obecný delegát <xref:System.Func%603>, hodnota `Name` atribut je "TResult" pro použití zásad runtime delegáta návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="519c1-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="519c1-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="519c1-115">Reflection</span></span>|<span data-ttu-id="519c1-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-116">Optional attribute.</span></span> <span data-ttu-id="519c1-117">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="519c1-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="519c1-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="519c1-118">Reflection</span></span>|<span data-ttu-id="519c1-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-119">Optional attribute.</span></span> <span data-ttu-id="519c1-120">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="519c1-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="519c1-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="519c1-121">Reflection</span></span>|<span data-ttu-id="519c1-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-122">Optional attribute.</span></span> <span data-ttu-id="519c1-123">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="519c1-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="519c1-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="519c1-124">Serialization</span></span>|<span data-ttu-id="519c1-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-125">Optional attribute.</span></span> <span data-ttu-id="519c1-126">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="519c1-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="519c1-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="519c1-127">Serialization</span></span>|<span data-ttu-id="519c1-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-128">Optional attribute.</span></span> <span data-ttu-id="519c1-129">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="519c1-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="519c1-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="519c1-130">Serialization</span></span>|<span data-ttu-id="519c1-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-131">Optional attribute.</span></span> <span data-ttu-id="519c1-132">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="519c1-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="519c1-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="519c1-133">Serialization</span></span>|<span data-ttu-id="519c1-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-134">Optional attribute.</span></span> <span data-ttu-id="519c1-135">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="519c1-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="519c1-136">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="519c1-136">Interop</span></span>|<span data-ttu-id="519c1-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-137">Optional attribute.</span></span> <span data-ttu-id="519c1-138">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="519c1-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="519c1-139">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="519c1-139">Interop</span></span>|<span data-ttu-id="519c1-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-140">Optional attribute.</span></span> <span data-ttu-id="519c1-141">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="519c1-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="519c1-142">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="519c1-142">Interop</span></span>|<span data-ttu-id="519c1-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-143">Optional attribute.</span></span> <span data-ttu-id="519c1-144">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="519c1-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="519c1-145">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="519c1-145">Name attribute</span></span>  
  
|<span data-ttu-id="519c1-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="519c1-146">Value</span></span>|<span data-ttu-id="519c1-147">Popis</span><span class="sxs-lookup"><span data-stu-id="519c1-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="519c1-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="519c1-148">*generic_parameter_name*</span></span>|<span data-ttu-id="519c1-149">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="519c1-149">Required attribute.</span></span> <span data-ttu-id="519c1-150">Název parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="519c1-150">The name of the generic type parameter.</span></span> <span data-ttu-id="519c1-151">Například pro obecný delegát <xref:System.Func%603>, *generic_parameter_name* hodnotu "TResult" platí zásady modulu runtime pro delegáta návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="519c1-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="519c1-152">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="519c1-152">All other attributes</span></span>  
  
|<span data-ttu-id="519c1-153">Hodnota</span><span class="sxs-lookup"><span data-stu-id="519c1-153">Value</span></span>|<span data-ttu-id="519c1-154">Popis</span><span class="sxs-lookup"><span data-stu-id="519c1-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="519c1-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="519c1-155">*policy_setting*</span></span>|<span data-ttu-id="519c1-156">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="519c1-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="519c1-157">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="519c1-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="519c1-158">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="519c1-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="519c1-159">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="519c1-159">Child Elements</span></span>  
 <span data-ttu-id="519c1-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="519c1-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="519c1-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="519c1-161">Parent Elements</span></span>  
  
|<span data-ttu-id="519c1-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="519c1-162">Element</span></span>|<span data-ttu-id="519c1-163">Popis</span><span class="sxs-lookup"><span data-stu-id="519c1-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="519c1-164">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="519c1-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="519c1-165">Platí zásady reflexe modulu runtime pro konstruktor nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="519c1-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="519c1-166">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="519c1-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="519c1-167">Platí pro konkrétní typ, jako je například třídu nebo strukturu zásady reflexe modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="519c1-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="519c1-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="519c1-168">Remarks</span></span>  
 <span data-ttu-id="519c1-169">`<GenericParameter>` Prvek je podřízeným buď [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) nebo [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element a se používá k aplikování zásad na konkrétní obecného typu parametr, který je zadat jeho název v obecný typ nebo metoda podpis.</span><span class="sxs-lookup"><span data-stu-id="519c1-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="519c1-170">`<GenericParameter>` Element je velmi užitečné při použití s serializátorů.</span><span class="sxs-lookup"><span data-stu-id="519c1-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="519c1-171">Následující příklad používá `<GenericParameter>` elementu, který chcete použít pro typ zásady `T` ve voláních serializátor NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="519c1-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="519c1-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="519c1-172">See Also</span></span>  
 [<span data-ttu-id="519c1-173">\<Metoda > elementu</span><span class="sxs-lookup"><span data-stu-id="519c1-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="519c1-174">\<Typ > elementu</span><span class="sxs-lookup"><span data-stu-id="519c1-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="519c1-175">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="519c1-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="519c1-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="519c1-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="519c1-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="519c1-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
