---
title: Používání protokolu WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 71090efbb096bc3b7b3d6bcf40ff496b78ac6252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600682"
---
# <a name="using-ws-atomictransaction"></a>Používání protokolu WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) je interoperabilní transakční protokol. Umožňuje flowovat distribuované transakce pomocí zpráv webové služby a mezi heterogenními transakčními infrastrukturami koordinovat vzájemně ovladatelné způsoby. WS-AT používá protokol dvoufázového potvrzení k řízení atomické výsledku mezi distribuovanými aplikacemi, správci transakcí a správci prostředků.  
  
 Implementace Windows Communication Foundation WCF (WS-AT Implementation) obsahuje službu protokolu, která je integrovaná do správce transakcí služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC). Pomocí WS-AT můžou aplikace WCF přesměrovat transakce do jiných aplikací, včetně interoperabilních webových služeb vytvořených pomocí technologie třetích stran.  
  
 Při toku transakce mezi klientskou aplikací a serverovou aplikací je použit protokol transakcí, který je určen vazbou, kterou server vystavuje na koncovém bodu vybraný klientem. Některé vazby poskytované systémem WCF standardně zadávají `OleTransactions` protokol jako formát šíření transakce, zatímco jiné výchozí určení protokolu WS-AT. Můžete také programově změnit volbu transakčního protokolu uvnitř dané vazby.  
  
 Volba vlivu protokolu:  
  
- Formát záhlaví zpráv použitých k flowování transakce z klienta na server.  
  
- Síťový protokol používaný ke spuštění dvoufázového protokolu potvrzení mezi správcem transakcí klienta a transakcí serveru, aby bylo možné vyřešit výsledek transakce.  
  
 Pokud se server a klient napíší pomocí WCF, nemusíte používat WS-AT. Místo toho můžete použít výchozí nastavení `NetTcpBinding` s `TransactionFlow` povoleným atributem, který bude `OleTransactions` místo toho používat protokol. Další informace najdete na webu [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md). V opačném případě, pokud provádíte tok transakcí do webových služeb postavených na technologiích třetích stran, je nutné použít WS-AT.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace podpory protokolu WS-AT (WS-Atomic Transactions)](configuring-ws-atomic-transaction-support.md)
