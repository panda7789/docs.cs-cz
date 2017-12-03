---
title: '&lt;NET.pipe&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 918ee745e12a339b71f228f3f79b366335d7824d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltnetpipegt"></a><span data-ttu-id="8f983-102">&lt;NET.pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="8f983-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="8f983-103">Určuje nastavení konfigurace s názvem kanálu aktivace služby, která spravuje životnost připojení pojmenovaný kanál a zpracovává požadavky na aktivaci, které přicházejí pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="8f983-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="8f983-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="8f983-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="8f983-105">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="8f983-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f983-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f983-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="8f983-107">Typ</span><span class="sxs-lookup"><span data-stu-id="8f983-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f983-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8f983-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8f983-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f983-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f983-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8f983-110">Attributes</span></span>  
  
|<span data-ttu-id="8f983-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8f983-111">Attribute</span></span>|<span data-ttu-id="8f983-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8f983-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="8f983-113">Celé číslo, které určuje maximální počet nezpracovaných souběžných přijímá vláken pro naslouchání koncový bod pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="8f983-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="8f983-114">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="8f983-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="8f983-115">Celé číslo, které určuje maximální počet připojení, která může čekat pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="8f983-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="8f983-116">Výchozí hodnota je 100.</span><span class="sxs-lookup"><span data-stu-id="8f983-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="8f983-117">A `TimeSpan` který určuje časový limit pro čtení dat rámcovacích a provádění připojení odeslání od připojení podtržení.</span><span class="sxs-lookup"><span data-stu-id="8f983-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="8f983-118">Výchozí hodnota je "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="8f983-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f983-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8f983-119">Child Elements</span></span>  
  
|<span data-ttu-id="8f983-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="8f983-120">Element</span></span>|<span data-ttu-id="8f983-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8f983-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f983-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="8f983-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="8f983-123">Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut k určení uživatelských účtů pro procesy, které hostují [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="8f983-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f983-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8f983-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8f983-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="8f983-125">Element</span></span>|<span data-ttu-id="8f983-126">Popis</span><span class="sxs-lookup"><span data-stu-id="8f983-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f983-127">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="8f983-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="8f983-128">Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="8f983-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f983-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f983-129">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
