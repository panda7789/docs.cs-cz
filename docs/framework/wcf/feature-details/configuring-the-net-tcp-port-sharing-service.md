---
title: "Konfigurace Služby sdílení portů Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 942b48ff6887e079beb7c0c24c6542a774eafe33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="d8575-102">Konfigurace Služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d8575-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="d8575-103">Samoobslužné hostované služby, které používají přenos Net.TCP můžete řídit několik upřesňujícího nastavení, jako například `ListenBacklog` a `MaxPendingAccepts`, kterými se řídí chování základní soket TCP používá pro síťovou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d8575-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="d8575-104">Však tato nastavení pro každou soketu použije pouze na úrovni vazby pokud vazba přenosu zakázal sdílení portů, který je ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="d8575-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="d8575-105">Když vazbu net.tcp umožňuje sdílení portů (nastavením `portSharingEnabled =true` na element vazby přenosu), umožňuje implicitně externího procesu (konkrétně SMSvcHost.exe, který hostuje službu Sdílení portů Net.TCP) ke správě soketu TCP jeho jménem.</span><span class="sxs-lookup"><span data-stu-id="d8575-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="d8575-106">Například při použití protokolu TCP, zadejte:</span><span class="sxs-lookup"><span data-stu-id="d8575-106">For example, when using TCP, specify:</span></span>  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 <span data-ttu-id="d8575-107">Při konfiguraci tímto způsobem, soketu nastaveno na element vazby služby přenosu se ignorují považuje nastavení soketu určeného SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="d8575-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="d8575-108">Pokud chcete nakonfigurovat SMSvcHost.exe, vytvořte konfigurační soubor XML s názvem konfigurace SmSvcHost.exe.config a umístěte jej ve stejném fyzickém adresáři jako spustitelný soubor SMSvcHost.exe (například C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="d8575-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="d8575-109">Následující příklad ilustruje ukázka konfigurace SMSvcHost.exe.config, výchozí nastavení pro všechny konfigurovatelné hodnoty výslovně uvedeny.</span><span class="sxs-lookup"><span data-stu-id="d8575-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!—16 * # of processors -->  
          maxPendingAccepts="4"<!— 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!—30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="d8575-110">Když k úpravě konfigurace SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="d8575-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="d8575-111">Obecně platí potřeba dát pozor při změně obsahu soubor konfigurace SMSvcHost.exe.config, protože všechna nastavení zadané v tomto souboru vliv na všechny služby v počítači, který používá služba Net.TCP Port Sharing.</span><span class="sxs-lookup"><span data-stu-id="d8575-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="d8575-112">To zahrnuje aplikace na [!INCLUDE[wv](../../../../includes/wv-md.md)] používající Aktivace protokolem TCP funkce služby pro aktivace procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="d8575-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="d8575-113">Ale někdy může musíte změnit výchozí konfiguraci služby Sdílení portů Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="d8575-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="d8575-114">Například výchozí hodnota pro `maxPendingAccepts` je 4 * počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="d8575-114">For example, the default value for `maxPendingAccepts` is 4 * number of processors.</span></span> <span data-ttu-id="d8575-115">Servery, které jsou hostiteli velký počet služeb, které používají sdílení portů může zvýšit tato hodnota k dosažení maximální propustnost.</span><span class="sxs-lookup"><span data-stu-id="d8575-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="d8575-116">Výchozí hodnota pro `maxPendingConnections` je 100.</span><span class="sxs-lookup"><span data-stu-id="d8575-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="d8575-117">Měli byste zvážit také zvýšení hodnoty tuto, pokud existuje více souběžných klientů volání služby a služby zahazuje připojení klientů.</span><span class="sxs-lookup"><span data-stu-id="d8575-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="d8575-118">Konfigurace SMSvcHost.exe.config také obsahuje informace o proces, který identity, které může být pomocí služby Sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="d8575-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="d8575-119">Když se tento proces se připojí k služby nutné používat sdílené TCP sdílení portů port, připojení identity procesu proces bude zkontrolován, seznam identit, které jsou povoleny, aby použití služby Sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="d8575-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="d8575-120">Tyto identity jsou určené jako identifikátory zabezpečení (SID) v \<allowAccounts > v souboru konfigurace SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d8575-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="d8575-121">Ve výchozím nastavení oprávnění k používání služby Sdílení portů oprávnění k účtům systému (LocalService, LocalSystem a NetworkService) a také členové skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="d8575-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="d8575-122">Aplikace, které umožňují proces, který běží jako jiný identity (například identitu uživatele) pro připojení k služby Sdílení portů musíte explicitně přidat odpovídající SID konfigurace SMSvcHost.exe.config (tyto změny nebudou použity, dokud je proces SMSvc.exe restartovat).</span><span class="sxs-lookup"><span data-stu-id="d8575-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8575-123">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systémy s řízení uživatelských účtů (UAC) povoleno, místní uživatelé vyžadují vyšší oprávnění, i když jejich účet je členem skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="d8575-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="d8575-124">Povolit tyto uživatele, aby použití služby bez zvýšení oprávnění, identifikátor SID uživatele (nebo identifikátor SID skupiny, ve které je uživatel členem) sdílení portů musí být explicitně přidán do \<allowAccounts > část konfigurace SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d8575-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d8575-125">Výchozí konfigurace SMSvcHost.exe.config soubor Určuje vlastní `etwProviderId` aby SMSvcHost.exe trasování zasahování trasování služby.</span><span class="sxs-lookup"><span data-stu-id="d8575-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8575-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8575-126">See Also</span></span>  
 [<span data-ttu-id="d8575-127">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="d8575-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
