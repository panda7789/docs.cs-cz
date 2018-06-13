---
title: Zabezpečení zpráv s klientem uživatelského jména
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7bda1bc18e2b5af1365c799c6f2be9d8d220e9ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495129"
---
# <a name="message-security-with-a-user-name-client"></a>Zabezpečení zpráv s klientem uživatelského jména
Následující obrázek znázorňuje služba Windows Communication Foundation (WCF) a klient zabezpečené pomocí zabezpečení na úrovni zpráv. Služba je ověření pomocí certifikátu X.509. Klient se ověří pomocí uživatelského jména a hesla.  
  
 Ukázkovou aplikaci, najdete v části [uživatelské jméno zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 ![Zabezpečení zpráv pomocí uživatelského jména ověřování](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Vlastnosti|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení.|Zpráva|  
|Interoperabilita|Windows Communication Foundation (WCF) pouze|  
|Ověřování (Server)|Počáteční vyjednávání vyžaduje ověření serveru|  
|Ověřování (klient)|Uživatelské jméno a heslo|  
|Integrita|Ano, kontextu sdílené zabezpečení|  
|Důvěrnost|Ano, kontextu sdílené zabezpečení|  
|Přenos|HTTP|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určená ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.  
  
-   Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a>Konfigurace  
 Místo kód se dají použít následující konfigurace:  
  
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
 Následující kód vytvoří klienta. Vazba je režim zabezpečení zpráv a typu pověření klienta nastavena na `UserName`. Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není konfigurovatelné). Kód, který vrátí uživatelské jméno a heslo není tady zobrazit, protože musíte to provést na úrovni aplikace. Například pomocí dialogového okna Windows Forms dotazovat uživatele pro data.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód konfiguruje klienta. Vazba je režim zabezpečení zpráv a typu pověření klienta nastavena na `UserName`. Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není konfigurovatelné).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Zabezpečení zpráv s uživatelským jménem](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
