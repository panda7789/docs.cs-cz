---
title: Zabezpečení zprávy s klientem Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: dcb311523c6ec41b62f6e69fe6bc7635b9d49708
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595229"
---
# <a name="message-security-with-a-windows-client"></a>Zabezpečení zprávy s klientem Windows
Tento scénář ukazuje klienta služby Windows Communication Foundation (WCF) a server zabezpečený režimem zabezpečení zpráv. Klient a služba jsou ověřovány pomocí pověření systému Windows.  
  
 ![Zabezpečení zpráv pomocí klienta Windows](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Zpráva|  
|Interoperabilita|Pouze WCF|  
|Ověřování (Server)|Vzájemné ověřování serveru a klienta|  
|Ověřování (klient)|Vzájemné ověřování serveru a klienta|  
|Integrita|Ano, použití sdíleného kontextu zabezpečení|  
|Důvěrnost|Ano, použití sdíleného kontextu zabezpečení|  
|Přenos|Pohyby. PROTOKOLU|  
|Vazba|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte některou z následujících akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k navázání zabezpečeného kontextu s počítačem s Windows.  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a>Konfigurace  
 K nastavení služby je možné použít následující konfiguraci:  
  
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
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte některou z následujících akcí:  
  
- Vytvořte samostatného klienta pomocí kódu (a kódu klienta).  
  
- Vytvořte klienta, který nedefinuje žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument. Například:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód vytvoří klienta. Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na hodnotu `Windows` .  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace se používá k nastavení vlastností klienta.  
  
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

- [Přehled zabezpečení](security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
