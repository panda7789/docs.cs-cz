---
title: "Zabezpečení přenosu pomocí ověřování systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 68550646f806b30f072b4270a336698011db54d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-with-windows-authentication"></a>Zabezpečení přenosu pomocí ověřování systému Windows
Následující scénář ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby Zabezpečené zabezpečení systému Windows. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]programování, najdete v části [postupy: zabezpečení služby s pověřeními Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
 Intranet webové služby zobrazí informace lidských zdrojů. Klient je aplikace formuláře Windows. Aplikace je nasazená v doméně pomocí protokolu Kerberos řadiče domény zabezpečení.  
  
 ![Zabezpečení pomocí ověřování systému Windows Transport](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")  
  
|Vlastnosti|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení.|Přenos|  
|Interoperabilita|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]pouze|  
|Ověřování (Server)<br /><br /> Ověřování (klient)|Ano (pomocí integrovaného ověřování systému Windows)<br /><br /> Ano (pomocí integrovaného ověřování systému Windows)|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|NET. TCP|  
|Vazba|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určená ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.  
  
-   Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení systému Windows.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Konfigurace  
 Místo kód nastavit koncový bod služby lze použít následující konfigurace:  
  
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
 Následující kód a konfigurace jsou určená ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvořte samostatnou klienta pomocí kódu (a kód klienta).  
  
-   Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace. Příklad:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód vytvoří klienta. Vazba je nakonfigurována pro použití režimu zabezpečení přenosu, s přenos TCP, s typu pověření klienta, který je nastaven na hodnotu Windows.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace můžete použít místo kód pro vytvoření klienta.  
  
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
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Postupy: zabezpečení služby pomocí pověření systému Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
