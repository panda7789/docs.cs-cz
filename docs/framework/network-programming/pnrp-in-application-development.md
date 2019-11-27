---
title: PNRP ve vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428203"
---
# <a name="pnrp-in-application-development"></a>PNRP ve vývoji aplikací
V systému Windows Vista mohou síťové aplikace získat přístup k funkcím pro publikování a rozlišení názvů prostřednictvím zjednodušeného rozhraní API (PNRP Application Programming Interface).  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementace protokolu PNRP (Peer Name Resolution Protocol)  
 Díky zjednodušenému rozhraní API pro PNRP nejsou cloudy explicitně určeny k registraci názvů a adres; komponenta PNRP automaticky určuje vhodné cloudy pro připojení a adresy pro publikování v rámci cloudů.  
  
 Pro vysoce zjednodušené rozlišení názvů PNRP v systému Windows Vista jsou nyní názvy PNRP integrovány do funkce getaddrinfo () Windows Sockets. Pokud chcete použít protokol PNRP k překladu názvu na adresu IPv6, můžou aplikace pomocí funkce getaddrinfo () přeložit plně kvalifikovaný název domény (FQDN) name.prnp.net, ve kterém je název název partnerského zařízení, který se řeší. Doména pnrp.net je vyhrazená doména v systému Windows Vista pro překlad názvů PNRP.  
  
 Předávání zpráv mezi aplikacemi PeerToPeer se pořád zpracovává základními architekturami, jako jsou PeerChannel a WCF [Velká data a streamování](../wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer>
