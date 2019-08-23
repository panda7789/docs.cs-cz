---
title: <add> z <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: df69b5f8a79489b722c1074f118b9c6f6e8e363d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926661"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="82b56-102">\<Přidat > \<> ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="82b56-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="82b56-103">Představuje výchozí mapování protokolů mezi schématem transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a vazbou Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="82b56-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="82b56-104">Při vytváření výchozích koncových bodů za běhu vyhledá WCF nakonfigurované mapování a rozhodne, které vazby použít pro konkrétní adresu založenou na.</span><span class="sxs-lookup"><span data-stu-id="82b56-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="82b56-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="82b56-105">\<system.serviceModel></span></span>  
<span data-ttu-id="82b56-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="82b56-106">\<protocolMapping></span></span>  
<span data-ttu-id="82b56-107">\<add></span><span class="sxs-lookup"><span data-stu-id="82b56-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b56-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82b56-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82b56-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="82b56-109">Attributes and Elements</span></span>  
 <span data-ttu-id="82b56-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="82b56-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82b56-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="82b56-111">Attributes</span></span>  
  
|<span data-ttu-id="82b56-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="82b56-112">Element</span></span>|<span data-ttu-id="82b56-113">Popis</span><span class="sxs-lookup"><span data-stu-id="82b56-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82b56-114">vazba</span><span class="sxs-lookup"><span data-stu-id="82b56-114">binding</span></span>|<span data-ttu-id="82b56-115">Řetězec, který určuje typ vazby, která se má použít pro koncový bod při vytváření výchozího koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="82b56-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="82b56-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="82b56-116">bindingConfiguration</span></span>|<span data-ttu-id="82b56-117">Řetězec, který určuje název konfiguračního oddílu vazby, na který se má odkazovat.</span><span class="sxs-lookup"><span data-stu-id="82b56-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="82b56-118">scheme</span><span class="sxs-lookup"><span data-stu-id="82b56-118">scheme</span></span>|<span data-ttu-id="82b56-119">Schéma přenosového protokolu, které se má použít pro výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="82b56-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82b56-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="82b56-120">Child Elements</span></span>  
 <span data-ttu-id="82b56-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="82b56-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82b56-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="82b56-122">Parent Elements</span></span>  
  
|<span data-ttu-id="82b56-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="82b56-123">Element</span></span>|<span data-ttu-id="82b56-124">Popis</span><span class="sxs-lookup"><span data-stu-id="82b56-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82b56-125">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="82b56-125">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="82b56-126">Představuje konfigurační oddíl pro definování výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a Windows Communication Foundation (WCF) vazby.</span><span class="sxs-lookup"><span data-stu-id="82b56-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82b56-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="82b56-127">Example</span></span>  
 <span data-ttu-id="82b56-128">Následující konfigurační příklad ukazuje výchozí mapování protokolu v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="82b56-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="82b56-129">Toto výchozí mapování na úrovni počítače můžete přepsat úpravou souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="82b56-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="82b56-130">Nebo pokud byste ho chtěli přepsat v rámci rozsahu aplikace, můžete tuto část přepsat v konfiguračním souboru aplikace a změnit mapování pro jednotlivá schémata protokolů.</span><span class="sxs-lookup"><span data-stu-id="82b56-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82b56-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82b56-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
