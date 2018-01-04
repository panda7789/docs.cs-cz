---
title: "Používání protokolu WS-AtomicTransaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 124c5dc0f6db94ae459fe140bd7a4290aa56e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-ws-atomictransaction"></a>Používání protokolu WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) je protokol umožňuje vzájemnou spolupráci transakce. Umožňuje toku distribuované transakce prostřednictvím zpráv, webové služby a koordinovat způsobem umožňuje vzájemnou spolupráci mezi infrastruktury heterogenní transakce. WS-AT používá protokol dvoufázový zápis k řízení atomic výsledek mezi distribuovaných aplikací, správci transakcí a správci prostředků.  
  
 Implementace služby WS-AT [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] poskytuje zahrnuje protokol služby integrovaný do správce transakcí Microsoft Distributed Transaction Coordinator služba MSDTC (). Pomocí protokolu WS-AT [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace můžete tok transakcí do jiných aplikací, včetně interoperabilní webové služby vytvořené pomocí technologie třetích stran.  
  
 Při toku transakce mezi klientské aplikace a aplikace serveru, transakční protokol použitý je určen podle vazby, že serveru zpřístupní v koncovém bodě klienta vybrané. Některé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výchozí vazby poskytované systémem k určení `OleTransactions` protokol jako formát šíření transakce, zatímco ostatní výchozí k určení WS-AT. Můžete také prostřednictvím kódu programu upravit volba transakčního protokolu v dané vazby.  
  
 Volba vlivy protokolu:  
  
-   Formát hlavičky zpráv použije k posunutí transakce z klienta na server.  
  
-   Síťový protokol použitý ke spuštění protokolu dvoufázového potvrzení mezi správce transakcí klienta a transakce serveru, aby bylo možné vyřešit výsledek transakce.  
  
 Pokud serveru a klienta jsou zapsány pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], není potřeba použít WS-AT. Místo toho můžete použít výchozí nastavení `NetTcpBinding` s `TransactionFlow` povoleno, atribut, který bude používat `OleTransactions` místo protokolu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). Jinak pokud jsou toku transakcí k webovým službám založen na technologiích třetích stran, musíte použít WS-AT.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace podpory protokolu WS-AtomicTransaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
