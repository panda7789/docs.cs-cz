---
title: Element &lt;AttributeImplies&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 960ee5716b9760ab82628a8d21728cd6675e5215
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395437"
---
# <a name="ltattributeimpliesgt-element-net-native"></a><span data-ttu-id="0c9ba-102">Element &lt;AttributeImplies&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0c9ba-102">&lt;AttributeImplies&gt; Element (.NET Native)</span></span>
<span data-ttu-id="0c9ba-103">Definuje zásady pro elementy kódu, který je použit obsahující atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c9ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c9ba-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c9ba-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0c9ba-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0c9ba-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c9ba-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0c9ba-107">Attributes</span></span>  
  
|<span data-ttu-id="0c9ba-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0c9ba-108">Attribute</span></span>|<span data-ttu-id="0c9ba-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="0c9ba-109">Attribute type</span></span>|<span data-ttu-id="0c9ba-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0c9ba-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="0c9ba-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0c9ba-111">Reflection</span></span>|<span data-ttu-id="0c9ba-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-112">Optional attribute.</span></span> <span data-ttu-id="0c9ba-113">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="0c9ba-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0c9ba-114">Reflection</span></span>|<span data-ttu-id="0c9ba-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-115">Optional attribute.</span></span> <span data-ttu-id="0c9ba-116">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="0c9ba-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0c9ba-117">Reflection</span></span>|<span data-ttu-id="0c9ba-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-118">Optional attribute.</span></span> <span data-ttu-id="0c9ba-119">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="0c9ba-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="0c9ba-120">Serialization</span></span>|<span data-ttu-id="0c9ba-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-121">Optional attribute.</span></span> <span data-ttu-id="0c9ba-122">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="0c9ba-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="0c9ba-123">Serialization</span></span>|<span data-ttu-id="0c9ba-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-124">Optional attribute.</span></span> <span data-ttu-id="0c9ba-125">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="0c9ba-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="0c9ba-126">Serialization</span></span>|<span data-ttu-id="0c9ba-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-127">Optional attribute.</span></span> <span data-ttu-id="0c9ba-128">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="0c9ba-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="0c9ba-129">Serialization</span></span>|<span data-ttu-id="0c9ba-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-130">Optional attribute.</span></span> <span data-ttu-id="0c9ba-131">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="0c9ba-132">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="0c9ba-132">Interop</span></span>|<span data-ttu-id="0c9ba-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-133">Optional attribute.</span></span> <span data-ttu-id="0c9ba-134">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="0c9ba-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="0c9ba-135">Interop</span></span>|<span data-ttu-id="0c9ba-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-136">Optional attribute.</span></span> <span data-ttu-id="0c9ba-137">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="0c9ba-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="0c9ba-138">Interop</span></span>|<span data-ttu-id="0c9ba-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-139">Optional attribute.</span></span> <span data-ttu-id="0c9ba-140">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="0c9ba-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="0c9ba-141">All attributes</span></span>  
  
|<span data-ttu-id="0c9ba-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0c9ba-142">Value</span></span>|<span data-ttu-id="0c9ba-143">Popis</span><span class="sxs-lookup"><span data-stu-id="0c9ba-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c9ba-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0c9ba-144">*policy_setting*</span></span>|<span data-ttu-id="0c9ba-145">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="0c9ba-146">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="0c9ba-147">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0c9ba-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c9ba-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0c9ba-148">Child Elements</span></span>  
 <span data-ttu-id="0c9ba-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="0c9ba-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c9ba-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0c9ba-150">Parent Elements</span></span>  
  
|<span data-ttu-id="0c9ba-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="0c9ba-151">Element</span></span>|<span data-ttu-id="0c9ba-152">Popis</span><span class="sxs-lookup"><span data-stu-id="0c9ba-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c9ba-153">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="0c9ba-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="0c9ba-154">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c9ba-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c9ba-155">Remarks</span></span>  
 <span data-ttu-id="0c9ba-156">`<AttributeImplies>` Elementu je použita, pokud jeho obsahující typ je atribut (který je třída odvozená z <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="0c9ba-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="0c9ba-157">Pokud atribut se použije k prvku určitého programu, zásady definované `<AttributeImplies>` element platí pro daný element programu.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="0c9ba-158">Reflexe, serializace a atributů spolupráce jsou nepovinné, ale alespoň jeden by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="0c9ba-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c9ba-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c9ba-159">See Also</span></span>  
 [<span data-ttu-id="0c9ba-160">\<Typ > elementu</span><span class="sxs-lookup"><span data-stu-id="0c9ba-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="0c9ba-161">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0c9ba-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="0c9ba-162">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0c9ba-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="0c9ba-163">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0c9ba-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
