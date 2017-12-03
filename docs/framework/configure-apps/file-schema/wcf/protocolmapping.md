---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88eb76a5657bd4a83bebb32ce30f73d32693be9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="17fc9-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="17fc9-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="17fc9-103">Představuje konfigurační oddíl pro definování sady výchozí protokol mapování mezi přenosu protokolu schémata (např. http, net.tcp, net.pipe atd.) a vazeb WCF.</span><span class="sxs-lookup"><span data-stu-id="17fc9-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="17fc9-104">Při vytváření výchozí koncové body v době běhu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] porovná nakonfigurované mapování a rozhodne, na které vazby pro konkrétní na základě adres.</span><span class="sxs-lookup"><span data-stu-id="17fc9-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="17fc9-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="17fc9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="17fc9-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="17fc9-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17fc9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17fc9-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17fc9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="17fc9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="17fc9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="17fc9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17fc9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="17fc9-110">Attributes</span></span>  
 <span data-ttu-id="17fc9-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="17fc9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17fc9-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="17fc9-112">Child Elements</span></span>  
  
|<span data-ttu-id="17fc9-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="17fc9-113">Element</span></span>|<span data-ttu-id="17fc9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="17fc9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17fc9-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="17fc9-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="17fc9-116">Obsahuje výchozí protokol mapování mezi přenosové schéma protokolu (např. http, net.tcp, net.pipe atd.) a vazbu WCF.</span><span class="sxs-lookup"><span data-stu-id="17fc9-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17fc9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="17fc9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="17fc9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="17fc9-118">Element</span></span>|<span data-ttu-id="17fc9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="17fc9-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17fc9-120">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="17fc9-120">system.ServiceModel</span></span>|<span data-ttu-id="17fc9-121">Kořenový element všechny konfigurační prvky WCF.</span><span class="sxs-lookup"><span data-stu-id="17fc9-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17fc9-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="17fc9-122">Example</span></span>  
 <span data-ttu-id="17fc9-123">Následující příklad konfigurace ukazuje výchozí mapování protokolu v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="17fc9-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="17fc9-124">Můžete přepsat toto výchozí mapování na úrovni počítače úpravou souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="17fc9-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="17fc9-125">Nebo pokud chcete pouze přepsání v rámci oboru aplikace, můžete přepsat v této části v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémat.</span><span class="sxs-lookup"><span data-stu-id="17fc9-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17fc9-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="17fc9-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
