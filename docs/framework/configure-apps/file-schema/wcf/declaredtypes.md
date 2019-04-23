---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: 8919ee717012f8badcf7015bf8d850ed431c5943
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090274"
---
# <a name="declaredtypes"></a><span data-ttu-id="ab953-101">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="ab953-101">\<declaredTypes></span></span>
<span data-ttu-id="ab953-102">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ab953-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="ab953-103">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="ab953-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="ab953-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="ab953-104">system.runtime.serialization</span></span>  
<span data-ttu-id="ab953-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="ab953-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="ab953-106">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="ab953-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab953-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab953-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab953-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab953-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ab953-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab953-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab953-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab953-110">Attributes</span></span>  
 <span data-ttu-id="ab953-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab953-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab953-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab953-112">Child Elements</span></span>  
  
|<span data-ttu-id="ab953-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab953-113">Element</span></span>|<span data-ttu-id="ab953-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ab953-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab953-115">\<add></span><span class="sxs-lookup"><span data-stu-id="ab953-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="ab953-116">Přidá typy, které vyžadují známých typů.</span><span class="sxs-lookup"><span data-stu-id="ab953-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab953-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab953-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ab953-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab953-118">Element</span></span>|<span data-ttu-id="ab953-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ab953-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab953-120">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="ab953-120">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="ab953-121">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ab953-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab953-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab953-122">Remarks</span></span>  
 <span data-ttu-id="ab953-123">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ab953-123">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab953-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab953-124">Example</span></span>  
 <span data-ttu-id="ab953-125">Následující kód XML ukazuje deklarované typy a známé typy, které jsou přidány do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="ab953-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="ab953-126">Příklad ukazuje přidání tří typů.</span><span class="sxs-lookup"><span data-stu-id="ab953-126">The example shows three types being added.</span></span> <span data-ttu-id="ab953-127">První je to vlastní typ s názvem "Orders", který používá známý typ s názvem "Item".</span><span class="sxs-lookup"><span data-stu-id="ab953-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="ab953-128">Druhá deklarovaný typ je <xref:System.Collections.Generic.List%601> , která používá `Item` jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="ab953-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="ab953-129">Nakonec třetí deklarovaný typ je <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="ab953-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="ab953-130"><xref:System.Collections.Generic.Dictionary%602> Typu třídy je obecný typ s dva parametry typu.</span><span class="sxs-lookup"><span data-stu-id="ab953-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="ab953-131">První představuje klíč, a druhá představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ab953-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="ab953-132">Následující příklad přidá <xref:System.Collections.Generic.List%601> druhého typu (hodnota) do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="ab953-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="ab953-133">Je nutné použít `index` atribut k určení, které parametr typu pro použití v známého typu.</span><span class="sxs-lookup"><span data-stu-id="ab953-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="ab953-134">V takovém případě je typ hodnoty označen atribut indexu nastavena na hodnotu "1" (kolekce je založený na nule).</span><span class="sxs-lookup"><span data-stu-id="ab953-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="ab953-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab953-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="ab953-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="ab953-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="ab953-137">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="ab953-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="ab953-138">\<add></span><span class="sxs-lookup"><span data-stu-id="ab953-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
