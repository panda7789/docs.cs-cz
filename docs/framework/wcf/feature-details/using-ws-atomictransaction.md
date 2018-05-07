---
title: Používání protokolu WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 7880d46d4827b36c7806c61877edf79faa766371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-ws-atomictransaction"></a>Používání protokolu WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) je protokol umožňuje vzájemnou spolupráci transakce. Umožňuje toku distribuované transakce prostřednictvím zpráv, webové služby a koordinovat způsobem umožňuje vzájemnou spolupráci mezi infrastruktury heterogenní transakce. WS-AT používá protokol dvoufázový zápis k řízení atomic výsledek mezi distribuovaných aplikací, správci transakcí a správci prostředků.  
  
 WS-AT implementace, které poskytuje Windows Communication Foundation (WCF) zahrnuje protokol služby integrovaný do správce transakcí Microsoft Distributed Transaction Coordinator služba MSDTC (). Pomocí protokolu WS-AT, aplikace WCF tok transakcí do jiných aplikací, včetně interoperabilní webové služby vytvořené pomocí technologie třetích stran.  
  
 Při toku transakce mezi klientské aplikace a aplikace serveru, transakční protokol použitý je určen podle vazby, že serveru zpřístupní v koncovém bodě klienta vybrané. Některé výchozí vazby poskytované systémem WCF k určení `OleTransactions` protokol jako formát šíření transakce, zatímco ostatní výchozí k určení WS-AT. Můžete také prostřednictvím kódu programu upravit volba transakčního protokolu v dané vazby.  
  
 Volba vlivy protokolu:  
  
-   Formát hlavičky zpráv použije k posunutí transakce z klienta na server.  
  
-   Síťový protokol použitý ke spuštění protokolu dvoufázového potvrzení mezi správce transakcí klienta a transakce serveru, aby bylo možné vyřešit výsledek transakce.  
  
 Pokud serveru a klienta jsou zapsány pomocí WCF, není potřeba použít WS-AT. Místo toho můžete použít výchozí nastavení `NetTcpBinding` s `TransactionFlow` povoleno, atribut, který bude používat `OleTransactions` místo protokolu. Další informace najdete v tématu [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). Jinak pokud jsou toku transakcí k webovým službám založen na technologiích třetích stran, musíte použít WS-AT.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace podpory protokolu WS-AtomicTransaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
