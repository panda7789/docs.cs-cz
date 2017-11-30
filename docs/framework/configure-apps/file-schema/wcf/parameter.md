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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9db1921e2a6ee1ae2780f744c45fdb25efbf797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltparametergt"></a><span data-ttu-id="1fd7a-102">&lt;Parametr&gt;</span><span class="sxs-lookup"><span data-stu-id="1fd7a-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="1fd7a-103">Určuje obecný parametr, pokud deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="1fd7a-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="1fd7a-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="1fd7a-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1fd7a-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="1fd7a-106">\<declaredTypes > elementu</span><span class="sxs-lookup"><span data-stu-id="1fd7a-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="1fd7a-107">\<Přidat > elementu pro \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="1fd7a-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="1fd7a-108">\<Třída knownType > elementu</span><span class="sxs-lookup"><span data-stu-id="1fd7a-108">\<knownType> Element</span></span>  
<span data-ttu-id="1fd7a-109">\<parametr > elementu</span><span class="sxs-lookup"><span data-stu-id="1fd7a-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fd7a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fd7a-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fd7a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1fd7a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1fd7a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fd7a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1fd7a-113">Attributes</span></span>  
  
|<span data-ttu-id="1fd7a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1fd7a-114">Attribute</span></span>|<span data-ttu-id="1fd7a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1fd7a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1fd7a-116">index</span><span class="sxs-lookup"><span data-stu-id="1fd7a-116">index</span></span>|<span data-ttu-id="1fd7a-117">Pokud je deklarovaný typ obecného typu, určuje obecný parametr, který vrátí typ známé.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="1fd7a-118">– typ</span><span class="sxs-lookup"><span data-stu-id="1fd7a-118">type</span></span>|<span data-ttu-id="1fd7a-119">Řetězec, který popisuje známý typ použitý k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="1fd7a-120">index atribut</span><span class="sxs-lookup"><span data-stu-id="1fd7a-120">index Attribute</span></span>  
  
|<span data-ttu-id="1fd7a-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fd7a-121">Value</span></span>|<span data-ttu-id="1fd7a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="1fd7a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1fd7a-123">"0"</span><span class="sxs-lookup"><span data-stu-id="1fd7a-123">"0"</span></span>|<span data-ttu-id="1fd7a-124">První parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-124">The first parameter in the generic type.</span></span> <span data-ttu-id="1fd7a-125">Například <xref:System.Collections.Generic.List%601> má jenom jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="1fd7a-126">Pokud se používají jako deklarovaný typ indexu by nastavena na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="1fd7a-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="1fd7a-127">"1"</span><span class="sxs-lookup"><span data-stu-id="1fd7a-127">"1"</span></span>|<span data-ttu-id="1fd7a-128">Druhý parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-128">The second parameter in a generic type.</span></span> <span data-ttu-id="1fd7a-129">Například <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="1fd7a-130">Pokud je známý typ vrácené druhý parametr, nastavte atribut index "1".</span><span class="sxs-lookup"><span data-stu-id="1fd7a-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fd7a-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1fd7a-131">Child Elements</span></span>  
 <span data-ttu-id="1fd7a-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="1fd7a-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fd7a-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1fd7a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1fd7a-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fd7a-134">Element</span></span>|<span data-ttu-id="1fd7a-135">Popis</span><span class="sxs-lookup"><span data-stu-id="1fd7a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fd7a-136">\<Třída knownType ></span><span class="sxs-lookup"><span data-stu-id="1fd7a-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="1fd7a-137">Určuje známému typu, který může být vrácen pouze pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fd7a-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fd7a-138">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="1fd7a-139">známé typy, najdete v části [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-139"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="1fd7a-140">Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="1fd7a-141">Tento element konfigurace nemůže mít oba atributy ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="1fd7a-142">Pokud oba atributy jsou nastavené, <xref:System.Configuration.ConfigurationErrorsException> dojde.</span><span class="sxs-lookup"><span data-stu-id="1fd7a-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fd7a-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fd7a-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="1fd7a-144">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="1fd7a-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="1fd7a-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1fd7a-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="1fd7a-146">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="1fd7a-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
