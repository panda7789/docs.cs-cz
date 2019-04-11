---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 22ef3c3c6d23d6c68c27d6b5d1ed35b7c9910d48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230795"
---
# <a name="parameter"></a><span data-ttu-id="d4ae0-101">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="d4ae0-101">\<parameter></span></span>
<span data-ttu-id="d4ae0-102">Určuje obecný parametr, je-li deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="d4ae0-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="d4ae0-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="d4ae0-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d4ae0-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="d4ae0-105">\<declaredTypes > – Element</span><span class="sxs-lookup"><span data-stu-id="d4ae0-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="d4ae0-106">\<Přidat > – element pro \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d4ae0-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="d4ae0-107">\<Třída knownType > – Element</span><span class="sxs-lookup"><span data-stu-id="d4ae0-107">\<knownType> Element</span></span>  
<span data-ttu-id="d4ae0-108">\<parametr > – Element</span><span class="sxs-lookup"><span data-stu-id="d4ae0-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ae0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4ae0-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4ae0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4ae0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4ae0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4ae0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4ae0-112">Attributes</span></span>  
  
|<span data-ttu-id="d4ae0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4ae0-113">Attribute</span></span>|<span data-ttu-id="d4ae0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d4ae0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4ae0-115">index</span><span class="sxs-lookup"><span data-stu-id="d4ae0-115">index</span></span>|<span data-ttu-id="d4ae0-116">Když je deklarovaný typ obecného typu, určuje obecný parametr, který vrací známý typ.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="d4ae0-117"> – typ</span><span class="sxs-lookup"><span data-stu-id="d4ae0-117">type</span></span>|<span data-ttu-id="d4ae0-118">Řetězec, který popisuje známý typ používaný k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="d4ae0-119">Atribut indexu</span><span class="sxs-lookup"><span data-stu-id="d4ae0-119">index Attribute</span></span>  
  
|<span data-ttu-id="d4ae0-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d4ae0-120">Value</span></span>|<span data-ttu-id="d4ae0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d4ae0-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4ae0-122">"0"</span><span class="sxs-lookup"><span data-stu-id="d4ae0-122">"0"</span></span>|<span data-ttu-id="d4ae0-123">První parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-123">The first parameter in the generic type.</span></span> <span data-ttu-id="d4ae0-124">Například <xref:System.Collections.Generic.List%601> má pouze jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="d4ae0-125">Pokud se používá jako deklarovaný typ, index se nastavuje na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="d4ae0-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="d4ae0-126">"1"</span><span class="sxs-lookup"><span data-stu-id="d4ae0-126">"1"</span></span>|<span data-ttu-id="d4ae0-127">Druhý parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-127">The second parameter in a generic type.</span></span> <span data-ttu-id="d4ae0-128">Například <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="d4ae0-129">Pokud známý typ není vrácena druhým parametrem, nastavte atribut indexu na hodnotu "1".</span><span class="sxs-lookup"><span data-stu-id="d4ae0-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4ae0-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4ae0-130">Child Elements</span></span>  
 <span data-ttu-id="d4ae0-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4ae0-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4ae0-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4ae0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d4ae0-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4ae0-133">Element</span></span>|<span data-ttu-id="d4ae0-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d4ae0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4ae0-135">\<knownType></span><span class="sxs-lookup"><span data-stu-id="d4ae0-135">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="d4ae0-136">Určuje známý typ, který může být vrácen pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4ae0-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4ae0-137">Remarks</span></span>  
 <span data-ttu-id="d4ae0-138">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-138">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d4ae0-139">Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-139">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="d4ae0-140">Tento prvek konfigurace nemůže mít oba atributy ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="d4ae0-141">Pokud jsou oba atributy nastavené, <xref:System.Configuration.ConfigurationErrorsException> vyvolá.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ae0-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4ae0-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="d4ae0-143">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="d4ae0-143">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="d4ae0-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d4ae0-144">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="d4ae0-145">\<add></span><span class="sxs-lookup"><span data-stu-id="d4ae0-145">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
