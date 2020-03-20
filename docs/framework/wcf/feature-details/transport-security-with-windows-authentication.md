---
title: Zabezpečení přenosu pomocí ověřování systému Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: d335cd47de68dccdbb6af7f402d1182fcd811a7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184319"
---
# <a name="transport-security-with-windows-authentication"></a>Zabezpečení přenosu pomocí ověřování systému Windows
Následující scénář ukazuje klienta a služby WCF (Windows Communication Foundation) zabezpečené zabezpečením systému Windows. Další informace o programování naleznete v [tématu How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
 Webová služba intranet zobrazuje informace o lidských zdrojích. Klient je aplikace Windows Form. Aplikace je nasazena v doméně s řadičem Kerberos, který doménu zabezpečuje.  
  
 ![Zabezpečení přenosu pomocí ověřování systému Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Přenos|  
|Vzájemná funkční spolupráce|Pouze WCF|  
|Ověřování (server)<br /><br /> Ověřování (klient)|Ano (pomocí integrovaného ověřování systému Windows)<br /><br /> Ano (pomocí integrovaného ověřování systému Windows)|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|Čisté. Tcp|  
|Vazba|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení systému Windows.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Konfigurace  
 K nastavení koncového bodu služby lze místo kódu použít následující konfiguraci:  
  
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
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvořte samostatného klienta pomocí kódu (a klientského kódu).  
  
- Vytvořte klienta, který nedefinuje žádné adresy koncového bodu. Místo toho použijte konstruktor klienta, který bere název konfigurace jako argument. Například:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>kód  
 Následující kód vytvoří klienta. Vazba je nakonfigurována tak, aby používala zabezpečení režimu přenosu s přenosem TCP s typem pověření klienta nastaveným na systém Windows.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfiguraci lze použít namísto kódu k vytvoření klienta.  
  
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

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
