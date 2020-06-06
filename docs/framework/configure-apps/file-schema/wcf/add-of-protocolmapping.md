---
title: <add> z <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850375"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="17622-102">\<add> z \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="17622-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="17622-103">Představuje výchozí mapování protokolů mezi schématem transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a vazbou Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="17622-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="17622-104">Při vytváření výchozích koncových bodů za běhu vyhledá WCF nakonfigurované mapování a rozhodne, které vazby použít pro konkrétní adresu založenou na.</span><span class="sxs-lookup"><span data-stu-id="17622-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="17622-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17622-105">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17622-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="17622-106">Attributes and Elements</span></span>  
 <span data-ttu-id="17622-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="17622-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17622-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="17622-108">Attributes</span></span>  
  
|<span data-ttu-id="17622-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="17622-109">Element</span></span>|<span data-ttu-id="17622-110">Description</span><span class="sxs-lookup"><span data-stu-id="17622-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17622-111">vazba</span><span class="sxs-lookup"><span data-stu-id="17622-111">binding</span></span>|<span data-ttu-id="17622-112">Řetězec, který určuje typ vazby, která se má použít pro koncový bod při vytváření výchozího koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="17622-112">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="17622-113">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="17622-113">bindingConfiguration</span></span>|<span data-ttu-id="17622-114">Řetězec, který určuje název konfiguračního oddílu vazby, na který se má odkazovat.</span><span class="sxs-lookup"><span data-stu-id="17622-114">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="17622-115">scheme</span><span class="sxs-lookup"><span data-stu-id="17622-115">scheme</span></span>|<span data-ttu-id="17622-116">Schéma přenosového protokolu, které se má použít pro výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="17622-116">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17622-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="17622-117">Child Elements</span></span>  
 <span data-ttu-id="17622-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="17622-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17622-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="17622-119">Parent Elements</span></span>  
  
|<span data-ttu-id="17622-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="17622-120">Element</span></span>|<span data-ttu-id="17622-121">Description</span><span class="sxs-lookup"><span data-stu-id="17622-121">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="17622-122">Představuje konfigurační oddíl pro definování výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a Windows Communication Foundation (WCF) vazby.</span><span class="sxs-lookup"><span data-stu-id="17622-122">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17622-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="17622-123">Example</span></span>  
 <span data-ttu-id="17622-124">Následující konfigurační příklad ukazuje výchozí mapování protokolu v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="17622-124">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="17622-125">Toto výchozí mapování na úrovni počítače můžete přepsat úpravou souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="17622-125">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="17622-126">Nebo pokud byste ho chtěli přepsat v rámci rozsahu aplikace, můžete tuto část přepsat v konfiguračním souboru aplikace a změnit mapování pro jednotlivá schémata protokolů.</span><span class="sxs-lookup"><span data-stu-id="17622-126">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17622-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="17622-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
