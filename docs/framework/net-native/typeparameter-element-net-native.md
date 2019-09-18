---
title: <TypeParameter>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0de00b9313b60b3a527dd0380ae90d82731a8c02
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049064"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="6d963-102">\<Element > TypeParameter (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6d963-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="6d963-103">Použije zásady na typ reprezentovaný argumentem typu předaným metodě.</span><span class="sxs-lookup"><span data-stu-id="6d963-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d963-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d963-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d963-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d963-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6d963-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d963-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d963-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d963-107">Attributes</span></span>  
  
|<span data-ttu-id="6d963-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="6d963-108">Attribute</span></span>|<span data-ttu-id="6d963-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="6d963-109">Attribute type</span></span>|<span data-ttu-id="6d963-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6d963-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6d963-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="6d963-111">General</span></span>|<span data-ttu-id="6d963-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-112">Required attribute.</span></span> <span data-ttu-id="6d963-113">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="6d963-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="6d963-114">Například pro signaturu `Type.GetInterfaceMap(Type interfaceType)`metody hodnota `Name` atributu je "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="6d963-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="6d963-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6d963-115">Reflection</span></span>|<span data-ttu-id="6d963-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-116">Optional attribute.</span></span> <span data-ttu-id="6d963-117">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="6d963-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6d963-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6d963-118">Reflection</span></span>|<span data-ttu-id="6d963-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-119">Optional attribute.</span></span> <span data-ttu-id="6d963-120">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="6d963-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6d963-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6d963-121">Reflection</span></span>|<span data-ttu-id="6d963-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-122">Optional attribute.</span></span> <span data-ttu-id="6d963-123">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="6d963-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6d963-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="6d963-124">Serialization</span></span>|<span data-ttu-id="6d963-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-125">Optional attribute.</span></span> <span data-ttu-id="6d963-126">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="6d963-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6d963-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="6d963-127">Serialization</span></span>|<span data-ttu-id="6d963-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-128">Optional attribute.</span></span> <span data-ttu-id="6d963-129">Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.</span><span class="sxs-lookup"><span data-stu-id="6d963-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6d963-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="6d963-130">Serialization</span></span>|<span data-ttu-id="6d963-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-131">Optional attribute.</span></span> <span data-ttu-id="6d963-132">Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.</span><span class="sxs-lookup"><span data-stu-id="6d963-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6d963-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="6d963-133">Serialization</span></span>|<span data-ttu-id="6d963-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-134">Optional attribute.</span></span> <span data-ttu-id="6d963-135">Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.</span><span class="sxs-lookup"><span data-stu-id="6d963-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6d963-136">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="6d963-136">Interop</span></span>|<span data-ttu-id="6d963-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-137">Optional attribute.</span></span> <span data-ttu-id="6d963-138">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="6d963-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6d963-139">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="6d963-139">Interop</span></span>|<span data-ttu-id="6d963-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-140">Optional attribute.</span></span> <span data-ttu-id="6d963-141">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6d963-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6d963-142">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="6d963-142">Interop</span></span>|<span data-ttu-id="6d963-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d963-143">Optional attribute.</span></span> <span data-ttu-id="6d963-144">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6d963-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6d963-145">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="6d963-145">Name attribute</span></span>  
  
|<span data-ttu-id="6d963-146">Value</span><span class="sxs-lookup"><span data-stu-id="6d963-146">Value</span></span>|<span data-ttu-id="6d963-147">Popis</span><span class="sxs-lookup"><span data-stu-id="6d963-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d963-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="6d963-148">*parameter_name*</span></span>|<span data-ttu-id="6d963-149">Název parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="6d963-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="6d963-150">Například pro signaturu `Type.GetInterfaceMap(Type interfaceType)`metody hodnota `Name` atributu je "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="6d963-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6d963-151">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="6d963-151">All other attributes</span></span>  
  
|<span data-ttu-id="6d963-152">Value</span><span class="sxs-lookup"><span data-stu-id="6d963-152">Value</span></span>|<span data-ttu-id="6d963-153">Popis</span><span class="sxs-lookup"><span data-stu-id="6d963-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d963-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6d963-154">*policy_setting*</span></span>|<span data-ttu-id="6d963-155">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="6d963-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="6d963-156">Možné hodnoty jsou `All`, `Public` `PublicAndInternal`,,, a`Required PublicAndInternal` .`Required All` `Required Public`</span><span class="sxs-lookup"><span data-stu-id="6d963-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6d963-157">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6d963-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d963-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d963-158">Child Elements</span></span>  
 <span data-ttu-id="6d963-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d963-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d963-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d963-160">Parent Elements</span></span>  
  
|<span data-ttu-id="6d963-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d963-161">Element</span></span>|<span data-ttu-id="6d963-162">Popis</span><span class="sxs-lookup"><span data-stu-id="6d963-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d963-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="6d963-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="6d963-164">Aplikuje zásady reflexe za běhu na konstruktor nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="6d963-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d963-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d963-165">Remarks</span></span>  
 <span data-ttu-id="6d963-166">Element je <xref:System.Type> [ podobný\<parametru >](parameter-element-net-native.md) element, s tím rozdílem, že lze použít pouze pro parametry typu. `<TypeParameter>`</span><span class="sxs-lookup"><span data-stu-id="6d963-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="6d963-167">Použije zásady na jakýkoli typ, který je reprezentován v době běhu podle argumentu typu určeného `Name` atributem.</span><span class="sxs-lookup"><span data-stu-id="6d963-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="6d963-168">Například serializátor Newtonsoft JSON obsahuje statickou `JsonConvert.DeserializeObject(String value, Type type)` metodu.</span><span class="sxs-lookup"><span data-stu-id="6d963-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="6d963-169">Následující direktivy reflexe:</span><span class="sxs-lookup"><span data-stu-id="6d963-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="6d963-170">Určete, že metadata pro typ modulu runtime reprezentovaného `type` argumentem by měla být k dispozici pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="6d963-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="6d963-171">Pokud se tyto direktivy modulu runtime vztahují na projekt, který obsahuje následující zdrojový kód:</span><span class="sxs-lookup"><span data-stu-id="6d963-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="6d963-172">direktivy reflexe zpřístupňují `StockQuote` metadata pro typ pro serializátor Newtonsoft JSON v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6d963-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d963-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d963-173">See also</span></span>

- [<span data-ttu-id="6d963-174">\<Metoda > element</span><span class="sxs-lookup"><span data-stu-id="6d963-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="6d963-175">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6d963-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6d963-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6d963-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="6d963-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6d963-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
