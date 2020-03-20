---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152967"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="2cbc0-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="2cbc0-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="2cbc0-103">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje <xref:System.Runtime.Serialization.DataContractSerializer>prvky pro nastavení možností .</span><span class="sxs-lookup"><span data-stu-id="2cbc0-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="2cbc0-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2cbc0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2cbc0-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span><span class="sxs-lookup"><span data-stu-id="2cbc0-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbc0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cbc0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cbc0-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2cbc0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2cbc0-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2cbc0-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cbc0-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="2cbc0-109">Attributes</span></span>  
 <span data-ttu-id="2cbc0-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="2cbc0-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2cbc0-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2cbc0-111">Child Elements</span></span>  
  
|<span data-ttu-id="2cbc0-112">Element</span><span class="sxs-lookup"><span data-stu-id="2cbc0-112">Element</span></span>|<span data-ttu-id="2cbc0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2cbc0-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cbc0-114">\<>dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="2cbc0-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="2cbc0-115">Umožňuje přidání známých typů, které mají být použity při rekonstrukci.</span><span class="sxs-lookup"><span data-stu-id="2cbc0-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2cbc0-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2cbc0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2cbc0-117">Element</span><span class="sxs-lookup"><span data-stu-id="2cbc0-117">Element</span></span>|<span data-ttu-id="2cbc0-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2cbc0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cbc0-119">\<konfigurace> Element</span><span class="sxs-lookup"><span data-stu-id="2cbc0-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="2cbc0-120">Prvek nejvyšší úrovně pro konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="2cbc0-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cbc0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cbc0-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="2cbc0-122">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="2cbc0-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="2cbc0-123">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="2cbc0-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
