---
title: '&lt;declaredTypes&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: 0fadb13d4fcfbe87eb2c08fc35323c726c0ac2a6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146417"
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="03485-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="03485-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="03485-103">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="03485-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="03485-104">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="03485-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="03485-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="03485-105">system.runtime.serialization</span></span>  
<span data-ttu-id="03485-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="03485-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="03485-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="03485-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03485-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03485-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03485-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03485-109">Attributes and Elements</span></span>  
 <span data-ttu-id="03485-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03485-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03485-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="03485-111">Attributes</span></span>  
 <span data-ttu-id="03485-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="03485-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03485-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03485-113">Child Elements</span></span>  
  
|<span data-ttu-id="03485-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="03485-114">Element</span></span>|<span data-ttu-id="03485-115">Popis</span><span class="sxs-lookup"><span data-stu-id="03485-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03485-116">\<add></span><span class="sxs-lookup"><span data-stu-id="03485-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="03485-117">Přidá typy, které vyžadují známých typů.</span><span class="sxs-lookup"><span data-stu-id="03485-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03485-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03485-118">Parent Elements</span></span>  
  
|<span data-ttu-id="03485-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="03485-119">Element</span></span>|<span data-ttu-id="03485-120">Popis</span><span class="sxs-lookup"><span data-stu-id="03485-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03485-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="03485-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="03485-122">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="03485-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03485-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03485-123">Remarks</span></span>  
 <span data-ttu-id="03485-124">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="03485-124">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03485-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="03485-125">Example</span></span>  
 <span data-ttu-id="03485-126">Následující kód XML ukazuje deklarované typy a známé typy, které jsou přidány do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="03485-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="03485-127">Příklad ukazuje přidání tří typů.</span><span class="sxs-lookup"><span data-stu-id="03485-127">The example shows three types being added.</span></span> <span data-ttu-id="03485-128">První je to vlastní typ s názvem "Orders", který používá známý typ s názvem "Item".</span><span class="sxs-lookup"><span data-stu-id="03485-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="03485-129">Druhá deklarovaný typ je <xref:System.Collections.Generic.List%601> , která používá `Item` jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="03485-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="03485-130">Nakonec třetí deklarovaný typ je <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="03485-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="03485-131"><xref:System.Collections.Generic.Dictionary%602> Typu třídy je obecný typ s dva parametry typu.</span><span class="sxs-lookup"><span data-stu-id="03485-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="03485-132">První představuje klíč, a druhá představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="03485-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="03485-133">Následující příklad přidá <xref:System.Collections.Generic.List%601> druhého typu (hodnota) do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="03485-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="03485-134">Je nutné použít `index` atribut k určení, které parametr typu pro použití v známého typu.</span><span class="sxs-lookup"><span data-stu-id="03485-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="03485-135">V takovém případě je typ hodnoty označen atribut indexu nastavena na hodnotu "1" (kolekce je založený na nule).</span><span class="sxs-lookup"><span data-stu-id="03485-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03485-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="03485-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="03485-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="03485-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="03485-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="03485-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="03485-139">\<add></span><span class="sxs-lookup"><span data-stu-id="03485-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
