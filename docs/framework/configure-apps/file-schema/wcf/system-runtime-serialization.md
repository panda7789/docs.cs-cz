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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5a47417ded6e0917fadf2134eed5997d9d3b3d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="77829-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="77829-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="77829-103">Reprezentuje kořenový element <xref:System.Runtime.Serialization> část oboru názvů a obsahuje prvky pro nastavení možností nástroje <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="77829-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="77829-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="77829-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77829-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77829-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77829-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="77829-106">Attributes and Elements</span></span>  
 <span data-ttu-id="77829-107">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="77829-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77829-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="77829-108">Attributes</span></span>  
 <span data-ttu-id="77829-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="77829-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="77829-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="77829-110">Child Elements</span></span>  
  
|<span data-ttu-id="77829-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="77829-111">Element</span></span>|<span data-ttu-id="77829-112">Popis</span><span class="sxs-lookup"><span data-stu-id="77829-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77829-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="77829-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="77829-114">Umožňuje přidání ze známých typů, který se má použít při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="77829-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77829-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="77829-115">Parent Elements</span></span>  
  
|<span data-ttu-id="77829-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="77829-116">Element</span></span>|<span data-ttu-id="77829-117">Popis</span><span class="sxs-lookup"><span data-stu-id="77829-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77829-118">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="77829-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="77829-119">Element na nejvyšší úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="77829-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77829-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="77829-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="77829-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="77829-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="77829-122">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="77829-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
