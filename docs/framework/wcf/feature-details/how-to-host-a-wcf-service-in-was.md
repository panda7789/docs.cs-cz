---
title: 'Postupy: Hostování služby WCF ve WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 157c18d1640ccf1a61f871e5e3e9fef70b6a7e79
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039088"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Postupy: Hostování služby WCF ve WAS
Toto téma ukazuje základní kroky potřebné k vytvoření služby Aktivace procesu Windows (WAS) hostovaná služba Windows Communication Foundation (WCF). BYL je nová aktivační služba procesů, který je generalizace funkcí Internetové informační služby (IIS), které pracují s jiným protokolem než HTTP přenosové protokoly. WCF rozhraní adaptér naslouchací proces používá ke komunikaci žádosti o aktivaci, které jsou přijímány prostřednictvím protokolů jiným protokolem než HTTP nepodporuje WCF, jako je například TCP, pojmenované kanály a služby Řízení front zpráv.  
  
 Tato možnost hostování vyžaduje, aby komponenty aktivace WAS správně nainstalován a nakonfigurován, ale nevyžaduje žádné hostování kódu má být zapsán jako součást aplikace. Další informace o instalaci a konfiguraci služby WAS najdete v tématu [jak: Instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
>  BYLA aktivace není podporována, pokud kanál pro zpracování požadavku webový server je nastavená na klasickém režimu. Kanál pro zpracování požadavku webový server musí být nastavena na integrovaný režim, který se má použít při aktivaci WAS.  
  
 Při je hostování služby WCF ve WAS standardní vazby používají obvyklým způsobem. Ale při použití <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> konfigurace WAS hostované služby, musí splňovat omezení. Při různých koncových bodů pomocí stejného dopravy, mají nastavení vazby tak, aby odpovídaly na sedm následující vlastnosti:  
  
- connectionBufferSize  
  
- třídě channelInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- ConnectionPoolSettings.IdleTimeout  
  
- ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 V opačném případě koncového bodu, který je inicializován nejdřív vždy zjistí hodnoty těchto vlastností a vyvolat pozdějším přidání koncových bodů <xref:System.ServiceModel.ServiceActivationException> Pokud shodné nejsou tato nastavení.  
  
 Pro zdrojovou kopii tohoto příkladu, naleznete v tématu [Aktivace protokolem TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Chcete-li vytvořit základní služba hostovaná společností WAS  
  
1. Definování kontraktu služby pro typ služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Implementace kontraktu služby ve třídě služby. Všimněte si, že není adresu nebo vazby informace zadat v rámci implementace služby. Kód také, není nutné zapsat, aby načítal příslušné informace z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Vytvořte soubor Web.config k definování <xref:System.ServiceModel.NetTcpBinding> vazby používané `CalculatorService` koncových bodů.  
  
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
  
4. Vytvořte Service.svc soubor, který obsahuje následující kód.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5. Umístěte soubor Service.svc virtuální adresář služby IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>K vytvoření klienta k používání služby  
  
1. Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Klient, který je generován obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Generovaný klientskou aplikací také obsahuje implementaci `ClientCalculator`. Všimněte si, že informace o adrese a vazby není zadán kdekoli uvnitř implementace služby. Kód také, není nutné zapsat, aby načítal příslušné informace z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Konfigurace pro klienta, který se používá <xref:System.ServiceModel.NetTcpBinding> také vygeneruje Svcutil.exe. Tento soubor by měl mít název v souboru App.config při používání sady Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. Vytvoření instance `ClientCalculator` v aplikaci a pak volání operací služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Kompilace a spuštění klienta.  
  
## <a name="see-also"></a>Viz také:

- [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
