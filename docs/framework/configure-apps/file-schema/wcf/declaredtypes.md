---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 138bc800625a8334d692bd46a3ceb7dfe2ea4ae1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="e2a06-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="e2a06-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="e2a06-103">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="e2a06-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="e2a06-104">Další informace o kontraktech dat a známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="e2a06-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="e2a06-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="e2a06-105">system.runtime.serialization</span></span>  
<span data-ttu-id="e2a06-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e2a06-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="e2a06-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="e2a06-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a06-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2a06-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2a06-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e2a06-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e2a06-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e2a06-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2a06-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e2a06-111">Attributes</span></span>  
 <span data-ttu-id="e2a06-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="e2a06-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2a06-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e2a06-113">Child Elements</span></span>  
  
|<span data-ttu-id="e2a06-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2a06-114">Element</span></span>|<span data-ttu-id="e2a06-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e2a06-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2a06-116">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="e2a06-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="e2a06-117">Přidá typy, které vyžadují známé typy.</span><span class="sxs-lookup"><span data-stu-id="e2a06-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2a06-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e2a06-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e2a06-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2a06-119">Element</span></span>|<span data-ttu-id="e2a06-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e2a06-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2a06-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e2a06-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e2a06-122">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e2a06-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2a06-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2a06-123">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="e2a06-124">známé typy, najdete v části [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e2a06-124"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2a06-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2a06-125">Example</span></span>  
 <span data-ttu-id="e2a06-126">Následující kód ukazuje deklarované známé typy a přidat do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="e2a06-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="e2a06-127">Příklad ukazuje tři typy, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="e2a06-127">The example shows three types being added.</span></span> <span data-ttu-id="e2a06-128">První je vlastního typu s názvem "Objednávky", který používá známý typ s názvem "Položka".</span><span class="sxs-lookup"><span data-stu-id="e2a06-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="e2a06-129">Druhý deklarovaný typ <xref:System.Collections.Generic.List%601> používající `Item` jako známému typu.</span><span class="sxs-lookup"><span data-stu-id="e2a06-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="e2a06-130">Nakonec třetí deklarovaný typ <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="e2a06-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="e2a06-131"><xref:System.Collections.Generic.Dictionary%602> Typu třídy je obecného typu, s parametry dva typy.</span><span class="sxs-lookup"><span data-stu-id="e2a06-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="e2a06-132">Představuje klíč první a druhý představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e2a06-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="e2a06-133">Následující příklad přidá <xref:System.Collections.Generic.List%601> druhého typu (hodnota) do seznamu ze známých typů.</span><span class="sxs-lookup"><span data-stu-id="e2a06-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="e2a06-134">Je nutné použít `index` které parametr typu pro použití v známý typ žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="e2a06-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="e2a06-135">Typ hodnoty v tomto případě je indikován atribut index, který je nastavený na hodnotu "1" (kolekce je počítáno od nuly).</span><span class="sxs-lookup"><span data-stu-id="e2a06-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2a06-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2a06-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="e2a06-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e2a06-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="e2a06-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="e2a06-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="e2a06-139">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="e2a06-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
