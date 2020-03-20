---
title: Zabezpečení zprávy s klientem Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: bcfeb5f863b1dd6cf9171a7fc53c8984ea68ecb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184619"
---
# <a name="message-security-with-a-windows-client"></a>Zabezpečení zprávy s klientem Windows
Tento scénář zobrazuje klienta a serveru WCF (Windows Communication Foundation) zabezpečeného režimem zabezpečení zpráv. Klient a služba jsou ověřovány pomocí pověření systému Windows.  
  
 ![Zabezpečení zpráv s klientem systému Windows](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Zpráva|  
|Vzájemná funkční spolupráce|Pouze WCF|  
|Ověřování (server)|Vzájemné ověřování serveru a klienta|  
|Ověřování (klient)|Vzájemné ověřování serveru a klienta|  
|Integrita|Ano, použití kontextu sdíleného zabezpečení|  
|Důvěrnost|Ano, použití kontextu sdíleného zabezpečení|  
|Přenos|Čisté. Tcp|  
|Vazba|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k vytvoření zabezpečeného kontextu s počítačem se systémem Windows.  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a>Konfigurace  
 K nastavení služby lze místo kódu použít následující konfiguraci:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
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
 Následující kód vytvoří klienta. Vazba je zabezpečení režimu zprávy a typ `Windows`pověření klienta je nastavena na .  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace slouží k nastavení vlastností klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"
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
- [Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
