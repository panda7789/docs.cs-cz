---
title: '&lt;Parametr&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdbb47fcb65273d03d226e13730849170d4345c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltparametergt"></a><span data-ttu-id="d4de8-102">&lt;Parametr&gt;</span><span class="sxs-lookup"><span data-stu-id="d4de8-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="d4de8-103">Určuje obecný parametr, pokud deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4de8-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="d4de8-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="d4de8-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="d4de8-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="d4de8-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="d4de8-106">\<declaredTypes > elementu</span><span class="sxs-lookup"><span data-stu-id="d4de8-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="d4de8-107">\<Přidat > elementu pro \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d4de8-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="d4de8-108">\<Třída knownType > elementu</span><span class="sxs-lookup"><span data-stu-id="d4de8-108">\<knownType> Element</span></span>  
<span data-ttu-id="d4de8-109">\<parametr > elementu</span><span class="sxs-lookup"><span data-stu-id="d4de8-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4de8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4de8-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4de8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4de8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d4de8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4de8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4de8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4de8-113">Attributes</span></span>  
  
|<span data-ttu-id="d4de8-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4de8-114">Attribute</span></span>|<span data-ttu-id="d4de8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d4de8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4de8-116">index</span><span class="sxs-lookup"><span data-stu-id="d4de8-116">index</span></span>|<span data-ttu-id="d4de8-117">Pokud je deklarovaný typ obecného typu, určuje obecný parametr, který vrátí typ známé.</span><span class="sxs-lookup"><span data-stu-id="d4de8-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="d4de8-118">– typ</span><span class="sxs-lookup"><span data-stu-id="d4de8-118">type</span></span>|<span data-ttu-id="d4de8-119">Řetězec, který popisuje známý typ použitý k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="d4de8-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="d4de8-120">index atribut</span><span class="sxs-lookup"><span data-stu-id="d4de8-120">index Attribute</span></span>  
  
|<span data-ttu-id="d4de8-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d4de8-121">Value</span></span>|<span data-ttu-id="d4de8-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d4de8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4de8-123">"0"</span><span class="sxs-lookup"><span data-stu-id="d4de8-123">"0"</span></span>|<span data-ttu-id="d4de8-124">První parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4de8-124">The first parameter in the generic type.</span></span> <span data-ttu-id="d4de8-125">Například <xref:System.Collections.Generic.List%601> má jenom jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="d4de8-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="d4de8-126">Pokud se používají jako deklarovaný typ indexu by nastavena na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="d4de8-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="d4de8-127">"1"</span><span class="sxs-lookup"><span data-stu-id="d4de8-127">"1"</span></span>|<span data-ttu-id="d4de8-128">Druhý parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4de8-128">The second parameter in a generic type.</span></span> <span data-ttu-id="d4de8-129">Například <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="d4de8-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="d4de8-130">Pokud je známý typ vrácené druhý parametr, nastavte atribut index "1".</span><span class="sxs-lookup"><span data-stu-id="d4de8-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4de8-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4de8-131">Child Elements</span></span>  
 <span data-ttu-id="d4de8-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4de8-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4de8-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4de8-133">Parent Elements</span></span>  
  
|<span data-ttu-id="d4de8-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4de8-134">Element</span></span>|<span data-ttu-id="d4de8-135">Popis</span><span class="sxs-lookup"><span data-stu-id="d4de8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4de8-136">\<Třída knownType ></span><span class="sxs-lookup"><span data-stu-id="d4de8-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="d4de8-137">Určuje známému typu, který může být vrácen pouze pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="d4de8-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4de8-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4de8-138">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="d4de8-139">známé typy, najdete v části [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d4de8-139"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d4de8-140">Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="d4de8-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="d4de8-141">Tento element konfigurace nemůže mít oba atributy ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="d4de8-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="d4de8-142">Pokud oba atributy jsou nastavené, <xref:System.Configuration.ConfigurationErrorsException> dojde.</span><span class="sxs-lookup"><span data-stu-id="d4de8-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4de8-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4de8-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="d4de8-144">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="d4de8-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="d4de8-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="d4de8-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="d4de8-146">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="d4de8-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
