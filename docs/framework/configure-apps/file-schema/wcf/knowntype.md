---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397876"
---
# <a name="knowntype"></a><span data-ttu-id="20701-101">\<Třída KnownType ></span><span class="sxs-lookup"><span data-stu-id="20701-101">\<knownType></span></span>
<span data-ttu-id="20701-102">Určuje typ, který má být použit <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="20701-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="20701-103">Element určuje známý typ, který je vrácen polem nebo vlastností deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="20701-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="20701-104">Další informace najdete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="20701-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="20701-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="20701-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20701-106">&nbsp;&nbsp;[ **\<System. Runtime. Serialization – >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="20701-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="20701-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="20701-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="20701-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="20701-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="20701-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Přidat >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="20701-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="20701-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Třída KnownType >**</span><span class="sxs-lookup"><span data-stu-id="20701-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20701-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20701-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="20701-112">type</span><span class="sxs-lookup"><span data-stu-id="20701-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20701-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="20701-113">Attributes and Elements</span></span>  
 <span data-ttu-id="20701-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20701-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20701-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="20701-115">Attributes</span></span>  
  
|<span data-ttu-id="20701-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="20701-116">Attribute</span></span>|<span data-ttu-id="20701-117">Popis</span><span class="sxs-lookup"><span data-stu-id="20701-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20701-118">– typ</span><span class="sxs-lookup"><span data-stu-id="20701-118">type</span></span>|<span data-ttu-id="20701-119">Určuje typ (včetně oboru názvů), název sestavení, verzi, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="20701-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20701-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="20701-120">Child Elements</span></span>  
  
|<span data-ttu-id="20701-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="20701-121">Element</span></span>|<span data-ttu-id="20701-122">Popis</span><span class="sxs-lookup"><span data-stu-id="20701-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20701-123">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="20701-123">\<parameter></span></span>](parameter.md)|<span data-ttu-id="20701-124">Určuje index parametru, pokud je deklarovaný typ obecný typ.</span><span class="sxs-lookup"><span data-stu-id="20701-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20701-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="20701-125">Parent Elements</span></span>  
  
|<span data-ttu-id="20701-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="20701-126">Element</span></span>|<span data-ttu-id="20701-127">Popis</span><span class="sxs-lookup"><span data-stu-id="20701-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20701-128">\<add></span><span class="sxs-lookup"><span data-stu-id="20701-128">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="20701-129">Přidá deklarovaný typ do kolekce deklarovaných typů.</span><span class="sxs-lookup"><span data-stu-id="20701-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20701-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20701-130">Remarks</span></span>  
 <span data-ttu-id="20701-131">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="20701-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="20701-132">Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="20701-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20701-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="20701-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20701-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20701-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="20701-135">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="20701-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="20701-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="20701-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="20701-137">\<add></span><span class="sxs-lookup"><span data-stu-id="20701-137">\<add></span></span>](add-of-declaredtypes-element.md)
