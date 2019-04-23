---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 2daeb28ee984e6df576fc3da0aacc9d5f7497c96
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077495"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
Můžete vytvořit připojení mezi klienty, kteří používají [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] pomocí vazby, které popisují parametry připojení. Převod [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace peer-to-peer připojení vyžaduje vazbu, která podporuje tuto technologii při vytváření připojení klienta. Protokolu peer Channel poskytuje vazby volá <xref:System.ServiceModel.NetPeerTcpBinding>, který můžete použít podobným způsobem jako do <xref:System.ServiceModel.NetTcpBinding>. Hlavní rozdíly zahrnují určení službě překládání a definování nastavení zabezpečení.  
  
 Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převod normální klient/server – na základě aplikace pro použití protokolu Peer Channel zahrnuje změnu názvu vazby z "NetTcpBinding" k "NetPeerTcpBinding" ve vaší aplikace konfigurační soubor – není potřeba změnit základní kód aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
