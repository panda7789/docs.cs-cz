---
title: <AttributeImplies>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181061"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="72031-102">\<AttributeImplikuje> element (nativní.NET)</span><span class="sxs-lookup"><span data-stu-id="72031-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="72031-103">Definuje zásadu pro prvky kódu, na které je použit obsažený atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72031-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72031-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72031-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72031-105">Attributes and Elements</span></span>  
 <span data-ttu-id="72031-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72031-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72031-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="72031-107">Attributes</span></span>  
  
|<span data-ttu-id="72031-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="72031-108">Attribute</span></span>|<span data-ttu-id="72031-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="72031-109">Attribute type</span></span>|<span data-ttu-id="72031-110">Popis</span><span class="sxs-lookup"><span data-stu-id="72031-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="72031-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="72031-111">Reflection</span></span>|<span data-ttu-id="72031-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-112">Optional attribute.</span></span> <span data-ttu-id="72031-113">Řídí přístup za běhu k konstruktorům, aby bylo možné aktivovat instance.</span><span class="sxs-lookup"><span data-stu-id="72031-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="72031-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="72031-114">Reflection</span></span>|<span data-ttu-id="72031-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-115">Optional attribute.</span></span> <span data-ttu-id="72031-116">Řídí dotazování na informace o prvcích programu, ale neumožňuje žádný přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="72031-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="72031-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="72031-117">Reflection</span></span>|<span data-ttu-id="72031-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-118">Optional attribute.</span></span> <span data-ttu-id="72031-119">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, aby bylo možné povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="72031-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="72031-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="72031-120">Serialization</span></span>|<span data-ttu-id="72031-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-121">Optional attribute.</span></span> <span data-ttu-id="72031-122">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby instance typu mohly být serializovány a deserializovány knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="72031-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="72031-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="72031-123">Serialization</span></span>|<span data-ttu-id="72031-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-124">Optional attribute.</span></span> <span data-ttu-id="72031-125">Řídí zásady serializace, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> která používá třídu.</span><span class="sxs-lookup"><span data-stu-id="72031-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="72031-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="72031-126">Serialization</span></span>|<span data-ttu-id="72031-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-127">Optional attribute.</span></span> <span data-ttu-id="72031-128">Řídí zásady pro serializaci JSON, který používá třídu. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="72031-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="72031-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="72031-129">Serialization</span></span>|<span data-ttu-id="72031-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-130">Optional attribute.</span></span> <span data-ttu-id="72031-131">Řídí zásady serializace XML, která používá třídu. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="72031-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="72031-132">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="72031-132">Interop</span></span>|<span data-ttu-id="72031-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-133">Optional attribute.</span></span> <span data-ttu-id="72031-134">Řídí zásady pro zařazování typů odkazů na prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="72031-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="72031-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="72031-135">Interop</span></span>|<span data-ttu-id="72031-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-136">Optional attribute.</span></span> <span data-ttu-id="72031-137">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="72031-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="72031-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="72031-138">Interop</span></span>|<span data-ttu-id="72031-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="72031-139">Optional attribute.</span></span> <span data-ttu-id="72031-140">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="72031-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="72031-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="72031-141">All attributes</span></span>  
  
|<span data-ttu-id="72031-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="72031-142">Value</span></span>|<span data-ttu-id="72031-143">Popis</span><span class="sxs-lookup"><span data-stu-id="72031-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72031-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="72031-144">*policy_setting*</span></span>|<span data-ttu-id="72031-145">Nastavení, které se má použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="72031-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="72031-146">Možné hodnoty `All` `Auto`jsou `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , a .</span><span class="sxs-lookup"><span data-stu-id="72031-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="72031-147">Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="72031-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72031-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72031-148">Child Elements</span></span>  
 <span data-ttu-id="72031-149">Žádné.</span><span class="sxs-lookup"><span data-stu-id="72031-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72031-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72031-150">Parent Elements</span></span>  
  
|<span data-ttu-id="72031-151">Element</span><span class="sxs-lookup"><span data-stu-id="72031-151">Element</span></span>|<span data-ttu-id="72031-152">Popis</span><span class="sxs-lookup"><span data-stu-id="72031-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72031-153">\<Typ></span><span class="sxs-lookup"><span data-stu-id="72031-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="72031-154">Použije zásady reflexe na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="72031-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72031-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72031-155">Remarks</span></span>  
 <span data-ttu-id="72031-156">Prvek `<AttributeImplies>` se používá, pokud jeho obsahující typ je atribut (to <xref:System.Attribute?displayProperty=nameWithType>znamená, že třída odvozená od ).</span><span class="sxs-lookup"><span data-stu-id="72031-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="72031-157">Pokud je atribut použit pro určitý prvek programu, `<AttributeImplies>` zásada definovaná tímto prvkem se vztahuje na tento prvek programu.</span><span class="sxs-lookup"><span data-stu-id="72031-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="72031-158">Reflexe, serializace a interop atributy jsou volitelné, i když alespoň jeden by měl být přítomen.</span><span class="sxs-lookup"><span data-stu-id="72031-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72031-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="72031-159">See also</span></span>

- [<span data-ttu-id="72031-160">\<Typ> element</span><span class="sxs-lookup"><span data-stu-id="72031-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="72031-161">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="72031-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="72031-162">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="72031-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="72031-163">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="72031-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
