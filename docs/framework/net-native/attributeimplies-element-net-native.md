---
title: <AttributeImplies>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181061"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="9d22c-102">\<AttributeImplies>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="9d22c-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="9d22c-103">Definuje zásadu pro prvky kódu, na které je obsažený atribut použit.</span><span class="sxs-lookup"><span data-stu-id="9d22c-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d22c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d22c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d22c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d22c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9d22c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d22c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d22c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d22c-107">Attributes</span></span>  
  
|<span data-ttu-id="9d22c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d22c-108">Attribute</span></span>|<span data-ttu-id="9d22c-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="9d22c-109">Attribute type</span></span>|<span data-ttu-id="9d22c-110">Description</span><span class="sxs-lookup"><span data-stu-id="9d22c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="9d22c-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="9d22c-111">Reflection</span></span>|<span data-ttu-id="9d22c-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-112">Optional attribute.</span></span> <span data-ttu-id="9d22c-113">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="9d22c-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="9d22c-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="9d22c-114">Reflection</span></span>|<span data-ttu-id="9d22c-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-115">Optional attribute.</span></span> <span data-ttu-id="9d22c-116">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="9d22c-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="9d22c-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="9d22c-117">Reflection</span></span>|<span data-ttu-id="9d22c-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-118">Optional attribute.</span></span> <span data-ttu-id="9d22c-119">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="9d22c-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="9d22c-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="9d22c-120">Serialization</span></span>|<span data-ttu-id="9d22c-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-121">Optional attribute.</span></span> <span data-ttu-id="9d22c-122">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="9d22c-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="9d22c-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="9d22c-123">Serialization</span></span>|<span data-ttu-id="9d22c-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-124">Optional attribute.</span></span> <span data-ttu-id="9d22c-125">Řídí zásady pro serializaci, která používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="9d22c-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="9d22c-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="9d22c-126">Serialization</span></span>|<span data-ttu-id="9d22c-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-127">Optional attribute.</span></span> <span data-ttu-id="9d22c-128">Řídí zásady pro serializaci JSON, které používají <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="9d22c-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="9d22c-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="9d22c-129">Serialization</span></span>|<span data-ttu-id="9d22c-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-130">Optional attribute.</span></span> <span data-ttu-id="9d22c-131">Řídí zásady pro serializaci XML, které používají <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídu.</span><span class="sxs-lookup"><span data-stu-id="9d22c-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="9d22c-132">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="9d22c-132">Interop</span></span>|<span data-ttu-id="9d22c-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-133">Optional attribute.</span></span> <span data-ttu-id="9d22c-134">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="9d22c-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="9d22c-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="9d22c-135">Interop</span></span>|<span data-ttu-id="9d22c-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-136">Optional attribute.</span></span> <span data-ttu-id="9d22c-137">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="9d22c-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="9d22c-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="9d22c-138">Interop</span></span>|<span data-ttu-id="9d22c-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d22c-139">Optional attribute.</span></span> <span data-ttu-id="9d22c-140">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="9d22c-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="9d22c-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="9d22c-141">All attributes</span></span>  
  
|<span data-ttu-id="9d22c-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9d22c-142">Value</span></span>|<span data-ttu-id="9d22c-143">Description</span><span class="sxs-lookup"><span data-stu-id="9d22c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d22c-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="9d22c-144">*policy_setting*</span></span>|<span data-ttu-id="9d22c-145">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="9d22c-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="9d22c-146">Možné hodnoty jsou `All` , `Auto` , `Excluded` , `Public` , `PublicAndInternal` , `Required Public` , a `Required PublicAndInternal` `Required All` .</span><span class="sxs-lookup"><span data-stu-id="9d22c-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="9d22c-147">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9d22c-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d22c-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d22c-148">Child Elements</span></span>  
 <span data-ttu-id="9d22c-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="9d22c-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d22c-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d22c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="9d22c-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d22c-151">Element</span></span>|<span data-ttu-id="9d22c-152">Description</span><span class="sxs-lookup"><span data-stu-id="9d22c-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="9d22c-153">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="9d22c-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d22c-154">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d22c-154">Remarks</span></span>  
 <span data-ttu-id="9d22c-155">`<AttributeImplies>`Element se používá, pokud je jeho nadřazený typ atribut (to znamená třída odvozená z <xref:System.Attribute?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="9d22c-155">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="9d22c-156">Pokud je atribut použit na konkrétní prvek programu, zásada definovaná `<AttributeImplies>` elementem se vztahuje na tento prvek programu.</span><span class="sxs-lookup"><span data-stu-id="9d22c-156">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="9d22c-157">Atributy Reflection, Serialization a interoperability jsou všechny volitelné, ale musí být přítomné aspoň jedno.</span><span class="sxs-lookup"><span data-stu-id="9d22c-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d22c-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d22c-158">See also</span></span>

- [<span data-ttu-id="9d22c-159">\<Type>Objekt</span><span class="sxs-lookup"><span data-stu-id="9d22c-159">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="9d22c-160">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9d22c-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9d22c-161">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9d22c-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9d22c-162">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9d22c-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
