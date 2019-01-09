---
title: '&lt;Parametr&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 82a2f5c46c698508695fe5f13f67059860a50713
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148289"
---
# <a name="ltparametergt"></a><span data-ttu-id="5f0d3-102">&lt;Parametr&gt;</span><span class="sxs-lookup"><span data-stu-id="5f0d3-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="5f0d3-103">Určuje obecný parametr, je-li deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="5f0d3-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="5f0d3-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="5f0d3-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5f0d3-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="5f0d3-106">\<declaredTypes > – Element</span><span class="sxs-lookup"><span data-stu-id="5f0d3-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="5f0d3-107">\<Přidat > – element pro \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="5f0d3-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="5f0d3-108">\<Třída knownType > – Element</span><span class="sxs-lookup"><span data-stu-id="5f0d3-108">\<knownType> Element</span></span>  
<span data-ttu-id="5f0d3-109">\<parametr > – Element</span><span class="sxs-lookup"><span data-stu-id="5f0d3-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0d3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f0d3-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f0d3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5f0d3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5f0d3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f0d3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5f0d3-113">Attributes</span></span>  
  
|<span data-ttu-id="5f0d3-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="5f0d3-114">Attribute</span></span>|<span data-ttu-id="5f0d3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5f0d3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f0d3-116">index</span><span class="sxs-lookup"><span data-stu-id="5f0d3-116">index</span></span>|<span data-ttu-id="5f0d3-117">Když je deklarovaný typ obecného typu, určuje obecný parametr, který vrací známý typ.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="5f0d3-118">– typ</span><span class="sxs-lookup"><span data-stu-id="5f0d3-118">type</span></span>|<span data-ttu-id="5f0d3-119">Řetězec, který popisuje známý typ používaný k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="5f0d3-120">Atribut indexu</span><span class="sxs-lookup"><span data-stu-id="5f0d3-120">index Attribute</span></span>  
  
|<span data-ttu-id="5f0d3-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f0d3-121">Value</span></span>|<span data-ttu-id="5f0d3-122">Popis</span><span class="sxs-lookup"><span data-stu-id="5f0d3-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f0d3-123">"0"</span><span class="sxs-lookup"><span data-stu-id="5f0d3-123">"0"</span></span>|<span data-ttu-id="5f0d3-124">První parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-124">The first parameter in the generic type.</span></span> <span data-ttu-id="5f0d3-125">Například <xref:System.Collections.Generic.List%601> má pouze jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="5f0d3-126">Pokud se používá jako deklarovaný typ, index se nastavuje na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="5f0d3-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="5f0d3-127">"1"</span><span class="sxs-lookup"><span data-stu-id="5f0d3-127">"1"</span></span>|<span data-ttu-id="5f0d3-128">Druhý parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-128">The second parameter in a generic type.</span></span> <span data-ttu-id="5f0d3-129">Například <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="5f0d3-130">Pokud známý typ není vrácena druhým parametrem, nastavte atribut indexu na hodnotu "1".</span><span class="sxs-lookup"><span data-stu-id="5f0d3-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f0d3-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5f0d3-131">Child Elements</span></span>  
 <span data-ttu-id="5f0d3-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="5f0d3-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f0d3-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5f0d3-133">Parent Elements</span></span>  
  
|<span data-ttu-id="5f0d3-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="5f0d3-134">Element</span></span>|<span data-ttu-id="5f0d3-135">Popis</span><span class="sxs-lookup"><span data-stu-id="5f0d3-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f0d3-136">\<Třída knownType ></span><span class="sxs-lookup"><span data-stu-id="5f0d3-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="5f0d3-137">Určuje známý typ, který může být vrácen pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f0d3-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f0d3-138">Remarks</span></span>  
 <span data-ttu-id="5f0d3-139">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5f0d3-140">Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="5f0d3-141">Tento prvek konfigurace nemůže mít oba atributy ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="5f0d3-142">Pokud jsou oba atributy nastavené, <xref:System.Configuration.ConfigurationErrorsException> vyvolá.</span><span class="sxs-lookup"><span data-stu-id="5f0d3-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0d3-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f0d3-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="5f0d3-144">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5f0d3-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="5f0d3-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5f0d3-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="5f0d3-146">\<add></span><span class="sxs-lookup"><span data-stu-id="5f0d3-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
