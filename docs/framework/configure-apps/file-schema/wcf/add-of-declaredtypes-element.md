---
title: <add><declaredTypes> elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920175"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="0067c-102">\<Přidat > \<prvku > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="0067c-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="0067c-103">Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> Při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="0067c-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="0067c-104">Každý deklarovaný typ obsahuje známé typy, které budou vráceny jako pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="0067c-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="0067c-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="0067c-105">system.runtime.serialization</span></span>  
<span data-ttu-id="0067c-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="0067c-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="0067c-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0067c-107">\<declaredTypes></span></span>  
<span data-ttu-id="0067c-108">\<Přidat > \<> declaredTypes</span><span class="sxs-lookup"><span data-stu-id="0067c-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0067c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0067c-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0067c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0067c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0067c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0067c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0067c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0067c-112">Attributes</span></span>  
  
|<span data-ttu-id="0067c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0067c-113">Attribute</span></span>|<span data-ttu-id="0067c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0067c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0067c-115">– typ</span><span class="sxs-lookup"><span data-stu-id="0067c-115">type</span></span>|<span data-ttu-id="0067c-116">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="0067c-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="0067c-117">Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="0067c-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0067c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0067c-118">Child Elements</span></span>  
  
|<span data-ttu-id="0067c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="0067c-119">Element</span></span>|<span data-ttu-id="0067c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0067c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0067c-121">\<knownType></span><span class="sxs-lookup"><span data-stu-id="0067c-121">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="0067c-122">Určuje známý typ pro deklarovaný typ, který se přidává.</span><span class="sxs-lookup"><span data-stu-id="0067c-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="0067c-123">Je-li deklarovaný typ obecný typ, je nutné také přidat prvek `<knownType>` parametru k elementu pro určení, který obecný parametr slouží k vrácení známého typu.</span><span class="sxs-lookup"><span data-stu-id="0067c-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0067c-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0067c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0067c-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="0067c-125">Element</span></span>|<span data-ttu-id="0067c-126">Popis</span><span class="sxs-lookup"><span data-stu-id="0067c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0067c-127">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="0067c-127">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="0067c-128">Obsahuje typy, které během deserializace <xref:System.Runtime.Serialization.DataContractSerializer>vyžadují známé typy.</span><span class="sxs-lookup"><span data-stu-id="0067c-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0067c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0067c-129">Remarks</span></span>  
 <span data-ttu-id="0067c-130">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0067c-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="0067c-131">Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0067c-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0067c-132">Pokud přidáte <xref:System.Object> typ `<declaredType>`jako, <xref:System.Configuration.ConfigurationErrorsException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="0067c-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="0067c-133">Důvodem je, že <xref:System.Object> typ nelze použít jako deklarovaný typ v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0067c-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0067c-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="0067c-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0067c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0067c-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="0067c-136">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="0067c-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0067c-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="0067c-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="0067c-138">\<Přidat > \<> declaredTypes</span><span class="sxs-lookup"><span data-stu-id="0067c-138">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
