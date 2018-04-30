---
title: '&lt;Parametr&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa4b2c870864a4359ebca0a1ae47fc1c8aaebca0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="ltparametergt"></a><span data-ttu-id="edcd4-102">&lt;Parametr&gt;</span><span class="sxs-lookup"><span data-stu-id="edcd4-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="edcd4-103">Určuje obecný parametr, pokud deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="edcd4-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="edcd4-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="edcd4-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="edcd4-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="edcd4-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="edcd4-106">\<declaredTypes > elementu</span><span class="sxs-lookup"><span data-stu-id="edcd4-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="edcd4-107">\<Přidat > elementu pro \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="edcd4-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="edcd4-108">\<Třída knownType > elementu</span><span class="sxs-lookup"><span data-stu-id="edcd4-108">\<knownType> Element</span></span>  
<span data-ttu-id="edcd4-109">\<parametr > elementu</span><span class="sxs-lookup"><span data-stu-id="edcd4-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edcd4-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edcd4-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edcd4-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="edcd4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="edcd4-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="edcd4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edcd4-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="edcd4-113">Attributes</span></span>  
  
|<span data-ttu-id="edcd4-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="edcd4-114">Attribute</span></span>|<span data-ttu-id="edcd4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="edcd4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="edcd4-116">index</span><span class="sxs-lookup"><span data-stu-id="edcd4-116">index</span></span>|<span data-ttu-id="edcd4-117">Pokud je deklarovaný typ obecného typu, určuje obecný parametr, který vrátí typ známé.</span><span class="sxs-lookup"><span data-stu-id="edcd4-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="edcd4-118">– typ</span><span class="sxs-lookup"><span data-stu-id="edcd4-118">type</span></span>|<span data-ttu-id="edcd4-119">Řetězec, který popisuje známý typ použitý k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="edcd4-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="edcd4-120">index atribut</span><span class="sxs-lookup"><span data-stu-id="edcd4-120">index Attribute</span></span>  
  
|<span data-ttu-id="edcd4-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="edcd4-121">Value</span></span>|<span data-ttu-id="edcd4-122">Popis</span><span class="sxs-lookup"><span data-stu-id="edcd4-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="edcd4-123">"0"</span><span class="sxs-lookup"><span data-stu-id="edcd4-123">"0"</span></span>|<span data-ttu-id="edcd4-124">První parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="edcd4-124">The first parameter in the generic type.</span></span> <span data-ttu-id="edcd4-125">Například <xref:System.Collections.Generic.List%601> má jenom jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="edcd4-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="edcd4-126">Pokud se používají jako deklarovaný typ indexu by nastavena na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="edcd4-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="edcd4-127">"1"</span><span class="sxs-lookup"><span data-stu-id="edcd4-127">"1"</span></span>|<span data-ttu-id="edcd4-128">Druhý parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="edcd4-128">The second parameter in a generic type.</span></span> <span data-ttu-id="edcd4-129">Například <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="edcd4-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="edcd4-130">Pokud je známý typ vrácené druhý parametr, nastavte atribut index "1".</span><span class="sxs-lookup"><span data-stu-id="edcd4-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edcd4-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="edcd4-131">Child Elements</span></span>  
 <span data-ttu-id="edcd4-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="edcd4-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="edcd4-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="edcd4-133">Parent Elements</span></span>  
  
|<span data-ttu-id="edcd4-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="edcd4-134">Element</span></span>|<span data-ttu-id="edcd4-135">Popis</span><span class="sxs-lookup"><span data-stu-id="edcd4-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edcd4-136">\<Třída knownType ></span><span class="sxs-lookup"><span data-stu-id="edcd4-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="edcd4-137">Určuje známému typu, který může být vrácen pouze pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="edcd4-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edcd4-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edcd4-138">Remarks</span></span>  
 <span data-ttu-id="edcd4-139">Další informace o známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="edcd4-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="edcd4-140">Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="edcd4-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="edcd4-141">Tento element konfigurace nemůže mít oba atributy ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="edcd4-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="edcd4-142">Pokud oba atributy jsou nastavené, <xref:System.Configuration.ConfigurationErrorsException> dojde.</span><span class="sxs-lookup"><span data-stu-id="edcd4-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edcd4-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="edcd4-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="edcd4-144">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="edcd4-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="edcd4-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="edcd4-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="edcd4-146">\<add></span><span class="sxs-lookup"><span data-stu-id="edcd4-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
