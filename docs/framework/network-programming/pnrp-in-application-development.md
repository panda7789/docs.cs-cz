---
title: PNRP při vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b085604d7d20eb9222507b4820be219ffeae4726
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="pnrp-in-application-development"></a>PNRP při vývoji aplikací
V systému Windows Vista, síťové aplikace mohou přistupovat k název publikace a funkce řešení prostřednictvím zjednodušené PNRP aplikačního programovacího rozhraní (API).  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementace protokolu Peer Name Resolution Protocol  
 S zjednodušené rozhraní API PNRP nejsou explicitně zadané cloudy k registraci názvu a adresy; součást PNRP automaticky určuje příslušné cloud pro připojení a adresy publikovat v rámci cloudy.  
  
 Pro vysoce zjednodušené PNRP překlad IP adres v systému Windows Vista jsou integrovány do getaddrinfo() funkce Windows Sockets teď PNRP názvy. Pokud chcete použít PNRP přeložit název na adresu IPv6, aplikace můžete použít funkci getaddrinfo() vyřešit name.prnp.net plně kvalifikovaný název domény (FQDN), který název je název partnerského zařízení přeloženy. Doména pnrp.net je vyhrazené domény v systému Windows Vista PNRP překladu IP adres.  
  
 Předávání mezi aplikacemi PeerToPeer zpráv se stále provádí základní architektury, jako je například PeerChannel a WCF [velkého množství dat a Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer>
