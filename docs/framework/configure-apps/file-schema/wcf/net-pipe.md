---
title: < net.pipe >
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: ddd25d3d25f4c4be1a9e26d444fa799a55c9cccc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283280"
---
# <a name="netpipe"></a><span data-ttu-id="86d32-102">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="86d32-102">\<net.pipe></span></span>
<span data-ttu-id="86d32-103">Určuje nastavení konfigurace služby Aktivace pojmenovaných kanálů, která spravuje životnost připojení pojmenovaného kanálu a zpracovává požadavky na aktivaci přicházející přes pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="86d32-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="86d32-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="86d32-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="86d32-105">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="86d32-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d32-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86d32-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="86d32-107">Typ</span><span class="sxs-lookup"><span data-stu-id="86d32-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86d32-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="86d32-108">Attributes and Elements</span></span>  
 <span data-ttu-id="86d32-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="86d32-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86d32-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="86d32-110">Attributes</span></span>  
  
|<span data-ttu-id="86d32-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="86d32-111">Attribute</span></span>|<span data-ttu-id="86d32-112">Popis</span><span class="sxs-lookup"><span data-stu-id="86d32-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="86d32-113">Celé číslo, které určuje maximální počet souběžně otevřených přijímacích vláken na koncový bod naslouchací služby pro sdílení.</span><span class="sxs-lookup"><span data-stu-id="86d32-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="86d32-114">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="86d32-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="86d32-115">Celé číslo určující maximální počet připojení, které mohou čekat na odeslání.</span><span class="sxs-lookup"><span data-stu-id="86d32-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="86d32-116">Výchozí hodnota je 100.</span><span class="sxs-lookup"><span data-stu-id="86d32-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="86d32-117">A `TimeSpan` , který určuje časový limit pro vytváření datových rámců a jejich odesílání z přidružených připojení.</span><span class="sxs-lookup"><span data-stu-id="86d32-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="86d32-118">Výchozí hodnota je "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="86d32-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86d32-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="86d32-119">Child Elements</span></span>  
  
|<span data-ttu-id="86d32-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="86d32-120">Element</span></span>|<span data-ttu-id="86d32-121">Popis</span><span class="sxs-lookup"><span data-stu-id="86d32-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86d32-122">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="86d32-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="86d32-123">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atributy uživatelské účty pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="86d32-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86d32-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="86d32-124">Parent Elements</span></span>  
  
|<span data-ttu-id="86d32-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="86d32-125">Element</span></span>|<span data-ttu-id="86d32-126">Popis</span><span class="sxs-lookup"><span data-stu-id="86d32-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86d32-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="86d32-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="86d32-128">Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="86d32-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86d32-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86d32-129">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
