---
title: Zabezpečení přenosu pomocí ověřování systému Windows
description: Přečtěte si tento scénář, který ukazuje klienta nebo službu WCF zabezpečené zabezpečením systému Windows. V tomto příkladu bude intranetová služba zobrazovat informace o lidských zdrojích.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: b6134d4cbdff0c1adea704a7f3aaff7e40fd75ec
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244761"
---
# <a name="transport-security-with-windows-authentication"></a>Zabezpečení přenosu pomocí ověřování systému Windows
V následujícím scénáři se zobrazuje klient a služba Windows Communication Foundation (WCF) zabezpečené zabezpečením systému Windows. Další informace o programování najdete v tématu [Postup: zabezpečení služby pomocí pověření systému Windows](../how-to-secure-a-service-with-windows-credentials.md).  
  
 Intranetová webová služba zobrazuje informace o lidských zdrojích. Klient je aplikace formuláře Windows. Aplikace je nasazena v doméně s řadičem protokolu Kerberos zabezpečení domény.  
  
 ![Zabezpečení přenosu s ověřováním systému Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|Charakteristika|Description|  
|--------------------|-----------------|  
|Režim zabezpečení|Přenos|  
|Interoperabilita|Pouze WCF|  
|Ověřování (Server)<br /><br /> Ověřování (klient)|Ano (pomocí integrovaného ověřování systému Windows)<br /><br /> Ano (pomocí integrovaného ověřování systému Windows)|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|Pohyby. PROTOKOLU|  
|Vazba|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z následujících akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení systému Windows.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Konfigurace  
 K nastavení koncového bodu služby se dá použít následující konfigurace:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z následujících akcí:  
  
- Vytvořte samostatného klienta pomocí kódu (a kódu klienta).  
  
- Vytvořte klienta, který nedefinuje žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument. Příklad:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód vytvoří klienta. Vazba je nakonfigurovaná tak, aby používala zabezpečení transportního režimu s přenosem TCP s typem přihlašovacích údajů klienta nastaveným na Windows.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfiguraci lze použít místo kódu k vytvoření klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Přehled zabezpečení](security-overview.md)
- [Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows](../how-to-secure-a-service-with-windows-credentials.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
