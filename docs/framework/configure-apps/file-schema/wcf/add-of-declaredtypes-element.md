---
title: <add><declaredTypes>elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400661"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="6e1aa-102">\<add>\<declaredTypes>elementu</span><span class="sxs-lookup"><span data-stu-id="6e1aa-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="6e1aa-103">Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> Při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="6e1aa-104">Každý deklarovaný typ obsahuje známé typy, které budou vráceny jako pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6e1aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e1aa-105">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e1aa-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e1aa-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6e1aa-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e1aa-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e1aa-108">Attributes</span></span>  
  
|<span data-ttu-id="6e1aa-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="6e1aa-109">Attribute</span></span>|<span data-ttu-id="6e1aa-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6e1aa-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e1aa-111">typ</span><span class="sxs-lookup"><span data-stu-id="6e1aa-111">type</span></span>|<span data-ttu-id="6e1aa-112">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="6e1aa-113">Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-113">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e1aa-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6e1aa-114">Child Elements</span></span>  
  
|<span data-ttu-id="6e1aa-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e1aa-115">Element</span></span>|<span data-ttu-id="6e1aa-116">Description</span><span class="sxs-lookup"><span data-stu-id="6e1aa-116">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="6e1aa-117">Určuje známý typ pro deklarovaný typ, který se přidává.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-117">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="6e1aa-118">Je-li deklarovaný typ obecný typ, je nutné také přidat prvek parametru k `<knownType>` elementu pro určení, který obecný parametr slouží k vrácení známého typu.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-118">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e1aa-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6e1aa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6e1aa-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e1aa-120">Element</span></span>|<span data-ttu-id="6e1aa-121">Description</span><span class="sxs-lookup"><span data-stu-id="6e1aa-121">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="6e1aa-122">Obsahuje typy, které během deserializace vyžadují známé typy <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="6e1aa-122">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e1aa-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e1aa-123">Remarks</span></span>  
 <span data-ttu-id="6e1aa-124">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="6e1aa-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6e1aa-125">[\<dataContractSerializer>](datacontractserializer-element.md)Příklad použití tohoto prvku naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-125">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e1aa-126">Pokud přidáte <xref:System.Object> typ jako `<declaredType>` , <xref:System.Configuration.ConfigurationErrorsException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-126">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="6e1aa-127">Důvodem je, že <xref:System.Object> typ nelze použít jako deklarovaný typ v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6e1aa-127">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e1aa-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e1aa-128">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="6e1aa-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e1aa-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="6e1aa-130">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="6e1aa-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="6e1aa-131">\<add>tohoto\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="6e1aa-131">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
