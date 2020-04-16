---
title: Konfigurace Služby sdílení portů Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: fea2e734099c4c623dcde2a37f4c164cf9ce61ac
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464197"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="a66a2-102">Konfigurace Služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="a66a2-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="a66a2-103">Samoobslužné služby, které používají přenos Net.TCP, `ListenBacklog` `MaxPendingAccepts`mohou řídit několik upřesňujících nastavení, například a , které řídí chování podkladového soketu TCP používaného pro síťovou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="a66a2-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="a66a2-104">Tato nastavení pro každý soket však platí pouze na úrovni vazby, pokud je přenosová vazba zakázáno sdílení portů, což je ve výchozím nastavení povoleno.</span><span class="sxs-lookup"><span data-stu-id="a66a2-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="a66a2-105">Pokud vazba net.tcp umožňuje sdílení `portSharingEnabled =true` portů (nastavením prvku vazby přenosu), implicitně umožňuje externímu procesu (konkrétně smsvcHost.exe, který je hostitelem služby Net.TCP Port Sharing Service) spravovat soket TCP jeho jménem.</span><span class="sxs-lookup"><span data-stu-id="a66a2-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="a66a2-106">Například při použití protokolu TCP zadejte:</span><span class="sxs-lookup"><span data-stu-id="a66a2-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="a66a2-107">Při konfiguraci tímto způsobem jsou všechna nastavení soketu zadaná na prvku transportní vazby služby ignorována ve prospěch nastavení soketu určeného smsvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="a66a2-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="a66a2-108">Chcete-li nakonfigurovat soubor SMSvcHost.exe, vytvořte konfigurační soubor XML s názvem SmSvcHost.exe.config a umístěte jej do stejného fyzického adresáře jako spustitelný soubor SMSvcHost.exe (například C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="a66a2-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="a66a2-109">Následující příklad ilustruje ukázku smsvcHost.exe.config, s výchozím nastavením pro všechny konfigurovatelné hodnoty explicitně.</span><span class="sxs-lookup"><span data-stu-id="a66a2-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
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
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="a66a2-110">Kdy změnit soubor SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="a66a2-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="a66a2-111">Obecně je třeba dbát na to, aby při úpravě obsahu souboru SMSvcHost.exe.config byla věnována pozornost, protože všechna nastavení konfigurace zadaná v tomto souboru ovlivňují všechny služby v počítači, který používá službu Sdílení portů Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="a66a2-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="a66a2-112">To zahrnuje aplikace v systému Windows Vista, které používají funkce aktivace protokolu TCP služby aktivace procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="a66a2-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="a66a2-113">Někdy však může být nutné změnit výchozí konfiguraci služby Sdílení portů Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="a66a2-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="a66a2-114">Například výchozí hodnota `maxPendingAccepts` pro je 4 \* počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="a66a2-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="a66a2-115">Servery, které jsou hostiteli velkého počtu služeb, které používají sdílení portů, mohou tuto hodnotu zvýšit, aby bylo dosaženo maximální propustnosti.</span><span class="sxs-lookup"><span data-stu-id="a66a2-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="a66a2-116">Výchozí hodnota `maxPendingConnections` pro je 100.</span><span class="sxs-lookup"><span data-stu-id="a66a2-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="a66a2-117">Měli byste zvážit zvýšení této hodnoty také v případě, že existuje více souběžných klientů volání služby a služba je uvolněním připojení klientů.</span><span class="sxs-lookup"><span data-stu-id="a66a2-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="a66a2-118">SMSvcHost.exe.config také obsahuje informace o identitách procesu, které mohou využívat službu sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="a66a2-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="a66a2-119">Když se proces připojí ke službě sdílení portů za účelem využití sdíleného portu TCP, je identita procesu připojování zkontrolována podle seznamu identit, které mohou využívat službu sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="a66a2-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="a66a2-120">Tyto identity jsou určeny jako identifikátory zabezpečení \<(SID) v části allowAccounts> souboru SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="a66a2-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="a66a2-121">Ve výchozím nastavení je oprávnění k použití služby sdílení portů uděleno systémovým účtům (LocalService, LocalSystem a NetworkService) a také členům skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="a66a2-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="a66a2-122">Aplikace, které umožňují proces spuštěný jako jinou identitu (například identitu uživatele) pro připojení ke službě sdílení portů, musí explicitně přidat příslušný sid do souboru SMSvcHost.exe.config (tyto změny nejsou použity, dokud nebude proces SMSvc.exe restartován).</span><span class="sxs-lookup"><span data-stu-id="a66a2-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a66a2-123">V systémech Windows Vista s povolenou kontrolou uživatelských účtů (UAC) vyžadují místní uživatelé zvýšená oprávnění i v případě, že jejich účet je členem skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="a66a2-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="a66a2-124">Chcete-li povolit těmto uživatelům využívat službu sdílení portů bez zvýšení oprávnění, musí být sid uživatele (nebo SID \<skupiny, ve které je uživatel členem) explicitně přidán do sekce allowAccounts> smsvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="a66a2-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a66a2-125">Výchozí soubor SMSvcHost.exe.config určuje `etwProviderId` vlastní, aby se zabránilo trasování SMSvcHost.exe v zasahování do trasování služby.</span><span class="sxs-lookup"><span data-stu-id="a66a2-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66a2-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a66a2-126">See also</span></span>

- [<span data-ttu-id="a66a2-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="a66a2-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
