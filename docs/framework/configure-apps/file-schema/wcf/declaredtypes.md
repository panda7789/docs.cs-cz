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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398051"
---
# \<declaredTypes>
<span data-ttu-id="5ba4e-101">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="5ba4e-102">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5ba4e-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="5ba4e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ba4e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ba4e-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ba4e-104">Attributes and Elements</span></span>  
 <span data-ttu-id="5ba4e-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ba4e-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ba4e-106">Attributes</span></span>  
 <span data-ttu-id="5ba4e-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="5ba4e-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ba4e-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ba4e-108">Child Elements</span></span>  
  
|<span data-ttu-id="5ba4e-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ba4e-109">Element</span></span>|<span data-ttu-id="5ba4e-110">Description</span><span class="sxs-lookup"><span data-stu-id="5ba4e-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="5ba4e-111">Přidá typy, které vyžadují známé typy.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ba4e-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ba4e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5ba4e-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ba4e-113">Element</span></span>|<span data-ttu-id="5ba4e-114">Description</span><span class="sxs-lookup"><span data-stu-id="5ba4e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="5ba4e-115">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="5ba4e-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ba4e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ba4e-116">Remarks</span></span>  
 <span data-ttu-id="5ba4e-117">Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="5ba4e-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ba4e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ba4e-118">Example</span></span>  
 <span data-ttu-id="5ba4e-119">Následující kód XML ukazuje deklarované typy a známé typy přidané do `DataContractSerializer` prvku.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="5ba4e-120">V příkladu se zobrazují tři přidávané typy.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-120">The example shows three types being added.</span></span> <span data-ttu-id="5ba4e-121">První je vlastní typ pojmenovaný "Orders", který používá známý typ s názvem "Item".</span><span class="sxs-lookup"><span data-stu-id="5ba4e-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="5ba4e-122">Druhý deklarovaný typ je <xref:System.Collections.Generic.List%601> , který používá `Item` jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="5ba4e-123">Nakonec třetí deklarovaný typ je <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="5ba4e-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="5ba4e-124"><xref:System.Collections.Generic.Dictionary%602>Typ třídy je obecný typ se dvěma parametry typu.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="5ba4e-125">První představuje klíč a druhý představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="5ba4e-126">Následující příklad přidá <xref:System.Collections.Generic.List%601> druhý typ (hodnota) do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="5ba4e-127">Je nutné použít `index` atribut k určení, který parametr typu má být použit v známém typu.</span><span class="sxs-lookup"><span data-stu-id="5ba4e-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="5ba4e-128">V tomto případě je typ hodnoty označen atributem index nastaveným na hodnotu "1" (kolekce je počítána od nuly).</span><span class="sxs-lookup"><span data-stu-id="5ba4e-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ba4e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ba4e-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="5ba4e-130">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5ba4e-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
