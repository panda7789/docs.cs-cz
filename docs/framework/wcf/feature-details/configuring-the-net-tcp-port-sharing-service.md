---
title: Konfigurace Služby sdílení portů Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: dbc27f0f15be41c5384d8a1f73f0226c3f0f83ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206808"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurace Služby sdílení portů Net.TCP
Několik upřesňující nastavení, můžete řídit, jako v místním prostředí služby, které používají přenos Net.TCP `ListenBacklog` a `MaxPendingAccepts`, které řídí chování základní soket TCP používá pro síťovou komunikaci. Však tato nastavení pro každý soket použije pouze na úrovni vazby Pokud vazby přenosu se vypne sdílení portů, která je ve výchozím nastavení povolené.  
  
 Když net.tcp vazba umožňuje sdílení portů (nastavením `portSharingEnabled =true` na element vazby přenosu), umožňuje implicitně externího procesu (konkrétně SMSvcHost.exe, který je hostitelem služby Sdílení portů Net.TCP) ke správě soket TCP svým jménem. Například při použití protokolu TCP, zadejte:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Při konfiguraci tímto způsobem, jsou soketu nastavené na element vazby přenosu služby ignorovat ve prospěch soketu nastavení určené SMSvcHost.exe.  
  
 Pokud chcete nakonfigurovat SMSvcHost.exe, vytvořte konfigurační soubor XML s názvem konfigurace SmSvcHost.exe.config a umístěte jej ve stejném fyzickém adresáři jako spustitelný soubor SMSvcHost.exe (například C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Následující příklad ukazuje příklad konfigurace SMSvcHost.exe.config, s výchozí nastavení pro všechny konfigurovatelné hodnoty explicitně nastavená.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Kdy k úpravě konfigurace SMSvcHost.exe.config  
 Obecně platí je třeba při úpravě obsahu souboru konfigurace SMSvcHost.exe.config, protože nějaká nastavení zadaná v tomto souboru vliv na všechny služby v počítači, který používá služba Sdílení portů Net.TCP. To zahrnuje i aplikace na [!INCLUDE[wv](../../../../includes/wv-md.md)] , které používají funkce Aktivace protokolem TCP služby pro aktivace procesů Windows (WAS).  
  
 Nicméně v některých případech budete muset změnit výchozí konfigurace služby Sdílení portů Net.TCP. Například výchozí hodnota pro `maxPendingAccepts` je 4 * počet procesorů. Tuto hodnotu k dosažení maximální propustnost může zvýšit servery, které hostují velké množství služeb, které používají sdílení portů. Výchozí hodnota pro `maxPendingConnections` je 100. Měli byste zvážit také zvýšení této hodnoty, pokud existuje více souběžných klientů volání služby a služby se vyřadit připojení klientů.  
  
 Konfigurace SMSvcHost.exe.config také obsahuje informace o procesu, který identity, které mohou používat služby Sdílení portů. Při procesu je připojen k portu služby k využití sdílené TCP sdílení portu, identitu procesu připojení procesu bude zkontrolován, seznam identit, které jsou povoleny, aby využívání služby Sdílení portů. Tyto identity jsou určené jako identifikátory zabezpečení (SID) v \<allowAccounts > část souboru konfigurace SMSvcHost.exe.config. Ve výchozím nastavení jsou udělena oprávnění k používání služby Sdílení portů u systémových účtů (LocalService, LocalSystem nebo NetworkService) a také členy skupiny Administrators. Aplikace, které umožní procesu spuštěnému jako jiný identity (třeba identitu uživatele) pro připojení do služby Sdílení portů musíte explicitně přidat odpovídající identifikátor SID konfigurace SMSvcHost.exe.config (tyto změny se neprojeví až do procesu SMSvc.exe restartovat).  
  
> [!NOTE]
>  Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systémy s řízení uživatelských účtů (UAC), pak se místní uživatelé vyžadují zvýšená oprávnění, i když svůj účet je členem skupiny Administrators. Chcete-li povolit tyto uživatele bude možné provést využívání služby bez zvýšení oprávnění, identifikátor SID uživatele (nebo SID skupiny, ve kterém je uživatel členem) sdílení portů musí být explicitně přidány do \<allowAccounts > oddíl konfigurace SMSvcHost.exe.config.  
  
> [!WARNING]
>  Výchozí konfigurace SMSvcHost.exe.config soubor Určuje vlastní `etwProviderId` chcete zakázat SMSvcHost.exe trasování z zasahovala do trasování služby.  
  
## <a name="see-also"></a>Viz také:

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
