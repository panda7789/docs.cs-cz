---
title: Adresování IPv6
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
ms.openlocfilehash: 1bad43b96fc6f66724e5e40cdf0ae6d76b46d867
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047856"
---
# <a name="ipv6-addressing"></a>Adresování IPv6

V protokolu IP verze 6 (IPv6) jsou adresy dlouhé 128 bitů. Jedním z důvodů tak velkého adresního prostoru je rozdělení dostupných adres do hierarchie směrovacích domén, které odrážejí topologii Internetu. Dalším důvodem je mapování adres síťových adaptérů (nebo rozhraní), které připojují zařízení k síti. IPv6 nabízí vlastní schopnost řešit adresy na nejnižší úrovni, která je na úrovni síťového rozhraní a má také možnosti automatické konfigurace.

## <a name="text-representation"></a>Reprezentace textu

Následují tři konvenční formuláře, které představují adresy IPv6 jako textové řetězce:

- **Dvojtečka-hexadecimální forma**. This is the preferred form n:n:n:n:n:n:n:n. Každý n představuje šestnáctkovou hodnotu jednoho z osmi 16bitových prvků adresy. Například: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.

- **Komprimovaný tvar**. Vzhledem k délce adresy je běžné mít adresy obsahující dlouhý řetězec nul. Chcete-li zjednodušit psaní těchto adres, použijte komprimovaný formulář, ve kterém je jedna souvislá posloupnost 0 bloků reprezentována symbolem dvojité dvojtečky (::). Tento symbol se může v adrese objevit pouze jednou. Například adresa `FFED:0:0:0:0:BA98:3210:4562` vícesměrového vysílání v `FFED::BA98:3210:4562`komprimované podobě je . Adresa `3FFE:FFFF:0:0:8:800:20C4:0` jednosměrového vysílání v `3FFE:FFFF::8:800:20C4:0`komprimované podobě je . Adresa `0:0:0:0:0:0:0:1` zpětné smyčky v komprimované podobě je `::`1. Nespecifikovaná `0:0:0:0:0:0:0:0` adresa v komprimované podobě je `::`.

- **Smíšená forma**. Tento formulář kombinuje adresy IPv4 a IPv6. In this case, the address format is n:n:n:n:n:n:d.d.d.d, where each n represents the hexadecimal values of the six IPv6 high-order 16-bit address elements, and each d represents the decimal value of an IPv4 address.

## <a name="address-types"></a>Typy adres

Úvodní bity v adrese definují konkrétní typ adresy IPv6. Pole proměnné délky obsahující tyto úvodní bity se nazývá předpona formátu (FP).

Adresa jednosměrového vysílání IPv6 je rozdělena na dvě části. První část obsahuje předponu adresy a druhá část obsahuje identifikátor rozhraní. Stručný způsob vyjádření kombinace adresy a předpony Protokolu IPv6 je následující: ipv6-address/prefix-length.

Následuje příklad adresy s 64bitovou předponou.

`3FFE:FFFF:0:CD30:0:0:0:0/64`.

Předpona v tomto `3FFE:FFFF:0:CD30`příkladu je . Adresu lze také zapsat v komprimované podobě, jako `3FFE:FFFF:0:CD30::/64`.

IPv6 definuje následující typy adres:

- **Adresa jednosměrového vysílání**. Identifikátor pro jedno rozhraní. Paket odeslaný na tuto adresu je doručen do identifikovaného rozhraní. Adresy jednosměrového vysílání se od adres vícesměrového vysílání odlišují hodnotou oktetu nejvyššího řádu. Oktet nejvyššího řádu adres vícesměrového vysílání má šestnáctkovou hodnotu FF. Jakákoli jiná hodnota pro tento oktet identifikuje adresu jednosměrového vysílání. Níže jsou uvedeny různé typy jednosměrových adres:

  - **Místní adresy propojení**. Tyto adresy se používají na jednom odkazu a mají následující formát: FE80::*InterfaceID*. Místní adresy propojení se používají mezi uzly na propojení pro konfiguraci automatické adresy, zjišťování sousedů nebo pokud nejsou k dispozici žádné směrovače. Lokální adresa propojení se používá především při spuštění a v případě, že systém ještě nezískal adresy většího rozsahu.

  - **Místní adresy na webu**. Tyto adresy se používají na jednom webu a mají následující formát: FEC0::*SubnetID*:*InterfaceID*. Místní adresy lokality se používají pro adresování uvnitř webu bez nutnosti globální předpony.

  - **Globální adresy jednosměrového vysílání IPv6**. Tyto adresy lze použít přes Internet a mají následující formát: 010 (FP, 3 bity) TLA ID (13 bitů) Vyhrazeno (8 bitů) NLA ID (24 bitů) SLA ID (16 bitů) *RozhraníID* (64 bitů).

- **Adresa vícesměrového vysílání**. Identifikátor pro sadu rozhraní (obvykle patří do různých uzlů). Paket odeslaný na tuto adresu je doručen na všechna rozhraní identifikovaná adresou. Typy adres vícesměrového vysílání nahrazují adresy všesměrového vysílání IPv4.

- **Adresa libovolného vysílání**. Identifikátor pro sadu rozhraní (obvykle patří do různých uzlů). Paket odeslaný na tuto adresu je doručen pouze na jedno rozhraní identifikované adresou. Toto je nejbližší rozhraní identifikované metrikami směrování. Adresy libovolného vysílání jsou převzaty z adresního prostoru jednosměrového vysílání a nejsou syntakticky rozlišitelné. Adresované rozhraní provádí rozlišení mezi jednosměrovým a anycast adresy jako funkce jeho konfigurace.

Obecně platí, že uzel má vždy místní adresu propojení. Může mít místní adresu webu a jednu nebo více globálních adres.

## <a name="see-also"></a>Viz také

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
