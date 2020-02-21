---
title: Šifrování a zabezpečení sítě – gRPC pro vývojáře WCF
description: Některé poznámky k zabezpečení sítě a šifrování v gRPC
ms.date: 09/02/2019
ms.openlocfilehash: f8a7aeaf2a65e4ff56ac33d728e40f09a436f7a6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542765"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="df55a-103">Šifrování a zabezpečení sítě</span><span class="sxs-lookup"><span data-stu-id="df55a-103">Encryption and network security</span></span>

<span data-ttu-id="df55a-104">Model zabezpečení sítě pro Windows Communication Foundation (WCF) je rozsáhlý a složitý.</span><span class="sxs-lookup"><span data-stu-id="df55a-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="df55a-105">Zahrnuje zabezpečení na úrovni přenosu pomocí protokolu HTTPS nebo TLS-over-TCP a zabezpečení na úrovni zpráv pomocí specifikace WS-Security k šifrování jednotlivých zpráv.</span><span class="sxs-lookup"><span data-stu-id="df55a-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="df55a-106">gRPC ponechá zabezpečené sítě k základnímu protokolu HTTP/2, který můžete zabezpečit pomocí certifikátů TLS.</span><span class="sxs-lookup"><span data-stu-id="df55a-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="df55a-107">Webové prohlížeče zachází s používáním připojení TLS pro HTTP/2, ale u většiny programových klientů, včetně. `HttpClient`netto můžou používat HTTP/2 přes nešifrovaná připojení.</span><span class="sxs-lookup"><span data-stu-id="df55a-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="df55a-108">`HttpClient` vyžaduje šifrování ve výchozím nastavení, ale můžete ho přepsat pomocí přepínače <xref:System.AppContext>.</span><span class="sxs-lookup"><span data-stu-id="df55a-108">`HttpClient` does require encryption by default, but you can override this by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="df55a-109">U veřejných rozhraní API byste měli vždycky používat připojení TLS a poskytovat platné certifikáty pro vaše služby od správné autority SSL.</span><span class="sxs-lookup"><span data-stu-id="df55a-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="df55a-110">[LetsEncrypt](https://letsencrypt.org) poskytuje bezplatné, automatizované certifikáty SSL a většina hostování infrastruktury dnes podporuje standard LetsEncrypt s běžnými moduly plug-in a rozšířeními.</span><span class="sxs-lookup"><span data-stu-id="df55a-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="df55a-111">Pro interní služby v podnikové síti byste měli i nadále zvážit použití protokolu TLS k zabezpečení síťového provozu do a z vašich služeb gRPC.</span><span class="sxs-lookup"><span data-stu-id="df55a-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="df55a-112">Pokud potřebujete použít explicitní protokol TLS mezi službami běžícími v Kubernetes, zvažte použití certifikační autority v clusteru a řadiče správce certifikátů, jako je například [správce](https://docs.cert-manager.io/en/latest/)certifikátů.</span><span class="sxs-lookup"><span data-stu-id="df55a-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="df55a-113">Pak můžete automaticky přiřadit certifikáty ke službám v době nasazení.</span><span class="sxs-lookup"><span data-stu-id="df55a-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="df55a-114">[Předchozí](channel-credentials.md)
>[Další](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="df55a-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
