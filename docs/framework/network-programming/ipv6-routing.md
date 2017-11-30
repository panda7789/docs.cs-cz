---
title: "Směrování IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 21edbfee91a759b0b48f9dd6c0c9e900cdff93f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-routing"></a>Směrování IPv6
Flexibilní mechanismus směrování je výhodou IPv6. Vzhledem ke způsobu, ve které IPv4 ID sítě byly a jsou přidělené, velké směrovacích tabulek třeba udržovat směrovače, které jsou na Internetu páteřním. Tyto směrovače musí znát všechny trasy k předávání paketů, které jsou potenciálně směrované do kteréhokoli uzlu na Internetu. S jeho schopnost agregační adresy IPv6 umožňuje flexibilní adresování a výrazně snižuje velikost směrovacích tabulek. V této nové adresování architektuře zprostředkující směrovače musí sledovat pouze místní část svoji síť k předávání zpráv správně.  
  
## <a name="neighbor-discovery"></a>ND  
 Některé funkce poskytované službou ND jsou:  
  
-   Zjišťování směrovače. To umožňuje hostitelům identifikovat místního směrovače.  
  
-   Překlad adres. To umožňuje uzly k překladu adresy linkové vrstvě pro odpovídající adresa dalšího směrování (náhrada za Address Resolution Protocol [ARP]).  
  
-   Adres automatické konfigurace. To umožňuje hostitelům pro automatickou konfiguraci místní a globální adresy.  
  
 ND používá Internet Control Message Protocol pro protokol IPv6 (ICMPv6) zprávy, které zahrnují:  
  
-   Inzerování směrovače. Jsou odesílány směrovačem částečně pravidelně nebo v reakci na vyhledávací. Směrovače IPv6 pomocí inzerování směrovače inzerovat jejich dostupnost, předpony a dalších parametrů.  
  
-   Oslovení směrovače. Odešle hostitele požadavku, že směrovače na tento odkaz Odeslat inzerování směrovače okamžitě.  
  
-   Oslovení sousedním. Odesílány uzly pro rozpoznání adresy, detekce duplicitních adres, a ověřte, zda je sousedním stále dostupný.  
  
-   Sousedním oznámení o inzerovaném programu. Odesílány uzly reagovat na sousedním oslovení nebo oznámení okolí změny v adrese linkové vrstvě.  
  
-   Přesměrování. Odesílá udávajících lepší adresa dalšího směrování na určité cílové místo pro odesílání uzel.  
  
## <a name="see-also"></a>Viz také  
 [Protokol IP verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)
