---
title: Vyrovnávání zatížení gRPC-gRPC pro vývojáře WCF
description: Výběr nástroje pro vyrovnávání zatížení pro práci s gRPC službami.
ms.date: 09/02/2019
ms.openlocfilehash: 070fc7fda73988302d15c8cec12b1ac359641317
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967443"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="1713e-103">GRPC vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="1713e-103">Load balancing gRPC</span></span>

<span data-ttu-id="1713e-104">Typické nasazení aplikace gRPC zahrnuje řadu stejných instancí služby, které poskytují odolnost a horizontální škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="1713e-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="1713e-105">Vyrovnávání zatížení distribuovaných příchozích požadavků napříč těmito instancemi, aby bylo zajištěno plné využití všech dostupných prostředků.</span><span class="sxs-lookup"><span data-stu-id="1713e-105">Load balancing distributed incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="1713e-106">Aby toto vyrovnávání zatížení nebylo pro klienta viditelné, je běžné použít server proxy nástroje pro vyrovnávání zatížení pro zpracování požadavků od klientů a jejich směrování na instance back-endu.</span><span class="sxs-lookup"><span data-stu-id="1713e-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="1713e-107">Nástroje pro vyrovnávání zatížení jsou klasifikovány podle *vrstvy* , na které pracují.</span><span class="sxs-lookup"><span data-stu-id="1713e-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="1713e-108">Nástroje pro vyrovnávání zatížení vrstvy 4 fungují na úrovni *přenosu* , například pomocí soketů TCP, připojení a paketů.</span><span class="sxs-lookup"><span data-stu-id="1713e-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections and packets.</span></span> <span data-ttu-id="1713e-109">Nástroje pro vyrovnávání zatížení vrstvy 7 pracují na úrovni *aplikace* , konkrétně zpracování požadavků HTTP/2 pro aplikace gRPC.</span><span class="sxs-lookup"><span data-stu-id="1713e-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="1713e-110">Nástroje pro vyrovnávání zatížení L4</span><span class="sxs-lookup"><span data-stu-id="1713e-110">L4 load balancers</span></span>

<span data-ttu-id="1713e-111">Nástroj pro vyrovnávání zatížení L4 přijímá požadavek na připojení TCP od klienta, otevírá jiné připojení k jedné z back-endové instance a kopíruje data mezi dvěma připojeními bez skutečného zpracování.</span><span class="sxs-lookup"><span data-stu-id="1713e-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="1713e-112">L4 nabízí vynikající výkon a nízkou latenci, ale velmi malým ovládacím prvkům nebo inteligentním funkcím.</span><span class="sxs-lookup"><span data-stu-id="1713e-112">L4 offers excellent performance and low latency, but very little control or intelligence.</span></span> <span data-ttu-id="1713e-113">Pokud klient udržuje připojení otevřené, všechny požadavky budou směrovány do stejné back-endové instance.</span><span class="sxs-lookup"><span data-stu-id="1713e-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

<span data-ttu-id="1713e-114">Příkladem nástroje pro vyrovnávání zatížení L4 je [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span><span class="sxs-lookup"><span data-stu-id="1713e-114">An example of an L4 load balancer is the [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="1713e-115">Nástroje pro vyrovnávání zatížení L7</span><span class="sxs-lookup"><span data-stu-id="1713e-115">L7 load balancers</span></span>

<span data-ttu-id="1713e-116">Nástroj pro vyrovnávání zatížení L7 analyzuje příchozí požadavky HTTP/2 a předá je do back-endové instance na základě požadavků. bez ohledu na to, jak dlouho je připojení uchováváno klientem.</span><span class="sxs-lookup"><span data-stu-id="1713e-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="1713e-117">Příklady nástrojů pro vyrovnávání zatížení L7 zahrnují:</span><span class="sxs-lookup"><span data-stu-id="1713e-117">Examples of L7 load balancers include:</span></span>

- [<span data-ttu-id="1713e-118">Nginx</span><span class="sxs-lookup"><span data-stu-id="1713e-118">Nginx</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="1713e-119">HAproxy</span><span class="sxs-lookup"><span data-stu-id="1713e-119">HAproxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="1713e-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="1713e-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="1713e-121">Jako pravidlo pro použití služby pro vyrovnávání zatížení L7 je nejvhodnější volbou pro gRPC a další aplikace HTTP/2 (ve skutečnosti ale pro aplikace HTTP všeobecně).</span><span class="sxs-lookup"><span data-stu-id="1713e-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="1713e-122">Nástroje pro vyrovnávání zatížení L4 budou *fungovat* s aplikacemi gRPC, ale jsou primárně užitečné v případě nízké latence a nízké režie v rámci nejdůležitějšího významu.</span><span class="sxs-lookup"><span data-stu-id="1713e-122">L4 load balancers will *work* with gRPC applications, but are primarily useful when low latency and low overhead are of paramount importance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1713e-123">V době psaní tohoto textu ne všechny nástroje pro vyrovnávání zatížení L7 podporují všechny části specifikace HTTP/2 požadované službami gRPC Services, jako jsou koncové hlavičky.</span><span class="sxs-lookup"><span data-stu-id="1713e-123">At the time of this writing, not all L7 load balancers support all parts of the HTTP/2 specification required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="1713e-124">Při použití šifrování TLS můžou nástroje pro vyrovnávání zatížení ukončit připojení TLS a předávat nešifrované požadavky do back-endové aplikace nebo předávat šifrovaný požadavek společně.</span><span class="sxs-lookup"><span data-stu-id="1713e-124">When using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or pass the encrypted request along.</span></span> <span data-ttu-id="1713e-125">V obou případech je nutné nakonfigurovat nástroj pro vyrovnávání zatížení pomocí veřejného a privátního klíče serveru, aby mohl dešifrovat požadavky na zpracování.</span><span class="sxs-lookup"><span data-stu-id="1713e-125">Either way, the load balancer will need to be configured with the server's public and private key, so that it can decrypt requests for processing.</span></span>

<span data-ttu-id="1713e-126">V dokumentaci k preferovanému nástroji pro vyrovnávání zatížení zjistíte, jak nakonfigurovat, aby zpracovávala požadavky HTTP/2 na vaše back-endové služby.</span><span class="sxs-lookup"><span data-stu-id="1713e-126">Refer to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="1713e-127">Vyrovnávání zatížení v rámci Kubernetes</span><span class="sxs-lookup"><span data-stu-id="1713e-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="1713e-128">Diskuzi o vyrovnávání zatížení napříč interními službami na Kubernetes najdete v [části o sítích služby](service-mesh.md) .</span><span class="sxs-lookup"><span data-stu-id="1713e-128">See [the section on Service Meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1713e-129">[Předchozí](service-mesh.md)
>[Další](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="1713e-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
