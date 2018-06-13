---
title: '&lt;add&gt; – &lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 4552cc030a88841d4fb80c097ba089d1c6a0066c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349008"
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="388aa-102">&lt;add&gt; – &lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="388aa-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="388aa-103">Představuje výchozí protokol mapování mezi přenosové schéma protokolu (např. http, net.tcp, net.pipe atd.) a vazbu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="388aa-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="388aa-104">Při vytváření výchozí koncové body za běhu, WCF porovná nakonfigurované mapování a rozhodne, na které vazby pro konkrétní na základě adres.</span><span class="sxs-lookup"><span data-stu-id="388aa-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="388aa-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="388aa-105">\<system.serviceModel></span></span>  
<span data-ttu-id="388aa-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="388aa-106">\<protocolMapping></span></span>  
<span data-ttu-id="388aa-107">\<add></span><span class="sxs-lookup"><span data-stu-id="388aa-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388aa-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="388aa-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="388aa-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="388aa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="388aa-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="388aa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="388aa-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="388aa-111">Attributes</span></span>  
  
|<span data-ttu-id="388aa-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="388aa-112">Element</span></span>|<span data-ttu-id="388aa-113">Popis</span><span class="sxs-lookup"><span data-stu-id="388aa-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="388aa-114">vazba</span><span class="sxs-lookup"><span data-stu-id="388aa-114">binding</span></span>|<span data-ttu-id="388aa-115">Řetězec, který určuje typ vazby má být použit pro koncový bod během vytváření výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="388aa-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="388aa-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="388aa-116">bindingConfiguration</span></span>|<span data-ttu-id="388aa-117">Řetězec, který určuje název konfiguračního oddílu vazba bude odkazovat.</span><span class="sxs-lookup"><span data-stu-id="388aa-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="388aa-118">scheme</span><span class="sxs-lookup"><span data-stu-id="388aa-118">scheme</span></span>|<span data-ttu-id="388aa-119">Schéma přenosu protokolu má být použit pro výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="388aa-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="388aa-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="388aa-120">Child Elements</span></span>  
 <span data-ttu-id="388aa-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="388aa-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="388aa-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="388aa-122">Parent Elements</span></span>  
  
|<span data-ttu-id="388aa-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="388aa-123">Element</span></span>|<span data-ttu-id="388aa-124">Popis</span><span class="sxs-lookup"><span data-stu-id="388aa-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="388aa-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="388aa-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="388aa-126">Představuje konfigurační oddíl pro definování výchozí protokol mapování mezi přenosu protokolu schémata (např. http, net.tcp, net.pipe atd.) a Windows Communication Foundation (WCF) vazby.</span><span class="sxs-lookup"><span data-stu-id="388aa-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="388aa-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="388aa-127">Example</span></span>  
 <span data-ttu-id="388aa-128">Následující příklad konfigurace ukazuje výchozí mapování protokolu v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="388aa-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="388aa-129">Můžete přepsat toto výchozí mapování na úrovni počítače úpravou souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="388aa-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="388aa-130">Nebo pokud chcete pouze přepsání v rámci oboru aplikace, můžete přepsat v této části v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémat.</span><span class="sxs-lookup"><span data-stu-id="388aa-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="388aa-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="388aa-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
