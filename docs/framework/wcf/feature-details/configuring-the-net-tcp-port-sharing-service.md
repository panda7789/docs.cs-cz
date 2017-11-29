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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8b0d1920e70f0d9b6f837800bcc049999f6fde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurace Služby sdílení portů Net.TCP
Samoobslužné hostované služby, které používají přenos Net.TCP můžete řídit několik upřesňujícího nastavení, jako například `ListenBacklog` a `MaxPendingAccepts`, kterými se řídí chování základní soket TCP používá pro síťovou komunikaci. Však tato nastavení pro každou soketu použije pouze na úrovni vazby pokud vazba přenosu zakázal sdílení portů, který je ve výchozím nastavení povolené.  
  
 Když vazbu net.tcp umožňuje sdílení portů (nastavením `portSharingEnabled =true` na element vazby přenosu), umožňuje implicitně externího procesu (konkrétně SMSvcHost.exe, který hostuje službu Sdílení portů Net.TCP) ke správě soketu TCP jeho jménem. Například při použití protokolu TCP, zadejte:  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 Při konfiguraci tímto způsobem, soketu nastaveno na element vazby služby přenosu se ignorují považuje nastavení soketu určeného SMSvcHost.exe.  
  
 Pokud chcete nakonfigurovat SMSvcHost.exe, vytvořte konfigurační soubor XML s názvem konfigurace SmSvcHost.exe.config a umístěte jej ve stejném fyzickém adresáři jako spustitelný soubor SMSvcHost.exe (například C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Následující příklad ilustruje ukázka konfigurace SMSvcHost.exe.config, výchozí nastavení pro všechny konfigurovatelné hodnoty výslovně uvedeny.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Když k úpravě konfigurace SMSvcHost.exe.config  
 Obecně platí potřeba dát pozor při změně obsahu soubor konfigurace SMSvcHost.exe.config, protože všechna nastavení zadané v tomto souboru vliv na všechny služby v počítači, který používá služba Net.TCP Port Sharing. To zahrnuje aplikace na [!INCLUDE[wv](../../../../includes/wv-md.md)] používající Aktivace protokolem TCP funkce služby pro aktivace procesů systému Windows (WAS).  
  
 Ale někdy může musíte změnit výchozí konfiguraci služby Sdílení portů Net.TCP. Například výchozí hodnota pro `maxPendingAccepts` je 4 * počet procesorů. Servery, které jsou hostiteli velký počet služeb, které používají sdílení portů může zvýšit tato hodnota k dosažení maximální propustnost. Výchozí hodnota pro `maxPendingConnections` je 100. Měli byste zvážit také zvýšení hodnoty tuto, pokud existuje více souběžných klientů volání služby a služby zahazuje připojení klientů.  
  
 Konfigurace SMSvcHost.exe.config také obsahuje informace o proces, který identity, které může být pomocí služby Sdílení portů. Když se tento proces se připojí k služby nutné používat sdílené TCP sdílení portů port, připojení identity procesu proces bude zkontrolován, seznam identit, které jsou povoleny, aby použití služby Sdílení portů. Tyto identity jsou určené jako identifikátory zabezpečení (SID) v \<allowAccounts > v souboru konfigurace SMSvcHost.exe.config. Ve výchozím nastavení oprávnění k používání služby Sdílení portů oprávnění k účtům systému (LocalService, LocalSystem a NetworkService) a také členové skupiny Administrators. Aplikace, které umožňují proces, který běží jako jiný identity (například identitu uživatele) pro připojení k služby Sdílení portů musíte explicitně přidat odpovídající SID konfigurace SMSvcHost.exe.config (tyto změny nebudou použity, dokud je proces SMSvc.exe restartovat).  
  
> [!NOTE]
>  Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systémy s řízení uživatelských účtů (UAC) povoleno, místní uživatelé vyžadují vyšší oprávnění, i když jejich účet je členem skupiny Administrators. Povolit tyto uživatele, aby použití služby bez zvýšení oprávnění, identifikátor SID uživatele (nebo identifikátor SID skupiny, ve které je uživatel členem) sdílení portů musí být explicitně přidán do \<allowAccounts > část konfigurace SMSvcHost.exe.config.  
  
> [!WARNING]
>  Výchozí konfigurace SMSvcHost.exe.config soubor Určuje vlastní `etwProviderId` aby SMSvcHost.exe trasování zasahování trasování služby.  
  
## <a name="see-also"></a>Viz také  
 [\<NET.TCP >](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
