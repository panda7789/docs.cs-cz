---
title: Zabezpečení zpráv s anonymním klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 058163c96bba036c3183695bf986b4d0424271ac
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595216"
---
# <a name="message-security-with-an-anonymous-client"></a>Zabezpečení zpráv s anonymním klientem

V následujícím scénáři vidíte klient a službu zabezpečený službou Windows Communication Foundation (WCF) zabezpečení zpráv. Cílem návrhu je použít zabezpečení zpráv místo zabezpečení přenosu, aby v budoucnu bylo možné podporovat bohatší model založený na deklaracích. Další informace o používání bohatých deklarací pro autorizaci najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](managing-claims-and-authorization-with-the-identity-model.md).

Ukázkovou aplikaci najdete v tématu [zabezpečení zpráv anonymně](../samples/message-security-anonymous.md).

![Zabezpečení zpráv pomocí anonymního klienta](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")

|Charakteristika|Popis|
|--------------------|-----------------|
|Režim zabezpečení|Zpráva|
|Interoperabilita|Pouze WCF|
|Ověřování (Server)|Počáteční vyjednávání vyžaduje ověření serveru, ale ne ověřování klientů.|
|Ověřování (klient)|Žádné|
|Integrita|Ano, použití sdíleného kontextu zabezpečení|
|Důvěrnost|Ano, použití sdíleného kontextu zabezpečení|
|Přenos|HTTP|

## <a name="service"></a>Služba

Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte některou z následujících akcí:

- Vytvořte samostatnou službu pomocí kódu bez konfigurace.

- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.

### <a name="code"></a>Kód

Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a>Konfigurace

Místo kódu lze použít následující konfiguraci. Element chování služby se používá k určení certifikátu, který se používá k ověření služby klientovi. Element Service musí určovat chování pomocí `behaviorConfiguration` atributu. Element Binding určuje, že typ přihlašovacích údajů klienta je `None` , což umožňuje anonymním klientům používat službu.

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

Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte některou z následujících akcí:

- Vytvořte samostatného klienta pomocí kódu (a kódu klienta).

- Vytvořte klienta, který nedefinuje žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument. Například:

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kód

Následující kód vytvoří instanci klienta. Vazba používá zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na hodnotu None.

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a>Konfigurace

Následující kód nakonfiguruje klienta.

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

- [Přehled zabezpečení](security-overview.md)
- [Zabezpečení distribuované aplikace](distributed-application-security.md)
- [Zabezpečení zpráv s anonymní metodou](../samples/message-security-anonymous.md)
- [Identita a ověřování služby](service-identity-and-authentication.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
