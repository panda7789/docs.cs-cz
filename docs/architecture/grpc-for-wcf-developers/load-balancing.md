---
title: Vyrovnávání zatížení gRPC-gRPC pro vývojáře WCF
description: Výběr nástroje pro vyrovnávání zatížení pro práci s gRPC službami.
ms.date: 09/02/2019
ms.openlocfilehash: 215c0983146bbf9168f01956d64733f80cea6faf
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711165"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="8dc99-103">GRPC vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="8dc99-103">Load balancing gRPC</span></span>

<span data-ttu-id="8dc99-104">Typické nasazení aplikace gRPC zahrnuje řadu stejných instancí služby, které poskytují odolnost a horizontální škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="8dc99-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="8dc99-105">Vyrovnávání zatížení distribuuje příchozí požadavky mezi tyto instance, aby poskytovala plné využití všech dostupných prostředků.</span><span class="sxs-lookup"><span data-stu-id="8dc99-105">Load balancing distributes incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="8dc99-106">Aby toto vyrovnávání zatížení nebylo pro klienta viditelné, je běžné použít server proxy nástroje pro vyrovnávání zatížení pro zpracování požadavků od klientů a jejich směrování na instance back-endu.</span><span class="sxs-lookup"><span data-stu-id="8dc99-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="8dc99-107">Nástroje pro vyrovnávání zatížení jsou klasifikovány podle *vrstvy* , na které pracují.</span><span class="sxs-lookup"><span data-stu-id="8dc99-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="8dc99-108">Nástroje pro vyrovnávání zatížení vrstvy 4 fungují na úrovni *přenosu* , například pomocí soketů TCP, připojení a paketů.</span><span class="sxs-lookup"><span data-stu-id="8dc99-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections, and packets.</span></span> <span data-ttu-id="8dc99-109">Nástroje pro vyrovnávání zatížení vrstvy 7 pracují na úrovni *aplikace* , konkrétně zpracování požadavků HTTP/2 pro aplikace gRPC.</span><span class="sxs-lookup"><span data-stu-id="8dc99-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="8dc99-110">Nástroje pro vyrovnávání zatížení L4</span><span class="sxs-lookup"><span data-stu-id="8dc99-110">L4 load balancers</span></span>

<span data-ttu-id="8dc99-111">Nástroj pro vyrovnávání zatížení L4 přijímá požadavek na připojení TCP od klienta, otevírá jiné připojení k jedné z back-endové instance a kopíruje data mezi dvěma připojeními bez skutečného zpracování.</span><span class="sxs-lookup"><span data-stu-id="8dc99-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="8dc99-112">L4 nabízí vynikající výkon a nízkou latenci, ale velmi malým ovládacím prvkům nebo inteligentním funkcím.</span><span class="sxs-lookup"><span data-stu-id="8dc99-112">L4 offers excellent performance and low latency, but very little control or intelligence.</span></span> <span data-ttu-id="8dc99-113">Pokud klient udržuje připojení otevřené, všechny požadavky budou směrovány do stejné back-endové instance.</span><span class="sxs-lookup"><span data-stu-id="8dc99-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

 <span data-ttu-id="8dc99-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) je příkladem nástroje pro vyrovnávání zatížení L4.</span><span class="sxs-lookup"><span data-stu-id="8dc99-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) is an example of an L4 load balancer.</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="8dc99-115">Nástroje pro vyrovnávání zatížení L7</span><span class="sxs-lookup"><span data-stu-id="8dc99-115">L7 load balancers</span></span>

<span data-ttu-id="8dc99-116">Nástroj pro vyrovnávání zatížení L7 analyzuje příchozí požadavky HTTP/2 a předá je do back-endové instance na základě požadavků. bez ohledu na to, jak dlouho je připojení uchováváno klientem.</span><span class="sxs-lookup"><span data-stu-id="8dc99-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="8dc99-117">Příklady nástrojů pro vyrovnávání zatížení L7:</span><span class="sxs-lookup"><span data-stu-id="8dc99-117">Examples of L7 load balancers:</span></span>

- [<span data-ttu-id="8dc99-118">NGINX</span><span class="sxs-lookup"><span data-stu-id="8dc99-118">NGINX</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="8dc99-119">HAProxy</span><span class="sxs-lookup"><span data-stu-id="8dc99-119">HAProxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="8dc99-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="8dc99-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="8dc99-121">Jako pravidlo pro použití služby pro vyrovnávání zatížení L7 je nejvhodnější volbou pro gRPC a další aplikace HTTP/2 (ve skutečnosti ale pro aplikace HTTP všeobecně).</span><span class="sxs-lookup"><span data-stu-id="8dc99-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="8dc99-122">Nástroje pro vyrovnávání zatížení L4 budou *fungovat* s aplikacemi gRPC, ale jsou zvláště užitečné, pokud je důležitá nízká latence a nízká režie.</span><span class="sxs-lookup"><span data-stu-id="8dc99-122">L4 load balancers will *work* with gRPC applications, but they're mainly useful when low latency and low overhead are important.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8dc99-123">V době psaní tohoto textu některé nástroje pro vyrovnávání zatížení L7 nepodporují všechny součásti specifikace HTTP/2, které vyžadují služby gRPC Services, například koncové hlavičky.</span><span class="sxs-lookup"><span data-stu-id="8dc99-123">At the time of this writing, some L7 load balancers don't support all the parts of the HTTP/2 specification that are required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="8dc99-124">Pokud používáte šifrování TLS, můžou nástroje pro vyrovnávání zatížení ukončit připojení TLS a předat nešifrované požadavky do back-endové aplikace, případně můžou předat šifrovaný požadavek společně.</span><span class="sxs-lookup"><span data-stu-id="8dc99-124">If you're using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or they can pass the encrypted request along.</span></span> <span data-ttu-id="8dc99-125">V obou případech je nutné nakonfigurovat nástroj pro vyrovnávání zatížení pomocí veřejného a privátního klíče serveru, aby mohl dešifrovat požadavky na zpracování.</span><span class="sxs-lookup"><span data-stu-id="8dc99-125">Either way, the load balancer will need to be configured with the server's public and private key so it can decrypt requests for processing.</span></span>

<span data-ttu-id="8dc99-126">V dokumentaci k preferovanému nástroji pro vyrovnávání zatížení zjistíte, jak nakonfigurovat, aby zpracovával požadavky HTTP/2 s vašimi back-end službami.</span><span class="sxs-lookup"><span data-stu-id="8dc99-126">See to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="8dc99-127">Vyrovnávání zatížení v rámci Kubernetes</span><span class="sxs-lookup"><span data-stu-id="8dc99-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="8dc99-128">Diskuzi o vyrovnávání zatížení napříč interními službami na Kubernetes najdete v [části o sítích služby](service-mesh.md) .</span><span class="sxs-lookup"><span data-stu-id="8dc99-128">See [the section on service meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8dc99-129">[Předchozí](service-mesh.md)
>[Další](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="8dc99-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
