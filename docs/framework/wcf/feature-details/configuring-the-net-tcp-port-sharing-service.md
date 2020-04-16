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
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurace Služby sdílení portů Net.TCP
Samoobslužné služby, které používají přenos Net.TCP, `ListenBacklog` `MaxPendingAccepts`mohou řídit několik upřesňujících nastavení, například a , které řídí chování podkladového soketu TCP používaného pro síťovou komunikaci. Tato nastavení pro každý soket však platí pouze na úrovni vazby, pokud je přenosová vazba zakázáno sdílení portů, což je ve výchozím nastavení povoleno.  
  
 Pokud vazba net.tcp umožňuje sdílení `portSharingEnabled =true` portů (nastavením prvku vazby přenosu), implicitně umožňuje externímu procesu (konkrétně smsvcHost.exe, který je hostitelem služby Net.TCP Port Sharing Service) spravovat soket TCP jeho jménem. Například při použití protokolu TCP zadejte:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Při konfiguraci tímto způsobem jsou všechna nastavení soketu zadaná na prvku transportní vazby služby ignorována ve prospěch nastavení soketu určeného smsvcHost.exe.  
  
 Chcete-li nakonfigurovat soubor SMSvcHost.exe, vytvořte konfigurační soubor XML s názvem SmSvcHost.exe.config a umístěte jej do stejného fyzického adresáře jako spustitelný soubor SMSvcHost.exe (například C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Následující příklad ilustruje ukázku smsvcHost.exe.config, s výchozím nastavením pro všechny konfigurovatelné hodnoty explicitně.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Kdy změnit soubor SMSvcHost.exe.config  
 Obecně je třeba dbát na to, aby při úpravě obsahu souboru SMSvcHost.exe.config byla věnována pozornost, protože všechna nastavení konfigurace zadaná v tomto souboru ovlivňují všechny služby v počítači, který používá službu Sdílení portů Net.TCP. To zahrnuje aplikace v systému Windows Vista, které používají funkce aktivace protokolu TCP služby aktivace procesů systému Windows (WAS).  
  
 Někdy však může být nutné změnit výchozí konfiguraci služby Sdílení portů Net.TCP. Například výchozí hodnota `maxPendingAccepts` pro je 4 * počet procesorů. Servery, které jsou hostiteli velkého počtu služeb, které používají sdílení portů, mohou tuto hodnotu zvýšit, aby bylo dosaženo maximální propustnosti. Výchozí hodnota `maxPendingConnections` pro je 100. Měli byste zvážit zvýšení této hodnoty také v případě, že existuje více souběžných klientů volání služby a služba je uvolněním připojení klientů.  
  
 SMSvcHost.exe.config také obsahuje informace o identitách procesu, které mohou využívat službu sdílení portů. Když se proces připojí ke službě sdílení portů za účelem využití sdíleného portu TCP, je identita procesu připojování zkontrolována podle seznamu identit, které mohou využívat službu sdílení portů. Tyto identity jsou určeny jako identifikátory zabezpečení \<(SID) v části allowAccounts> souboru SMSvcHost.exe.config. Ve výchozím nastavení je oprávnění k použití služby sdílení portů uděleno systémovým účtům (LocalService, LocalSystem a NetworkService) a také členům skupiny Administrators. Aplikace, které umožňují proces spuštěný jako jinou identitu (například identitu uživatele) pro připojení ke službě sdílení portů, musí explicitně přidat příslušný sid do souboru SMSvcHost.exe.config (tyto změny nejsou použity, dokud nebude proces SMSvc.exe restartován).  
  
> [!NOTE]
> V systémech Windows Vista s povolenou kontrolou uživatelských účtů (UAC) vyžadují místní uživatelé zvýšená oprávnění i v případě, že jejich účet je členem skupiny Administrators. Chcete-li povolit těmto uživatelům využívat službu sdílení portů bez zvýšení oprávnění, musí být sid uživatele (nebo SID \<skupiny, ve které je uživatel členem) explicitně přidán do sekce allowAccounts> smsvcHost.exe.config.  
  
> [!WARNING]
> Výchozí soubor SMSvcHost.exe.config určuje `etwProviderId` vlastní, aby se zabránilo trasování SMSvcHost.exe v zasahování do trasování služby.  
  
## <a name="see-also"></a>Viz také

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
