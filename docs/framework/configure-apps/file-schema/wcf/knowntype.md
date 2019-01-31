---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 1224a410d030669e340bd328c9158c85cdfeaeee
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266452"
---
# <a name="knowntype"></a><span data-ttu-id="e9d29-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="e9d29-101">\<knownType></span></span>
<span data-ttu-id="e9d29-102">Určuje typ používané <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="e9d29-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="e9d29-103">Určuje element "známý typ", který je vrácen pole nebo vlastnost "deklarovaného typu".</span><span class="sxs-lookup"><span data-stu-id="e9d29-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="e9d29-104">Další informace najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="e9d29-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="e9d29-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="e9d29-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="e9d29-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e9d29-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="e9d29-107">\<declaredTypes > – Element</span><span class="sxs-lookup"><span data-stu-id="e9d29-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="e9d29-108">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="e9d29-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="e9d29-109">\<Třída knownType > – Element</span><span class="sxs-lookup"><span data-stu-id="e9d29-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9d29-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9d29-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="e9d29-111">Typ</span><span class="sxs-lookup"><span data-stu-id="e9d29-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9d29-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9d29-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e9d29-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9d29-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9d29-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9d29-114">Attributes</span></span>  
  
|<span data-ttu-id="e9d29-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="e9d29-115">Attribute</span></span>|<span data-ttu-id="e9d29-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e9d29-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9d29-117">– typ</span><span class="sxs-lookup"><span data-stu-id="e9d29-117">type</span></span>|<span data-ttu-id="e9d29-118">Určuje typ (včetně oboru názvů), název sestavení, verzi, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="e9d29-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9d29-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e9d29-119">Child Elements</span></span>  
  
|<span data-ttu-id="e9d29-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9d29-120">Element</span></span>|<span data-ttu-id="e9d29-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e9d29-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9d29-122">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="e9d29-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="e9d29-123">Určuje index parametru, je-li deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="e9d29-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9d29-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e9d29-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e9d29-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9d29-125">Element</span></span>|<span data-ttu-id="e9d29-126">Popis</span><span class="sxs-lookup"><span data-stu-id="e9d29-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9d29-127">\<add></span><span class="sxs-lookup"><span data-stu-id="e9d29-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="e9d29-128">Přidá do kolekce deklarované typy deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="e9d29-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9d29-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9d29-129">Remarks</span></span>  
 <span data-ttu-id="e9d29-130">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e9d29-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="e9d29-131">Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="e9d29-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9d29-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9d29-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9d29-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9d29-133">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="e9d29-134">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="e9d29-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="e9d29-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e9d29-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="e9d29-136">\<add></span><span class="sxs-lookup"><span data-stu-id="e9d29-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
