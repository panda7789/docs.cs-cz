---
title: Protokol PNRP (Peer Name Resolution Protocol)
description: Přečtěte si o protokolu PNRP (Peer Name Resolution Protocol), zabezpečené, škálovatelné a dynamické registraci názvů a protokolu překladu názvů.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502220"
---
# <a name="peer-name-resolution-protocol"></a>Protokol PNRP (Peer Name Resolution Protocol)
V prostředích peer-to-peer používají partneři konkrétní systémy překladu názvů k řešení různých síťových umístění (adres, protokolů a portů) v názvech nebo jiných typech identifikátorů. V minulosti bylo překlad IP adres komplikovanější díky složitě přechodným připojením a dalším nedostatkům v systému DNS (Domain Name System).  
  
 Microsoft® Windows® peer-to-peer networking řeší tento problém s protokolem PNRP (Peer Name Resolution Protocol), je nejdříve vyvinutá zabezpečená, škálovatelná a dynamická registrace názvů a protokol překladu IP adres, který se pro Windows XP napoprvé upgradovala a pak Upgradoval v systému Windows Vista™. PNRP funguje velmi jinak než tradiční systémy pro překlad názvů a otevírá Skvělé nové možnosti pro vývojáře aplikací.  
  
 S protokolem PNRP lze pro počítač nebo jednotlivé aplikace nebo služby na počítači použít rovnocenné názvy. Překlad názvů partnerů zahrnuje adresu, port a případně rozšířenou datovou část. Mezi výhody tohoto systému patří odolnost proti chybám, žádné kritické body a překlad názvů, které nikdy nevrátí zastaralé adresy. Díky tomuto protokolu máte vynikající řešení pro hledání mobilních uživatelů.  
  
 Z hlediska zabezpečení je možné názvy partnerských uzlů publikovat jako zabezpečené (chráněné) nebo nezabezpečené (bez ochrany). Protokol PNRP používá kryptografii s veřejným klíčem k ochraně názvů bezpečných partnerských uzlů proti falšování identity; oba počítače i služby můžou mít název s protokolem PNRP.  
  
Protokol PNRP (Peer Name Resolution Protocol) ukazuje následující vlastnosti:  
  
- Distribuováno a skoro zcela bez serveru. Servery jsou vyžadovány pouze pro zaváděcí proces.  
  
- Zabezpečené publikování názvu bez účasti třetích stran. Na rozdíl od publikování názvu DNS je publikace názvu PNRP okamžitá a bez finančních nákladů.  
  
- Aktualizace PNRP v reálném čase, což brání vyřešení zastaralých adres.  
  
- Překlad názvů prostřednictvím protokolu PNRP překračuje počítače tím, že umožňuje překlad názvů služeb.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Obor názvů System .NET. PeerToPeer  
  
- Funkce PNRP je definována <xref:System.Net.PeerToPeer> oborem názvů v rámci .NET Framework verze 3,5. Poskytuje sadu typů, které se dají použít k registraci a překladu názvů partnerských uzlů pomocí dostupné služby PNRP.  
  
- (Pomocí typů poskytovaných v oboru názvů lze vytvořit instanci překladačů PNRP a vlastních partnerských uzlů <xref:System.ServiceModel.PeerResolvers> .)  
  
- Následující typy, které se používají k registraci a překladu názvů pomocí dostupné služby PNRP, jsou tyto:  
  
- <xref:System.Net.PeerToPeer.Cloud>: Definuje informace popisující dostupný Cloud PNRP, včetně jeho oboru.  
  
- <xref:System.Net.PeerToPeer.PeerName>: Definuje název partnerského zařízení, který se dá použít k registraci a následnému vyřešení partnerského vztahu v rámci cloudu.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord>: Definuje záznam v cloudu PNRP, který obsahuje informace o registraci pro partnera, který obsahuje koncové body sítě, na kterých se dá partnerský uzel kontaktovat.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definuje proces registrace pro název partnerského zařízení, včetně metod, jak spustit a zastavit registraci názvu rovnocenného uzlu.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver>: Definuje proces pro překlad názvu partnerského vztahu na jeho koncové body sítě, včetně synchronních i asynchronních metod pro řešení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Ukázky programování sítě](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
