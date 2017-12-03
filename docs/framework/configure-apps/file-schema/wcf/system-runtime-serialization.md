---
title: '&lt;System.Runtime.Serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a6eb2b152f2ab11bbe0e08ff1ad22f94d45057e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="a0668-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="a0668-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="a0668-103">Reprezentuje kořenový element <xref:System.Runtime.Serialization> část oboru názvů a obsahuje prvky pro nastavení možností nástroje <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a0668-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="a0668-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="a0668-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0668-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0668-105">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0668-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0668-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a0668-107">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0668-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0668-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0668-108">Attributes</span></span>  
 <span data-ttu-id="a0668-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="a0668-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0668-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0668-110">Child Elements</span></span>  
  
|<span data-ttu-id="a0668-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0668-111">Element</span></span>|<span data-ttu-id="a0668-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a0668-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0668-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="a0668-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="a0668-114">Umožňuje přidání ze známých typů, který se má použít při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="a0668-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0668-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0668-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a0668-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0668-116">Element</span></span>|<span data-ttu-id="a0668-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a0668-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0668-118">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="a0668-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a0668-119">Element na nejvyšší úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a0668-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0668-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0668-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="a0668-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="a0668-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="a0668-122">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="a0668-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
