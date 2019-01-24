---
title: Podpora transakcí
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: f53a6081102991c73543b4cd76365f7e2c0faf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517198"
---
# <a name="transaction-support"></a>Podpora transakcí
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje tři modely odlišné transakcí. Následuje seznam těchto modelů v pořadí kontroly.  
  
## <a name="explicit-local-transaction"></a>Explicitní místní transakce  
 Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána, pokud <xref:System.Data.Linq.DataContext.Transaction%2A> je nastavena na (`IDbTransaction`) transakce, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> provádění volání v rámci stejné transakce.  
  
 Je vaší odpovědností, abyste potvrzení nebo vrácení zpět transakcí po úspěšném spuštění transakce. Připojení odpovídající transakce musí odpovídat připojení použité pro tvorbu <xref:System.Data.Linq.DataContext>. Pokud se používá jiné připojení, je vyvolána výjimka.  
  
## <a name="explicit-distributable-transaction"></a>Explicitní Distribuovatelný transakce  
 Můžete volat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozhraní API (včetně, ale nikoli výhradně <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) v rámci aktivní <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zjistí, že volání je v oboru transakce a nevytvoří novou transakci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] také se vyhnete v tomto případě Probíhá ukončování připojení. Provedením dotazu a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> prováděných v rámci těchto transakcí.  
  
## <a name="implicit-transaction"></a>Implicitní transakce  
 Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kontroluje, zda je v rámci volání <xref:System.Transactions.Transaction> nebo, pokud `Transaction` vlastnosti (`IDbTransaction`) je nastavena na místní transakce uživatel začal. Pokud najde žádná transakce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí místní transakce (`IDbTransaction`) a používá ke spouštění generované příkazů SQL. Po úspěšném dokončení všech příkazů SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] potvrzení místní transakci a vrátí.  
  
## <a name="see-also"></a>Viz také:
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Postupy: Závorky odeslání dat pomocí transakce](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
