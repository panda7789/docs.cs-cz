---
title: '&lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: c50ca451052c9ad9d7ab6a0cb5387e644196191e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525003"
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="74d18-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="74d18-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="74d18-103">Představuje konfigurační oddíl pro definování sady výchozích mapování protokolů mezi schématy přenosových protokolů (např. http, net.tcp, net.pipe atd.) a vazbami WCF.</span><span class="sxs-lookup"><span data-stu-id="74d18-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="74d18-104">Při vytváření výchozí koncové body za běhu, Windows Communication Foundation (WCF) zabývá nakonfigurované mapování a určuje, na které vazby pro konkrétní základě adresu.</span><span class="sxs-lookup"><span data-stu-id="74d18-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[<span data-ttu-id="74d18-105">**\<system.serviceModel >**</span><span class="sxs-lookup"><span data-stu-id="74d18-105">**\<system.serviceModel>**</span></span>](system-servicemodel.md)  
<span data-ttu-id="74d18-106">&nbsp;&nbsp;**\<protocolMapping >**</span><span class="sxs-lookup"><span data-stu-id="74d18-106">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d18-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74d18-107">Syntax</span></span>  
  
```xml
<protocolMapping>
   <add binding="String" bindingConfiguration="String" scheme="http/net.msmq/net.pipe/net.tcp"/>
</protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74d18-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74d18-108">Attributes and Elements</span></span>  
 <span data-ttu-id="74d18-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74d18-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74d18-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="74d18-110">Attributes</span></span>  
 <span data-ttu-id="74d18-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="74d18-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74d18-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74d18-112">Child Elements</span></span>  
  
|<span data-ttu-id="74d18-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="74d18-113">Element</span></span>|<span data-ttu-id="74d18-114">Popis</span><span class="sxs-lookup"><span data-stu-id="74d18-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74d18-115">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="74d18-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="74d18-116">Obsahuje výchozí mapování protokolů mezi schématem přenosového protokolu (např. http, net.tcp, net.pipe atd.) a vazeb WCF.</span><span class="sxs-lookup"><span data-stu-id="74d18-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74d18-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74d18-117">Parent Elements</span></span>  
  
|<span data-ttu-id="74d18-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="74d18-118">Element</span></span>|<span data-ttu-id="74d18-119">Popis</span><span class="sxs-lookup"><span data-stu-id="74d18-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74d18-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74d18-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="74d18-121">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="74d18-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="74d18-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="74d18-122">Example</span></span>  
 <span data-ttu-id="74d18-123">Následující příklad konfigurace ukazuje výchozí mapování protokolů v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="74d18-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="74d18-124">Můžete přepsat toto výchozí mapování na úrovni počítače tak, že upravíte soubor machine.config.</span><span class="sxs-lookup"><span data-stu-id="74d18-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="74d18-125">Nebo pokud chcete pouze přepsat v rámci oboru aplikace, můžete ignorovat tento oddíl v konfiguračním souboru aplikace a změnit mapování pro jednotlivé protokol schémata.</span><span class="sxs-lookup"><span data-stu-id="74d18-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74d18-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="74d18-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
