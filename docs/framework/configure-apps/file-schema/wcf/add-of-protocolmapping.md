---
title: "&lt;add&gt; – &lt;protocolMapping&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 255cd8518bd9c6c6c199c75aa32ca086c801d23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="1fa1c-102">&lt;add&gt; – &lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="1fa1c-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="1fa1c-103">Představuje výchozí protokol mapování mezi přenosové schéma protokolu (např. http, net.tcp, net.pipe atd.) a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] vazby.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span> <span data-ttu-id="1fa1c-104">Při vytváření výchozí koncové body v době běhu [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] porovná nakonfigurované mapování a rozhodne, na které vazby pro konkrétní na základě adres.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="1fa1c-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1fa1c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1fa1c-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="1fa1c-106">\<protocolMapping></span></span>  
<span data-ttu-id="1fa1c-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="1fa1c-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa1c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fa1c-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1fa1c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1fa1c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1fa1c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fa1c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1fa1c-111">Attributes</span></span>  
  
|<span data-ttu-id="1fa1c-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fa1c-112">Element</span></span>|<span data-ttu-id="1fa1c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1fa1c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1fa1c-114">vazba</span><span class="sxs-lookup"><span data-stu-id="1fa1c-114">binding</span></span>|<span data-ttu-id="1fa1c-115">Řetězec, který určuje typ vazby má být použit pro koncový bod během vytváření výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="1fa1c-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1fa1c-116">bindingConfiguration</span></span>|<span data-ttu-id="1fa1c-117">Řetězec, který určuje název konfiguračního oddílu vazba bude odkazovat.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="1fa1c-118">scheme</span><span class="sxs-lookup"><span data-stu-id="1fa1c-118">scheme</span></span>|<span data-ttu-id="1fa1c-119">Schéma přenosu protokolu má být použit pro výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fa1c-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1fa1c-120">Child Elements</span></span>  
 <span data-ttu-id="1fa1c-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="1fa1c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fa1c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1fa1c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1fa1c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fa1c-123">Element</span></span>|<span data-ttu-id="1fa1c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="1fa1c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fa1c-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="1fa1c-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="1fa1c-126">Představuje konfigurační oddíl pro definování výchozí protokol mapování mezi přenosu protokolu schémata (např. http, net.tcp, net.pipe atd.) a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] vazby.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1fa1c-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fa1c-127">Example</span></span>  
 <span data-ttu-id="1fa1c-128">Následující příklad konfigurace ukazuje výchozí mapování protokolu v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="1fa1c-129">Můžete přepsat toto výchozí mapování na úrovni počítače úpravou souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="1fa1c-130">Nebo pokud chcete pouze přepsání v rámci oboru aplikace, můžete přepsat v této části v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémat.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fa1c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fa1c-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
