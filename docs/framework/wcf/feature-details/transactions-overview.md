---
title: "Transakce ve Windows Communication Foundation – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb90d0f93e9bdf7dd9779ffd5d4b1288ba56e7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a>Transakce ve Windows Communication Foundation – přehled
Transakce poskytují způsob k seskupení sady akcí nebo operací do jedné jednotky nedělitelných provádění. Transakce je soubor operací s následujícími vlastnostmi:  
  
-   Nedělitelnost. To zajišťuje, že buď všechny aktualizace byla dokončena v rámci konkrétní transakce se potvrdí a provedené trvanlivý nebo jsou všechny přerušena a vrácena zpět do jejich předchozího stavu.  
  
-   Konzistence. To zaručuje, že změny provedené v rámci transakce představují transformaci z jednoho konzistentního stavu do jiného. Například transakci, která převádí peníze z účtu kontroluje účet nezmění množství peníze na celkové bankovní účet.  
  
-   Izolace. Tím se zabrání transakce z sledování nepotvrzené změny, které patří do dalších souběžných transakcí. Izolace poskytuje abstrakci souběžnosti při zajišťovat jednu transakci nelze mít neočekávané dopad na provádění jiné transakci.  
  
-   Odolnost. To znamená, že jakmile potvrzené, aktualizace spravované prostředky (například záznam databáze) bude trvalé při krátkodobém selhání.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje bohatou sadu funkcí, které vám umožní vytvořit distribuovaných transakcí v aplikace webové služby.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje podporu pro protokol WS-AtomicTransaction (WS-AT), který umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace tok transakcí do umožňuje vzájemnou spolupráci aplikace, jako je například umožňuje vzájemnou spolupráci webové služby vytvořené pomocí jiných výrobců technologie. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]také implementuje podporu protokolu OLE transakce, který můžete použít ve scénářích, kde není nutné spolupráce funkci, která umožní toku transakcí.  
  
 Konfigurační soubor aplikace můžete použít ke konfiguraci vazby na povolit nebo zakázat toku transakcí stejně jako nastavit požadovanou transakčního protokolu u vazby. Kromě toho můžete nastavit časové limity transakce na úrovni služby pomocí konfiguračního souboru. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Povolení toku transakcí](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Atributy transakce v <xref:System.ServiceModel> oboru názvů umožňují postupujte takto:  
  
-   Konfigurace transakce vypršení časových limitů a úroveň izolace filtrování pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut.  
  
-   Povolení funkce transakce a konfigurace pomocí chování dokončení transakce <xref:System.ServiceModel.OperationBehaviorAttribute> atribut.  
  
-   Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributů na metodu kontrakt tak, aby vyžadovala, povolit nebo odepřít toku transakcí.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Atributy transakce ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy transakce ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [Povolení toku transakcí](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
