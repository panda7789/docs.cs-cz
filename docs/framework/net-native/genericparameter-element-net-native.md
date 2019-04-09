---
title: <GenericParameter> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40fef845a55412e5731ec08bd1e038d6b311694c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111654"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="bd600-102">\<GenericParameter > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="bd600-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="bd600-103">Použije zásady na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="bd600-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd600-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd600-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd600-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bd600-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bd600-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bd600-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd600-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="bd600-107">Attributes</span></span>  
  
|<span data-ttu-id="bd600-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="bd600-108">Attribute</span></span>|<span data-ttu-id="bd600-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="bd600-109">Attribute type</span></span>|<span data-ttu-id="bd600-110">Popis</span><span class="sxs-lookup"><span data-stu-id="bd600-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="bd600-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="bd600-111">General</span></span>|<span data-ttu-id="bd600-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-112">Required attribute.</span></span> <span data-ttu-id="bd600-113">Název obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="bd600-113">The name of the generic parameter.</span></span> <span data-ttu-id="bd600-114">Například pro obecný delegát <xref:System.Func%603>, hodnota `Name` atribut je "TResult" runtime zásadu chcete uplatnit na návratovou hodnotu tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="bd600-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="bd600-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="bd600-115">Reflection</span></span>|<span data-ttu-id="bd600-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-116">Optional attribute.</span></span> <span data-ttu-id="bd600-117">Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="bd600-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="bd600-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="bd600-118">Reflection</span></span>|<span data-ttu-id="bd600-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-119">Optional attribute.</span></span> <span data-ttu-id="bd600-120">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bd600-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="bd600-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="bd600-121">Reflection</span></span>|<span data-ttu-id="bd600-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-122">Optional attribute.</span></span> <span data-ttu-id="bd600-123">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="bd600-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="bd600-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="bd600-124">Serialization</span></span>|<span data-ttu-id="bd600-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-125">Optional attribute.</span></span> <span data-ttu-id="bd600-126">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="bd600-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="bd600-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="bd600-127">Serialization</span></span>|<span data-ttu-id="bd600-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-128">Optional attribute.</span></span> <span data-ttu-id="bd600-129">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="bd600-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="bd600-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="bd600-130">Serialization</span></span>|<span data-ttu-id="bd600-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-131">Optional attribute.</span></span> <span data-ttu-id="bd600-132">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="bd600-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="bd600-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="bd600-133">Serialization</span></span>|<span data-ttu-id="bd600-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-134">Optional attribute.</span></span> <span data-ttu-id="bd600-135">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="bd600-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="bd600-136">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="bd600-136">Interop</span></span>|<span data-ttu-id="bd600-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-137">Optional attribute.</span></span> <span data-ttu-id="bd600-138">Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.</span><span class="sxs-lookup"><span data-stu-id="bd600-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="bd600-139">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="bd600-139">Interop</span></span>|<span data-ttu-id="bd600-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-140">Optional attribute.</span></span> <span data-ttu-id="bd600-141">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="bd600-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="bd600-142">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="bd600-142">Interop</span></span>|<span data-ttu-id="bd600-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-143">Optional attribute.</span></span> <span data-ttu-id="bd600-144">Určuje zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="bd600-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="bd600-145">Název atributu</span><span class="sxs-lookup"><span data-stu-id="bd600-145">Name attribute</span></span>  
  
|<span data-ttu-id="bd600-146">Value</span><span class="sxs-lookup"><span data-stu-id="bd600-146">Value</span></span>|<span data-ttu-id="bd600-147">Popis</span><span class="sxs-lookup"><span data-stu-id="bd600-147">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="bd600-148">generic_parameter_name</span><span class="sxs-lookup"><span data-stu-id="bd600-148">generic_parameter_name</span></span>*|<span data-ttu-id="bd600-149">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd600-149">Required attribute.</span></span> <span data-ttu-id="bd600-150">Název parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="bd600-150">The name of the generic type parameter.</span></span> <span data-ttu-id="bd600-151">Například pro obecný delegát <xref:System.Func%603>, *generic_parameter_name* hodnotu "TResult" platí zásady modulu runtime pro vrácené hodnoty delegáta.</span><span class="sxs-lookup"><span data-stu-id="bd600-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="bd600-152">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="bd600-152">All other attributes</span></span>  
  
|<span data-ttu-id="bd600-153">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bd600-153">Value</span></span>|<span data-ttu-id="bd600-154">Popis</span><span class="sxs-lookup"><span data-stu-id="bd600-154">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="bd600-155">policy_setting</span><span class="sxs-lookup"><span data-stu-id="bd600-155">policy_setting</span></span>*|<span data-ttu-id="bd600-156">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="bd600-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="bd600-157">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="bd600-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="bd600-158">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="bd600-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd600-159">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bd600-159">Child Elements</span></span>  
 <span data-ttu-id="bd600-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="bd600-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd600-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bd600-161">Parent Elements</span></span>  
  
|<span data-ttu-id="bd600-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="bd600-162">Element</span></span>|<span data-ttu-id="bd600-163">Popis</span><span class="sxs-lookup"><span data-stu-id="bd600-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd600-164">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="bd600-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="bd600-165">Použije zásady reflexe runtime konstruktoru nebo metody.</span><span class="sxs-lookup"><span data-stu-id="bd600-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="bd600-166">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="bd600-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="bd600-167">Použije zásady reflexe runtime určitého typu, jako je například třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="bd600-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd600-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd600-168">Remarks</span></span>  
 <span data-ttu-id="bd600-169">`<GenericParameter>` Element je podřízeným prvkem buď [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) nebo [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu a se používá k aplikování zásad pro konkrétní typ obecný parametr, který je zadat pomocí jejího názvu do obecného typu nebo metodě podpis.</span><span class="sxs-lookup"><span data-stu-id="bd600-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="bd600-170">`<GenericParameter>` Element je nejužitečnější při použití se serializátory.</span><span class="sxs-lookup"><span data-stu-id="bd600-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="bd600-171">V následujícím příkladu `<GenericParameter>` element uplatňovat zásady na typ `T` ve voláních serializátor NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (řetězec)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="bd600-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd600-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd600-172">See also</span></span>

- [<span data-ttu-id="bd600-173">\<Metoda > – Element</span><span class="sxs-lookup"><span data-stu-id="bd600-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="bd600-174">\<Typ > – Element</span><span class="sxs-lookup"><span data-stu-id="bd600-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="bd600-175">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="bd600-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="bd600-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="bd600-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="bd600-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="bd600-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
