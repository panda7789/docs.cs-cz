---
title: Šifrování a zabezpečení sítě – gRPC pro vývojáře WCF
description: Některé poznámky k zabezpečení sítě a šifrování v gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 8a115b59337003669b4e5436edffe239489ca79e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184461"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="ae185-103">Šifrování a zabezpečení sítě</span><span class="sxs-lookup"><span data-stu-id="ae185-103">Encryption and network security</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ae185-104">Model zabezpečení sítě WCF je rozsáhlý a složitý, včetně zabezpečení na úrovni přenosu pomocí protokolu HTTPS nebo TLS-over-TCP a zabezpečení na úrovni zpráv pomocí specifikace WS-Security k šifrování jednotlivých zpráv.</span><span class="sxs-lookup"><span data-stu-id="ae185-104">WCF's network security model is extensive and complex, including transport-level security using HTTPS or TLS-over-TCP, and message-level security using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="ae185-105">gRPC ponechá zabezpečenou síť k základnímu protokolu HTTP/2, který je možné zabezpečit pomocí běžných certifikátů TLS.</span><span class="sxs-lookup"><span data-stu-id="ae185-105">gRPC leaves secure networking to the underlying HTTP/2 protocol, which can be secured using regular TLS certificates.</span></span>

<span data-ttu-id="ae185-106">Webové prohlížeče zachází s používáním připojení TLS pro HTTP/2, ale u většiny programových klientů, včetně. `HttpClient`Netto může používat HTTP/2 přes nešifrovaná připojení.</span><span class="sxs-lookup"><span data-stu-id="ae185-106">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="ae185-107">`HttpClient`*vyžaduje šifrování* ve výchozím nastavení, ale můžete ho přepsat pomocí <xref:System.AppContext> přepínače.</span><span class="sxs-lookup"><span data-stu-id="ae185-107">`HttpClient` *does* require encryption by default, but you can override this using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="ae185-108">U veřejných rozhraní API byste měli vždycky používat připojení TLS a poskytovat platné certifikáty pro vaše služby od správné autority SSL.</span><span class="sxs-lookup"><span data-stu-id="ae185-108">For public APIs, you should always use TLS connections and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="ae185-109">[LetsEncrypt](https://letsencrypt.org) poskytují bezplatné, automatizované certifikáty SSL a většina hostování infrastruktury dnes podporuje standard LetsEncrypt s běžnými moduly plug-in a rozšířeními.</span><span class="sxs-lookup"><span data-stu-id="ae185-109">[LetsEncrypt](https://letsencrypt.org) provide free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="ae185-110">Pro interní služby v podnikové síti byste měli i nadále zvážit použití protokolu TLS k zabezpečení síťového provozu do a z vašich služeb gRPC.</span><span class="sxs-lookup"><span data-stu-id="ae185-110">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="ae185-111">Komunikace mezi mikroslužbami v clusteru, jako je Kubernetes nebo Docker Swarm, je obecně automaticky šifrovaná pomocí síťové vrstvy kontejneru, takže implementace TLS v službách, které běží výhradně v takovém clusteru, není nutná.</span><span class="sxs-lookup"><span data-stu-id="ae185-111">Communication between microservices in a cluster like Kubernetes or Docker Swarm is in general automatically encrypted by the container networking layer, so implementing TLS in services running exclusively in such a cluster isn't necessary.</span></span> <span data-ttu-id="ae185-112">V části "síť služby" v další kapitole bude tento předmět další.</span><span class="sxs-lookup"><span data-stu-id="ae185-112">There will be more on this subject in the "Service Mesh" section of the next chapter.</span></span>

<span data-ttu-id="ae185-113">Pokud potřebujete použít explicitní protokol TLS mezi službami běžícími v Kubernetes, zvažte použití certifikační autority v clusteru a řadiče správce certifikátů, jako je například [správce](https://docs.cert-manager.io/en/latest/) certifikátů k přiřazení automatických certifikátů službám v době nasazení.</span><span class="sxs-lookup"><span data-stu-id="ae185-113">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster Certificate Authority and a Certificate Manager Controller like [cert-manager](https://docs.cert-manager.io/en/latest/) to assign automatically certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ae185-114">[Předchozí](channel-credentials.md)
>[Další](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="ae185-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
