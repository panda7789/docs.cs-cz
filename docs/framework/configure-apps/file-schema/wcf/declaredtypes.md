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
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398051"
---
# <a name="declaredtypes"></a><span data-ttu-id="5a547-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="5a547-101">\<declaredTypes></span></span>
<span data-ttu-id="5a547-102">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="5a547-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="5a547-103">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5a547-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="5a547-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a547-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a547-105">&nbsp;&nbsp;[ **\<System. Runtime. Serialization – >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="5a547-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="5a547-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="5a547-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="5a547-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<declaredTypes >**</span><span class="sxs-lookup"><span data-stu-id="5a547-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a547-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a547-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a547-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a547-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5a547-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a547-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a547-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a547-111">Attributes</span></span>  
 <span data-ttu-id="5a547-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a547-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a547-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a547-113">Child Elements</span></span>  
  
|<span data-ttu-id="5a547-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a547-114">Element</span></span>|<span data-ttu-id="5a547-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5a547-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a547-116">\<add></span><span class="sxs-lookup"><span data-stu-id="5a547-116">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="5a547-117">Přidá typy, které vyžadují známé typy.</span><span class="sxs-lookup"><span data-stu-id="5a547-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a547-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a547-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5a547-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a547-119">Element</span></span>|<span data-ttu-id="5a547-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5a547-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a547-121">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5a547-121">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="5a547-122">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5a547-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a547-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a547-123">Remarks</span></span>  
 <span data-ttu-id="5a547-124">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5a547-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a547-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a547-125">Example</span></span>  
 <span data-ttu-id="5a547-126">Následující kód XML ukazuje deklarované typy a známé typy přidané do `DataContractSerializer` prvku.</span><span class="sxs-lookup"><span data-stu-id="5a547-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="5a547-127">V příkladu se zobrazují tři přidávané typy.</span><span class="sxs-lookup"><span data-stu-id="5a547-127">The example shows three types being added.</span></span> <span data-ttu-id="5a547-128">První je vlastní typ pojmenovaný "Orders", který používá známý typ s názvem "Item".</span><span class="sxs-lookup"><span data-stu-id="5a547-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="5a547-129">Druhý deklarovaný typ je <xref:System.Collections.Generic.List%601> , který používá `Item` jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="5a547-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="5a547-130">Nakonec třetí deklarovaný typ je <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="5a547-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="5a547-131">Typ <xref:System.Collections.Generic.Dictionary%602> třídy je obecný typ se dvěma parametry typu.</span><span class="sxs-lookup"><span data-stu-id="5a547-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="5a547-132">První představuje klíč a druhý představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5a547-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="5a547-133">Následující příklad přidá <xref:System.Collections.Generic.List%601> druhý typ (hodnota) do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="5a547-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="5a547-134">Je nutné použít `index` atribut k určení, který parametr typu má být použit v známém typu.</span><span class="sxs-lookup"><span data-stu-id="5a547-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="5a547-135">V tomto případě je typ hodnoty označen atributem index nastaveným na hodnotu "1" (kolekce je počítána od nuly).</span><span class="sxs-lookup"><span data-stu-id="5a547-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a547-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a547-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="5a547-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5a547-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="5a547-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5a547-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5a547-139">\<add></span><span class="sxs-lookup"><span data-stu-id="5a547-139">\<add></span></span>](add-of-declaredtypes-element.md)
