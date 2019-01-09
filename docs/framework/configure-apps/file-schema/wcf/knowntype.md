---
title: '&lt;Třída knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 6156f102573333ec0d5533b8f1a8506d91215f47
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151927"
---
# <a name="ltknowntypegt"></a><span data-ttu-id="9aea3-102">&lt;Třída knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="9aea3-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="9aea3-103">Určuje typ používané <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="9aea3-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="9aea3-104">Určuje element "známý typ", který je vrácen pole nebo vlastnost "deklarovaného typu".</span><span class="sxs-lookup"><span data-stu-id="9aea3-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="9aea3-105">Další informace najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="9aea3-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="9aea3-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="9aea3-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="9aea3-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9aea3-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="9aea3-108">\<declaredTypes > – Element</span><span class="sxs-lookup"><span data-stu-id="9aea3-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="9aea3-109">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="9aea3-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="9aea3-110">\<Třída knownType > – Element</span><span class="sxs-lookup"><span data-stu-id="9aea3-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aea3-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aea3-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="9aea3-112">Typ</span><span class="sxs-lookup"><span data-stu-id="9aea3-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9aea3-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9aea3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9aea3-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9aea3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9aea3-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="9aea3-115">Attributes</span></span>  
  
|<span data-ttu-id="9aea3-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="9aea3-116">Attribute</span></span>|<span data-ttu-id="9aea3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9aea3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9aea3-118">– typ</span><span class="sxs-lookup"><span data-stu-id="9aea3-118">type</span></span>|<span data-ttu-id="9aea3-119">Určuje typ (včetně oboru názvů), název sestavení, verzi, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9aea3-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9aea3-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9aea3-120">Child Elements</span></span>  
  
|<span data-ttu-id="9aea3-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="9aea3-121">Element</span></span>|<span data-ttu-id="9aea3-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9aea3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9aea3-123">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="9aea3-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="9aea3-124">Určuje index parametru, je-li deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="9aea3-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9aea3-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9aea3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9aea3-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="9aea3-126">Element</span></span>|<span data-ttu-id="9aea3-127">Popis</span><span class="sxs-lookup"><span data-stu-id="9aea3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9aea3-128">\<add></span><span class="sxs-lookup"><span data-stu-id="9aea3-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="9aea3-129">Přidá do kolekce deklarované typy deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="9aea3-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aea3-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9aea3-130">Remarks</span></span>  
 <span data-ttu-id="9aea3-131">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9aea3-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="9aea3-132">Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="9aea3-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aea3-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="9aea3-133">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="9aea3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="9aea3-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="9aea3-135">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="9aea3-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="9aea3-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9aea3-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="9aea3-137">\<add></span><span class="sxs-lookup"><span data-stu-id="9aea3-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
