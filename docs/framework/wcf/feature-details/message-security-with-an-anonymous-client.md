---
title: Zabezpečení zpráv s anonymním klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b8cab1762a8c8c672d557c7bcccc2f339cbaefe9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495051"
---
# <a name="message-security-with-an-anonymous-client"></a>Zabezpečení zpráv s anonymním klientem
Následující příklad ukazuje klienta a služby Zabezpečené zabezpečení zpráv Windows Communication Foundation (WCF). Návrh cílem je používat zabezpečení zpráv, nikoli zabezpečení přenosu, tak, aby v budoucnu může podporovat model bohatší založené na deklaracích identity. Další informace o použití bohaté deklarací identity pro ověřování najdete v tématu [správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Ukázkovou aplikaci, najdete v části [zpráva zabezpečení anonymní](../../../../docs/framework/wcf/samples/message-security-anonymous.md).  
  
 ![Zpráva zabezpečení s klientem anynymous](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")  
  
|Vlastnosti|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení.|Zpráva|  
|Interoperabilita|Pouze WCF|  
|Ověřování (Server)|Počáteční vyjednávání vyžaduje ověřování serveru, ale není ověření klienta|  
|Ověřování (klient)|Žádné|  
|Integrita|Ano, kontextu sdílené zabezpečení|  
|Důvěrnost|Ano, kontextu sdílené zabezpečení|  
|Přenos|HTTP|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určená ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.  
  
-   Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace můžete použít místo kód. Element chování služby slouží k určení certifikát, který se používá k ověření služby klienta. Service element musíte zadat chování pomocí `behaviorConfiguration` atribut. Element vazby Určuje, že je typu pověření klienta `None`, umožňuje anonymní klientům používat službu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
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
 Následující kód vytvoří instanci klienta. Vazba používá režim zabezpečení zpráv a typu pověření klienta je nastavena na hodnotu none.  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód konfiguruje klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
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
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Zabezpečení distribuované aplikace](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [Zabezpečení zpráv s anonymní metodou](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
