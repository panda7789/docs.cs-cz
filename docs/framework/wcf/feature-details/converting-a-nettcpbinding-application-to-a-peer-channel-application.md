---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 362945959a781fac360c42475148fee1e47a1183
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960132"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
Můžete vytvořit připojení mezi klienty, kteří používají WinFX pomocí vazby, které popisují parametry připojení. Převedení aplikace rozhraní .NET Framework peer-to-peer připojení vyžaduje vazbu, která podporuje tuto technologii při vytváření připojení klientů. Protokolu peer Channel poskytuje vazby volá <xref:System.ServiceModel.NetPeerTcpBinding>, který můžete použít podobným způsobem jako do <xref:System.ServiceModel.NetTcpBinding>. Hlavní rozdíly zahrnují určení službě překládání a definování nastavení zabezpečení.  
  
 Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převod normální klient/server – na základě aplikace pro použití protokolu Peer Channel zahrnuje změnu názvu vazby z "NetTcpBinding" k "NetPeerTcpBinding" ve vaší aplikace konfigurační soubor – není potřeba změnit základní kód aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
