---
title: Adresování IPv6
description: Přečtěte si o Internet Protocol verze 6 (IPv6), adresách, včetně textové reprezentace a typů adres.
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
ms.openlocfilehash: fbf68cb5f40450c2f9ecf4900801ee55e326fcb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502337"
---
# <a name="ipv6-addressing"></a>Adresování IPv6

Ve verzi Internet Protocol 6 (IPv6) jsou adresy 128 bitů dlouhé. Jedním z důvodů takového dlouhého adresního prostoru je rozdělení dostupných adres do hierarchie domén směrování, které odrážejí topologii Internetu. Dalším důvodem je mapování adres síťových adaptérů (nebo rozhraní), které připojují zařízení k síti. Protokol IPv6 obsahuje schopnost překládat adresy na nejnižší úrovni, která je na úrovni síťového rozhraní, a má taky možnosti automatické konfigurace.

## <a name="text-representation"></a>Reprezentace textu

Níže jsou uvedené tři konvenční formuláře používané k reprezentování adres IPv6 jako textové řetězce:

- **Dvojtečka – šestnáctkový tvar**. Toto je preferovaný tvar n:n: n:n: n:n: n:n. Každá hodnota n představuje hexadecimální hodnotu jednoho z 8 16 prvků adresy. Například: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.

- **Komprimovaný formulář**. Z důvodu délky adresy je běžné mít adresy obsahující dlouhé řetězce nul. Pro zjednodušení psaní těchto adres používejte komprimovaný formulář, ve kterém je jedna souvislá sekvence 0 bloků reprezentovaná symbolem dvojité dvojtečky (::). Tento symbol se může v adrese objevit jenom jednou. Například adresa vícesměrového vysílání `FFED:0:0:0:0:BA98:3210:4562` v komprimované podobě je `FFED::BA98:3210:4562` . Adresa jednosměrového vysílání `3FFE:FFFF:0:0:8:800:20C4:0` v komprimovaném formátu je `3FFE:FFFF::8:800:20C4:0` . Adresa zpětné smyčky `0:0:0:0:0:0:0:1` v komprimované formě je `::` 1. Nespecifikovaná adresa `0:0:0:0:0:0:0:0` v komprimované formě je `::` .

- **Smíšený formulář**. Tento formulář kombinuje adresy IPv4 a IPv6. V tomto případě formát adresy je n:n: m:n: n:n: d. d. d. d, kde každá hodnota n představuje hexadecimální hodnoty šesti 32bitových prvků adresy IPv6, přičemž každý d představuje desítkovou hodnotu adresy IPv4.

## <a name="address-types"></a>Typy adres

Počáteční bity v adrese definují konkrétní typ adresy IPv6. Pole s proměnnou délkou obsahující tyto úvodní bity se nazývá předpona formátu (FP).

Adresa jednosměrového vysílání IPv6 je rozdělena do dvou částí. První část obsahuje předponu adresy a druhá část obsahuje identifikátor rozhraní. Stručný způsob, jak vyjádřit kombinaci adresy a předpony IPv6, je následující: IPv6-Address/prefix-length.

Následuje příklad adresy s 64 předponou.

`3FFE:FFFF:0:CD30:0:0:0:0/64`.

Předpona v tomto příkladu je `3FFE:FFFF:0:CD30` . Adresa může být také zapsána do komprimovaného tvaru, jako `3FFE:FFFF:0:CD30::/64` .

Protokol IPv6 definuje následující typy adres:

- **Adresa jednosměrového vysílání**. Identifikátor pro jedno rozhraní. Do identifikovaného rozhraní se doručí paket odeslaný do této adresy. Adresy jednosměrového vysílání se odlišují od adres vícesměrového vysílání hodnotou oktetu vysokého řádu. Oktet adres vícesměrového vysílání vysokého řádu má hexadecimální hodnotu FF. Jakákoli jiná hodnota pro tento oktet identifikuje adresu jednosměrového vysílání. Následují různé typy adres jednosměrového vysílání:

  - **Místní adresy odkazů**. Tyto adresy se používají na jednom propojení a mají následující formát: FE80::*InterfaceID*. Místní adresy odkazů se používají mezi uzly na propojení pro konfiguraci s automatickou adresou, sousedním zjišťováním nebo v případě, že nejsou k dispozici žádné směrovače. Místní adresa pro propojení se používá primárně při spuštění a v případě, že systém ještě nezískal adresy většího rozsahu.

  - **Místní adresy pro lokalitu**. Tyto adresy se používají v jedné lokalitě a mají následující formát: FEC0::*SubnetID*:*InterfaceID*. Místní adresy lokality se používají k adresování v lokalitě bez nutnosti globální předpony.

  - **Globální adresy jednosměrového vysílání IPv6**. Tyto adresy lze použít v Internetu a mají následující formát: 010 (FP, 3 bity) TLA ID (13 bitů) rezervované (8 bitů) NLA ID (24 bitů) ID SLA (16 bitů) *InterfaceID* (64 bitů).

- **Adresa vícesměrového vysílání**. Identifikátor pro sadu rozhraní (obvykle patřící do různých uzlů). Paket odeslaný této adrese se doručuje na všechna rozhraní identifikovaná adresou. Typy adres vícesměrového vysílání nahrazují adresy všesměrového vysílání IPv4.

- **Adresa libovolného vysílání** Identifikátor pro sadu rozhraní (obvykle patřící do různých uzlů). Paket odeslaný této adrese je dodán pouze do jednoho rozhraní identifikovaného adresou. Toto je nejbližší rozhraní identifikované pomocí metrik směrování. Adresy libovolného vysílání se přebírají z adresního prostoru jednosměrového vysílání a nejsou syntakticky rozlišovat. Adresované rozhraní provádí rozdíl mezi jednosměrovým vysíláním a adresou libovolného vysílání jako funkcí své konfigurace.

Obecně platí, že uzel má vždy místní adresu propojení. Může mít místní adresu lokality a jednu nebo více globálních adres.

## <a name="see-also"></a>Viz také:

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
