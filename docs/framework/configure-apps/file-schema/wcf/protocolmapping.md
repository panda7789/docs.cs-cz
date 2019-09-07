---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: be4224ef1a8b17653df8123aaf89e105a496355a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400024"
---
# <a name="protocolmapping"></a><span data-ttu-id="b5644-101">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="b5644-101">\<protocolMapping></span></span>
<span data-ttu-id="b5644-102">Představuje konfigurační oddíl pro definování sady výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe atd.) a vazbami WCF.</span><span class="sxs-lookup"><span data-stu-id="b5644-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="b5644-103">Při vytváření výchozích koncových bodů za běhu, Windows Communication Foundation (WCF) se podívá na nakonfigurované mapování a rozhodne o tom, která vazba se má použít pro konkrétní adresu založenou na.</span><span class="sxs-lookup"><span data-stu-id="b5644-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
<span data-ttu-id="b5644-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b5644-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b5644-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b5644-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b5644-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<protocolMapping >**</span><span class="sxs-lookup"><span data-stu-id="b5644-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5644-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5644-107">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5644-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b5644-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b5644-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b5644-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5644-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b5644-110">Attributes</span></span>  
 <span data-ttu-id="b5644-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="b5644-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5644-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b5644-112">Child Elements</span></span>  
  
|<span data-ttu-id="b5644-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="b5644-113">Element</span></span>|<span data-ttu-id="b5644-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b5644-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5644-115">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="b5644-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="b5644-116">Obsahuje výchozí mapování protokolů mezi schématem transportního protokolu (např. http, NET. TCP, NET. pipe atd.) a vazbou WCF.</span><span class="sxs-lookup"><span data-stu-id="b5644-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5644-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b5644-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b5644-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="b5644-118">Element</span></span>|<span data-ttu-id="b5644-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b5644-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5644-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b5644-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="b5644-121">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b5644-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b5644-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5644-122">Example</span></span>  
 <span data-ttu-id="b5644-123">Následující konfigurační příklad ukazuje výchozí mapování protokolu v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="b5644-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="b5644-124">Toto výchozí mapování na úrovni počítače můžete přepsat úpravou souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="b5644-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="b5644-125">Nebo pokud byste ho chtěli přepsat v rámci rozsahu aplikace, můžete tuto část přepsat v konfiguračním souboru aplikace a změnit mapování pro jednotlivá schémata protokolů.</span><span class="sxs-lookup"><span data-stu-id="b5644-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5644-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5644-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
