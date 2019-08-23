---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 4ec5cd19ccdc5c21a3caf426520d51442dc5ab3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938926"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="7a684-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="7a684-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="7a684-103">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7a684-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="7a684-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="7a684-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a684-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a684-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a684-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7a684-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7a684-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7a684-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a684-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="7a684-108">Attributes</span></span>  
 <span data-ttu-id="7a684-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="7a684-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7a684-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7a684-110">Child Elements</span></span>  
  
|<span data-ttu-id="7a684-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a684-111">Element</span></span>|<span data-ttu-id="7a684-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7a684-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a684-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="7a684-113">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="7a684-114">Umožňuje přidání známých typů, které se použijí při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="7a684-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a684-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7a684-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7a684-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a684-116">Element</span></span>|<span data-ttu-id="7a684-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7a684-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a684-118">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7a684-118">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="7a684-119">Element nejvyšší úrovně pro konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7a684-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a684-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a684-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="7a684-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="7a684-121">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="7a684-122">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="7a684-122">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
