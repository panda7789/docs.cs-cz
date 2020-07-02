---
ms.openlocfilehash: fb9436ec9e525afb497033775e34b6b636ced22d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621154"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>Služby WCF, které používají NETTCP se zabezpečením SSL a ověřováním certifikátů MD5

#### <a name="details"></a>Podrobnosti

.NET Framework 4,6 přidá do seznamu výchozích protokolů protokolu WCF protokolu TLS 1,1 a TLS 1,2. Pokud jsou v klientské i serverové počítače nainstalované .NET Framework 4,6 nebo novější, pro vyjednávání se používá TLS 1,2. TLS 1,2 nepodporuje ověřování certifikátu MD5. Výsledkem je, že pokud zákazník používá certifikát MD5, klient služby WCF se nebude moct připojit ke službě WCF.

#### <a name="suggestion"></a>Návrh

Tento problém můžete obejít tak, aby se klient WCF mohl připojit k serveru WCF pomocí kterékoli z následujících možností:

- Aktualizujte certifikát, aby nepoužíval algoritmus MD5. Toto je doporučené řešení.
- Pokud není vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1,1 nebo dřívější verzi protokolu. To vám umožní pokračovat v používání certifikátu s algoritmem hash MD5.

> [!WARNING]
> Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

Následující konfigurační soubor provede toto:

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <netTcpBinding>
        <binding>
          <security mode= "None/Transport/Message/TransportWithMessageCredential" >
            <transport clientCredentialType="None/Windows/Certificate"
                       protectionLevel="None/Sign/EncryptAndSign"
                       sslProtocols="Ssl3/Tls1/Tls11">
            </transport>
          </security>
        </binding>
      </netTcpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

- Pokud je vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> vlastnost na použití TLS 1,1 ( <xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> nebo starší verze protokolu ve zdrojovém kódu.

> [!WARNING]
> Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

| Name    | Hodnota   |
|:--------|:--------|
| Rozsah   | Vedlejší   |
| Verze | 4.6     |
| Typ    | Modul runtime |
