---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400115"
---
# <a name="parameter"></a><span data-ttu-id="74d07-101">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="74d07-101">\<parameter></span></span>
<span data-ttu-id="74d07-102">Určuje obecný parametr, je-li deklarovaný typ obecný typ.</span><span class="sxs-lookup"><span data-stu-id="74d07-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
<span data-ttu-id="74d07-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="74d07-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="74d07-104">&nbsp;&nbsp;[ **\<System. Runtime. Serialization – >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="74d07-104">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="74d07-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="74d07-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="74d07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="74d07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="74d07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Přidat >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="74d07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="74d07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Třída KnownType >** ](knowntype.md)</span><span class="sxs-lookup"><span data-stu-id="74d07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)</span></span>\
<span data-ttu-id="74d07-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> parametru**</span><span class="sxs-lookup"><span data-stu-id="74d07-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d07-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74d07-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74d07-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74d07-111">Attributes and Elements</span></span>  
 <span data-ttu-id="74d07-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74d07-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74d07-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="74d07-113">Attributes</span></span>  
  
|<span data-ttu-id="74d07-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="74d07-114">Attribute</span></span>|<span data-ttu-id="74d07-115">Popis</span><span class="sxs-lookup"><span data-stu-id="74d07-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74d07-116">index</span><span class="sxs-lookup"><span data-stu-id="74d07-116">index</span></span>|<span data-ttu-id="74d07-117">Když deklarovaný typ je obecný typ, určuje obecný parametr, který vrátí známý typ.</span><span class="sxs-lookup"><span data-stu-id="74d07-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="74d07-118">– typ</span><span class="sxs-lookup"><span data-stu-id="74d07-118">type</span></span>|<span data-ttu-id="74d07-119">Řetězec, který popisuje známý typ používaný pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="74d07-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="74d07-120">index – atribut</span><span class="sxs-lookup"><span data-stu-id="74d07-120">index Attribute</span></span>  
  
|<span data-ttu-id="74d07-121">Value</span><span class="sxs-lookup"><span data-stu-id="74d07-121">Value</span></span>|<span data-ttu-id="74d07-122">Popis</span><span class="sxs-lookup"><span data-stu-id="74d07-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="74d07-123">"0"</span><span class="sxs-lookup"><span data-stu-id="74d07-123">"0"</span></span>|<span data-ttu-id="74d07-124">První parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="74d07-124">The first parameter in the generic type.</span></span> <span data-ttu-id="74d07-125">Například <xref:System.Collections.Generic.List%601> má pouze jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="74d07-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="74d07-126">Pokud je použit jako deklarovaný typ, index by byl nastaven na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="74d07-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="74d07-127">"1"</span><span class="sxs-lookup"><span data-stu-id="74d07-127">"1"</span></span>|<span data-ttu-id="74d07-128">Druhý parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="74d07-128">The second parameter in a generic type.</span></span> <span data-ttu-id="74d07-129">Například a <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="74d07-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="74d07-130">Pokud je známý typ vrácen druhým parametrem, nastavte atribut index na hodnotu "1".</span><span class="sxs-lookup"><span data-stu-id="74d07-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74d07-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74d07-131">Child Elements</span></span>  
 <span data-ttu-id="74d07-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="74d07-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74d07-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74d07-133">Parent Elements</span></span>  
  
|<span data-ttu-id="74d07-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="74d07-134">Element</span></span>|<span data-ttu-id="74d07-135">Popis</span><span class="sxs-lookup"><span data-stu-id="74d07-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74d07-136">\<knownType></span><span class="sxs-lookup"><span data-stu-id="74d07-136">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="74d07-137">Určuje známý typ, který může být vrácen polem nebo vlastností deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="74d07-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74d07-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74d07-138">Remarks</span></span>  
 <span data-ttu-id="74d07-139">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="74d07-139">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="74d07-140">Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="74d07-140">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="74d07-141">Tento prvek konfigurace nemůže obsahovat oba atributy současně.</span><span class="sxs-lookup"><span data-stu-id="74d07-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="74d07-142">Pokud jsou nastaveny oba atributy, <xref:System.Configuration.ConfigurationErrorsException> dojde k.</span><span class="sxs-lookup"><span data-stu-id="74d07-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d07-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74d07-143">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="74d07-144">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="74d07-144">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="74d07-145">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="74d07-145">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="74d07-146">\<add></span><span class="sxs-lookup"><span data-stu-id="74d07-146">\<add></span></span>](add-of-declaredtypes-element.md)
