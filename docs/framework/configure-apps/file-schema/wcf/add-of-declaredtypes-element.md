---
title: <add><declaredTypes> elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400661"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="f2e20-102">\<Přidat > \<prvku > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="f2e20-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="f2e20-103">Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> Při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="f2e20-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="f2e20-104">Každý deklarovaný typ obsahuje známé typy, které budou vráceny jako pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="f2e20-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
<span data-ttu-id="f2e20-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2e20-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2e20-106">&nbsp;&nbsp;[ **\<System. Runtime. Serialization – >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="f2e20-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="f2e20-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="f2e20-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="f2e20-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="f2e20-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="f2e20-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="f2e20-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e20-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2e20-110">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2e20-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2e20-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f2e20-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2e20-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2e20-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2e20-113">Attributes</span></span>  
  
|<span data-ttu-id="f2e20-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="f2e20-114">Attribute</span></span>|<span data-ttu-id="f2e20-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f2e20-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2e20-116">– typ</span><span class="sxs-lookup"><span data-stu-id="f2e20-116">type</span></span>|<span data-ttu-id="f2e20-117">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="f2e20-117">Required string attribute.</span></span><br /><br /> <span data-ttu-id="f2e20-118">Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="f2e20-118">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2e20-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2e20-119">Child Elements</span></span>  
  
|<span data-ttu-id="f2e20-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2e20-120">Element</span></span>|<span data-ttu-id="f2e20-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f2e20-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2e20-122">\<knownType></span><span class="sxs-lookup"><span data-stu-id="f2e20-122">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="f2e20-123">Určuje známý typ pro deklarovaný typ, který se přidává.</span><span class="sxs-lookup"><span data-stu-id="f2e20-123">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="f2e20-124">Je-li deklarovaný typ obecný typ, je nutné také přidat prvek `<knownType>` parametru k elementu pro určení, který obecný parametr slouží k vrácení známého typu.</span><span class="sxs-lookup"><span data-stu-id="f2e20-124">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2e20-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2e20-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f2e20-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2e20-126">Element</span></span>|<span data-ttu-id="f2e20-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f2e20-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2e20-128">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="f2e20-128">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="f2e20-129">Obsahuje typy, které během deserializace <xref:System.Runtime.Serialization.DataContractSerializer>vyžadují známé typy.</span><span class="sxs-lookup"><span data-stu-id="f2e20-129">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2e20-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2e20-130">Remarks</span></span>  
 <span data-ttu-id="f2e20-131">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f2e20-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f2e20-132">Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="f2e20-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2e20-133">Pokud přidáte <xref:System.Object> typ `<declaredType>`jako, <xref:System.Configuration.ConfigurationErrorsException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f2e20-133">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="f2e20-134">Důvodem je, že <xref:System.Object> typ nelze použít jako deklarovaný typ v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f2e20-134">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2e20-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e20-135">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2e20-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2e20-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="f2e20-137">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="f2e20-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="f2e20-138">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f2e20-138">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="f2e20-139">\<Přidat > \<> declaredTypes</span><span class="sxs-lookup"><span data-stu-id="f2e20-139">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
