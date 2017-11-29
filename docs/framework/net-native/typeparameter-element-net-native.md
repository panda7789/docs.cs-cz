---
title: Element &lt;TypeParameter&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94c7b2fe5cf586c0f8a58d1698cdf3870b5b5c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttypeparametergt-element-net-native"></a><span data-ttu-id="cb1d1-102">Element &lt;TypeParameter&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="cb1d1-102">&lt;TypeParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="cb1d1-103">Zásady se vztahuje na typ zastoupený typ argument předaný metodu.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb1d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb1d1-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb1d1-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cb1d1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cb1d1-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb1d1-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="cb1d1-107">Attributes</span></span>  
  
|<span data-ttu-id="cb1d1-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="cb1d1-108">Attribute</span></span>|<span data-ttu-id="cb1d1-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="cb1d1-109">Attribute type</span></span>|<span data-ttu-id="cb1d1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="cb1d1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="cb1d1-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="cb1d1-111">General</span></span>|<span data-ttu-id="cb1d1-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-112">Required attribute.</span></span> <span data-ttu-id="cb1d1-113">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="cb1d1-114">Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="cb1d1-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="cb1d1-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="cb1d1-115">Reflection</span></span>|<span data-ttu-id="cb1d1-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-116">Optional attribute.</span></span> <span data-ttu-id="cb1d1-117">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="cb1d1-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="cb1d1-118">Reflection</span></span>|<span data-ttu-id="cb1d1-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-119">Optional attribute.</span></span> <span data-ttu-id="cb1d1-120">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="cb1d1-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="cb1d1-121">Reflection</span></span>|<span data-ttu-id="cb1d1-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-122">Optional attribute.</span></span> <span data-ttu-id="cb1d1-123">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="cb1d1-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="cb1d1-124">Serialization</span></span>|<span data-ttu-id="cb1d1-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-125">Optional attribute.</span></span> <span data-ttu-id="cb1d1-126">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="cb1d1-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="cb1d1-127">Serialization</span></span>|<span data-ttu-id="cb1d1-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-128">Optional attribute.</span></span> <span data-ttu-id="cb1d1-129">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="cb1d1-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="cb1d1-130">Serialization</span></span>|<span data-ttu-id="cb1d1-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-131">Optional attribute.</span></span> <span data-ttu-id="cb1d1-132">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="cb1d1-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="cb1d1-133">Serialization</span></span>|<span data-ttu-id="cb1d1-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-134">Optional attribute.</span></span> <span data-ttu-id="cb1d1-135">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="cb1d1-136">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="cb1d1-136">Interop</span></span>|<span data-ttu-id="cb1d1-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-137">Optional attribute.</span></span> <span data-ttu-id="cb1d1-138">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="cb1d1-139">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="cb1d1-139">Interop</span></span>|<span data-ttu-id="cb1d1-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-140">Optional attribute.</span></span> <span data-ttu-id="cb1d1-141">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="cb1d1-142">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="cb1d1-142">Interop</span></span>|<span data-ttu-id="cb1d1-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-143">Optional attribute.</span></span> <span data-ttu-id="cb1d1-144">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="cb1d1-145">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-145">Name attribute</span></span>  
  
|<span data-ttu-id="cb1d1-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cb1d1-146">Value</span></span>|<span data-ttu-id="cb1d1-147">Popis</span><span class="sxs-lookup"><span data-stu-id="cb1d1-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb1d1-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="cb1d1-148">*parameter_name*</span></span>|<span data-ttu-id="cb1d1-149">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="cb1d1-150">Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="cb1d1-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="cb1d1-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="cb1d1-151">All other attributes</span></span>  
  
|<span data-ttu-id="cb1d1-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cb1d1-152">Value</span></span>|<span data-ttu-id="cb1d1-153">Popis</span><span class="sxs-lookup"><span data-stu-id="cb1d1-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb1d1-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="cb1d1-154">*policy_setting*</span></span>|<span data-ttu-id="cb1d1-155">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="cb1d1-156">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="cb1d1-157">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="cb1d1-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb1d1-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cb1d1-158">Child Elements</span></span>  
 <span data-ttu-id="cb1d1-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="cb1d1-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb1d1-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cb1d1-160">Parent Elements</span></span>  
  
|<span data-ttu-id="cb1d1-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="cb1d1-161">Element</span></span>|<span data-ttu-id="cb1d1-162">Popis</span><span class="sxs-lookup"><span data-stu-id="cb1d1-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb1d1-163">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="cb1d1-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="cb1d1-164">Platí zásady reflexe modulu runtime pro konstruktor nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb1d1-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb1d1-165">Remarks</span></span>  
 <span data-ttu-id="cb1d1-166">`<TypeParameter>` Element je podobná [ \<parametr >](../../../docs/framework/net-native/parameter-element-net-native.md) elementu, s výjimkou toho, které lze použít pouze pro parametry typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="cb1d1-167">Platí zásady pro jakýkoli typ je reprezentována v době běhu argument typu určeného `Name` atribut.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="cb1d1-168">Například serializátor NewtonSoft JSON obsahuje statický `JsonConvert.DeserializeObject(String value, Type type)` metoda.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="cb1d1-169">Následující direktivy reflexe:</span><span class="sxs-lookup"><span data-stu-id="cb1d1-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="cb1d1-170">určit, aby metadata pro typ modulu runtime reprezentována `type` argument má být k dispozici pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="cb1d1-171">Pokud tyto direktivy modulu runtime platí pro projekt, který zahrnuje následující zdrojový kód:</span><span class="sxs-lookup"><span data-stu-id="cb1d1-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="cb1d1-172">direktivy reflexe zkontrolujte metadata `StockQuote` typu, které jsou k dispozici pro serializátor NewtonSoft JSON za běhu.</span><span class="sxs-lookup"><span data-stu-id="cb1d1-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb1d1-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb1d1-173">See Also</span></span>  
 [<span data-ttu-id="cb1d1-174">\<Metoda > elementu</span><span class="sxs-lookup"><span data-stu-id="cb1d1-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="cb1d1-175">Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="cb1d1-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="cb1d1-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="cb1d1-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="cb1d1-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="cb1d1-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
