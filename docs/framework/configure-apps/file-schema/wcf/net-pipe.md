---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397716"
---
# \<net.pipe>
<span data-ttu-id="a56e2-102">Určuje nastavení konfigurace pro aktivační službu pojmenovaného kanálu, která spravuje životnost připojení pojmenovaného kanálu a zpracovává požadavky na aktivaci přicházející přes pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="a56e2-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="a56e2-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a56e2-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="a56e2-104">Typ</span><span class="sxs-lookup"><span data-stu-id="a56e2-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a56e2-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a56e2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a56e2-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a56e2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a56e2-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a56e2-107">Attributes</span></span>  
  
|<span data-ttu-id="a56e2-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a56e2-108">Attribute</span></span>|<span data-ttu-id="a56e2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a56e2-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="a56e2-110">Celé číslo, které určuje maximální počet nedokončených souběžných přijímajících vláken na koncovém bodu naslouchání pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="a56e2-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="a56e2-111">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="a56e2-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="a56e2-112">Celé číslo, které určuje maximální počet připojení, které mohou čekat na odeslání.</span><span class="sxs-lookup"><span data-stu-id="a56e2-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="a56e2-113">Výchozí hodnota je 100.</span><span class="sxs-lookup"><span data-stu-id="a56e2-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a56e2-114">A <xref:System.TimeSpan> Určuje časový limit pro čtení dat rámců a provádění odesílání připojení z připojení s podtržením.</span><span class="sxs-lookup"><span data-stu-id="a56e2-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="a56e2-115">Výchozí hodnota je "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="a56e2-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a56e2-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a56e2-116">Child Elements</span></span>  
  
|<span data-ttu-id="a56e2-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a56e2-117">Element</span></span>|<span data-ttu-id="a56e2-118">Description</span><span class="sxs-lookup"><span data-stu-id="a56e2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="a56e2-119">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="a56e2-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a56e2-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a56e2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a56e2-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a56e2-121">Element</span></span>|<span data-ttu-id="a56e2-122">Description</span><span class="sxs-lookup"><span data-stu-id="a56e2-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="a56e2-123">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="a56e2-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a56e2-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a56e2-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
