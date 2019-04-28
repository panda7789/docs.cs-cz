---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760685"
---
# <a name="knowntype"></a><span data-ttu-id="cb3cb-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="cb3cb-101">\<knownType></span></span>
<span data-ttu-id="cb3cb-102">Určuje typ používané <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="cb3cb-103">Určuje element "známý typ", který je vrácen pole nebo vlastnost "deklarovaného typu".</span><span class="sxs-lookup"><span data-stu-id="cb3cb-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="cb3cb-104">Další informace najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cb3cb-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="cb3cb-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="cb3cb-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="cb3cb-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="cb3cb-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="cb3cb-107">\<declaredTypes > – Element</span><span class="sxs-lookup"><span data-stu-id="cb3cb-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="cb3cb-108">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="cb3cb-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="cb3cb-109">\<Třída knownType > – Element</span><span class="sxs-lookup"><span data-stu-id="cb3cb-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3cb-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb3cb-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="cb3cb-111">Type</span><span class="sxs-lookup"><span data-stu-id="cb3cb-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb3cb-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cb3cb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cb3cb-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb3cb-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="cb3cb-114">Attributes</span></span>  
  
|<span data-ttu-id="cb3cb-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="cb3cb-115">Attribute</span></span>|<span data-ttu-id="cb3cb-116">Popis</span><span class="sxs-lookup"><span data-stu-id="cb3cb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb3cb-117"> – typ</span><span class="sxs-lookup"><span data-stu-id="cb3cb-117">type</span></span>|<span data-ttu-id="cb3cb-118">Určuje typ (včetně oboru názvů), název sestavení, verzi, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb3cb-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cb3cb-119">Child Elements</span></span>  
  
|<span data-ttu-id="cb3cb-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="cb3cb-120">Element</span></span>|<span data-ttu-id="cb3cb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="cb3cb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb3cb-122">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="cb3cb-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="cb3cb-123">Určuje index parametru, je-li deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb3cb-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cb3cb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cb3cb-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="cb3cb-125">Element</span></span>|<span data-ttu-id="cb3cb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="cb3cb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb3cb-127">\<add></span><span class="sxs-lookup"><span data-stu-id="cb3cb-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="cb3cb-128">Přidá do kolekce deklarované typy deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb3cb-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb3cb-129">Remarks</span></span>  
 <span data-ttu-id="cb3cb-130">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="cb3cb-131">Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb3cb-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb3cb-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb3cb-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb3cb-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="cb3cb-134">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="cb3cb-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="cb3cb-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="cb3cb-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="cb3cb-136">\<add></span><span class="sxs-lookup"><span data-stu-id="cb3cb-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
