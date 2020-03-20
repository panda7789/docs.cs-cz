---
ms.openlocfilehash: 9e8fdb54bddc32c08adbe114e2d46e2508585bc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858630"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>Služby WCF, které používají protokol NETTCP se zabezpečením SSL a ověřováním certifikátů MD5

|   |   |
|---|---|
|Podrobnosti|Rozhraní .NET Framework 4.6 přidá tls 1.1 a TLS 1.2 do seznamu výchozího protokolu WCF SSL. Pokud jsou klientské i serverové počítače nainstalovány rozhraní .NET Framework 4.6 nebo novější, tls 1.2 se používá pro vyjednávání. TLS 1.2 nepodporuje ověřování certifikátu MD5. V důsledku toho pokud zákazník používá certifikát MD5, klient WCF se nezdaří připojení ke službě WCF.|
|Návrh|Tento problém můžete vyřešit tak, aby se klient WCF mohl připojit k serveru WCF, a to některou z následujících akcí:<ul><li>Aktualizujte certifikát tak, aby nepoužíval algoritmus MD5. Toto je doporučené řešení.</li><li>Pokud vazba není dynamicky konfigurována ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1.1 nebo starší verzi protokolu. To umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.</li></ul> <blockquote> [!WARNING] Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</blockquote> Následující konfigurační soubor provádí toto:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>Pokud je vazba dynamicky konfigurována <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> ve zdrojovém kódu, aktualizujte vlastnost tak, aby používala TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> nebo starší verzi protokolu ve zdrojovém kódu.</li></ul> <blockquote> [!WARNING] Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</blockquote> |
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
