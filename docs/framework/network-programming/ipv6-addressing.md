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
ms.openlocfilehash: 50df0e0710c1f722d4e769ad89b653f6a8d5e394
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121950"
---
# <a name="ipv6-addressing"></a>Adresování IPv6
V Internet Protocol verze 6 (IPv6) jsou adresy 128 bitů. Jedním z důvodů rozsáhlý adresní prostor je rozdělit do hierarchie směrování domén, které odpovídají Internetu topologie dostupných adres. Dalším důvodem je mapovat adresy síťových adaptérů (nebo rozhraní), které se zařízení připojují k síti. IPv6 obsahuje schopnost přeložit adresy na nejnižší úrovni, na úrovni síťových rozhraní, a také funkce automatické konfigurace.  
  
## <a name="text-representation"></a>Textové vyjádření  
 Tady jsou tři běžné formuláře používá k reprezentování adresy IPv6 jako textové řetězce:  
  
-   **Formulář dvojtečkami**. To je forma upřednostňovaná n:n:n:n:n:n:n:n. Každá n představuje jeden z elementů osm 16 bitů adresy šestnáctkovou hodnotu. Například: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.  
  
-   **Komprimované formě**. Z důvodu délky adresy je běžné mít adres, které obsahují dlouhý řetězec nulové hodnoty. Pokud chcete zjednodušit psaní tyto adresy, použijte komprimované formě, ve kterém jeden souvislý sekvence 0 bloků jsou reprezentovány symbol dvěma dvojtečkami (::). Tento symbol se může objevit pouze jednou v adrese. Například adresu vícesměrového vysílání `FFED:0:0:0:0:BA98:3210:4562` je v komprimované formě `FFED::BA98:3210:4562`. Adresy jednosměrového vysílání `3FFE:FFFF:0:0:8:800:20C4:0` je v komprimované formě `3FFE:FFFF::8:800:20C4:0`. Na adresu zpětné smyčky `0:0:0:0:0:0:0:1` je v komprimované formě `::`1. Nespecifikovaná adresa `0:0:0:0:0:0:0:0` je v komprimované formě `::`.  
  
-   **Smíšené formuláře**. Tento formulář kombinuje adresy IPv4 a IPv6. Formát adresy v tomto případě je n:n:n:n:n:n:d.d.d.d každé n představuje šestnáctkových hodnot šest prvky nejvyšším 16 bitů adresy IPv6, kde každé d představuje desetinnou hodnotou adresu IPv4.  
  
## <a name="address-types"></a>Typy adres  
 Přední bitů v adrese definovat konkrétní typ adresy IPv6. Pole proměnné délky obsahující těchto úvodních bitů je volána formát Předpona.  
  
 Adresy jednosměrového vysílání IPv6 je rozdělena na dva oddíly. První část obsahuje předponu adresy a druhá část obsahuje identifikátoru rozhraní. Stručné způsob, jak vyjádřit kombinaci/předpona adresy IPv6 je následujícím způsobem:-adresa/délka předpony protokolu ipv6 –.  
  
 Následuje příklad adresy s předponou 64-bit.  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 Předpona v tomto příkladu je `3FFE:FFFF:0:CD30`. Adresu lze také zapsat v komprimované formě jako `3FFE:FFFF:0:CD30::/64`.  
  
 IPv6 definuje následující typy adres:  
  
-   **Adresy jednosměrového vysílání**. Identifikátor pro jedno rozhraní. Pakety odeslané na tuto adresu se doručí do identifikovaného rozhraní. Adresy jednosměrového vysílání rozlišují z adresy vícesměrového vysílání hodnotou nejvyšším octet. Oktet nejvyšším adresy vícesměrového vysílání má hodnotu šestnáctkové FF. Jakákoli jiná hodnota pro tento octet identifikuje adresy jednosměrového vysílání. Následující jsou různé druhy adresy jednosměrového vysílání:  
  
    -   **Specifická pro připojení adresy**. Tyto adresy se používají na jedno propojení a mít následující formát: FE80::*InterfaceID*. Specifická pro připojení adresy se používají mezi uzly na odkaz pro konfiguraci automatického adres, ND, nebo když žádné směrovače používají. Adresa specifická pro připojení se používá hlavně při spuštění a systém nebyl dosud získat adresy větší rozsah.  
  
    -   **Místní adresy**. Tyto adresy jsou používány v jedné lokalitě a mít následující formát: FEC0::*SubnetID*:*InterfaceID*. Adresy specifická pro server se používají pro adresování uvnitř lokality bez potřeby globální předpony.  
  
    -   **Globální adresy jednosměrového vysílání IPv6**. Tyto adresy je možné v síti Internet a mít následující formát: 010 (FP 3 bits) TLA ID (13 bits) vyhrazené (8 bitů) ID smlouvy SLA NLA ID (24 bitů) (16 bitů) *InterfaceID* (64 bitů).  
  
-   **Adresa vícesměrového vysílání**. Identifikátor pro sadu rozhraní (obvykle patří do různých uzlech). Pakety odeslané na tuto adresu se doručí do všech rozhraní adresou. Typy adres vícesměrového vysílání mají přednost před všesměrového vysílání adres protokolu IPv4.  
  
-   **Adresa všesměrového vysílání**. Identifikátor pro sadu rozhraní (obvykle patří do různých uzlech). Pakety odeslané na tuto adresu se doručí do pouze jedno rozhraní adresou. Toto je nejbližší rozhraní pomocí směrování metriky. Anycast adresy pocházejí z adresního prostoru jednosměrového vysílání a nejsou syntakticky odlišit. Rozhraní adresovaný provádí rozdíl mezi jednosměrovým vysíláním a všesměrovým anycast adres jako funkce její konfiguraci.  
  
 Obecně platí uzel má vždy Adresa specifická pro připojení. Adresa specifická pro server a jednu nebo více globálních adres může mít.  
  
## <a name="see-also"></a>Viz také:

- [Protokol IP (Internet Protocol) verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [Sokety](../../../docs/framework/network-programming/sockets.md)
