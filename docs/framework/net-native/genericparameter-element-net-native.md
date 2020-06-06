---
title: <GenericParameter>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: d0b18211206a8f9d4365ab3affe6d1c376003348
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128424"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="40280-102">\<GenericParameter>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="40280-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="40280-103">Použije zásady na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="40280-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40280-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40280-104">Syntax</span></span>  
  
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
                  MarshalStructure="policy_type" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40280-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40280-105">Attributes and Elements</span></span>  
 <span data-ttu-id="40280-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40280-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40280-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="40280-107">Attributes</span></span>  
  
|<span data-ttu-id="40280-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="40280-108">Attribute</span></span>|<span data-ttu-id="40280-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="40280-109">Attribute type</span></span>|<span data-ttu-id="40280-110">Description</span><span class="sxs-lookup"><span data-stu-id="40280-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="40280-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="40280-111">General</span></span>|<span data-ttu-id="40280-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-112">Required attribute.</span></span> <span data-ttu-id="40280-113">Název obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="40280-113">The name of the generic parameter.</span></span> <span data-ttu-id="40280-114">Například u obecného delegáta <xref:System.Func%603> hodnota `Name` atributu je "TResult", aby se pro návratovou hodnotu delegáta použili zásada modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="40280-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="40280-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="40280-115">Reflection</span></span>|<span data-ttu-id="40280-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-116">Optional attribute.</span></span> <span data-ttu-id="40280-117">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="40280-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="40280-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="40280-118">Reflection</span></span>|<span data-ttu-id="40280-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-119">Optional attribute.</span></span> <span data-ttu-id="40280-120">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="40280-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="40280-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="40280-121">Reflection</span></span>|<span data-ttu-id="40280-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-122">Optional attribute.</span></span> <span data-ttu-id="40280-123">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="40280-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="40280-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="40280-124">Serialization</span></span>|<span data-ttu-id="40280-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-125">Optional attribute.</span></span> <span data-ttu-id="40280-126">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="40280-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="40280-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="40280-127">Serialization</span></span>|<span data-ttu-id="40280-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-128">Optional attribute.</span></span> <span data-ttu-id="40280-129">Řídí zásady pro serializaci, která používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="40280-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="40280-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="40280-130">Serialization</span></span>|<span data-ttu-id="40280-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-131">Optional attribute.</span></span> <span data-ttu-id="40280-132">Řídí zásady pro serializaci JSON, které používají <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="40280-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="40280-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="40280-133">Serialization</span></span>|<span data-ttu-id="40280-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-134">Optional attribute.</span></span> <span data-ttu-id="40280-135">Řídí zásady pro serializaci XML, které používají <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="40280-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="40280-136">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="40280-136">Interop</span></span>|<span data-ttu-id="40280-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-137">Optional attribute.</span></span> <span data-ttu-id="40280-138">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="40280-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="40280-139">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="40280-139">Interop</span></span>|<span data-ttu-id="40280-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-140">Optional attribute.</span></span> <span data-ttu-id="40280-141">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="40280-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="40280-142">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="40280-142">Interop</span></span>|<span data-ttu-id="40280-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-143">Optional attribute.</span></span> <span data-ttu-id="40280-144">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="40280-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="40280-145">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="40280-145">Name attribute</span></span>  
  
|<span data-ttu-id="40280-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="40280-146">Value</span></span>|<span data-ttu-id="40280-147">Description</span><span class="sxs-lookup"><span data-stu-id="40280-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40280-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="40280-148">*generic_parameter_name*</span></span>|<span data-ttu-id="40280-149">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="40280-149">Required attribute.</span></span> <span data-ttu-id="40280-150">Název parametru obecného typu</span><span class="sxs-lookup"><span data-stu-id="40280-150">The name of the generic type parameter.</span></span> <span data-ttu-id="40280-151">Například u obecného delegáta <xref:System.Func%603> *generic_parameter_name* hodnota "TResult" aplikuje zásady modulu runtime na návratovou hodnotu delegáta.</span><span class="sxs-lookup"><span data-stu-id="40280-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="40280-152">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="40280-152">All other attributes</span></span>  
  
|<span data-ttu-id="40280-153">Hodnota</span><span class="sxs-lookup"><span data-stu-id="40280-153">Value</span></span>|<span data-ttu-id="40280-154">Description</span><span class="sxs-lookup"><span data-stu-id="40280-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40280-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="40280-155">*policy_setting*</span></span>|<span data-ttu-id="40280-156">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="40280-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="40280-157">Možné hodnoty jsou `All` , `Public` , `PublicAndInternal` , `Required Public` , a `Required PublicAndInternal` `Required All` .</span><span class="sxs-lookup"><span data-stu-id="40280-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="40280-158">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="40280-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40280-159">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40280-159">Child Elements</span></span>  
 <span data-ttu-id="40280-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="40280-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40280-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40280-161">Parent Elements</span></span>  
  
|<span data-ttu-id="40280-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="40280-162">Element</span></span>|<span data-ttu-id="40280-163">Description</span><span class="sxs-lookup"><span data-stu-id="40280-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="40280-164">Aplikuje zásady reflexe za běhu na konstruktor nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="40280-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="40280-165">Aplikuje zásady odrazu za běhu na konkrétní typ, jako je třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="40280-165">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40280-166">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40280-166">Remarks</span></span>  
 <span data-ttu-id="40280-167">`<GenericParameter>`Prvek je podřízeným prvkem nebo, který [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) se používá k aplikování zásad na konkrétní parametr obecného typu, který je určen jeho názvem v obecném typu nebo podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="40280-167">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="40280-168">`<GenericParameter>`Element je nejužitečnější při použití se serializátory.</span><span class="sxs-lookup"><span data-stu-id="40280-168">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="40280-169">Následující příklad používá `<GenericParameter>` element pro použití zásad na typ `T` v volání metody přetížení [JsonConvert. DeserializeObject \<T> (String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) serializátoru Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="40280-169">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40280-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="40280-170">See also</span></span>

- [<span data-ttu-id="40280-171">\<Method>Objekt</span><span class="sxs-lookup"><span data-stu-id="40280-171">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="40280-172">\<Type>Objekt</span><span class="sxs-lookup"><span data-stu-id="40280-172">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="40280-173">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="40280-173">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="40280-174">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="40280-174">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="40280-175">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="40280-175">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
