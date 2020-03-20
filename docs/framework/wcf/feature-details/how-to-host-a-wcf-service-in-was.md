---
title: 'Postupy: Hostování služby WCF ve WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184915"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Postupy: Hostování služby WCF ve WAS
Toto téma popisuje základní kroky potřebné k vytvoření služby aktivace procesů systému Windows (označované také jako SLUŽBA WAS) hostované službou WCF (Windows Communication Foundation). WAS je nová služba aktivace procesů, která je generalizací funkcí Internetové informační služby (IIS), které pracují s přenosovými protokoly bez protokolu HTTP. WCF používá rozhraní adaptéru naslouchacího procesu ke komunikaci požadavků na aktivaci, které jsou přijímány prostřednictvím protokolů bez protokolu HTTP podporovaných protokoly WCF, jako je například TCP, pojmenované kanály a služba Řízení front zpráv.  
  
 Tato možnost hostování vyžaduje, aby byly aktivační součásti služby WAS správně nainstalovány a nakonfigurovány, ale nevyžaduje, aby byl jako součást aplikace zapsán žádný kód pro hostování. Další informace o instalaci a konfiguraci služby WAS naleznete v [tématu Postup: Instalace a konfigurace součástí aktivace WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
> Aktivace služby WAS není podporována, pokud je kanál zpracování požadavků webového serveru nastaven na klasický režim. Kanál zpracování požadavků webového serveru musí být nastaven na integrovaný režim, pokud má být použita aktivace služby WAS.  
  
 Pokud je služba WCF hostována v WAS, standardní vazby se používají obvyklým způsobem. Však při <xref:System.ServiceModel.NetTcpBinding> použití <xref:System.ServiceModel.NetNamedPipeBinding> a konfigurovat službu hostované was, omezení musí být splněna. Pokud různé koncové body používají stejný přenos, nastavení vazby musí odpovídat následujících sedm vlastností:  
  
- ConnectionBufferSize  
  
- ChannelInitializationTimeout  
  
- MaxPendingConnections  
  
- Zpoždění max.4.  
  
- MaxPendingPřijímá  
  
- ConnectionPoolSettings.IdleTimeout  
  
- ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 V opačném případě koncový bod, který je inicializován nejprve vždy určuje <xref:System.ServiceModel.ServiceActivationException> hodnoty těchto vlastností a koncové body přidané později vyvolat, pokud neodpovídají těmto nastavením.  
  
 Zdrojovou kopii tohoto příkladu naleznete v tématu [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Vytvoření základní služby hostované společností WAS  
  
1. Definujte servisní smlouvu pro typ služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Implementujte servisní smlouvu ve třídě služeb. Všimněte si, že adresa nebo informace o vazbě není zadán v rámci provádění služby. Kód také nemusí být zapsán, aby bylo možné načíst tyto informace z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Vytvořte soubor Web.config <xref:System.ServiceModel.NetTcpBinding> a definujte vazbu, kterou mají `CalculatorService` koncové body používat.  
  
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
  
4. Vytvořte soubor Service.svc, který obsahuje následující kód.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Umístěte soubor Service.svc do virtuálního adresáře služby IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Vytvoření klienta pro použití služby  
  
1. Nástroj [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku slouží ke generování kódu z metadat služby.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Klient, který je generován `ICalculator` obsahuje rozhraní, které definuje servisní smlouvy, které implementace klienta musí splňovat.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Vygenerovaná klientská aplikace `ClientCalculator`také obsahuje implementaci . Všimněte si, že adresa a informace o vazbě není zadán nikde uvnitř implementace služby. Kód také nemusí být zapsán, aby bylo možné načíst tyto informace z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Konfigurace pro klienta, <xref:System.ServiceModel.NetTcpBinding> který používá je také generovánsvcutil.exe. Tento soubor by měl být pojmenován v souboru App.config při použití sady Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. Vytvořte instanci v aplikaci `ClientCalculator` a pak volejte operace služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také

- [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
