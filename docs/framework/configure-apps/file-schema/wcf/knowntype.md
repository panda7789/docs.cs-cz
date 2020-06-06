---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397876"
---
# \<knownType>
<span data-ttu-id="6c6ad-101">Určuje typ, který má být použit <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="6c6ad-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="6c6ad-102">Element určuje známý typ, který je vrácen polem nebo vlastností deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="6c6ad-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="6c6ad-103">Další informace najdete v tématu [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="6c6ad-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="6c6ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c6ad-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="6c6ad-105">Typ</span><span class="sxs-lookup"><span data-stu-id="6c6ad-105">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c6ad-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6c6ad-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6c6ad-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6c6ad-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c6ad-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6c6ad-108">Attributes</span></span>  
  
|<span data-ttu-id="6c6ad-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="6c6ad-109">Attribute</span></span>|<span data-ttu-id="6c6ad-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6c6ad-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c6ad-111">typ</span><span class="sxs-lookup"><span data-stu-id="6c6ad-111">type</span></span>|<span data-ttu-id="6c6ad-112">Určuje typ (včetně oboru názvů), název sestavení, verzi, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="6c6ad-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c6ad-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6c6ad-113">Child Elements</span></span>  
  
|<span data-ttu-id="6c6ad-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c6ad-114">Element</span></span>|<span data-ttu-id="6c6ad-115">Description</span><span class="sxs-lookup"><span data-stu-id="6c6ad-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="6c6ad-116">Určuje index parametru, pokud je deklarovaný typ obecný typ.</span><span class="sxs-lookup"><span data-stu-id="6c6ad-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c6ad-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6c6ad-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6c6ad-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c6ad-118">Element</span></span>|<span data-ttu-id="6c6ad-119">Description</span><span class="sxs-lookup"><span data-stu-id="6c6ad-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="6c6ad-120">Přidá deklarovaný typ do kolekce deklarovaných typů.</span><span class="sxs-lookup"><span data-stu-id="6c6ad-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c6ad-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c6ad-121">Remarks</span></span>  
 <span data-ttu-id="6c6ad-122">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="6c6ad-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6c6ad-123">[\<dataContractSerializer>](datacontractserializer-element.md)Příklad použití tohoto prvku naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="6c6ad-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c6ad-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c6ad-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c6ad-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c6ad-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="6c6ad-126">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="6c6ad-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
