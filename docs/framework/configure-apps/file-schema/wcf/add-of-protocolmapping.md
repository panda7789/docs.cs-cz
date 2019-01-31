---
title: <add> z <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 18b50ec2d848bc6bb920fb8f630ac7703654b286
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280732"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="cc6b7-102">\<Přidat > z \<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="cc6b7-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="cc6b7-103">Představuje výchozí mapování protokolů mezi schématem přenosového protokolu (např. http, net.tcp, net.pipe atd.) a vazbou Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cc6b7-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="cc6b7-104">Při vytváření výchozí koncové body za běhu, WCF zabývá nakonfigurované mapování a určuje, na které vazby pro konkrétní základě adresu.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="cc6b7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cc6b7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cc6b7-106">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="cc6b7-106">\<protocolMapping></span></span>  
<span data-ttu-id="cc6b7-107">\<add></span><span class="sxs-lookup"><span data-stu-id="cc6b7-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6b7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc6b7-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc6b7-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cc6b7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cc6b7-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc6b7-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="cc6b7-111">Attributes</span></span>  
  
|<span data-ttu-id="cc6b7-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc6b7-112">Element</span></span>|<span data-ttu-id="cc6b7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cc6b7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc6b7-114">vazba</span><span class="sxs-lookup"><span data-stu-id="cc6b7-114">binding</span></span>|<span data-ttu-id="cc6b7-115">Řetězec, který určuje typ vazby, které se použijí pro koncový bod při vytváření výchozího koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="cc6b7-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc6b7-116">bindingConfiguration</span></span>|<span data-ttu-id="cc6b7-117">Řetězec určující název oddílu konfigurace vazby, která má odkazovat.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="cc6b7-118">scheme</span><span class="sxs-lookup"><span data-stu-id="cc6b7-118">scheme</span></span>|<span data-ttu-id="cc6b7-119">Schématem přenosového protokolu použitého pro výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc6b7-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cc6b7-120">Child Elements</span></span>  
 <span data-ttu-id="cc6b7-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="cc6b7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc6b7-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cc6b7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cc6b7-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc6b7-123">Element</span></span>|<span data-ttu-id="cc6b7-124">Popis</span><span class="sxs-lookup"><span data-stu-id="cc6b7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc6b7-125">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="cc6b7-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="cc6b7-126">Představuje konfigurační oddíl pro definování výchozích mapování protokolů mezi schématy přenosových protokolů (např. http, net.tcp, net.pipe atd.) a vazby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cc6b7-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cc6b7-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc6b7-127">Example</span></span>  
 <span data-ttu-id="cc6b7-128">Následující příklad konfigurace ukazuje výchozí mapování protokolů v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="cc6b7-129">Můžete přepsat toto výchozí mapování na úrovni počítače tak, že upravíte soubor machine.config.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="cc6b7-130">Nebo pokud chcete pouze přepsat v rámci oboru aplikace, můžete ignorovat tento oddíl v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémata.</span><span class="sxs-lookup"><span data-stu-id="cc6b7-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="cc6b7-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc6b7-131">See also</span></span>
- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
