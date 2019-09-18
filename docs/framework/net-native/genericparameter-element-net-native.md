---
title: <GenericParameter>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2898d804f7a351045b2fbce42042f9fd322ebb0a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049749"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="7f077-102">\<Element > GenericParameter (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7f077-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="7f077-103">Použije zásady na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="7f077-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f077-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f077-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f077-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f077-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7f077-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f077-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f077-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f077-107">Attributes</span></span>  
  
|<span data-ttu-id="7f077-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f077-108">Attribute</span></span>|<span data-ttu-id="7f077-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="7f077-109">Attribute type</span></span>|<span data-ttu-id="7f077-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7f077-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="7f077-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="7f077-111">General</span></span>|<span data-ttu-id="7f077-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-112">Required attribute.</span></span> <span data-ttu-id="7f077-113">Název obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="7f077-113">The name of the generic parameter.</span></span> <span data-ttu-id="7f077-114">Například u obecného delegáta <xref:System.Func%603>hodnota `Name` atributu je "TResult", aby se pro návratovou hodnotu delegáta použili zásada modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7f077-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="7f077-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7f077-115">Reflection</span></span>|<span data-ttu-id="7f077-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-116">Optional attribute.</span></span> <span data-ttu-id="7f077-117">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="7f077-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="7f077-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7f077-118">Reflection</span></span>|<span data-ttu-id="7f077-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-119">Optional attribute.</span></span> <span data-ttu-id="7f077-120">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="7f077-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="7f077-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7f077-121">Reflection</span></span>|<span data-ttu-id="7f077-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-122">Optional attribute.</span></span> <span data-ttu-id="7f077-123">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="7f077-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="7f077-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f077-124">Serialization</span></span>|<span data-ttu-id="7f077-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-125">Optional attribute.</span></span> <span data-ttu-id="7f077-126">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="7f077-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="7f077-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f077-127">Serialization</span></span>|<span data-ttu-id="7f077-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-128">Optional attribute.</span></span> <span data-ttu-id="7f077-129">Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.</span><span class="sxs-lookup"><span data-stu-id="7f077-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="7f077-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f077-130">Serialization</span></span>|<span data-ttu-id="7f077-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-131">Optional attribute.</span></span> <span data-ttu-id="7f077-132">Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.</span><span class="sxs-lookup"><span data-stu-id="7f077-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="7f077-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f077-133">Serialization</span></span>|<span data-ttu-id="7f077-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-134">Optional attribute.</span></span> <span data-ttu-id="7f077-135">Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.</span><span class="sxs-lookup"><span data-stu-id="7f077-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="7f077-136">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="7f077-136">Interop</span></span>|<span data-ttu-id="7f077-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-137">Optional attribute.</span></span> <span data-ttu-id="7f077-138">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="7f077-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="7f077-139">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="7f077-139">Interop</span></span>|<span data-ttu-id="7f077-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-140">Optional attribute.</span></span> <span data-ttu-id="7f077-141">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7f077-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="7f077-142">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="7f077-142">Interop</span></span>|<span data-ttu-id="7f077-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-143">Optional attribute.</span></span> <span data-ttu-id="7f077-144">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7f077-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="7f077-145">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="7f077-145">Name attribute</span></span>  
  
|<span data-ttu-id="7f077-146">Value</span><span class="sxs-lookup"><span data-stu-id="7f077-146">Value</span></span>|<span data-ttu-id="7f077-147">Popis</span><span class="sxs-lookup"><span data-stu-id="7f077-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f077-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="7f077-148">*generic_parameter_name*</span></span>|<span data-ttu-id="7f077-149">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f077-149">Required attribute.</span></span> <span data-ttu-id="7f077-150">Název parametru obecného typu</span><span class="sxs-lookup"><span data-stu-id="7f077-150">The name of the generic type parameter.</span></span> <span data-ttu-id="7f077-151">Například u obecného delegáta <xref:System.Func%603>hodnota *generic_parameter_name* "TResult" aplikuje zásadu modulu runtime na návratovou hodnotu delegáta.</span><span class="sxs-lookup"><span data-stu-id="7f077-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="7f077-152">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="7f077-152">All other attributes</span></span>  
  
|<span data-ttu-id="7f077-153">Value</span><span class="sxs-lookup"><span data-stu-id="7f077-153">Value</span></span>|<span data-ttu-id="7f077-154">Popis</span><span class="sxs-lookup"><span data-stu-id="7f077-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f077-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7f077-155">*policy_setting*</span></span>|<span data-ttu-id="7f077-156">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="7f077-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="7f077-157">Možné hodnoty jsou `All`, `Public` `PublicAndInternal`,,, a`Required PublicAndInternal` .`Required All` `Required Public`</span><span class="sxs-lookup"><span data-stu-id="7f077-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="7f077-158">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7f077-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f077-159">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f077-159">Child Elements</span></span>  
 <span data-ttu-id="7f077-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f077-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f077-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f077-161">Parent Elements</span></span>  
  
|<span data-ttu-id="7f077-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f077-162">Element</span></span>|<span data-ttu-id="7f077-163">Popis</span><span class="sxs-lookup"><span data-stu-id="7f077-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f077-164">\<Method></span><span class="sxs-lookup"><span data-stu-id="7f077-164">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="7f077-165">Aplikuje zásady reflexe za běhu na konstruktor nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="7f077-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="7f077-166">\<Zadejte ></span><span class="sxs-lookup"><span data-stu-id="7f077-166">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="7f077-167">Aplikuje zásady odrazu za běhu na konkrétní typ, jako je třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="7f077-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f077-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f077-168">Remarks</span></span>  
 <span data-ttu-id="7f077-169">Element je podřízeným [ \<objektem metody >](method-element-net-native.md) nebo [ \<typu >](type-element-net-native.md) elementu a používá se pro aplikování zásad na konkrétní parametr obecného typu, který je určen jeho názvem v obecném typu nebo metodě. `<GenericParameter>` označení.</span><span class="sxs-lookup"><span data-stu-id="7f077-169">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="7f077-170">`<GenericParameter>` Element je nejužitečnější při použití se serializátory.</span><span class="sxs-lookup"><span data-stu-id="7f077-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="7f077-171">Následující příklad používá `<GenericParameter>` element pro použití zásad na typ `T` v voláních metody [JsonConvert. DeserializeObject\<> T](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) serializátoru Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="7f077-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f077-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f077-172">See also</span></span>

- [<span data-ttu-id="7f077-173">\<Metoda > element</span><span class="sxs-lookup"><span data-stu-id="7f077-173">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="7f077-174">\<Typ > element</span><span class="sxs-lookup"><span data-stu-id="7f077-174">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="7f077-175">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7f077-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7f077-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7f077-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="7f077-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7f077-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
