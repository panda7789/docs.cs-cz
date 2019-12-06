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
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurace Služby sdílení portů Net.TCP
Samoobslužné služby, které používají přenos NET. TCP, mohou řídit několik pokročilých nastavení, například `ListenBacklog` a `MaxPendingAccepts`, což řídí chování základního soketu protokolu TCP používaného pro síťovou komunikaci. Nicméně tato nastavení pro každý soket platí jenom na úrovni vazby, pokud přenosová vazba zakázala sdílení portů, což je ve výchozím nastavení povolené.  
  
 Když vazba NET. TCP povolí sdílení portů (nastavením `portSharingEnabled =true` na elementu Transport Socket), implicitně umožňuje externímu procesu (konkrétně SMSvcHost. exe, který hostuje službu sdílení portů Net. TCP) za účelem správy soketu TCP jménem. Pokud například používáte protokol TCP, zadejte:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 V takovém případě se všechna nastavení soketu zadaná v elementu transportních vazeb služby ignorují ve prospěch nastavení soketu určeného parametrem SMSvcHost. exe.  
  
 Chcete-li nakonfigurovat SMSvcHost. exe, vytvořte konfigurační soubor XML s názvem SmSvcHost. exe. config a umístěte jej do stejného fyzického adresáře jako spustitelný soubor SMSvcHost. exe (například C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Následující příklad znázorňuje ukázkový soubor SMSvcHost. exe. config s výchozím nastavením pro všechny konfigurovatelné hodnoty, které jsou uvedeny explicitně.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Kdy upravit SMSvcHost. exe. config  
 Obecně platí, že při úpravě obsahu souboru SMSvcHost. exe. config je třeba dbát na to, že všechna nastavení konfigurace zadaná v tomto souboru ovlivňují všechny služby v počítači, který používá službu sdílení portů Net. TCP. To zahrnuje aplikace v systému Windows Vista, které používají funkce aktivace protokolem TCP aktivační služby procesů systému Windows (WAS).  
  
 Někdy ale možná budete muset změnit výchozí konfiguraci služby sdílení portů Net. TCP. Například výchozí hodnota pro `maxPendingAccepts` je 4 * počet procesorů. Servery, které hostují velký počet služeb využívajících sdílení portů, můžou tuto hodnotu zvýšit, aby dosáhly maximální propustnosti. Výchozí hodnota pro `maxPendingConnections` je 100. Tuto hodnotu byste měli zvážit také v případě, že existuje více souběžných klientů volajících službu a služba vyřazuje připojení klientů.  
  
 SMSvcHost. exe. config obsahuje také informace o identitách procesu, které mohou využívat službu sdílení portů. Když se proces připojí ke službě sdílení portů, aby využíval sdílený port TCP, je identita procesu připojujícího se procesu zkontrolována podle seznamu identit, které mají povoleno používat službu sdílení portů. Tyto identity jsou zadané jako identifikátory zabezpečení (SID) v části \<allowAccounts > souboru SMSvcHost. exe. config. Ve výchozím nastavení je oprávnění používat službu sdílení portů uděleno účtům systému (LocalService, LocalSystem a NetworkService) a také členům skupiny Administrators. Aplikace, které umožňují procesu běžícímu jako jiné identity (například identity uživatele) pro připojení ke službě sdílení portů, musí explicitně přidat odpovídající identifikátor SID do souboru SMSvcHost. exe. config (tyto změny se neprojeví, dokud nebude proces SMSvc. exe restartován).  
  
> [!NOTE]
> V systémech Windows Vista s povolenou službou Řízení uživatelských účtů (UAC) vyžadují místní uživatelé zvýšená oprávnění, i když je jejich účet členem skupiny Administrators. Pokud chcete, aby tito uživatelé mohli používat službu sdílení portů bez zvýšení oprávnění, je nutné explicitně přidat SID uživatele (nebo identifikátor SID skupiny, ve které je uživatel členem), do \<allowAccounts > oddílu SMSvcHost. exe. config.  
  
> [!WARNING]
> Výchozí soubor SMSvcHost. exe. config určuje vlastní `etwProviderId`, který zabrání trasování SMSvcHost. exe v konfliktu s trasováním služby.  
  
## <a name="see-also"></a>Viz také:

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
