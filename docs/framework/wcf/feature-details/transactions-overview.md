---
title: Transakce ve Windows Communication Foundation – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 63f3826215f24a4bab6d84709c2f9da6a9c8f4f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communication-foundation-transactions-overview"></a>Transakce ve Windows Communication Foundation – přehled
Transakce poskytují způsob k seskupení sady akcí nebo operací do jedné jednotky nedělitelných provádění. Transakce je soubor operací s následujícími vlastnostmi:  
  
-   Nedělitelnost. To zajišťuje, že buď všechny aktualizace byla dokončena v rámci konkrétní transakce se potvrdí a provedené trvanlivý nebo jsou všechny přerušena a vrácena zpět do jejich předchozího stavu.  
  
-   Konzistence. To zaručuje, že změny provedené v rámci transakce představují transformaci z jednoho konzistentního stavu do jiného. Například transakci, která převádí peníze z účtu kontroluje účet nezmění množství peníze na celkové bankovní účet.  
  
-   Izolace. Tím se zabrání transakce z sledování nepotvrzené změny, které patří do dalších souběžných transakcí. Izolace poskytuje abstrakci souběžnosti při zajišťovat jednu transakci nelze mít neočekávané dopad na provádění jiné transakci.  
  
-   Odolnost. To znamená, že jakmile potvrzené, aktualizace spravované prostředky (například záznam databáze) bude trvalé při krátkodobém selhání.  
  
 Windows Communication Foundation (WCF) poskytuje bohatou sadu funkcí, které vám umožní vytvořit distribuovaných transakcí v aplikace webové služby.  
  
 WCF implementuje podporu pro protokol WS-AtomicTransaction (WS-AT), která umožňuje aplikacím toku transakcí umožňuje vzájemnou spolupráci aplikace, jako je například umožňuje vzájemnou spolupráci webové služby vytvořené pomocí jiných výrobců technologie WCF. WCF také implementuje podporu protokolu OLE transakce, který můžete použít ve scénářích, kde není nutné spolupráce funkci, která umožní toku transakcí.  
  
 Konfigurační soubor aplikace můžete použít ke konfiguraci vazby na povolit nebo zakázat toku transakcí stejně jako nastavit požadovanou transakčního protokolu u vazby. Kromě toho můžete nastavit časové limity transakce na úrovni služby pomocí konfiguračního souboru. Další informace najdete v tématu [povolení toku transakcí](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Atributy transakce v <xref:System.ServiceModel> oboru názvů umožňují postupujte takto:  
  
-   Konfigurace transakce vypršení časových limitů a úroveň izolace filtrování pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut.  
  
-   Povolení funkce transakce a konfigurace pomocí chování dokončení transakce <xref:System.ServiceModel.OperationBehaviorAttribute> atribut.  
  
-   Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributů na metodu kontrakt tak, aby vyžadovala, povolit nebo odepřít toku transakcí.  
  
 Další informace najdete v tématu [atributy transakce ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy transakce ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [Povolení toku transakcí](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
