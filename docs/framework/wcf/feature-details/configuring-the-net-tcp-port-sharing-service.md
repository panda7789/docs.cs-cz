---
title: Konfigurace Služby sdílení portů Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 2ff622dc97e63bd0ee10f00c7515692be8df09a1
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837451"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="01970-102">Konfigurace Služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="01970-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="01970-103">Samoobslužné služby, které používají přenos NET. TCP, mohou řídit několik pokročilých nastavení, například `ListenBacklog` a `MaxPendingAccepts`, což řídí chování základního soketu protokolu TCP používaného pro síťovou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="01970-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="01970-104">Nicméně tato nastavení pro každý soket platí jenom na úrovni vazby, pokud přenosová vazba zakázala sdílení portů, což je ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="01970-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="01970-105">Když vazba NET. TCP povolí sdílení portů (nastavením `portSharingEnabled =true` na elementu Transport Socket), implicitně umožňuje externímu procesu (konkrétně SMSvcHost. exe, který hostuje službu sdílení portů Net. TCP) za účelem správy soketu TCP jménem.</span><span class="sxs-lookup"><span data-stu-id="01970-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="01970-106">Pokud například používáte protokol TCP, zadejte:</span><span class="sxs-lookup"><span data-stu-id="01970-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="01970-107">V takovém případě se všechna nastavení soketu zadaná v elementu transportních vazeb služby ignorují ve prospěch nastavení soketu určeného parametrem SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="01970-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="01970-108">Chcete-li nakonfigurovat SMSvcHost. exe, vytvořte konfigurační soubor XML s názvem SmSvcHost. exe. config a umístěte jej do stejného fyzického adresáře jako spustitelný soubor SMSvcHost. exe (například C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="01970-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="01970-109">Následující příklad znázorňuje ukázkový soubor SMSvcHost. exe. config s výchozím nastavením pro všechny konfigurovatelné hodnoty, které jsou uvedeny explicitně.</span><span class="sxs-lookup"><span data-stu-id="01970-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="01970-110">Kdy upravit SMSvcHost. exe. config</span><span class="sxs-lookup"><span data-stu-id="01970-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="01970-111">Obecně platí, že při úpravě obsahu souboru SMSvcHost. exe. config je třeba dbát na to, že všechna nastavení konfigurace zadaná v tomto souboru ovlivňují všechny služby v počítači, který používá službu sdílení portů Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="01970-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="01970-112">To zahrnuje aplikace v systému Windows Vista, které používají funkce aktivace protokolem TCP aktivační služby procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="01970-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="01970-113">Někdy ale možná budete muset změnit výchozí konfiguraci služby sdílení portů Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="01970-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="01970-114">Například výchozí hodnota pro `maxPendingAccepts` je 4 \* počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="01970-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="01970-115">Servery, které hostují velký počet služeb využívajících sdílení portů, můžou tuto hodnotu zvýšit, aby dosáhly maximální propustnosti.</span><span class="sxs-lookup"><span data-stu-id="01970-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="01970-116">Výchozí hodnota pro `maxPendingConnections` je 100.</span><span class="sxs-lookup"><span data-stu-id="01970-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="01970-117">Tuto hodnotu byste měli zvážit také v případě, že existuje více souběžných klientů volajících službu a služba vyřazuje připojení klientů.</span><span class="sxs-lookup"><span data-stu-id="01970-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="01970-118">SMSvcHost. exe. config obsahuje také informace o identitách procesu, které mohou využívat službu sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="01970-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="01970-119">Když se proces připojí ke službě sdílení portů, aby využíval sdílený port TCP, je identita procesu připojujícího se procesu zkontrolována podle seznamu identit, které mají povoleno používat službu sdílení portů.</span><span class="sxs-lookup"><span data-stu-id="01970-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="01970-120">Tyto identity jsou zadané jako identifikátory zabezpečení (SID) v části \<allowAccounts > souboru SMSvcHost. exe. config.</span><span class="sxs-lookup"><span data-stu-id="01970-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="01970-121">Ve výchozím nastavení je oprávnění používat službu sdílení portů uděleno účtům systému (LocalService, LocalSystem a NetworkService) a také členům skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="01970-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="01970-122">Aplikace, které umožňují procesu běžícímu jako jiné identity (například identity uživatele) pro připojení ke službě sdílení portů, musí explicitně přidat odpovídající identifikátor SID do souboru SMSvcHost. exe. config (tyto změny se neprojeví, dokud nebude proces SMSvc. exe restartován).</span><span class="sxs-lookup"><span data-stu-id="01970-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01970-123">V systémech Windows Vista s povolenou službou Řízení uživatelských účtů (UAC) vyžadují místní uživatelé zvýšená oprávnění, i když je jejich účet členem skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="01970-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="01970-124">Pokud chcete, aby tito uživatelé mohli používat službu sdílení portů bez zvýšení oprávnění, je nutné explicitně přidat SID uživatele (nebo identifikátor SID skupiny, ve které je uživatel členem), do \<allowAccounts > oddílu SMSvcHost. exe. config.</span><span class="sxs-lookup"><span data-stu-id="01970-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="01970-125">Výchozí soubor SMSvcHost. exe. config určuje vlastní `etwProviderId`, který zabrání trasování SMSvcHost. exe v konfliktu s trasováním služby.</span><span class="sxs-lookup"><span data-stu-id="01970-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01970-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01970-126">See also</span></span>

- [<span data-ttu-id="01970-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="01970-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
