---
title: "&lt;dataContractSerializer&gt; – &lt;system.runtime.serialization&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39d24f03bde729e99b629162aee86efe4b60fdd1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="266d9-102">&lt;dataContractSerializer&gt; – &lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="266d9-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="266d9-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="266d9-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="266d9-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="266d9-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="266d9-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="266d9-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="266d9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="266d9-106">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
            maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String">  
          <knownType type="String">  
             <parameter index="Integer"  
                        type="String" />  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="266d9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="266d9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="266d9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="266d9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="266d9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="266d9-109">Attributes</span></span>  
  
|<span data-ttu-id="266d9-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="266d9-110">Element</span></span>|<span data-ttu-id="266d9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="266d9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="266d9-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="266d9-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="266d9-113">Logická hodnota, která určuje, jestli se ignorovat dat uvedených v koncovém bodě při jeho serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="266d9-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="266d9-114">Tento atribut je nastavit pouze na `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="266d9-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="266d9-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="266d9-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="266d9-116">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="266d9-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="266d9-117">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="266d9-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="266d9-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="266d9-118">Child Elements</span></span>  
  
|<span data-ttu-id="266d9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="266d9-119">Element</span></span>|<span data-ttu-id="266d9-120">Popis</span><span class="sxs-lookup"><span data-stu-id="266d9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="266d9-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="266d9-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="266d9-122">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="266d9-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="266d9-123">Další informace o kontraktech dat a známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="266d9-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="266d9-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="266d9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="266d9-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="266d9-125">Element</span></span>|<span data-ttu-id="266d9-126">Popis</span><span class="sxs-lookup"><span data-stu-id="266d9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="266d9-127">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="266d9-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="266d9-128">Reprezentuje kořenový element <xref:System.Runtime.Serialization> část oboru názvů a obsahuje prvky pro nastavení možností nástroje <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="266d9-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="266d9-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="266d9-129">Remarks</span></span>  
 <span data-ttu-id="266d9-130">Další informace o známé typy najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="266d9-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="266d9-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="266d9-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="266d9-132">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="266d9-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
