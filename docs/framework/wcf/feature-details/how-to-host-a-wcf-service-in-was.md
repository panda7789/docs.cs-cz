---
title: 'Postupy: Hostování služby WCF ve WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 9945e398bbd33776cce808b44388a4415da297a1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964775"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Postupy: Hostování služby WCF ve WAS
Toto téma popisuje základní kroky potřebné k vytvoření služby Aktivace procesů systému Windows (označované také jako) hostované služby Windows Communication Foundation (WCF). BYLA Nová aktivační služba procesů, která je generalizací funkcí služby Internetová informační služba (IIS), které fungují s protokoly přenosů bez protokolu HTTP. Služba WCF používá rozhraní naslouchacího adaptéru ke komunikaci s požadavky na aktivaci, které jsou přijímány prostřednictvím protokolů jiných než HTTP podporovaných službou WCF, jako je například TCP, pojmenované kanály a služba Řízení front zpráv.  
  
 Tato možnost hostování vyžaduje, aby byly aktivační komponenty správně nainstalované a nakonfigurované, ale nevyžadují, aby se v rámci aplikace napsal žádný hostující kód. Další informace o instalaci a konfiguraci nástroje najdete v tématu [Postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
> Aktivace byla Nepodporovaná, pokud je kanál pro zpracování požadavků webového serveru nastavený na klasický režim. Pokud byla použita aktivace, musí být kanál zpracování požadavků webového serveru nastaven na integrovaný režim.  
  
 Když je služba WCF hostována v nástroji, používají se standardní vazby obvyklým způsobem. Při použití <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> ke konfiguraci služby, která byla hostovaná, ale musí být splněno omezení. Pokud různé koncové body používají stejný přenos, nastavení vazby musí odpovídat následující sedm vlastností:  
  
- connectionBufferSize  
  
- channelInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- ConnectionPoolSettings.IdleTimeout  
  
- ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 V opačném případě bude koncový bod, který se inicializuje jako první, určit hodnoty těchto vlastností a koncové body přidané později vyvolají <xref:System.ServiceModel.ServiceActivationException>, pokud se neshodují s těmito nastaveními.  
  
 Zdrojovou kopii tohoto příkladu najdete v tématu [Aktivace protokolem TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Vytvoření základní služby hostované nástrojem WAS  
  
1. Definujte kontrakt služby pro typ služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Implementujte kontrakt služby ve třídě služby. Všimněte si, že v rámci implementace služby není zadaná adresa nebo informace o vazbě. Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Vytvořte soubor Web. config a definujte <xref:System.ServiceModel.NetTcpBinding> vazby, které budou použity koncovými body `CalculatorService`.  
  
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
  
4. Vytvořte soubor Service. svc, který obsahuje následující kód.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Umístěte soubor Service. svc do virtuálního adresáře služby IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Vytvoření klienta pro používání služby  
  
1. K vygenerování kódu z metadat služby použijte [Nástroj Svcutil. exe (s metadaty ServiceModel)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Vygenerovaný klient obsahuje rozhraní `ICalculator` definující kontrakt služby, který musí implementace klienta splňovat.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Vygenerovaná klientská aplikace obsahuje také implementaci `ClientCalculator`. Všimněte si, že informace o adrese a vazbě nejsou zadány kamkoli v rámci implementace služby. Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Konfigurace klienta, který používá <xref:System.ServiceModel.NetTcpBinding>, je vygenerována také nástrojem Svcutil. exe. Tento soubor by měl být pojmenován v souboru App. config při použití sady Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. Vytvořte v aplikaci instanci `ClientCalculator` a potom zavolejte operace služby.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také:

- [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
