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
# <a name="load-balancing-grpc"></a>GRPC vyrovnávání zatížení

Typické nasazení aplikace gRPC zahrnuje řadu stejných instancí služby, které poskytují odolnost a horizontální škálovatelnost. Vyrovnávání zatížení distribuuje příchozí požadavky mezi tyto instance, aby poskytovala plné využití všech dostupných prostředků. Aby toto vyrovnávání zatížení nebylo pro klienta viditelné, je běžné použít server proxy nástroje pro vyrovnávání zatížení pro zpracování požadavků od klientů a jejich směrování na instance back-endu.

Nástroje pro vyrovnávání zatížení jsou klasifikovány podle *vrstvy* , na které pracují. Nástroje pro vyrovnávání zatížení vrstvy 4 fungují na úrovni *přenosu* , například pomocí soketů TCP, připojení a paketů. Nástroje pro vyrovnávání zatížení vrstvy 7 pracují na úrovni *aplikace* , konkrétně zpracování požadavků HTTP/2 pro aplikace gRPC.

## <a name="l4-load-balancers"></a>Nástroje pro vyrovnávání zatížení L4

Nástroj pro vyrovnávání zatížení L4 přijímá požadavek na připojení TCP od klienta, otevírá jiné připojení k jedné z back-endové instance a kopíruje data mezi dvěma připojeními bez skutečného zpracování. L4 nabízí vynikající výkon a nízkou latenci, ale velmi malým ovládacím prvkům nebo inteligentním funkcím. Pokud klient udržuje připojení otevřené, všechny požadavky budou směrovány do stejné back-endové instance.

 [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) je příkladem nástroje pro vyrovnávání zatížení L4.

## <a name="l7-load-balancers"></a>Nástroje pro vyrovnávání zatížení L7

Nástroj pro vyrovnávání zatížení L7 analyzuje příchozí požadavky HTTP/2 a předá je do back-endové instance na základě požadavků. bez ohledu na to, jak dlouho je připojení uchováváno klientem.

Příklady nástrojů pro vyrovnávání zatížení L7:

- [NGINX](https://www.nginx.com/)
- [HAProxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

Jako pravidlo pro použití služby pro vyrovnávání zatížení L7 je nejvhodnější volbou pro gRPC a další aplikace HTTP/2 (ve skutečnosti ale pro aplikace HTTP všeobecně). Nástroje pro vyrovnávání zatížení L4 budou *fungovat* s aplikacemi gRPC, ale jsou zvláště užitečné, pokud je důležitá nízká latence a nízká režie.

> [!IMPORTANT]
> V době psaní tohoto textu některé nástroje pro vyrovnávání zatížení L7 nepodporují všechny součásti specifikace HTTP/2, které vyžadují služby gRPC Services, například koncové hlavičky.

Pokud používáte šifrování TLS, můžou nástroje pro vyrovnávání zatížení ukončit připojení TLS a předat nešifrované požadavky do back-endové aplikace, případně můžou předat šifrovaný požadavek společně. V obou případech je nutné nakonfigurovat nástroj pro vyrovnávání zatížení pomocí veřejného a privátního klíče serveru, aby mohl dešifrovat požadavky na zpracování.

V dokumentaci k preferovanému nástroji pro vyrovnávání zatížení zjistíte, jak nakonfigurovat, aby zpracovával požadavky HTTP/2 s vašimi back-end službami.

## <a name="load-balancing-within-kubernetes"></a>Vyrovnávání zatížení v rámci Kubernetes

Diskuzi o vyrovnávání zatížení napříč interními službami na Kubernetes najdete v [části o sítích služby](service-mesh.md) .

>[!div class="step-by-step"]
>[Předchozí](service-mesh.md)
>[Další](application-performance-management.md)
