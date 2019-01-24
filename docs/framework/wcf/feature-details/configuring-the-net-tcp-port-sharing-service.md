---
title: Konfigurace Služby sdílení portů Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 9bc625f9e998f27b6227a5951f11c7d85220ae7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585520"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="17d93-102">Konfigurace Služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="17d93-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="17d93-103">Několik upřesňující nastavení, můžete řídit, jako v místním prostředí služby, které používají přenos Net.TCP `ListenBacklog` a `MaxPendingAccepts`, které řídí chování základní soket TCP používá pro síťovou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="17d93-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="17d93-104">Však tato nastavení pro každý soket použije pouze na úrovni vazby Pokud vazby přenosu se vypne sdílení portů, která je ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="17d93-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="17d93-105">Když net.tcp vazba umožňuje sdílení portů (nastavením `portSharingEnabled =true` na element vazby přenosu), umožňuje implicitně externího procesu (konkrétně SMSvcHost.exe, který je hostitelem služby Sdílení portů Net.TCP) ke správě soket TCP svým jménem.</span><span class="sxs-lookup"><span data-stu-id="17d93-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="17d93-106">Například při použití protokolu TCP, zadejte:</span><span class="sxs-lookup"><span data-stu-id="17d93-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="17d93-107">Při konfiguraci tímto způsobem, jsou soketu nastavené na element vazby přenosu služby ignorovat ve prospěch soketu nastavení určené SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="17d93-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="17d93-108">Pokud chcete nakonfigurovat SMSvcHost.exe, vytvořte konfigurační soubor XML s názvem konfigurace SmSvcHost.exe.config a umístěte jej ve stejném fyzickém adresáři jako spustitelný soubor SMSvcHost.exe (například C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="17d93-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="17d93-109">Následující příklad ukazuje příklad konfigurace SMSvcHost.exe.config, s výchozí nastavení pro všechny konfigurovatelné hodnoty explicitně nastavená.</span><span class="sxs-lookup"><span data-stu-id="17d93-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!--16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!--30 seconds -->  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="17d93-110">Kdy k úpravě konfigurace SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="17d93-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="17d93-111">Obecně platí je třeba při úpravě obsahu souboru konfigurace SMSvcHost.exe.config, protože nějaká nastavení zadaná v tomto souboru vliv na všechny služby v počítači, který používá služba Sdílení portů Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="17d93-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="17d93-112">To zahrnuje i aplikace na [!INCLUDE[wv](../../../../includes/wv-md.md)] , které používají funkce Aktivace protokolem TCP služby pro aktivace procesů Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="17d93-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="17d93-113">Nicméně v některých případech budete muset změnit výchozí konfigurace služby Sdílení portů Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="17d93-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="17d93-114">Například výchozí hodnota pro `maxPendingAccepts` je 4 \* počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="17d93-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="17d93-115">Tuto hodnotu k dosažení maximální propustnost může zvýšit servery, které hostují velké množství služeb, které používají sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="17d93-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="17d93-116">Výchozí hodnota pro `maxPendingConnections` je 100.</span><span class="sxs-lookup"><span data-stu-id="17d93-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="17d93-117">Měli byste zvážit také zvýšení této hodnoty, pokud existuje více souběžných klientů volání služby a služby se vyřadit připojení klientů.</span><span class="sxs-lookup"><span data-stu-id="17d93-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="17d93-118">Konfigurace SMSvcHost.exe.config také obsahuje informace o procesu, který identity, které mohou používat služby Sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="17d93-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="17d93-119">Při procesu je připojen k portu služby k využití sdílené TCP sdílení portu, identitu procesu připojení procesu bude zkontrolován, seznam identit, které jsou povoleny, aby využívání služby Sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="17d93-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="17d93-120">Tyto identity jsou určené jako identifikátory zabezpečení (SID) v \<allowAccounts > část souboru konfigurace SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="17d93-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="17d93-121">Ve výchozím nastavení jsou udělena oprávnění k používání služby Sdílení portů u systémových účtů (LocalService, LocalSystem nebo NetworkService) a také členy skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="17d93-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="17d93-122">Aplikace, které umožní procesu spuštěnému jako jiný identity (třeba identitu uživatele) pro připojení do služby Sdílení portů musíte explicitně přidat odpovídající identifikátor SID konfigurace SMSvcHost.exe.config (tyto změny se neprojeví až do procesu SMSvc.exe restartovat).</span><span class="sxs-lookup"><span data-stu-id="17d93-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17d93-123">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systémy s řízení uživatelských účtů (UAC), pak se místní uživatelé vyžadují zvýšená oprávnění, i když svůj účet je členem skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="17d93-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="17d93-124">Chcete-li povolit tyto uživatele bude možné provést využívání služby bez zvýšení oprávnění, identifikátor SID uživatele (nebo SID skupiny, ve kterém je uživatel členem) sdílení portů musí být explicitně přidány do \<allowAccounts > oddíl konfigurace SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="17d93-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="17d93-125">Výchozí konfigurace SMSvcHost.exe.config soubor Určuje vlastní `etwProviderId` chcete zakázat SMSvcHost.exe trasování z zasahovala do trasování služby.</span><span class="sxs-lookup"><span data-stu-id="17d93-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d93-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17d93-126">See also</span></span>
- [<span data-ttu-id="17d93-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="17d93-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
