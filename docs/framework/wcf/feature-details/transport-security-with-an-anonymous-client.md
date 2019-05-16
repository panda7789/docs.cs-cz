---
title: Zabezpečení přenosu s anonymním klientem – WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: aac3b2ac6cfcca137bddaefafd290e744ee991eb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637438"
---
# <a name="transport-security-with-an-anonymous-client"></a>Zabezpečení přenosu s anonymním klientem

Tento scénář Windows Communication Foundation (WCF) používá k zajištění důvěrnost a integrita zabezpečení přenosu (HTTPS). Server musí být ověřené pomocí certifikátu vrstvy SSL (Secure Sockets) a klienti musí důvěřovat certifikátu serveru. Klient není ověřována každý použitý mechanizmus a je proto anonymní.

Ukázková aplikace, najdete v části [zabezpečení přenosu WS](../samples/ws-transport-security.md). Další informace o zabezpečení přenosu, naleznete v tématu [Přehled zabezpečení přenosu](transport-security-overview.md).

Další informace o pomocí certifikátu služby najdete v tématu [Working with Certificates](working-with-certificates.md) a [jak: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

![Pomocí zabezpečení přenosu s anonymním klientem](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|Vlastnost|Popis|
|--------------------|-----------------|
|Režim zabezpečení|Přenos|
|Interoperabilita|Existující webové služby a klienti|
|Ověření (Server)<br /><br /> Ověření (klient)|Ano<br /><br /> Úroveň aplikace (bez podpory WCF)|
|Integrita|Ano|
|Důvěrnost|Ano|
|Přenos|HTTPS|
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Služba

Následující kód a konfigurace mají běžet nezávisle. Proveďte jednu z těchto akcí:

- Vytvoření samostatné služby pomocí kódu bez konfigurace.

- Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.

### <a name="code"></a>Kód

Následující kód ukazuje, jak vytvořit koncový bod pomocí zabezpečení přenosu:

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a>Konfiguraci

Následující kód nastaví stejný koncový bod pomocí konfigurace. Klient není ověřována každý použitý mechanizmus a proto je anonymní.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="SecuredByTransportEndpoint"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator">
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a>Klient

Následující kód a konfigurace mají běžet nezávisle. Proveďte jednu z těchto akcí:

- Vytvoření samostatného klienta pomocí kódu (a kód klienta).

- Vytvoření klienta, která nedefinuje žádné adresy koncových bodů. Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace. Příklad:

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kód

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a>Konfiguraci

Následující konfigurace lze namísto kódu k nastavení služby Azure.

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](security-overview.md)
- [Zabezpečení přenosu WS](../samples/ws-transport-security.md)
- [Přehled zabezpečení přenosu](transport-security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
