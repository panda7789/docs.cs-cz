---
title: Vyrovnávání zatížení gRPC-gRPC pro vývojáře WCF
description: Výběr nástroje pro vyrovnávání zatížení pro práci s gRPC službami.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 18965b9c4765ac693c6ba36ad3ea9848ce858a5c
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846624"
---
# <a name="load-balancing-grpc"></a>GRPC vyrovnávání zatížení

Typické nasazení aplikace gRPC zahrnuje řadu stejných instancí služby, které poskytují odolnost a horizontální škálovatelnost. Vyrovnávání zatížení distribuovaných příchozích požadavků napříč těmito instancemi, aby bylo zajištěno plné využití všech dostupných prostředků. Aby toto vyrovnávání zatížení nebylo pro klienta viditelné, je běžné použít server proxy nástroje pro vyrovnávání zatížení pro zpracování požadavků od klientů a jejich směrování na instance back-endu.

Nástroje pro vyrovnávání zatížení jsou klasifikovány podle *vrstvy* , na které pracují. Nástroje pro vyrovnávání zatížení vrstvy 4 fungují na úrovni *přenosu* , například pomocí soketů TCP, připojení a paketů. Nástroje pro vyrovnávání zatížení vrstvy 7 pracují na úrovni *aplikace* , konkrétně zpracování požadavků HTTP/2 pro aplikace gRPC.

## <a name="l4-load-balancers"></a>Nástroje pro vyrovnávání zatížení L4

Nástroj pro vyrovnávání zatížení L4 přijímá požadavek na připojení TCP od klienta, otevírá jiné připojení k jedné z back-endové instance a kopíruje data mezi dvěma připojeními bez skutečného zpracování. L4 nabízí vynikající výkon a nízkou latenci, ale velmi malým ovládacím prvkům nebo inteligentním funkcím. Pokud klient udržuje připojení otevřené, všechny požadavky budou směrovány do stejné back-endové instance.

Příkladem nástroje pro vyrovnávání zatížení L4 je [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).

## <a name="l7-load-balancers"></a>Nástroje pro vyrovnávání zatížení L7

Nástroj pro vyrovnávání zatížení L7 analyzuje příchozí požadavky HTTP/2 a předá je do back-endové instance na základě požadavků. bez ohledu na to, jak dlouho je připojení uchováváno klientem.

Příklady nástrojů pro vyrovnávání zatížení L7 zahrnují:

- [Nginx](https://www.nginx.com/)
- [HAproxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

Jako pravidlo pro použití služby pro vyrovnávání zatížení L7 je nejvhodnější volbou pro gRPC a další aplikace HTTP/2 (ve skutečnosti ale pro aplikace HTTP všeobecně). Nástroje pro vyrovnávání zatížení L4 budou *fungovat* s aplikacemi gRPC, ale jsou primárně užitečné v případě nízké latence a nízké režie v rámci nejdůležitějšího významu.

> [!IMPORTANT]
> V době psaní tohoto textu ne všechny nástroje pro vyrovnávání zatížení L7 podporují všechny části specifikace HTTP/2 požadované službami gRPC Services, jako jsou koncové hlavičky.

Při použití šifrování TLS můžou nástroje pro vyrovnávání zatížení ukončit připojení TLS a předávat nešifrované požadavky do back-endové aplikace nebo předávat šifrovaný požadavek společně. V obou případech je nutné nakonfigurovat nástroj pro vyrovnávání zatížení pomocí veřejného a privátního klíče serveru, aby mohl dešifrovat požadavky na zpracování.

V dokumentaci k preferovanému nástroji pro vyrovnávání zatížení zjistíte, jak nakonfigurovat, aby zpracovávala požadavky HTTP/2 na vaše back-endové služby.

## <a name="load-balancing-within-kubernetes"></a>Vyrovnávání zatížení v rámci Kubernetes

Diskuzi o vyrovnávání zatížení napříč interními službami na Kubernetes najdete v [části o sítích služby](service-mesh.md) .

>[!div class="step-by-step"]
>[Předchozí](service-mesh.md)
>[Další](application-performance-management.md)
