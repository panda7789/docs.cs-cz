---
ms.openlocfilehash: fb9436ec9e525afb497033775e34b6b636ced22d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621154"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a><span data-ttu-id="05212-101">Služby WCF, které používají NETTCP se zabezpečením SSL a ověřováním certifikátů MD5</span><span class="sxs-lookup"><span data-stu-id="05212-101">WCF services that use NETTCP with SSL security and MD5 certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="05212-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="05212-102">Details</span></span>

<span data-ttu-id="05212-103">.NET Framework 4,6 přidá do seznamu výchozích protokolů protokolu WCF protokolu TLS 1,1 a TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="05212-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL default protocol list.</span></span> <span data-ttu-id="05212-104">Pokud jsou v klientské i serverové počítače nainstalované .NET Framework 4,6 nebo novější, pro vyjednávání se používá TLS 1,2. TLS 1,2 nepodporuje ověřování certifikátu MD5.</span><span class="sxs-lookup"><span data-stu-id="05212-104">When both client and server machines have the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="05212-105">Výsledkem je, že pokud zákazník používá certifikát MD5, klient služby WCF se nebude moct připojit ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="05212-105">As a result, if a customer uses an MD5 certificate, the WCF client will fail to connect to the WCF service.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="05212-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="05212-106">Suggestion</span></span>

<span data-ttu-id="05212-107">Tento problém můžete obejít tak, aby se klient WCF mohl připojit k serveru WCF pomocí kterékoli z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="05212-107">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="05212-108">Aktualizujte certifikát, aby nepoužíval algoritmus MD5.</span><span class="sxs-lookup"><span data-stu-id="05212-108">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="05212-109">Toto je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="05212-109">This is the recommended solution.</span></span>
- <span data-ttu-id="05212-110">Pokud není vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1,1 nebo dřívější verzi protokolu.</span><span class="sxs-lookup"><span data-stu-id="05212-110">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="05212-111">To vám umožní pokračovat v používání certifikátu s algoritmem hash MD5.</span><span class="sxs-lookup"><span data-stu-id="05212-111">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

> [!WARNING]
> <span data-ttu-id="05212-112">Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</span><span class="sxs-lookup"><span data-stu-id="05212-112">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

<span data-ttu-id="05212-113">Následující konfigurační soubor provede toto:</span><span class="sxs-lookup"><span data-stu-id="05212-113">The following configuration file does this:</span></span>

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

- <span data-ttu-id="05212-114">Pokud je vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> vlastnost na použití TLS 1,1 ( <xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> nebo starší verze protokolu ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="05212-114">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> or an earlier version of the protocol in the source code.</span></span>

> [!WARNING]
> <span data-ttu-id="05212-115">Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</span><span class="sxs-lookup"><span data-stu-id="05212-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

| <span data-ttu-id="05212-116">Name</span><span class="sxs-lookup"><span data-stu-id="05212-116">Name</span></span>    | <span data-ttu-id="05212-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="05212-117">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="05212-118">Rozsah</span><span class="sxs-lookup"><span data-stu-id="05212-118">Scope</span></span>   | <span data-ttu-id="05212-119">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="05212-119">Minor</span></span>   |
| <span data-ttu-id="05212-120">Verze</span><span class="sxs-lookup"><span data-stu-id="05212-120">Version</span></span> | <span data-ttu-id="05212-121">4.6</span><span class="sxs-lookup"><span data-stu-id="05212-121">4.6</span></span>     |
| <span data-ttu-id="05212-122">Typ</span><span class="sxs-lookup"><span data-stu-id="05212-122">Type</span></span>    | <span data-ttu-id="05212-123">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="05212-123">Runtime</span></span> |
