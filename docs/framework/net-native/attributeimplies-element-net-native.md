---
title: <AttributeImplies> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d59f1f48be19a21ccc7ee5bb73cebfffc387fec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165058"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="b7e92-102">\<AttributeImplies > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b7e92-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="b7e92-103">Definuje zásady pro prvky kódu, nadřazený atribut se používá k.</span><span class="sxs-lookup"><span data-stu-id="b7e92-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7e92-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7e92-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b7e92-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b7e92-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b7e92-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7e92-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b7e92-107">Attributes</span></span>  
  
|<span data-ttu-id="b7e92-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b7e92-108">Attribute</span></span>|<span data-ttu-id="b7e92-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="b7e92-109">Attribute type</span></span>|<span data-ttu-id="b7e92-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b7e92-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="b7e92-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="b7e92-111">Reflection</span></span>|<span data-ttu-id="b7e92-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-112">Optional attribute.</span></span> <span data-ttu-id="b7e92-113">Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="b7e92-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="b7e92-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="b7e92-114">Reflection</span></span>|<span data-ttu-id="b7e92-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-115">Optional attribute.</span></span> <span data-ttu-id="b7e92-116">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b7e92-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="b7e92-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="b7e92-117">Reflection</span></span>|<span data-ttu-id="b7e92-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-118">Optional attribute.</span></span> <span data-ttu-id="b7e92-119">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="b7e92-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="b7e92-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="b7e92-120">Serialization</span></span>|<span data-ttu-id="b7e92-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-121">Optional attribute.</span></span> <span data-ttu-id="b7e92-122">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="b7e92-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="b7e92-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="b7e92-123">Serialization</span></span>|<span data-ttu-id="b7e92-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-124">Optional attribute.</span></span> <span data-ttu-id="b7e92-125">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="b7e92-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="b7e92-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="b7e92-126">Serialization</span></span>|<span data-ttu-id="b7e92-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-127">Optional attribute.</span></span> <span data-ttu-id="b7e92-128">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="b7e92-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="b7e92-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="b7e92-129">Serialization</span></span>|<span data-ttu-id="b7e92-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-130">Optional attribute.</span></span> <span data-ttu-id="b7e92-131">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="b7e92-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="b7e92-132">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="b7e92-132">Interop</span></span>|<span data-ttu-id="b7e92-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-133">Optional attribute.</span></span> <span data-ttu-id="b7e92-134">Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b7e92-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="b7e92-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="b7e92-135">Interop</span></span>|<span data-ttu-id="b7e92-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-136">Optional attribute.</span></span> <span data-ttu-id="b7e92-137">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b7e92-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="b7e92-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="b7e92-138">Interop</span></span>|<span data-ttu-id="b7e92-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7e92-139">Optional attribute.</span></span> <span data-ttu-id="b7e92-140">Určuje zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b7e92-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="b7e92-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="b7e92-141">All attributes</span></span>  
  
|<span data-ttu-id="b7e92-142">Value</span><span class="sxs-lookup"><span data-stu-id="b7e92-142">Value</span></span>|<span data-ttu-id="b7e92-143">Popis</span><span class="sxs-lookup"><span data-stu-id="b7e92-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b7e92-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b7e92-144">*policy_setting*</span></span>|<span data-ttu-id="b7e92-145">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="b7e92-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="b7e92-146">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="b7e92-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b7e92-147">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b7e92-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7e92-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b7e92-148">Child Elements</span></span>  
 <span data-ttu-id="b7e92-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="b7e92-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7e92-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b7e92-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b7e92-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7e92-151">Element</span></span>|<span data-ttu-id="b7e92-152">Popis</span><span class="sxs-lookup"><span data-stu-id="b7e92-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7e92-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="b7e92-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="b7e92-154">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="b7e92-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7e92-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7e92-155">Remarks</span></span>  
 <span data-ttu-id="b7e92-156">`<AttributeImplies>` Elementu je použita, pokud jeho nadřazený typ je atribut (to znamená, že třída odvozená z <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="b7e92-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="b7e92-157">Pokud je atribut použit na konkrétní aplikaci prvku, zásady definované `<AttributeImplies>` element platí pro tento prvek programu.</span><span class="sxs-lookup"><span data-stu-id="b7e92-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="b7e92-158">Reflexe, serializace a atributů spolupráce jsou nepovinné, ale alespoň jeden by měl být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b7e92-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e92-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7e92-159">See also</span></span>

- [<span data-ttu-id="b7e92-160">\<Typ > – Element</span><span class="sxs-lookup"><span data-stu-id="b7e92-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="b7e92-161">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="b7e92-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b7e92-162">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="b7e92-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="b7e92-163">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="b7e92-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
