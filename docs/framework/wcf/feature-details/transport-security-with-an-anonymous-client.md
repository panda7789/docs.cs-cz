---
title: Zabezpečení přenosu pomocí anonymního klienta
description: Projděte si tento scénář WCF, který používá zabezpečení přenosu k ověření serveru pomocí certifikátu, který důvěřuje klientovi. Klient není ověřen.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245008"
---
# <a name="transport-security-with-an-anonymous-client"></a>Zabezpečení přenosu pomocí anonymního klienta

Tento scénář Windows Communication Foundation (WCF) používá k zajištění důvěrnosti a integrity zabezpečení přenosu (HTTPS). Server musí být ověřený s certifikátem SSL (Secure Sockets Layer) (SSL) a klienti musí důvěřovat certifikátu serveru. Klient není ověřen žádným mechanismem a proto je anonymní.

Ukázkovou aplikaci najdete v tématu [zabezpečení přenosu v protokolu WS](../samples/ws-transport-security.md). Další informace o zabezpečení přenosu najdete v tématu [Přehled zabezpečení přenosu](transport-security-overview.md).

Další informace o používání certifikátu se službou najdete v tématu [práce s certifikáty](working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

![Použití zabezpečení přenosu u anonymního klienta](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|Charakteristika|Description|
|--------------------|-----------------|
|Režim zabezpečení|Přenos|
|Interoperabilita|Se stávajícími webovými službami a klienty|
|Ověřování (Server)<br /><br /> Ověřování (klient)|Ano<br /><br /> Úroveň aplikace (žádná podpora WCF)|
|Integrita|Ano|
|Důvěrnost|Ano|
|Přenos|HTTPS|
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Služba

Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z následujících akcí:

- Vytvořte samostatnou službu pomocí kódu bez konfigurace.

- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.

### <a name="code"></a>Kód

Následující kód ukazuje, jak vytvořit koncový bod pomocí zabezpečení přenosu:

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a>Konfigurace

Následující kód nastaví stejný koncový bod pomocí konfigurace. Klient není ověřen žádným mechanismem a proto je anonymní.

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

Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z následujících akcí:

- Vytvořte samostatného klienta pomocí kódu (a kódu klienta).

- Vytvořte klienta, který nedefinuje žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument. Příklad:

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kód

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a>Konfigurace

Následující konfiguraci lze použít místo kódu k nastavení služby.

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

## <a name="see-also"></a>Viz také

- [Přehled zabezpečení](security-overview.md)
- [Zabezpečení přenosu WS](../samples/ws-transport-security.md)
- [Přehled zabezpečení přenosu](transport-security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
