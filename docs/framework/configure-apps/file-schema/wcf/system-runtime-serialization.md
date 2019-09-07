---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399467"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="1bdca-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="1bdca-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="1bdca-103">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1bdca-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="1bdca-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1bdca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1bdca-105">&nbsp;&nbsp; **\<System. Runtime. Serialization – >**</span><span class="sxs-lookup"><span data-stu-id="1bdca-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdca-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bdca-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bdca-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1bdca-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1bdca-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1bdca-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bdca-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="1bdca-109">Attributes</span></span>  
 <span data-ttu-id="1bdca-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="1bdca-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1bdca-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1bdca-111">Child Elements</span></span>  
  
|<span data-ttu-id="1bdca-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="1bdca-112">Element</span></span>|<span data-ttu-id="1bdca-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1bdca-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bdca-114">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="1bdca-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="1bdca-115">Umožňuje přidání známých typů, které se použijí při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="1bdca-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1bdca-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1bdca-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1bdca-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="1bdca-117">Element</span></span>|<span data-ttu-id="1bdca-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1bdca-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bdca-119">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1bdca-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="1bdca-120">Element nejvyšší úrovně pro konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1bdca-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bdca-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bdca-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="1bdca-122">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="1bdca-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="1bdca-123">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="1bdca-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
 