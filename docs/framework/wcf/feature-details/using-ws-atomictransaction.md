---
title: Používání protokolu WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 8a8265873e4287e1455659aa4d9fae7e1d570a00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932844"
---
# <a name="using-ws-atomictransaction"></a>Používání protokolu WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) je protokol interoperabilní transakce. Umožňuje vám tok distribuovaných transakcí pomocí webové služby zpráv a koordinovat interoperabilní způsobem mezi transakce heterogenní infrastruktury. WS-AT používá protokol dvoufázového potvrzení Centrum umožňující prosazovat atomic výsledek mezi distribuovaných aplikací, transakce správci a správci prostředků.  
  
 Implementace WS-AT, kterou poskytuje Windows Communication Foundation (WCF) zahrnuje protokol služba integrovaná do správce transakcí Microsoft distribuované transakce koordinátor (MSDTC). Pomocí WS-AT aplikací WCF tok transakcí do jiných aplikací, včetně interoperabilní webové služby vytvořené pomocí technologií jiných výrobců.  
  
 Proudění transakcí mezi klientskou aplikací a serverové aplikace, protokol transakce použitý určuje vazbu, že server zpřístupní na koncový bod klienta, vybraná. Některé výchozí vazeb poskytovaných systémem WCF se zadáním `OleTransactions` protokol jako formát šíření transakcí, zatímco ostatní výchozí zadání WS-AT. Můžete také programově upravit možnost transakčního protokolu uvnitř Zadaná vazba.  
  
 Volba ovlivňuje protokolu:  
  
- Formát záhlaví zpráv používá k toku transakce z klienta na server.  
  
- Síťový protokol použitý ke spuštění protokol dvoufázového potvrzení mezi správce transakcí klienta a transakce serveru, aby bylo možné přeložit výsledek transakce.  
  
 Pokud server a klienta jsou zapsány pomocí WCF, není potřeba použít WS-AT. Místo toho můžete použít výchozí nastavení pro položky `NetTcpBinding` s `TransactionFlow` atribut povolena, pomocí něhož `OleTransactions` místo protokolu. Další informace najdete v tématu [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). V opačném případě pokud se tok transakcí do webovými službami postavenými na technologiemi třetích stran, musíte použít WS-AT.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace podpory protokolu WS-AtomicTransaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
