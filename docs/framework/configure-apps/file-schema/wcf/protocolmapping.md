---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: e26044340bda84fe38b7e286edf833affa94b86c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118208"
---
# <a name="protocolmapping"></a><span data-ttu-id="a9c65-101">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="a9c65-101">\<protocolMapping></span></span>
<span data-ttu-id="a9c65-102">Představuje konfigurační oddíl pro definování sady výchozích mapování protokolů mezi schématy přenosových protokolů (např. http, net.tcp, net.pipe atd.) a vazbami WCF.</span><span class="sxs-lookup"><span data-stu-id="a9c65-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="a9c65-103">Při vytváření výchozí koncové body za běhu, Windows Communication Foundation (WCF) zabývá nakonfigurované mapování a určuje, na které vazby pro konkrétní základě adresu.</span><span class="sxs-lookup"><span data-stu-id="a9c65-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**<span data-ttu-id="a9c65-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a9c65-104">\<system.serviceModel></span></span>**](system-servicemodel.md)  
<span data-ttu-id="a9c65-105">&nbsp;&nbsp;**\<protocolMapping>**</span><span class="sxs-lookup"><span data-stu-id="a9c65-105">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9c65-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9c65-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9c65-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a9c65-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a9c65-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a9c65-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9c65-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a9c65-109">Attributes</span></span>  
 <span data-ttu-id="a9c65-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="a9c65-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a9c65-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a9c65-111">Child Elements</span></span>  
  
|<span data-ttu-id="a9c65-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9c65-112">Element</span></span>|<span data-ttu-id="a9c65-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a9c65-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9c65-114">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="a9c65-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="a9c65-115">Obsahuje výchozí mapování protokolů mezi schématem přenosového protokolu (např. http, net.tcp, net.pipe atd.) a vazeb WCF.</span><span class="sxs-lookup"><span data-stu-id="a9c65-115">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9c65-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a9c65-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a9c65-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9c65-117">Element</span></span>|<span data-ttu-id="a9c65-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a9c65-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9c65-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a9c65-119">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="a9c65-120">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="a9c65-120">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a9c65-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9c65-121">Example</span></span>  
 <span data-ttu-id="a9c65-122">Následující příklad konfigurace ukazuje výchozí mapování protokolů v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="a9c65-122">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="a9c65-123">Můžete přepsat toto výchozí mapování na úrovni počítače tak, že upravíte soubor machine.config.</span><span class="sxs-lookup"><span data-stu-id="a9c65-123">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="a9c65-124">Nebo pokud chcete pouze přepsat v rámci oboru aplikace, můžete ignorovat tento oddíl v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémata.</span><span class="sxs-lookup"><span data-stu-id="a9c65-124">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9c65-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9c65-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
