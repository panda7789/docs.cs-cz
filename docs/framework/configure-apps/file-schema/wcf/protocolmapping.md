---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: be4224ef1a8b17653df8123aaf89e105a496355a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400024"
---
# \<protocolMapping>
<span data-ttu-id="0e1d8-101">Představuje konfigurační oddíl pro definování sady výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe atd.) a vazbami WCF.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-101">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="0e1d8-102">Při vytváření výchozích koncových bodů za běhu, Windows Communication Foundation (WCF) se podívá na nakonfigurované mapování a rozhodne o tom, která vazba se má použít pro konkrétní adresu založenou na.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-102">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="0e1d8-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e1d8-103">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e1d8-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0e1d8-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0e1d8-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e1d8-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e1d8-106">Attributes</span></span>  
 <span data-ttu-id="0e1d8-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="0e1d8-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e1d8-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0e1d8-108">Child Elements</span></span>  
  
|<span data-ttu-id="0e1d8-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e1d8-109">Element</span></span>|<span data-ttu-id="0e1d8-110">Description</span><span class="sxs-lookup"><span data-stu-id="0e1d8-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="0e1d8-111">Obsahuje výchozí mapování protokolů mezi schématem transportního protokolu (např. http, NET. TCP, NET. pipe atd.) a vazbou WCF.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-111">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e1d8-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0e1d8-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0e1d8-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e1d8-113">Element</span></span>|<span data-ttu-id="0e1d8-114">Description</span><span class="sxs-lookup"><span data-stu-id="0e1d8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="0e1d8-115">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-115">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e1d8-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e1d8-116">Example</span></span>  
 <span data-ttu-id="0e1d8-117">Následující konfigurační příklad ukazuje výchozí mapování protokolu v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-117">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="0e1d8-118">Toto výchozí mapování na úrovni počítače můžete přepsat úpravou souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-118">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="0e1d8-119">Nebo pokud byste ho chtěli přepsat v rámci rozsahu aplikace, můžete tuto část přepsat v konfiguračním souboru aplikace a změnit mapování pro jednotlivá schémata protokolů.</span><span class="sxs-lookup"><span data-stu-id="0e1d8-119">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e1d8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e1d8-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
