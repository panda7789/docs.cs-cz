---
title: <TypeParameter> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b478f963156a2c8f189bbbdbc027927df8974dc2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263560"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="45e1d-102">\<TypeParameter > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="45e1d-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="45e1d-103">Použije zásady na typ zastoupený argument typu předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="45e1d-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45e1d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45e1d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="45e1d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="45e1d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="45e1d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45e1d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="45e1d-107">Attributes</span></span>  
  
|<span data-ttu-id="45e1d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="45e1d-108">Attribute</span></span>|<span data-ttu-id="45e1d-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="45e1d-109">Attribute type</span></span>|<span data-ttu-id="45e1d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="45e1d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="45e1d-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="45e1d-111">General</span></span>|<span data-ttu-id="45e1d-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-112">Required attribute.</span></span> <span data-ttu-id="45e1d-113">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="45e1d-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="45e1d-114">Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="45e1d-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="45e1d-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="45e1d-115">Reflection</span></span>|<span data-ttu-id="45e1d-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-116">Optional attribute.</span></span> <span data-ttu-id="45e1d-117">Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="45e1d-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="45e1d-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="45e1d-118">Reflection</span></span>|<span data-ttu-id="45e1d-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-119">Optional attribute.</span></span> <span data-ttu-id="45e1d-120">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="45e1d-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="45e1d-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="45e1d-121">Reflection</span></span>|<span data-ttu-id="45e1d-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-122">Optional attribute.</span></span> <span data-ttu-id="45e1d-123">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="45e1d-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="45e1d-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="45e1d-124">Serialization</span></span>|<span data-ttu-id="45e1d-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-125">Optional attribute.</span></span> <span data-ttu-id="45e1d-126">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="45e1d-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="45e1d-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="45e1d-127">Serialization</span></span>|<span data-ttu-id="45e1d-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-128">Optional attribute.</span></span> <span data-ttu-id="45e1d-129">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="45e1d-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="45e1d-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="45e1d-130">Serialization</span></span>|<span data-ttu-id="45e1d-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-131">Optional attribute.</span></span> <span data-ttu-id="45e1d-132">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="45e1d-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="45e1d-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="45e1d-133">Serialization</span></span>|<span data-ttu-id="45e1d-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-134">Optional attribute.</span></span> <span data-ttu-id="45e1d-135">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="45e1d-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="45e1d-136">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="45e1d-136">Interop</span></span>|<span data-ttu-id="45e1d-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-137">Optional attribute.</span></span> <span data-ttu-id="45e1d-138">Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.</span><span class="sxs-lookup"><span data-stu-id="45e1d-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="45e1d-139">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="45e1d-139">Interop</span></span>|<span data-ttu-id="45e1d-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-140">Optional attribute.</span></span> <span data-ttu-id="45e1d-141">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="45e1d-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="45e1d-142">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="45e1d-142">Interop</span></span>|<span data-ttu-id="45e1d-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-143">Optional attribute.</span></span> <span data-ttu-id="45e1d-144">Určuje zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="45e1d-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="45e1d-145">Název atributu</span><span class="sxs-lookup"><span data-stu-id="45e1d-145">Name attribute</span></span>  
  
|<span data-ttu-id="45e1d-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="45e1d-146">Value</span></span>|<span data-ttu-id="45e1d-147">Popis</span><span class="sxs-lookup"><span data-stu-id="45e1d-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45e1d-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="45e1d-148">*parameter_name*</span></span>|<span data-ttu-id="45e1d-149">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="45e1d-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="45e1d-150">Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="45e1d-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="45e1d-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="45e1d-151">All other attributes</span></span>  
  
|<span data-ttu-id="45e1d-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="45e1d-152">Value</span></span>|<span data-ttu-id="45e1d-153">Popis</span><span class="sxs-lookup"><span data-stu-id="45e1d-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45e1d-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="45e1d-154">*policy_setting*</span></span>|<span data-ttu-id="45e1d-155">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="45e1d-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="45e1d-156">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="45e1d-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="45e1d-157">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="45e1d-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45e1d-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="45e1d-158">Child Elements</span></span>  
 <span data-ttu-id="45e1d-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="45e1d-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45e1d-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="45e1d-160">Parent Elements</span></span>  
  
|<span data-ttu-id="45e1d-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="45e1d-161">Element</span></span>|<span data-ttu-id="45e1d-162">Popis</span><span class="sxs-lookup"><span data-stu-id="45e1d-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45e1d-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="45e1d-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="45e1d-164">Použije zásady reflexe runtime konstruktoru nebo metody.</span><span class="sxs-lookup"><span data-stu-id="45e1d-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45e1d-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45e1d-165">Remarks</span></span>  
 <span data-ttu-id="45e1d-166">`<TypeParameter>` Element je podobný [ \<parametr >](../../../docs/framework/net-native/parameter-element-net-native.md) elementu, s tím rozdílem, že lze použít pouze u parametrů typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="45e1d-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="45e1d-167">Platí zásady pro jakýkoli typ v době běhu reprezentována argument typu určeného `Name` atribut.</span><span class="sxs-lookup"><span data-stu-id="45e1d-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="45e1d-168">Serializátor NewtonSoft JSON patří třeba statickou `JsonConvert.DeserializeObject(String value, Type type)` metody.</span><span class="sxs-lookup"><span data-stu-id="45e1d-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="45e1d-169">Následující direktivy reflection:</span><span class="sxs-lookup"><span data-stu-id="45e1d-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="45e1d-170">Zadejte těchto metadat pro typ runtime reprezentována `type` argument by měl být k dispozici pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="45e1d-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="45e1d-171">Pokud tyto direktivy modulu runtime platí pro projekt, který obsahuje následující zdrojový kód:</span><span class="sxs-lookup"><span data-stu-id="45e1d-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="45e1d-172">direktivy reflection usnadňují metadat `StockQuote` typu, které jsou k dispozici pro serializátor NewtonSoft JSON v době běhu.</span><span class="sxs-lookup"><span data-stu-id="45e1d-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e1d-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45e1d-173">See also</span></span>
- [<span data-ttu-id="45e1d-174">\<Metoda > – Element</span><span class="sxs-lookup"><span data-stu-id="45e1d-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="45e1d-175">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="45e1d-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="45e1d-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="45e1d-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="45e1d-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="45e1d-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
