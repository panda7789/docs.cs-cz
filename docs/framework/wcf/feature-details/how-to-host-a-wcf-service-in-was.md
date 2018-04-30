---
title: 'Postupy: Hostování služby WCF ve WAS'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4613587d829b082ee7182cc32e34d2d2d563241
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Postupy: Hostování služby WCF ve WAS
Toto téma popisuje základní kroky potřebné k vytvořit proces aktivace služby Windows (WAS) hostovaná [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby. BYL je nová služba aktivace procesů, která je generalizace funkcí Internetové informační služby (IIS), které pracují s jiným protokolem než HTTP přenosové protokoly. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá ke komunikaci žádosti o aktivaci, které jsou přijaty prostřednictvím protokolů než HTTP nepodporuje rozhraní adaptér naslouchání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], jako jsou například TCP, pojmenované kanály a služby Řízení front zpráv.  
  
 Tato hostování možnost vyžaduje součásti aktivace WAS správně nainstalován a nakonfigurován, ale nevyžaduje žádné hostování kódu má být zapsán v rámci aplikace. Další informace o instalaci a konfiguraci WAS najdete v tématu [postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
>  BYLA aktivace není podporováno, pokud kanál pro zpracování požadavku webový server je nastaven na klasickém režimu. Kanál pro zpracování požadavku webový server musí být nastavena pro integrovaný režim, pokud je aktivace WAS pro použití.  
  
 Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostována v WAS, se používají standardní vazby obvyklým způsobem. Ale při použití <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> konfigurace WAS hostované služby, je nutné splnit omezení. Když různými koncovými body používají stejné přenos, závazné nastavení se tak, aby odpovídala na sedm následující vlastnosti:  
  
-   ConnectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   maxPendingConnections  
  
-   maxOutputDelay  
  
-   maxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Jinak koncového bodu, který je inicializován nejdřív vždy zjistí hodnoty těchto vlastností a výjimku později přidat koncové body <xref:System.ServiceModel.ServiceActivationException> Pokud tato nastavení nejsou shodné.  
  
 Zdroj kopírování tohoto příkladu, najdete v části [Aktivace protokolem TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Chcete-li vytvořit základní služba hostovaná společností WAS  
  
1.  Definování kontraktu služby pro typ služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  Implementujte kontrakt služby v třídě služby. Všimněte si, že není adresu nebo vazba informace zadat v rámci implementace služby. Kód také nemá k zapsání k načtení těchto informací z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  Vytvořte soubor Web.config k definování <xref:System.ServiceModel.NetTcpBinding> vazby má být používána `CalculatorService` koncové body.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Vytvořte soubor Service.svc, který obsahuje následující kód.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  Umístěte soubor Service.svc virtuální adresáře služby IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Chcete-li vytvořit klienta k využití služby  
  
1.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Obsahuje klienta, který se generuje `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  Generovaného klienta aplikace také obsahuje implementace `ClientCalculator`. Všimněte si, že informace o adrese a vazba není zadán kdekoli uvnitř implementace služby. Kód také nemá k zapsání k načtení těchto informací z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  Konfigurace pro klienta, který používá <xref:System.ServiceModel.NetTcpBinding> je také generován Svcutil.exe. Tento soubor má název v souboru App.config, když pomocí sady Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  Vytvoření instance `ClientCalculator` v aplikaci a pak volání operací služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  Zkompilování a spuštění klienta.  
  
## <a name="see-also"></a>Viz také  
 [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
