---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400115"
---
# \<parameter>
<span data-ttu-id="8046c-101">Určuje obecný parametr, je-li deklarovaný typ obecný typ.</span><span class="sxs-lookup"><span data-stu-id="8046c-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="8046c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8046c-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8046c-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8046c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8046c-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8046c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8046c-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="8046c-105">Attributes</span></span>  
  
|<span data-ttu-id="8046c-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="8046c-106">Attribute</span></span>|<span data-ttu-id="8046c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8046c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8046c-108">index</span><span class="sxs-lookup"><span data-stu-id="8046c-108">index</span></span>|<span data-ttu-id="8046c-109">Když deklarovaný typ je obecný typ, určuje obecný parametr, který vrátí známý typ.</span><span class="sxs-lookup"><span data-stu-id="8046c-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="8046c-110">typ</span><span class="sxs-lookup"><span data-stu-id="8046c-110">type</span></span>|<span data-ttu-id="8046c-111">Řetězec, který popisuje známý typ používaný pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="8046c-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="8046c-112">index – atribut</span><span class="sxs-lookup"><span data-stu-id="8046c-112">index Attribute</span></span>  
  
|<span data-ttu-id="8046c-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8046c-113">Value</span></span>|<span data-ttu-id="8046c-114">Description</span><span class="sxs-lookup"><span data-stu-id="8046c-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8046c-115">"0"</span><span class="sxs-lookup"><span data-stu-id="8046c-115">"0"</span></span>|<span data-ttu-id="8046c-116">První parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="8046c-116">The first parameter in the generic type.</span></span> <span data-ttu-id="8046c-117">Například <xref:System.Collections.Generic.List%601> má pouze jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="8046c-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="8046c-118">Pokud je použit jako deklarovaný typ, index by byl nastaven na hodnotu "0".</span><span class="sxs-lookup"><span data-stu-id="8046c-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="8046c-119">1</span><span class="sxs-lookup"><span data-stu-id="8046c-119">"1"</span></span>|<span data-ttu-id="8046c-120">Druhý parametr v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="8046c-120">The second parameter in a generic type.</span></span> <span data-ttu-id="8046c-121">Například a <xref:System.Collections.Generic.Dictionary%602> má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="8046c-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="8046c-122">Pokud je známý typ vrácen druhým parametrem, nastavte atribut index na hodnotu "1".</span><span class="sxs-lookup"><span data-stu-id="8046c-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8046c-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8046c-123">Child Elements</span></span>  
 <span data-ttu-id="8046c-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="8046c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8046c-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8046c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8046c-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="8046c-126">Element</span></span>|<span data-ttu-id="8046c-127">Description</span><span class="sxs-lookup"><span data-stu-id="8046c-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="8046c-128">Určuje známý typ, který může být vrácen polem nebo vlastností deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="8046c-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8046c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8046c-129">Remarks</span></span>  
 <span data-ttu-id="8046c-130">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8046c-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="8046c-131">[\<dataContractSerializer>](datacontractserializer-element.md)Příklad použití tohoto prvku naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="8046c-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="8046c-132">Tento prvek konfigurace nemůže obsahovat oba atributy současně.</span><span class="sxs-lookup"><span data-stu-id="8046c-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="8046c-133">Pokud jsou nastaveny oba atributy, <xref:System.Configuration.ConfigurationErrorsException> dojde k.</span><span class="sxs-lookup"><span data-stu-id="8046c-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8046c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="8046c-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="8046c-135">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="8046c-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
