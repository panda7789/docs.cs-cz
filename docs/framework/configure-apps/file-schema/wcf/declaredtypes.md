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
ms.openlocfilehash: cef34a8836c7b17fe9a85cac190090f42653df14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919238"
---
# <a name="declaredtypes"></a><span data-ttu-id="43f86-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="43f86-101">\<declaredTypes></span></span>
<span data-ttu-id="43f86-102">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="43f86-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="43f86-103">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="43f86-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="43f86-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="43f86-104">system.runtime.serialization</span></span>  
<span data-ttu-id="43f86-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43f86-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="43f86-106">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="43f86-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f86-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43f86-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43f86-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43f86-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43f86-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43f86-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43f86-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="43f86-110">Attributes</span></span>  
 <span data-ttu-id="43f86-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="43f86-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43f86-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43f86-112">Child Elements</span></span>  
  
|<span data-ttu-id="43f86-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="43f86-113">Element</span></span>|<span data-ttu-id="43f86-114">Popis</span><span class="sxs-lookup"><span data-stu-id="43f86-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43f86-115">\<add></span><span class="sxs-lookup"><span data-stu-id="43f86-115">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="43f86-116">Přidá typy, které vyžadují známé typy.</span><span class="sxs-lookup"><span data-stu-id="43f86-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43f86-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43f86-117">Parent Elements</span></span>  
  
|<span data-ttu-id="43f86-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="43f86-118">Element</span></span>|<span data-ttu-id="43f86-119">Popis</span><span class="sxs-lookup"><span data-stu-id="43f86-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43f86-120">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43f86-120">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="43f86-121">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="43f86-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43f86-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43f86-122">Remarks</span></span>  
 <span data-ttu-id="43f86-123">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="43f86-123">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43f86-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="43f86-124">Example</span></span>  
 <span data-ttu-id="43f86-125">Následující kód XML ukazuje deklarované typy a známé typy přidané do `DataContractSerializer` prvku.</span><span class="sxs-lookup"><span data-stu-id="43f86-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="43f86-126">V příkladu se zobrazují tři přidávané typy.</span><span class="sxs-lookup"><span data-stu-id="43f86-126">The example shows three types being added.</span></span> <span data-ttu-id="43f86-127">První je vlastní typ pojmenovaný "Orders", který používá známý typ s názvem "Item".</span><span class="sxs-lookup"><span data-stu-id="43f86-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="43f86-128">Druhý deklarovaný typ je <xref:System.Collections.Generic.List%601> , který používá `Item` jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="43f86-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="43f86-129">Nakonec třetí deklarovaný typ je <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="43f86-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="43f86-130">Typ <xref:System.Collections.Generic.Dictionary%602> třídy je obecný typ se dvěma parametry typu.</span><span class="sxs-lookup"><span data-stu-id="43f86-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="43f86-131">První představuje klíč a druhý představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="43f86-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="43f86-132">Následující příklad přidá <xref:System.Collections.Generic.List%601> druhý typ (hodnota) do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="43f86-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="43f86-133">Je nutné použít `index` atribut k určení, který parametr typu má být použit v známém typu.</span><span class="sxs-lookup"><span data-stu-id="43f86-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="43f86-134">V tomto případě je typ hodnoty označen atributem index nastaveným na hodnotu "1" (kolekce je počítána od nuly).</span><span class="sxs-lookup"><span data-stu-id="43f86-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43f86-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43f86-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="43f86-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43f86-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="43f86-137">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="43f86-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="43f86-138">\<add></span><span class="sxs-lookup"><span data-stu-id="43f86-138">\<add></span></span>](add-of-declaredtypes-element.md)
