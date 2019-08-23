---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932838"
---
# <a name="parameter"></a><span data-ttu-id="ac668-101">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="ac668-101">\<parameter></span></span>
<span data-ttu-id="ac668-102">Určuje obecný parametr, je-li deklarovaný typ obecný typ.</span><span class="sxs-lookup"><span data-stu-id="ac668-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="ac668-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="ac668-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="ac668-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="ac668-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="ac668-105">\<declaredTypes – element ></span><span class="sxs-lookup"><span data-stu-id="ac668-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="ac668-106">\<Přidat > element pro \<> declaredTypes</span><span class="sxs-lookup"><span data-stu-id="ac668-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="ac668-107">\<Třída KnownType – element ></span><span class="sxs-lookup"><span data-stu-id="ac668-107">\<knownType> Element</span></span>  
<span data-ttu-id="ac668-108">\<parametr > element</span><span class="sxs-lookup"><span data-stu-id="ac668-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac668-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac668-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac668-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ac668-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ac668-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ac668-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac668-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ac668-112">Attributes</span></span>  
  
|<span data-ttu-id="ac668-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ac668-113">Attribute</span></span>|<span data-ttu-id="ac668-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ac668-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac668-115">index</span><span class="sxs-lookup"><span data-stu-id="ac668-115">index</span></span>|<span data-ttu-id="ac668-116">Když deklarovaný typ je obecný typ, určuje obecný parametr, který vrátí známý typ.</span><span class="sxs-lookup"><span data-stu-id="ac668-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="ac668-117">– typ</span><span class="sxs-lookup"><span data-stu-id="ac668-117">type</span></span>|<span data-ttu-id="ac668-118">Řetězec, který popisuje známý typ používaný pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ac668-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="ac668-119">index – atribut</span><span class="sxs-lookup"><span data-stu-id="ac668-119">index Attribute</span></span>  
  
|<span data-ttu-id="ac668-120">Value</span><span class="sxs-lookup"><span data-stu-id="ac668-120">Value</span></span>|<span data-ttu-id="ac668-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ac668-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac668-122">"0"</span><span class="sxs-lookup"><span data-stu-id="ac668-122">"0"</span></span>|<span data-ttu-id="ac668-123">První parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="ac668-123">The first parameter in the generic type.</span></span> <span data-ttu-id="ac668-124">Například <xref:System.Collections.Generic.List%601> má pouze jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="ac668-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="ac668-125">Pokud je použit jako deklarovaný typ, index by byl nastaven na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="ac668-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="ac668-126">"1"</span><span class="sxs-lookup"><span data-stu-id="ac668-126">"1"</span></span>|<span data-ttu-id="ac668-127">Druhý parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="ac668-127">The second parameter in a generic type.</span></span> <span data-ttu-id="ac668-128">Například a <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="ac668-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="ac668-129">Pokud je známý typ vrácen druhým parametrem, nastavte atribut index na hodnotu "1".</span><span class="sxs-lookup"><span data-stu-id="ac668-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac668-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ac668-130">Child Elements</span></span>  
 <span data-ttu-id="ac668-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="ac668-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac668-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ac668-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ac668-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="ac668-133">Element</span></span>|<span data-ttu-id="ac668-134">Popis</span><span class="sxs-lookup"><span data-stu-id="ac668-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac668-135">\<knownType></span><span class="sxs-lookup"><span data-stu-id="ac668-135">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="ac668-136">Určuje známý typ, který může být vrácen polem nebo vlastností deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="ac668-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac668-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac668-137">Remarks</span></span>  
 <span data-ttu-id="ac668-138">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ac668-138">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="ac668-139">Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ac668-139">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="ac668-140">Tento prvek konfigurace nemůže obsahovat oba atributy současně.</span><span class="sxs-lookup"><span data-stu-id="ac668-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="ac668-141">Pokud jsou nastaveny oba atributy, <xref:System.Configuration.ConfigurationErrorsException> dojde k.</span><span class="sxs-lookup"><span data-stu-id="ac668-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac668-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac668-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="ac668-143">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="ac668-143">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="ac668-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="ac668-144">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="ac668-145">\<add></span><span class="sxs-lookup"><span data-stu-id="ac668-145">\<add></span></span>](add-of-declaredtypes-element.md)
