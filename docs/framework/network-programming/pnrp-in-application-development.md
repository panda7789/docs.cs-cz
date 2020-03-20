---
title: PNRP ve vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428203"
---
# <a name="pnrp-in-application-development"></a>PNRP ve vývoji aplikací
V systému Windows Vista mohou síťové aplikace přistupovat k funkcím publikování názvů a rozlišení prostřednictvím zjednodušeného aplikačního programovacího rozhraní (API) protokolu PNRP.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementace protokolu pro překlad názvů rovnocenných stran  
 Pomocí zjednodušeného rozhraní PNRP API nejsou mraky explicitně určeny pro registraci názvu a adres. Komponenta PNRP automaticky určuje příslušné cloudy, které se mají spojit, a adresy, které mají být publikovány v rámci cloudů.  
  
 Pro velmi zjednodušené překlad názvů PNRP v systému Windows Vista, PNRP názvy jsou nyní integrovány do getaddrinfo() Windows Sockets funkce. Chcete-li použít PNRP k překladu názvu na adresu IPv6, mohou aplikace použít funkci getaddrinfo() k vyřešení plně kvalifikovaného názvu domény (FQDN) name.prnp.net, ve kterém je název peer název přeložen. Doména pnrp.net je vyhrazená doména v systému Windows Vista pro překlad názvů PNRP.  
  
 Zprávy předávají mezi aplikacemi PeerToPeer je stále zpracovává základní architektury, jako je PeerChannel a WCF [velkých dat a streamování](../wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer>
