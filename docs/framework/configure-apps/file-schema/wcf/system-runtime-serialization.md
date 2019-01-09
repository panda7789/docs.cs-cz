---
title: '&lt;System.Runtime.Serialization&gt;'
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 7cda0918ec14f9065ab1aea2479a14c8d224fcf8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150549"
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="5a1f2-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="5a1f2-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="5a1f2-103">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5a1f2-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5a1f2-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="5a1f2-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a1f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a1f2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a1f2-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a1f2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5a1f2-107">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a1f2-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a1f2-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a1f2-108">Attributes</span></span>  
 <span data-ttu-id="5a1f2-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a1f2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a1f2-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a1f2-110">Child Elements</span></span>  
  
|<span data-ttu-id="5a1f2-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a1f2-111">Element</span></span>|<span data-ttu-id="5a1f2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5a1f2-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a1f2-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5a1f2-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="5a1f2-114">Umožňuje přidání ze známých typů, který se má použít při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="5a1f2-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a1f2-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a1f2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5a1f2-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a1f2-116">Element</span></span>|<span data-ttu-id="5a1f2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5a1f2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a1f2-118">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="5a1f2-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="5a1f2-119">Element nejvyšší úrovně pro konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5a1f2-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a1f2-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a1f2-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="5a1f2-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5a1f2-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="5a1f2-122">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5a1f2-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
