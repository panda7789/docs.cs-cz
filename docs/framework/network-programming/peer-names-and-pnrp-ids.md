---
title: Názvy partnerských uzlů a ID PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: 15b74317507f69d2339a2e5e49b54ae72cda1a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047494"
---
# <a name="peer-names-and-pnrp-ids"></a>Názvy partnerských uzlů a ID PNRP
Peer Name představuje koncový bod pro komunikaci, který může být počítač, uživatel, skupina, služba nebo cokoli přidružené k peer, které lze přeložit na adresu IPv6. Protokol PNRP (Peer Name Resolution Protocol) přebírá statisticky jedinečný název partnera pro vytvoření ID PNRP, které se používá k identifikaci členů cloudu.  
  
## <a name="peer-names"></a>Názvy rovnocenných počítačů  
 Názvy rovnocenných počítačů mohou být registrovány jako nezabezpečené nebo zabezpečené. Nezabezpečené názvy jsou pouze textové řetězce, které podléhají falšování, protože kdokoli může zaregistrovat duplicitní nezabezpečený název. Nezabezpečené názvy se nejlépe používají v privátních nebo jinak chráněných sítích. Zabezpečené názvy jsou chráněny certifikátem a digitálním podpisem. Vlastnictví zabezpečeného jména bude moci prokázat pouze původní vydavatel.  
  
 Kombinace cloudu a oboru poskytuje přiměřeně zabezpečené prostředí pro partnery, kteří se účastní aktivity PNRP. Použití zabezpečeného názvu partnera však nezajišťuje celkové zabezpečení síťové aplikace. Zabezpečení aplikace závisí na implementaci.  
  
 Zabezpečené názvy rovnocenných počítačů jsou registrovány pouze jejich vlastníkem a jsou chráněny kryptografií s veřejným klíčem. Zabezpečený název partnera je považován za vlastněný partnerem entity, která má odpovídající soukromý klíč. Vlastnictví lze prokázat prostřednictvím certifikované partnerské adresy (CPA), která je podepsána pomocí soukromého klíče. Uživatel se zlými úmysly nemůže zfalšovat vlastnictví názvu partnera bez odpovídajícího soukromého klíče.  
  
## <a name="pnrp-ids"></a>ID PNRP  
 ![PNRP ID](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 ID PNRP se skládají z následujících:  
  
- High-order 128 bitů, označované jako ID peer-to-peer (P2P), jsou hash názvu partnera přiřazeného ke koncovému bodu. Název partnera má následující formát: *Authority.Classifier*. Pro zabezpečené názvy *authority* je algoritmus secure hash 1 (SHA1) hash veřejného klíče názvu partnera v šestnáctkové znaky. Pro nezabezpečené názvy je *úřad* jediným znakem "0". *Třídění* je řetězec, který identifikuje aplikaci. Žádný klasifikátor názvu partnera může být větší `null` než 149 znaků, včetně zakončení.  
  
- Nízké pořadí 128 bitů se používají pro umístění služby, což je generované číslo, které identifikuje různé instance stejného ID P2P ve stejném cloudu.  
  
 Tato kombinace P2P ID a umístění služby umožňuje více PNRP ID, které mají být registrovány z jednoho počítače.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
