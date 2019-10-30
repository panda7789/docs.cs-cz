---
title: 'Omezení rizik: služby WCF a ověřování certifikátů'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14fafa68e55ae7c1f3b6672b150cd0b149a3ffcd
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039555"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="1accc-102">Omezení rizik: služby WCF a ověřování certifikátů</span><span class="sxs-lookup"><span data-stu-id="1accc-102">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="1accc-103">.NET Framework 4,6 přidá do seznamu výchozí seznam protokolu WCF SSL protokol TLS 1,1 a TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="1accc-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="1accc-104">Pokud jsou v klientské i serverové počítače nainstalované .NET Framework 4,6 nebo novější, pro vyjednávání se používá TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="1accc-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="1accc-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="1accc-105">Impact</span></span>

<span data-ttu-id="1accc-106">TLS 1,2 nepodporuje ověřování certifikátu MD5.</span><span class="sxs-lookup"><span data-stu-id="1accc-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="1accc-107">Výsledkem je, že pokud zákazník používá certifikát SSL, který používá MD5 pro algoritmus hash, klient služby WCF se nemůže připojit ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="1accc-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="1accc-108">Další informace najdete v tématu [zmírnění rizik: služby WCF a ověřování certifikátů](mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1accc-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="1accc-109">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="1accc-109">Mitigation</span></span>

<span data-ttu-id="1accc-110">Tento problém můžete obejít tak, aby se klient WCF mohl připojit k serveru WCF pomocí kterékoli z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="1accc-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="1accc-111">Aktualizujte certifikát, aby nepoužíval algoritmus MD5.</span><span class="sxs-lookup"><span data-stu-id="1accc-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="1accc-112">Toto je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="1accc-112">This is the recommended solution.</span></span>

- <span data-ttu-id="1accc-113">Pokud není vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1,1 nebo dřívější verzi protokolu.</span><span class="sxs-lookup"><span data-stu-id="1accc-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="1accc-114">To vám umožní pokračovat v používání certifikátu s algoritmem hash MD5.</span><span class="sxs-lookup"><span data-stu-id="1accc-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="1accc-115">Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</span><span class="sxs-lookup"><span data-stu-id="1accc-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="1accc-116">Následující konfigurační soubor provede toto:</span><span class="sxs-lookup"><span data-stu-id="1accc-116">The following configuration file does this:</span></span>

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

- <span data-ttu-id="1accc-117">Pokud je vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte vlastnost <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> na použití TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verze protokolu ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1accc-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="1accc-118">Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.</span><span class="sxs-lookup"><span data-stu-id="1accc-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="1accc-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1accc-119">See also</span></span>

- [<span data-ttu-id="1accc-120">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="1accc-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
