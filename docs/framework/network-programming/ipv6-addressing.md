---
title: IPv6 adresy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 01d4fd0fbeeb0f111505fde0f8154c54b2bdcc38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ipv6-addressing"></a>IPv6 adresy
V Internet Protocol verze 6 (IPv6) adresy jsou 128 bitů. Jedním z důvodů rozsáhlý adresní prostor je dostupných adres rozdělte hierarchie směrování domén, které odpovídají topologie k Internetu. Dalším důvodem je mapování adres síťových adaptérů (nebo rozhraní), které připojení zařízení k síti. IPv6 funkce schopnost překládání adres na nejnižší úrovni, který je na úrovni rozhraní sítě a také má funkce automatické konfigurace.  
  
## <a name="text-representation"></a>Reprezentace textu  
 Tady jsou tři běžné formuláře používá k reprezentování adresy IPv6 jako textové řetězce:  
  
-   **Šestnáctkovém formátu**. Toto je upřednostňovaný formuláře n:n:n:n:n:n:n:n. Každý n představuje jeden z osm elementů 16bitové adresy šestnáctkové hodnoty. Příklad: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.  
  
-   **Komprimované formuláře**. Z důvodu délky adres se běžně používají adres, které obsahují dlouhý řetězec nul. Aby se zjednodušila zápis použít tyto adresy komprimované formě, ve kterém jeden souvislý posloupnost 0 bloky jsou reprezentované pomocí symbol dvojité dvojtečky (:). Tento symbol může vyskytovat pouze jednou v adresu. Například adresa vícesměrového vysílání `FFED:0:0:0:0:BA98:3210:4562` v komprimované formě je `FFED::BA98:3210:4562`. Adresy jednosměrového vysílání `3FFE:FFFF:0:0:8:800:20C4:0` v komprimované formě je `3FFE:FFFF::8:800:20C4:0`. Adresu zpětné smyčky `0:0:0:0:0:0:0:1` v komprimované formě `::`1. Nespecifikovaná adresa `0:0:0:0:0:0:0:0` v komprimované formě je `::`.  
  
-   **Ve smíšeném formuláře**. Tento formulář je kombinací adresy IPv4 a IPv6. Formát adresy v tomto případě je n:n:n:n:n:n:d.d.d.d, každý n reprezentuje hexadecimální hodnoty elementů šesti horní 16bitové adresu IPv6, kde každé d představuje desetinnou hodnotu adresu IPv4.  
  
## <a name="address-types"></a>Typy adres  
 Úvodních bitů v adrese definovat konkrétní typ adresy IPv6. Proměnnou délkou pole obsahující tyto úvodních bitů se nazývá formát Předponou.  
  
 Adresy jednosměrového vysílání IPv6 je rozdělena na dva oddíly. První část předpona adresy, a druhá část obsahuje identifikátor rozhraní. Jednoduchý způsob pro express kombinace adresu nebo předponu IPv6 je následující: ipv6-délka adresy nebo předpony.  
  
 Následuje příklad adresy s předponou 64-bit.  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 Předpona v tomto příkladu se `3FFE:FFFF:0:CD30`. Adresu lze zapsat také v komprimované formě, jako `3FFE:FFFF:0:CD30::/64`.  
  
 IPv6 definuje následující typy adres:  
  
-   **Adresy jednosměrového vysílání**. Identifikátor pro jedno rozhraní. Pakety odeslané na tuto adresu doručuje do identifikovaného rozhraní. Adresy jednosměrového vysílání, jsou z adresy vícesměrového vysílání rozlišené hodnotu vyšší oktet. Adresy vícesměrového vysílání vyšší oktet má šestnáctkové hodnoty FF. Žádné jiné hodnoty pro tento octet identifikuje adresa jednosměrového vysílání. Tady jsou různé typy adresy jednosměrového vysílání:  
  
    -   **Místní adresy**. Tyto adresy jsou používány na odkaz a mít následující formát: FE80::*ID rozhraní*. Adresy link-local se používají mezi uzly na odkaz pro konfiguraci automatického řešení, ND, nebo pokud žádné směrovače jsou k dispozici. Místní adresa se používá hlavně při spuštění a systém nebyl ještě získali adresy větší rozsah.  
  
    -   **Místní adresy**. Tyto adresy jsou používány v jedné lokalitě a mít následující formát: FEC0::*SubnetID*:*ID rozhraní*. Místní adresy se používají pro adresování v rámci lokality bez nutnosti globální předpony.  
  
    -   **Globální adresy jednosměrového vysílání IPv6**. Tyto adresy lze použít v rámci Internetu a mít následující formát: 010 (FP, 3 bits) TLA ID (13 bits) vyhrazené (8 bitů) NLA ID (24 bits) ID smlouvy o úrovni služeb (16 bitů) *ID rozhraní* (64bitová verze).  
  
-   **Adresa vícesměrového vysílání**. Identifikátor pro sadu rozhraní (obvykle patřící do jiných uzlů). Pakety odeslané na tuto adresu se doručí na všechna rozhraní adresou. Adresa vícesměrového vysílání typy mají přednost před všesměrového vysílání adresy IPv4.  
  
-   **Adresa všesměrového vysílání**. Identifikátor pro sadu rozhraní (obvykle patřící do jiných uzlů). Pakety odeslané na tuto adresu doručuje do pouze jedno rozhraní adresou. Toto je nejbližší rozhraní, jako se identifikovanou pomocí směrování metriky. Adresy všesměrového vysílání jsou převzaty z prostoru adres jednosměrového vysílání a nejsou syntakticky odlišit. Rozhraní adresovaný provede rozdíl mezi jednosměrovým vysíláním a všesměrového vysílání adres jako funkce její konfiguraci.  
  
 Obecně platí uzel má vždy místní adresa. Může mít místní adresa a minimálně jeden globální adresy.  
  
## <a name="see-also"></a>Viz také  
 [Protokol IP (Internet Protocol) verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)
