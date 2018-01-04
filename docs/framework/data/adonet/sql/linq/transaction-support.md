---
title: "Podpora transakcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 79cd52f137347ec24e7cc9a646d0306d95fe53d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-support"></a>Podpora transakcí
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje tři modely odlišné transakcí. Následující seznam obsahuje tyto modely v pořadí provést kontroly.  
  
## <a name="explicit-local-transaction"></a>Explicitní místní transakce  
 Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána, pokud <xref:System.Data.Linq.DataContext.Transaction%2A> je nastavena na (`IDbTransaction`) transakce, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volání je provést v rámci stejné transakci.  
  
 Je vaší povinností potvrzení nebo vrácení změn transakce po úspěšné provedení transakce. Připojení odpovídající transakce musí odpovídat připojení používané pro tvorbu <xref:System.Data.Linq.DataContext>. Pokud se používá jiné připojení, je vyvolána výjimka.  
  
## <a name="explicit-distributable-transaction"></a>Explicitní distribuovatelného transakce  
 Můžete volat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozhraní API (mimo jiné včetně <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) v rámci oboru aktivní <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zjistí, že volání je v oboru transakce a nevytvoří nové transakce. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]také je zabráněno v tomto případě Probíhá ukončování připojení. Můžete provést dotaz a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> spuštěních v kontextu tuto transakci.  
  
## <a name="implicit-transaction"></a>Implicitní transakce  
 Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kontroluje, zda volání je v oboru <xref:System.Transactions.Transaction> nebo, pokud `Transaction` vlastnost (`IDbTransaction`) je nastaven na spuštění uživatele místní transakce. Pokud najde ani transakce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí místní transakce (`IDbTransaction`) a používá je generovaný příkazy SQL. Po úspěšném dokončení všechny příkazy SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] potvrdí místní transakci a vrátí.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Postupy: Vytvoření transakčních sad pro odesílání dat](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
