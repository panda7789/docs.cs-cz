---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: b89afbe59b73288ba357fa55ec5d55c1fb18352b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582783"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
Můžete vytvořit připojení mezi klienty, kteří používají [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] pomocí vazby, které popisují parametry připojení. Převedení aplikace rozhraní .NET Framework peer-to-peer připojení vyžaduje vazbu, která podporuje tuto technologii při vytváření připojení klientů. Protokolu peer Channel poskytuje vazby volá <xref:System.ServiceModel.NetPeerTcpBinding>, který můžete použít podobným způsobem jako do <xref:System.ServiceModel.NetTcpBinding>. Hlavní rozdíly zahrnují určení službě překládání a definování nastavení zabezpečení.  
  
 Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převod normální klient/server – na základě aplikace pro použití protokolu Peer Channel zahrnuje změnu názvu vazby z "NetTcpBinding" k "NetPeerTcpBinding" ve vaší aplikace konfigurační soubor – není potřeba změnit základní kód aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
