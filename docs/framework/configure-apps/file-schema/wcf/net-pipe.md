---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397716"
---
# <a name="netpipe"></a><span data-ttu-id="4d977-102">\<> NET. pipe</span><span class="sxs-lookup"><span data-stu-id="4d977-102">\<net.pipe></span></span>
<span data-ttu-id="4d977-103">Určuje nastavení konfigurace pro aktivační službu pojmenovaného kanálu, která spravuje životnost připojení pojmenovaného kanálu a zpracovává požadavky na aktivaci přicházející přes pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="4d977-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
<span data-ttu-id="4d977-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4d977-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4d977-105">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="4d977-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="4d977-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> NET. pipe**</span><span class="sxs-lookup"><span data-stu-id="4d977-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d977-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d977-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="4d977-108">type</span><span class="sxs-lookup"><span data-stu-id="4d977-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d977-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d977-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d977-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d977-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d977-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d977-111">Attributes</span></span>  
  
|<span data-ttu-id="4d977-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4d977-112">Attribute</span></span>|<span data-ttu-id="4d977-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4d977-113">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="4d977-114">Celé číslo, které určuje maximální počet nedokončených souběžných přijímajících vláken na koncovém bodu naslouchání pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="4d977-114">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="4d977-115">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="4d977-115">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="4d977-116">Celé číslo, které určuje maximální počet připojení, které mohou čekat na odeslání.</span><span class="sxs-lookup"><span data-stu-id="4d977-116">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="4d977-117">Výchozí hodnota je 100.</span><span class="sxs-lookup"><span data-stu-id="4d977-117">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4d977-118">A <xref:System.TimeSpan> určuje časový limit pro čtení dat rámců a provádění odesílání připojení z připojení s podtržením.</span><span class="sxs-lookup"><span data-stu-id="4d977-118">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="4d977-119">Výchozí hodnota je "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="4d977-119">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d977-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d977-120">Child Elements</span></span>  
  
|<span data-ttu-id="4d977-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d977-121">Element</span></span>|<span data-ttu-id="4d977-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4d977-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d977-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="4d977-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="4d977-124">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="4d977-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d977-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d977-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4d977-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d977-126">Element</span></span>|<span data-ttu-id="4d977-127">Popis</span><span class="sxs-lookup"><span data-stu-id="4d977-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d977-128">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="4d977-128">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="4d977-129">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="4d977-129">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d977-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d977-130">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
