---
title: Transakce ve Windows Communication Foundation – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 42276a9b450b6f0664901747239195ab13f7c44d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223105"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Transakce ve Windows Communication Foundation – přehled
Transakce poskytují způsob seskupení sady akcí nebo operací do jedné jednotky nedělitelných spuštění. Transakce je soubor operací s následujícími vlastnostmi:  
  
-   Atomicitu. Tím se zajistí, že všechny aktualizace dokončeno v rámci konkrétní transakce potvrzena a chrání nebo jsou všechny přerušena a vrátit zpět do jejich předchozího stavu.  
  
-   Konzistence. Zaručí se tak, že změny provedené v rámci transakce představují transformace z jednoho konzistentní stavu do druhého. Například transakce, které se přenese z účtu kontroluje peníze účet nezmění množství peníze celkové bankovním účtu.  
  
-   Izolace. To zabraňuje transakce pozorovat nepotvrzené změny, které patří do jiných souběžných transakcí. Izolace poskytuje abstrakci souběžnosti přitom zajistit jedna transakce nemůže mít neočekávané vliv na provádění jiné transakci.  
  
-   Odolnost. To znamená, že po potvrzení aktualizací pro spravované prostředky (například záznam v databázi) bude trvalé i v případě selhání.  
  
 Windows Communication Foundation (WCF) poskytuje bohatou sadu funkcí, které umožňují vytvářet distribuované transakce ve webové aplikaci služby.  
  
 WCF implementuje podporu protokolu WS-AtomicTransaction (WS-AT), která umožňuje aplikacím WCF tok transakcí, které interoperabilní aplikací, jako je například interoperabilní webové služby vytvořené pomocí technologií jiných výrobců. WCF také implementuje podporu pro protokol transakcí OLE, který můžete použít ve scénářích, kdy není nutné spolupráce funkce, které umožňují tok transakcí.  
  
 Konfigurační soubor aplikace můžete použít ke konfiguraci vazby na povolit nebo zakázat tok transakcí a také jako nastavte požadovaný transakčního protokolu na vazbu. Kromě toho můžete nastavit časové limity transakcí na úrovni služby, který je používán konfigurační soubor. Další informace najdete v tématu [povolení toku transakcí](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Atributy transakce v <xref:System.ServiceModel> oboru názvů umožňují postupujte takto:  
  
-   Nakonfigurujte časové limity transakcí a úroveň izolace filtrování pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut.  
  
-   Povolit funkci transakce a nakonfigurujte pomocí chování dokončení transakce <xref:System.ServiceModel.OperationBehaviorAttribute> atribut.  
  
-   Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributů pro metodu smlouvy tak, aby vyžadovala, povolit nebo odepřít tok transakcí.  
  
 Další informace najdete v tématu [atributy transakce ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Viz také:

- [Atributy transakce ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)
- [Povolení toku transakcí](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
