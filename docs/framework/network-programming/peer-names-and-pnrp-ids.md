---
title: Názvy partnerských uzlů a ID PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: 15b74317507f69d2339a2e5e49b54ae72cda1a7b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047494"
---
# <a name="peer-names-and-pnrp-ids"></a>Názvy partnerských uzlů a ID PNRP
Partnerský název představuje koncový bod pro komunikaci. může to být počítač, uživatel, skupina, služba nebo cokoli spojené s partnerským vztahem, který je možné přeložit na adresu IPv6. Protokol PNRP (Peer Name Resolution Protocol) používá statisticky jedinečný název partnerského zařízení pro vytvoření ID PNRP, které se používá k identifikaci členů cloudu.  
  
## <a name="peer-names"></a>Názvy partnerů  
 Názvy partnerů můžou být registrované jako nezabezpečené nebo zabezpečené. Nezabezpečené názvy jsou pouze textové řetězce, které podléhají falšování identity, protože kdokoli může zaregistrovat duplicitní nezabezpečený název. Nezabezpečené názvy se nejlépe využívají v privátních nebo v chráněných sítích. Zabezpečené názvy jsou chráněny certifikátem a digitálním podpisem. Vlastnictví zabezpečeného názvu bude moci prokázat pouze původní Vydavatel.  
  
 Kombinace cloudu a oboru poskytuje dostatečně zabezpečené prostředí pro partnery, kteří se účastní aktivity PNRP. Použití zabezpečeného partnerského názvu ale nezajišťuje celkové zabezpečení síťové aplikace. Zabezpečení aplikace je závislé na implementaci.  
  
 Názvy zabezpečených partnerských uzlů jsou registrované jenom jejich vlastníkem a jsou chráněné pomocí kryptografie s veřejným klíčem. Název zabezpečeného partnerského vztahu je považován za vlastněný entitou peer s odpovídajícím privátním klíčem. Vlastnictví se dá prokázat prostřednictvím certifikovaného partnerského adresy (CPA), která je podepsaná pomocí privátního klíče. Uživatel se zlými úmysly nemůže zfalšovat vlastnictví partnerského názvu bez odpovídajícího privátního klíče.  
  
## <a name="pnrp-ids"></a>Identifikátory PNRP  
 ![PNRP ID](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 Identifikátory PNRP se skládají z těchto možností:  
  
- Vysoké pořadí 128 bitů, označované jako ID partnerského vztahu (P2P), jsou hodnota hash rovnocenného názvu, který je přiřazen ke koncovému bodu. Název partnerského zařízení má následující formát: *Autorita. klasifikátor* U zabezpečených názvů *autorita* je hodnota hash algoritmus SHA-1 (Secure Hash ALGORITHM) (SHA1) veřejného klíče názvu partnera v šestnáctkových znacích. U nezabezpečených názvů je *autorita* jedním znakem "0". *Klasifikátor* je řetězec, který identifikuje aplikaci. Žádné třídění rovnocenných názvů nesmí být delší než 149 znaků, včetně `null` ukončovacího znaku.  
  
- Pro umístění služby se používají bity s nízkou úrovní 128, což je vygenerované číslo, které identifikuje různé instance stejného ID P2P ve stejném cloudu.  
  
 Tato kombinace ID a umístění služby P2P umožňuje registraci více identifikátorů PNRP z jednoho počítače.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
