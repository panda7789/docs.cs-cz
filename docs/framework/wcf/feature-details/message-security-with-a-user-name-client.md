---
title: Zabezpečení zpráv s klientem uživatelského jména
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 547c23509096b66c1fdbd46117a10f4de1692387
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212050"
---
# <a name="message-security-with-a-user-name-client"></a>Zabezpečení zpráv s klientem uživatelského jména
Následující ilustrace znázorňuje službu Windows Communication Foundation (WCF) a klienta zabezpečenou pomocí zabezpečení na úrovni zprávy. Služba se ověřuje pomocí certifikátu X. 509. Klient se ověřuje pomocí uživatelského jména a hesla.  
  
 Ukázkovou aplikaci najdete v tématu [zabezpečení zpráv – uživatelské jméno](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 ![Zabezpečení zpráv pomocí ověřování uživatelského jména](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Zpráva|  
|Interoperabilita|Pouze Windows Communication Foundation (WCF)|  
|Ověřování (Server)|Počáteční vyjednávání vyžaduje ověření serveru.|  
|Ověřování (klient)|Uživatelské jméno a heslo|  
|Integrita|Ano, použití sdíleného kontextu zabezpečení|  
|Důvěrnost|Ano, použití sdíleného kontextu zabezpečení|  
|Doprava|HTTP|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Service  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a>Konfigurace  
 Místo kódu lze použít následující konfiguraci:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"     
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">              
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
  
### <a name="code"></a>Kód  
 Následující kód vytvoří klienta. Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na `UserName`. Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není možné je konfigurovat). Kód pro vrácení uživatelského jména a hesla zde není zobrazen, protože musí být proveden na úrovni aplikace. Můžete například použít dialogové okno model Windows Forms k dotazování uživatele na data.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód nakonfiguruje klienta. Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na `UserName`. Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není možné je konfigurovat).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Zabezpečení zpráv s uživatelským jménem](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
