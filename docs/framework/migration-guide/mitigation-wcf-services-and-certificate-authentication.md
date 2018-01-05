---
title: "Omezení rizik: Služby WCF a ověřování pomocí certifikátu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b106dd7a6853e5af6aa53bcc8a66ae1d949f0f0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="ded3d-102">Omezení rizik: Služby WCF a ověřování pomocí certifikátu</span><span class="sxs-lookup"><span data-stu-id="ded3d-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="ded3d-103">Rozhraní .NET Framework 4.6 přidá do seznamu výchozích protokol WCF SSL protokoly TLS 1.1 a TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="ded3d-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="ded3d-104">Když klientské a serverové počítače nainstalována rozhraní .NET Framework 4.6 nebo vyšší, použije se pro vyjednávání protokolu TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="ded3d-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ded3d-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="ded3d-105">Impact</span></span>  
 <span data-ttu-id="ded3d-106">Protokol TLS 1.2 nepodporuje ověřování pomocí certifikátu MD5.</span><span class="sxs-lookup"><span data-stu-id="ded3d-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="ded3d-107">Výsledkem je, pokud zákazník používá certifikát SSL, který je používán pro algoritmus hash MD5, WCF klientovi nepodaří připojit ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="ded3d-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="ded3d-108">Další informace najdete v tématu [omezení rizik: služby WCF a ověřování pomocí certifikátu](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ded3d-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ded3d-109">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="ded3d-109">Mitigation</span></span>  
 <span data-ttu-id="ded3d-110">Tento problém můžete vyřešit tak, aby klienta WCF můžete připojit k serveru WCF pomocí některého z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="ded3d-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
-   <span data-ttu-id="ded3d-111">Aktualizujte certifikát nechcete použít algoritmus MD5.</span><span class="sxs-lookup"><span data-stu-id="ded3d-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="ded3d-112">Toto je doporučená řešení.</span><span class="sxs-lookup"><span data-stu-id="ded3d-112">This is the recommended solution.</span></span>  
  
-   <span data-ttu-id="ded3d-113">Pokud vazba není nakonfigurováno dynamicky ve zdrojovém kódu, aktualizujte soubor konfigurace aplikace k použití protokolu TLS 1.1 nebo starší verzi protokolu.</span><span class="sxs-lookup"><span data-stu-id="ded3d-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="ded3d-114">Umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.</span><span class="sxs-lookup"><span data-stu-id="ded3d-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="ded3d-115">Toto řešení se nedoporučuje, protože certifikát se algoritmus hash MD5 považuje za nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="ded3d-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="ded3d-116">Následující konfigurační soubor nemá toto:</span><span class="sxs-lookup"><span data-stu-id="ded3d-116">The following configuration file does this:</span></span>  
  
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
  
-   <span data-ttu-id="ded3d-117">Pokud je vazba dynamicky konfigurována ve zdrojovém kódu, aktualizovat <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> vlastnost na používání protokolu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verzi protokolu ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="ded3d-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="ded3d-118">Toto řešení se nedoporučuje, protože certifikát se algoritmus hash MD5 považuje za nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="ded3d-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded3d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ded3d-119">See Also</span></span>  
 [<span data-ttu-id="ded3d-120">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ded3d-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
