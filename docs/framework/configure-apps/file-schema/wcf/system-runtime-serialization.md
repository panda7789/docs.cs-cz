---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152967"
---
# \<system.runtime.serialization>
<span data-ttu-id="6e030-102">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="6e030-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="6e030-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e030-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e030-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e030-104">Attributes and Elements</span></span>  
 <span data-ttu-id="6e030-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e030-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e030-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e030-106">Attributes</span></span>  
 <span data-ttu-id="6e030-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e030-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6e030-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6e030-108">Child Elements</span></span>  
  
|<span data-ttu-id="6e030-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e030-109">Element</span></span>|<span data-ttu-id="6e030-110">Description</span><span class="sxs-lookup"><span data-stu-id="6e030-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="6e030-111">Umožňuje přidání známých typů, které se použijí při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="6e030-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e030-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6e030-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6e030-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e030-113">Element</span></span>|<span data-ttu-id="6e030-114">Description</span><span class="sxs-lookup"><span data-stu-id="6e030-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e030-115">\<configuration>Objekt</span><span class="sxs-lookup"><span data-stu-id="6e030-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="6e030-116">Element nejvyšší úrovně pro konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6e030-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e030-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e030-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="6e030-118">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="6e030-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="6e030-119">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="6e030-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
