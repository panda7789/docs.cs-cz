---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 7d868d84318db8c9fe188293154dc275060a3952
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933186"
---
# <a name="netpipe"></a><span data-ttu-id="29641-102">\<> NET. pipe</span><span class="sxs-lookup"><span data-stu-id="29641-102">\<net.pipe></span></span>
<span data-ttu-id="29641-103">Určuje nastavení konfigurace pro aktivační službu pojmenovaného kanálu, která spravuje životnost připojení pojmenovaného kanálu a zpracovává požadavky na aktivaci přicházející přes pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="29641-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="29641-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="29641-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="29641-105">\<> NET. pipe</span><span class="sxs-lookup"><span data-stu-id="29641-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29641-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29641-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="29641-107">type</span><span class="sxs-lookup"><span data-stu-id="29641-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29641-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29641-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29641-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29641-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29641-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="29641-110">Attributes</span></span>  
  
|<span data-ttu-id="29641-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="29641-111">Attribute</span></span>|<span data-ttu-id="29641-112">Popis</span><span class="sxs-lookup"><span data-stu-id="29641-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="29641-113">Celé číslo, které určuje maximální počet nedokončených souběžných přijímajících vláken na koncovém bodu naslouchání pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="29641-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="29641-114">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="29641-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="29641-115">Celé číslo, které určuje maximální počet připojení, které mohou čekat na odeslání.</span><span class="sxs-lookup"><span data-stu-id="29641-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="29641-116">Výchozí hodnota je 100.</span><span class="sxs-lookup"><span data-stu-id="29641-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="29641-117">A <xref:System.TimeSpan> určuje časový limit pro čtení dat rámců a provádění odesílání připojení z připojení s podtržením.</span><span class="sxs-lookup"><span data-stu-id="29641-117">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="29641-118">Výchozí hodnota je "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="29641-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29641-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29641-119">Child Elements</span></span>  
  
|<span data-ttu-id="29641-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="29641-120">Element</span></span>|<span data-ttu-id="29641-121">Popis</span><span class="sxs-lookup"><span data-stu-id="29641-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29641-122">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="29641-122">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="29641-123">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="29641-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29641-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29641-124">Parent Elements</span></span>  
  
|<span data-ttu-id="29641-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="29641-125">Element</span></span>|<span data-ttu-id="29641-126">Popis</span><span class="sxs-lookup"><span data-stu-id="29641-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29641-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="29641-127">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="29641-128">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="29641-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29641-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29641-129">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
