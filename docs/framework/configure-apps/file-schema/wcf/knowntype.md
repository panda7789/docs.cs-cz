---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: a0794314cfcb87df00d66b6832356fb130787eba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928858"
---
# <a name="knowntype"></a><span data-ttu-id="4361e-101">\<Třída KnownType ></span><span class="sxs-lookup"><span data-stu-id="4361e-101">\<knownType></span></span>
<span data-ttu-id="4361e-102">Určuje typ, který má být použit <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="4361e-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="4361e-103">Element určuje známý typ, který je vrácen polem nebo vlastností deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="4361e-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="4361e-104">Další informace najdete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="4361e-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="4361e-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="4361e-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="4361e-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="4361e-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="4361e-107">\<declaredTypes – element ></span><span class="sxs-lookup"><span data-stu-id="4361e-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="4361e-108">\<Přidat > \<> declaredTypes</span><span class="sxs-lookup"><span data-stu-id="4361e-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="4361e-109">\<Třída KnownType – element ></span><span class="sxs-lookup"><span data-stu-id="4361e-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4361e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4361e-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="4361e-111">type</span><span class="sxs-lookup"><span data-stu-id="4361e-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4361e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4361e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4361e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4361e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4361e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="4361e-114">Attributes</span></span>  
  
|<span data-ttu-id="4361e-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="4361e-115">Attribute</span></span>|<span data-ttu-id="4361e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4361e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4361e-117">– typ</span><span class="sxs-lookup"><span data-stu-id="4361e-117">type</span></span>|<span data-ttu-id="4361e-118">Určuje typ (včetně oboru názvů), název sestavení, verzi, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="4361e-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4361e-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4361e-119">Child Elements</span></span>  
  
|<span data-ttu-id="4361e-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4361e-120">Element</span></span>|<span data-ttu-id="4361e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4361e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4361e-122">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="4361e-122">\<parameter></span></span>](parameter.md)|<span data-ttu-id="4361e-123">Určuje index parametru, pokud je deklarovaný typ obecný typ.</span><span class="sxs-lookup"><span data-stu-id="4361e-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4361e-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4361e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4361e-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="4361e-125">Element</span></span>|<span data-ttu-id="4361e-126">Popis</span><span class="sxs-lookup"><span data-stu-id="4361e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4361e-127">\<add></span><span class="sxs-lookup"><span data-stu-id="4361e-127">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="4361e-128">Přidá deklarovaný typ do kolekce deklarovaných typů.</span><span class="sxs-lookup"><span data-stu-id="4361e-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4361e-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4361e-129">Remarks</span></span>  
 <span data-ttu-id="4361e-130">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4361e-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="4361e-131">Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="4361e-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4361e-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="4361e-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4361e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4361e-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="4361e-134">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="4361e-134">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="4361e-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="4361e-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="4361e-136">\<add></span><span class="sxs-lookup"><span data-stu-id="4361e-136">\<add></span></span>](add-of-declaredtypes-element.md)
