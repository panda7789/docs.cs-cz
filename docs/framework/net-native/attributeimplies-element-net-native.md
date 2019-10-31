---
title: <AttributeImplies> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 94f7813938e2179a2355e6ab2eff22479122d4b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128485"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="47c17-102">\<element > AttributeImplies (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="47c17-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="47c17-103">Definuje zásadu pro prvky kódu, na které je obsažený atribut použit.</span><span class="sxs-lookup"><span data-stu-id="47c17-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47c17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47c17-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47c17-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="47c17-105">Attributes and Elements</span></span>  
 <span data-ttu-id="47c17-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="47c17-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47c17-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="47c17-107">Attributes</span></span>  
  
|<span data-ttu-id="47c17-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="47c17-108">Attribute</span></span>|<span data-ttu-id="47c17-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="47c17-109">Attribute type</span></span>|<span data-ttu-id="47c17-110">Popis</span><span class="sxs-lookup"><span data-stu-id="47c17-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="47c17-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="47c17-111">Reflection</span></span>|<span data-ttu-id="47c17-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-112">Optional attribute.</span></span> <span data-ttu-id="47c17-113">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="47c17-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="47c17-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="47c17-114">Reflection</span></span>|<span data-ttu-id="47c17-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-115">Optional attribute.</span></span> <span data-ttu-id="47c17-116">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="47c17-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="47c17-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="47c17-117">Reflection</span></span>|<span data-ttu-id="47c17-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-118">Optional attribute.</span></span> <span data-ttu-id="47c17-119">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="47c17-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="47c17-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="47c17-120">Serialization</span></span>|<span data-ttu-id="47c17-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-121">Optional attribute.</span></span> <span data-ttu-id="47c17-122">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="47c17-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="47c17-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="47c17-123">Serialization</span></span>|<span data-ttu-id="47c17-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-124">Optional attribute.</span></span> <span data-ttu-id="47c17-125">Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47c17-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="47c17-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="47c17-126">Serialization</span></span>|<span data-ttu-id="47c17-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-127">Optional attribute.</span></span> <span data-ttu-id="47c17-128">Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47c17-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="47c17-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="47c17-129">Serialization</span></span>|<span data-ttu-id="47c17-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-130">Optional attribute.</span></span> <span data-ttu-id="47c17-131">Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47c17-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="47c17-132">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="47c17-132">Interop</span></span>|<span data-ttu-id="47c17-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-133">Optional attribute.</span></span> <span data-ttu-id="47c17-134">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="47c17-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="47c17-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="47c17-135">Interop</span></span>|<span data-ttu-id="47c17-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-136">Optional attribute.</span></span> <span data-ttu-id="47c17-137">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="47c17-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="47c17-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="47c17-138">Interop</span></span>|<span data-ttu-id="47c17-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="47c17-139">Optional attribute.</span></span> <span data-ttu-id="47c17-140">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="47c17-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="47c17-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="47c17-141">All attributes</span></span>  
  
|<span data-ttu-id="47c17-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="47c17-142">Value</span></span>|<span data-ttu-id="47c17-143">Popis</span><span class="sxs-lookup"><span data-stu-id="47c17-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47c17-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="47c17-144">*policy_setting*</span></span>|<span data-ttu-id="47c17-145">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="47c17-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="47c17-146">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="47c17-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="47c17-147">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="47c17-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47c17-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="47c17-148">Child Elements</span></span>  
 <span data-ttu-id="47c17-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="47c17-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47c17-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="47c17-150">Parent Elements</span></span>  
  
|<span data-ttu-id="47c17-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="47c17-151">Element</span></span>|<span data-ttu-id="47c17-152">Popis</span><span class="sxs-lookup"><span data-stu-id="47c17-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47c17-153">Typ\<</span><span class="sxs-lookup"><span data-stu-id="47c17-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="47c17-154">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="47c17-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47c17-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47c17-155">Remarks</span></span>  
 <span data-ttu-id="47c17-156">Element `<AttributeImplies>` se používá, pokud je jeho nadřazený typ atribut (to je třída odvozená z <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="47c17-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="47c17-157">Pokud je atribut použit na konkrétní prvek programu, zásada definovaná elementem `<AttributeImplies>` se vztahuje na tento prvek programu.</span><span class="sxs-lookup"><span data-stu-id="47c17-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="47c17-158">Atributy Reflection, Serialization a interoperability jsou všechny volitelné, ale musí být přítomné aspoň jedno.</span><span class="sxs-lookup"><span data-stu-id="47c17-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c17-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47c17-159">See also</span></span>

- [<span data-ttu-id="47c17-160">\<typ > elementu</span><span class="sxs-lookup"><span data-stu-id="47c17-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="47c17-161">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="47c17-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="47c17-162">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="47c17-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="47c17-163">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="47c17-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
