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
ms.workload: dotnet
ms.openlocfilehash: ee88d7692abb1f640b6e50d845691adf8938f841
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttypeparametergt-element-net-native"></a><span data-ttu-id="f3f4c-102">Element &lt;TypeParameter&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="f3f4c-102">&lt;TypeParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="f3f4c-103">Zásady se vztahuje na typ zastoupený typ argument předaný metodu.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3f4c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3f4c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3f4c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f3f4c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3f4c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3f4c-107">Attributes</span></span>  
  
|<span data-ttu-id="f3f4c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3f4c-108">Attribute</span></span>|<span data-ttu-id="f3f4c-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="f3f4c-109">Attribute type</span></span>|<span data-ttu-id="f3f4c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f3f4c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="f3f4c-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="f3f4c-111">General</span></span>|<span data-ttu-id="f3f4c-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-112">Required attribute.</span></span> <span data-ttu-id="f3f4c-113">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="f3f4c-114">Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="f3f4c-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="f3f4c-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="f3f4c-115">Reflection</span></span>|<span data-ttu-id="f3f4c-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-116">Optional attribute.</span></span> <span data-ttu-id="f3f4c-117">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="f3f4c-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="f3f4c-118">Reflection</span></span>|<span data-ttu-id="f3f4c-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-119">Optional attribute.</span></span> <span data-ttu-id="f3f4c-120">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="f3f4c-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="f3f4c-121">Reflection</span></span>|<span data-ttu-id="f3f4c-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-122">Optional attribute.</span></span> <span data-ttu-id="f3f4c-123">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="f3f4c-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="f3f4c-124">Serialization</span></span>|<span data-ttu-id="f3f4c-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-125">Optional attribute.</span></span> <span data-ttu-id="f3f4c-126">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="f3f4c-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="f3f4c-127">Serialization</span></span>|<span data-ttu-id="f3f4c-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-128">Optional attribute.</span></span> <span data-ttu-id="f3f4c-129">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="f3f4c-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="f3f4c-130">Serialization</span></span>|<span data-ttu-id="f3f4c-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-131">Optional attribute.</span></span> <span data-ttu-id="f3f4c-132">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="f3f4c-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="f3f4c-133">Serialization</span></span>|<span data-ttu-id="f3f4c-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-134">Optional attribute.</span></span> <span data-ttu-id="f3f4c-135">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="f3f4c-136">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="f3f4c-136">Interop</span></span>|<span data-ttu-id="f3f4c-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-137">Optional attribute.</span></span> <span data-ttu-id="f3f4c-138">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="f3f4c-139">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="f3f4c-139">Interop</span></span>|<span data-ttu-id="f3f4c-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-140">Optional attribute.</span></span> <span data-ttu-id="f3f4c-141">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="f3f4c-142">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="f3f4c-142">Interop</span></span>|<span data-ttu-id="f3f4c-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-143">Optional attribute.</span></span> <span data-ttu-id="f3f4c-144">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="f3f4c-145">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-145">Name attribute</span></span>  
  
|<span data-ttu-id="f3f4c-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3f4c-146">Value</span></span>|<span data-ttu-id="f3f4c-147">Popis</span><span class="sxs-lookup"><span data-stu-id="f3f4c-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3f4c-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="f3f4c-148">*parameter_name*</span></span>|<span data-ttu-id="f3f4c-149">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="f3f4c-150">Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="f3f4c-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="f3f4c-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="f3f4c-151">All other attributes</span></span>  
  
|<span data-ttu-id="f3f4c-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3f4c-152">Value</span></span>|<span data-ttu-id="f3f4c-153">Popis</span><span class="sxs-lookup"><span data-stu-id="f3f4c-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3f4c-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="f3f4c-154">*policy_setting*</span></span>|<span data-ttu-id="f3f4c-155">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="f3f4c-156">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="f3f4c-157">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f3f4c-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3f4c-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3f4c-158">Child Elements</span></span>  
 <span data-ttu-id="f3f4c-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3f4c-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3f4c-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3f4c-160">Parent Elements</span></span>  
  
|<span data-ttu-id="f3f4c-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3f4c-161">Element</span></span>|<span data-ttu-id="f3f4c-162">Popis</span><span class="sxs-lookup"><span data-stu-id="f3f4c-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3f4c-163">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="f3f4c-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="f3f4c-164">Platí zásady reflexe modulu runtime pro konstruktor nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3f4c-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3f4c-165">Remarks</span></span>  
 <span data-ttu-id="f3f4c-166">`<TypeParameter>` Element je podobná [ \<parametr >](../../../docs/framework/net-native/parameter-element-net-native.md) elementu, s výjimkou toho, které lze použít pouze pro parametry typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="f3f4c-167">Platí zásady pro jakýkoli typ je reprezentována v době běhu argument typu určeného `Name` atribut.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="f3f4c-168">Například serializátor NewtonSoft JSON obsahuje statický `JsonConvert.DeserializeObject(String value, Type type)` metoda.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="f3f4c-169">Následující direktivy reflexe:</span><span class="sxs-lookup"><span data-stu-id="f3f4c-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="f3f4c-170">určit, aby metadata pro typ modulu runtime reprezentována `type` argument má být k dispozici pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="f3f4c-171">Pokud tyto direktivy modulu runtime platí pro projekt, který zahrnuje následující zdrojový kód:</span><span class="sxs-lookup"><span data-stu-id="f3f4c-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="f3f4c-172">direktivy reflexe zkontrolujte metadata `StockQuote` typu, které jsou k dispozici pro serializátor NewtonSoft JSON za běhu.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f4c-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3f4c-173">See Also</span></span>  
 [<span data-ttu-id="f3f4c-174">\<Metoda > elementu</span><span class="sxs-lookup"><span data-stu-id="f3f4c-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="f3f4c-175">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="f3f4c-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="f3f4c-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f3f4c-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="f3f4c-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f3f4c-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
