---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 5aa5d75e12852fe6a0e4e9a2eb4ae57d25d1022c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272676"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="04caf-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="04caf-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="04caf-103">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="04caf-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="04caf-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="04caf-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04caf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04caf-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04caf-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04caf-106">Attributes and Elements</span></span>  
 <span data-ttu-id="04caf-107">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04caf-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04caf-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="04caf-108">Attributes</span></span>  
 <span data-ttu-id="04caf-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="04caf-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04caf-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04caf-110">Child Elements</span></span>  
  
|<span data-ttu-id="04caf-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="04caf-111">Element</span></span>|<span data-ttu-id="04caf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="04caf-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04caf-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="04caf-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="04caf-114">Umožňuje přidání ze známých typů, který se má použít při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="04caf-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04caf-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04caf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="04caf-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="04caf-116">Element</span></span>|<span data-ttu-id="04caf-117">Popis</span><span class="sxs-lookup"><span data-stu-id="04caf-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04caf-118">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="04caf-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="04caf-119">Element nejvyšší úrovně pro konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="04caf-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04caf-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04caf-120">See also</span></span>
- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="04caf-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="04caf-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="04caf-122">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="04caf-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
