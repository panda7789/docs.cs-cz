---
title: Názvy partnerů a ID PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 02e6d65baac0a0eab9bfde545a117d3636239c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="peer-names-and-pnrp-ids"></a>Názvy partnerů a ID PNRP
Název partnerského zařízení představuje koncový bod pro komunikaci, což může být do počítače, uživatele, skupiny, službou nebo nic přidružené partnerského uzlu, který lze přeložit na adresu IPv6. Řešení protokolu PNRP (Peer Name) trvá statisticky jedinečný název partnerského zařízení pro vytvoření PNRP ID, které slouží k identifikaci členů cloudu.  
  
## <a name="peer-names"></a>Názvy partnerů  
 Názvy partnerů může být registrován jako nezabezpečená nebo zabezpečené. Zabezpečená názvy jsou pouze textové řetězce, které se vztahují falšování identity, každý, kdo může registraci duplicitní název zabezpečená. Zabezpečená názvy jsou nejvhodnější v privátní nebo jinak chráněné sítě. Zabezpečené názvy jsou chráněny certifikát a digitální podpis. Původní vydavatel bude schopni prokázat vlastnictví zabezpečený název.  
  
 Kombinace cloudu a oboru poskytuje přiměřené zabezpečeném prostředí pro partnerské uzly, které jsou součástí PNRP aktivity. Pomocí názvu zabezpečené sdílené ale nezajišťuje celkového zabezpečení síťových aplikací. Zabezpečení aplikace je závislá na implementaci.  
  
 Zabezpečené sdílené názvy jsou registrovat jenom podle jejich vlastníka a jsou chráněné službou kryptografie využívající veřejného klíče. Název zabezpečené partnera považuje za vlastní sdílené entita má odpovídající soukromý klíč. Vlastnictví lze prokázat přes adresu certifikovaných sdílené (CPA), která je podepsaná pomocí soukromého klíče. Uživatel se zlými úmysly nelze forge vlastnictví název partnerského zařízení bez odpovídajícího privátního klíče.  
  
## <a name="pnrp-ids"></a>ID PNRP  
 ![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 ID PNRP se skládají z následujících akcí:  
  
-   Nejvyšších 128 bitů, označované jako ID peer-to-peer (P2P), je hodnota hash název partnera přiřazené ke koncovému bodu. Název partnerského zařízení má následující formát: *Authority.Classifier*. Pro zabezpečené názvy *autority* je Secure Hash Algorithm 1 (SHA1) hodnota hash veřejného klíče pro název partnerského zařízení v hexadecimálních znaků. Pro zabezpečená názvy *autority* je jeden znak "0". *Klasifikátor* je řetězec, který identifikuje aplikaci. Žádné sdílené název třídění může být větší než 149 znaků včetně `null` ukončovací znak.  
  
-   Nejnižší 128 bitů se používá pro umístění služby, což je generovaným číslem, který identifikuje různé instance stejné ID P2P ve stejném cloudu.  
  
 Tato kombinace P2P ID a umístění služby umožňuje více ID PNRP registraci z jednoho počítače.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer.PeerName>  
 <xref:System.Net.PeerToPeer>
