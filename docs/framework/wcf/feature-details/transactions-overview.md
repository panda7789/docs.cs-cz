---
title: Transakce ve Windows Communication Foundation – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: a8e3306612e016568ad7cfd5138ab538af771a17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585828"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Transakce ve Windows Communication Foundation – přehled
Transakce poskytují způsob, jak seskupit sadu akcí nebo operací do jedné neoddělitelné jednotky spuštění. Transakce je kolekce operací s následujícími vlastnostmi:  
  
- Atomicitu. Tím se zajistí, že všechny aktualizace dokončené v určité transakci jsou potvrzené a mají trvalé nebo všechny jsou přerušené a vrátí se zpátky do předchozího stavu.  
  
- Shody. To zaručuje, že změny provedené v transakci reprezentují transformaci z jednoho konzistentního stavu na jiný. Například transakce, která přenáší peníze z účtu pro kontrolu na účet úspory, nemění množství peněz v rámci celkového bankovního účtu.  
  
- Izolace. To brání transakci v pozorování nepotvrzených změn, které patří do jiných souběžných transakcí. Izolace poskytuje abstrakci souběžnosti a zároveň zajišťuje, že jedna transakce nemůže mít neočekávaný dopad na provedení jiné transakce.  
  
- Vlastností. To znamená, že po potvrzení budou aktualizace spravovaných prostředků (například záznamu v databázi) trvalé při selhání.  
  
 Windows Communication Foundation (WCF) poskytuje bohatou sadu funkcí, které umožňují vytvářet distribuované transakce v aplikaci webové služby.  
  
 Služba WCF implementuje podporu pro protokol WS-AtomicTransaction (WS-AT), který umožňuje aplikacím WCF tok transakcí do interoperabilních aplikací, jako jsou interoperabilní webové služby vytvořené pomocí technologie třetích stran. WCF také implementuje podporu protokolu OLE Transactions, který může být použit ve scénářích, kde nepotřebujete funkce spolupráce, aby bylo možné tok transakcí povolit.  
  
 Konfigurační soubor aplikace můžete použít ke konfiguraci vazeb pro povolení nebo zakázání toku transakce a také k nastavení požadovaného transakčního protokolu pro vazbu. Kromě toho můžete nastavit časový limit transakcí na úrovni služby pomocí konfiguračního souboru. Další informace najdete v tématu [Povolení toku transakce](enabling-transaction-flow.md).  
  
 Atributy transakce v <xref:System.ServiceModel> oboru názvů umožňují následující akce:  
  
- Nakonfigurujte časové limity transakce a filtrování na úrovni izolace pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu.  
  
- Povolte funkce transakcí a nakonfigurujte chování při dokončování transakcí pomocí <xref:System.ServiceModel.OperationBehaviorAttribute> atributu.  
  
- Použijte <xref:System.ServiceModel.ServiceContractAttribute> atributy a <xref:System.ServiceModel.OperationContractAttribute> v metodě kontraktu pro vyžadování, povolení nebo zamítnutí toku transakce.  
  
 Další informace najdete v tématu [atributy transakce ServiceModel](servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Viz také

- [Atributy transakce ServiceModel](servicemodel-transaction-attributes.md)
- [Povolení toku transakcí](enabling-transaction-flow.md)
