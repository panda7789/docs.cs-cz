---
title: '&lt;system.serviceModel.activation&gt;'
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: fed7bf41e8c893d10254e09a9733572765ce1661
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146716"
---
# <a name="ltsystemservicemodelactivationgt"></a><span data-ttu-id="1e606-102">&lt;system.serviceModel.activation&gt;</span><span class="sxs-lookup"><span data-stu-id="1e606-102">&lt;system.serviceModel.activation&gt;</span></span>
<span data-ttu-id="1e606-103">Tento konfigurační oddíl představuje nastavení konfigurace pro nástroj SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="1e606-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="1e606-104">Konfigurační prvky můžete nakonfigurovat v souboru konfigurace SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="1e606-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="1e606-105">Konkrétně obsahuje všechna nastavení celý počítač, musí být nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="1e606-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="1e606-106">Ukázkový konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="1e606-106">Sample Configuration File</span></span>  
 <span data-ttu-id="1e606-107">Následuje ukázkový soubor konfigurace (konfigurace SMSvcHost.exe.config), který je používán procesem naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="1e606-107">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>
  <runtime>
    <gcConcurrent enabled="false" />
  </runtime>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="10"
             maxPendingAccepts="2"
             maxPendingConnections="100"
             receiveTimeout="00:00:10"
             teredoEnabled="false">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
    <net.pipe maxConnectionsPendingDispatch="100"
              maxPendingAccepts="2"
              receiveTimeout="00:00:10">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
    <diagnostics performanceCountersEnabled="true" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="1e606-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e606-108">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration>
