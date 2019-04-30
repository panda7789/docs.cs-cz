---
title: 'Omezení rizik: Služby WCF a ověřování pomocí certifikátu'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacf5fc4a5c73fc60df961432089ee65dd0cfaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871420"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="60397-102">Omezení rizik: Služby WCF a ověřování pomocí certifikátu</span><span class="sxs-lookup"><span data-stu-id="60397-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="60397-103">Rozhraní .NET Framework 4.6 přidá do seznamu výchozích protokol WCF SSL TLS 1.1 a TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="60397-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="60397-104">Když klientských i serverových počítačích mít rozhraní .NET Framework 4.6 nebo novější, použije se pro vyjednávání protokolu TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="60397-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="60397-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="60397-105">Impact</span></span>  
 <span data-ttu-id="60397-106">Protokol TLS 1.2 nepodporuje ověřování pomocí certifikátu MD5.</span><span class="sxs-lookup"><span data-stu-id="60397-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="60397-107">V důsledku toho pokud zákazník používá třeba certifikát SSL, který se používá pro algoritmus hash MD5, klienta WCF se nepodařilo připojit ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="60397-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="60397-108">Další informace najdete v tématu [omezení rizik: Služby WCF a ověřování pomocí certifikátu](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="60397-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="60397-109">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="60397-109">Mitigation</span></span>  
 <span data-ttu-id="60397-110">Tento problém můžete obejít tak, aby klient WCF můžete připojit k serveru WCF pomocí některého z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="60397-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
- <span data-ttu-id="60397-111">Aktualizujte certifikát nechcete použít algoritmus MD5.</span><span class="sxs-lookup"><span data-stu-id="60397-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="60397-112">Toto je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="60397-112">This is the recommended solution.</span></span>  
  
- <span data-ttu-id="60397-113">Pokud se vazba není dynamicky nakonfigurována ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace pro použití protokolu TLS 1.1 nebo starší verzi protokolu.</span><span class="sxs-lookup"><span data-stu-id="60397-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="60397-114">To umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.</span><span class="sxs-lookup"><span data-stu-id="60397-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="60397-115">Toto řešení se nedoporučuje, protože certifikátu s algoritmem hash MD5 se považuje za nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="60397-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="60397-116">Následující konfigurační soubor provede následující:</span><span class="sxs-lookup"><span data-stu-id="60397-116">The following configuration file does this:</span></span>  
  
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
        </system.ServiceModel>  
    </configuration>  
    ```  
  
- <span data-ttu-id="60397-117">Pokud je vazba konfigurována dynamicky ve zdrojovém kódu, aktualizujte <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> vlastnost na používání protokolu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verzi protokolu ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="60397-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="60397-118">Toto řešení se nedoporučuje, protože certifikátu s algoritmem hash MD5 se považuje za nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="60397-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60397-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60397-119">See also</span></span>

- [<span data-ttu-id="60397-120">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="60397-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
