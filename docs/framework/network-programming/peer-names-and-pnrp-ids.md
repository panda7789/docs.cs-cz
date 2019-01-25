---
title: Názvy partnerských uzlů a ID PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: 3f82d472e1f8913e2f518abbefa2bb6407d6f54c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690785"
---
# <a name="peer-names-and-pnrp-ids"></a>Názvy partnerských uzlů a ID PNRP
Název partnerského zařízení představuje koncový bod pro komunikaci, která může být počítač, uživatele, skupinu, služby nebo něco přidružené partnera, který lze převést na IPv6 adresu. Řešení protokolu PNRP (Peer Name) trvá statisticky jedinečný. název partnerského zařízení pro zřízení ID PNRP, který slouží k určení členů cloudu.  
  
## <a name="peer-names"></a>Názvy partnerských uzlů  
 Názvy partnerských uzlů může být registrován jako nezabezpečená nebo zabezpečené. Zabezpečená názvy jsou pouze textové řetězce, které jsou v souladu s falšování identity, všem uživatelům registrovat duplicitní název zabezpečená. Zabezpečená názvy uplatňují nejlépe v privátní nebo jinak chráněných sítích. Zabezpečené názvy jsou chráněné pomocí certifikátu a digitální podpis. Pouze původní vydavatel bude možné prokázat, že vlastnictví názvu zabezpečené.  
  
 Kombinace cloudu a oboru poskytuje rozumně zabezpečené prostředí pro partnerské uzly, které jsou součástí PNRP aktivity. Pomocí názvu zabezpečené sdílené ale nezajistí celkové zabezpečení síťové aplikace. Zabezpečení aplikace je závislý na implementaci.  
  
 Názvy partnerských uzlů zabezpečené jsou registrovány pouze jeho vlastník a jsou chráněné službou kryptografii využívající veřejného klíče. Název zabezpečené partnera se považuje za vlastněné sdílené entity s odpovídající privátní klíč. Vlastnictví můžete prokázat prostřednictvím certifikovaného partnera adresy (CPA), která je podepsána pomocí soukromého klíče. Uživatel se zlými úmysly nemůže zfalšovat vlastnictví název partnerského zařízení bez odpovídajícího privátního klíče.  
  
## <a name="pnrp-ids"></a>ID PNRP  
 ![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 ID PNRP se skládá z následujících akcí:  
  
-   128 bitů nejvyšším označovaný jako ID (P2P) peer-to-peer, jsou hodnoty hash název partnerského zařízení přiřazené ke koncovému bodu. Název partnerského zařízení má následující formát: *Authority.Classifier*. Pro zabezpečené názvy *autority* je zabezpečit hashovací algoritmus (SHA1 1) hodnota hash veřejného klíče v šestnáctkové znaky názvu partnera. Pro nezabezpečený názvy *autority* je jednoho znaku "0". *Třídění* je řetězec, který identifikuje aplikaci. Žádné sdílené název třídění může být větší než 149 znaků, včetně `null` ukončovací znak.  
  
-   Nižšího řádu 128 bitů se používá pro umístění služby, což je generované číslo, který identifikuje různé instance stejné ID P2P ve stejném cloudu.  
  
 Tato kombinace P2P ID a umístění služby umožňuje víc ID PNRP k registraci z jednoho počítače.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
