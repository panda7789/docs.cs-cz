---
title: 'Zmírnění rizik: WCF services a ověřování certifikátů'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: 8c8493efa2c3223809ad87e01e3faddaea859ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457792"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="82114-102">Zmírnění rizik: WCF services a ověřování certifikátů</span><span class="sxs-lookup"><span data-stu-id="82114-102">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="82114-103">Rozhraní .NET Framework 4.6 přidá tls 1.1 a TLS 1.2 do výchozího seznamu protokolu WCF.</span><span class="sxs-lookup"><span data-stu-id="82114-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="82114-104">Pokud jsou klientské i serverové počítače nainstalovány rozhraní .NET Framework 4.6 nebo novější, tls 1.2 se používá pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="82114-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="82114-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="82114-105">Impact</span></span>

<span data-ttu-id="82114-106">TLS 1.2 nepodporuje ověřování certifikátu MD5.</span><span class="sxs-lookup"><span data-stu-id="82114-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="82114-107">V důsledku toho pokud zákazník používá certifikát SSL, který používá MD5 pro algoritmus hash, klient WCF se nepodaří připojit ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="82114-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="82114-108">Další informace naleznete [v tématu Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="82114-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="82114-109">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="82114-109">Mitigation</span></span>

<span data-ttu-id="82114-110">Tento problém můžete vyřešit tak, aby se klient WCF mohl připojit k serveru WCF, a to některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="82114-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="82114-111">Aktualizujte certifikát tak, aby nepoužíval algoritmus MD5.</span><span class="sxs-lookup"><span data-stu-id="82114-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="82114-112">Toto je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="82114-112">This is the recommended solution.</span></span>

- <span data-ttu-id="82114-113">Pokud vazba není dynamicky konfigurována ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1.1 nebo starší verzi protokolu.</span><span class="sxs-lookup"><span data-stu-id="82114-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="82114-114">To umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.</span><span class="sxs-lookup"><span data-stu-id="82114-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="82114-115">Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</span><span class="sxs-lookup"><span data-stu-id="82114-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="82114-116">Následující konfigurační soubor provádí toto:</span><span class="sxs-lookup"><span data-stu-id="82114-116">The following configuration file does this:</span></span>

  ```xml
  <configuration>
      <system.serviceModel>
          <bindings>
              <netTcpBinding>
                  <binding>
                      <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                          <transport clientCredentialType="None|Windows|Certificate"
                                              protectionLevel="None|Sign|EncryptAndSign"
                                              sslProtocols="Ssl3|Tls1|Tls11">
                          </transport>
                      </security>
                  </binding>
              </netTcpBinding>
          </bindings>
      </system.serviceModel>
  </configuration>
  ```

- <span data-ttu-id="82114-117">Pokud je vazba dynamicky konfigurována <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> ve zdrojovém kódu, aktualizujte vlastnost tak, aby používala TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verzi protokolu ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="82114-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="82114-118">Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</span><span class="sxs-lookup"><span data-stu-id="82114-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="82114-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="82114-119">See also</span></span>

- [<span data-ttu-id="82114-120">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="82114-120">Application compatibility</span></span>](application-compatibility.md)
