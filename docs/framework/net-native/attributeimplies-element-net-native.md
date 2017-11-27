---
title: Element &lt;AttributeImplies&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec2bc90283aa39b8258ad14777cda7180c043c69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltattributeimpliesgt-element-net-native"></a><span data-ttu-id="44b83-102">Element &lt;AttributeImplies&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="44b83-102">&lt;AttributeImplies&gt; Element (.NET Native)</span></span>
<span data-ttu-id="44b83-103">Definuje zásady pro elementy kódu, který je použit obsahující atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44b83-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44b83-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44b83-105">Attributes and Elements</span></span>  
 <span data-ttu-id="44b83-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44b83-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44b83-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="44b83-107">Attributes</span></span>  
  
|<span data-ttu-id="44b83-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="44b83-108">Attribute</span></span>|<span data-ttu-id="44b83-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="44b83-109">Attribute type</span></span>|<span data-ttu-id="44b83-110">Popis</span><span class="sxs-lookup"><span data-stu-id="44b83-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="44b83-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="44b83-111">Reflection</span></span>|<span data-ttu-id="44b83-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-112">Optional attribute.</span></span> <span data-ttu-id="44b83-113">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="44b83-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="44b83-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="44b83-114">Reflection</span></span>|<span data-ttu-id="44b83-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-115">Optional attribute.</span></span> <span data-ttu-id="44b83-116">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="44b83-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="44b83-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="44b83-117">Reflection</span></span>|<span data-ttu-id="44b83-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-118">Optional attribute.</span></span> <span data-ttu-id="44b83-119">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="44b83-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="44b83-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="44b83-120">Serialization</span></span>|<span data-ttu-id="44b83-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-121">Optional attribute.</span></span> <span data-ttu-id="44b83-122">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="44b83-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="44b83-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="44b83-123">Serialization</span></span>|<span data-ttu-id="44b83-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-124">Optional attribute.</span></span> <span data-ttu-id="44b83-125">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="44b83-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="44b83-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="44b83-126">Serialization</span></span>|<span data-ttu-id="44b83-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-127">Optional attribute.</span></span> <span data-ttu-id="44b83-128">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="44b83-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="44b83-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="44b83-129">Serialization</span></span>|<span data-ttu-id="44b83-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-130">Optional attribute.</span></span> <span data-ttu-id="44b83-131">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="44b83-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="44b83-132">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="44b83-132">Interop</span></span>|<span data-ttu-id="44b83-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-133">Optional attribute.</span></span> <span data-ttu-id="44b83-134">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="44b83-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="44b83-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="44b83-135">Interop</span></span>|<span data-ttu-id="44b83-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-136">Optional attribute.</span></span> <span data-ttu-id="44b83-137">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="44b83-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="44b83-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="44b83-138">Interop</span></span>|<span data-ttu-id="44b83-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44b83-139">Optional attribute.</span></span> <span data-ttu-id="44b83-140">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="44b83-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="44b83-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="44b83-141">All attributes</span></span>  
  
|<span data-ttu-id="44b83-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="44b83-142">Value</span></span>|<span data-ttu-id="44b83-143">Popis</span><span class="sxs-lookup"><span data-stu-id="44b83-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44b83-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="44b83-144">*policy_setting*</span></span>|<span data-ttu-id="44b83-145">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="44b83-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="44b83-146">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="44b83-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="44b83-147">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="44b83-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44b83-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44b83-148">Child Elements</span></span>  
 <span data-ttu-id="44b83-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="44b83-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44b83-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44b83-150">Parent Elements</span></span>  
  
|<span data-ttu-id="44b83-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="44b83-151">Element</span></span>|<span data-ttu-id="44b83-152">Popis</span><span class="sxs-lookup"><span data-stu-id="44b83-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44b83-153">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="44b83-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="44b83-154">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="44b83-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44b83-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44b83-155">Remarks</span></span>  
 <span data-ttu-id="44b83-156">`<AttributeImplies>` Elementu je použita, pokud jeho obsahující typ je atribut (který je třída odvozená z <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="44b83-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="44b83-157">Pokud atribut se použije k prvku určitého programu, zásady definované `<AttributeImplies>` element platí pro daný element programu.</span><span class="sxs-lookup"><span data-stu-id="44b83-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="44b83-158">Reflexe, serializace a atributů spolupráce jsou nepovinné, ale alespoň jeden by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="44b83-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b83-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="44b83-159">See Also</span></span>  
 [<span data-ttu-id="44b83-160">\<Typ > elementu</span><span class="sxs-lookup"><span data-stu-id="44b83-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="44b83-161">Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="44b83-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="44b83-162">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="44b83-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="44b83-163">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="44b83-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
