---
title: Zápis transakční aplikace
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 048df434ff0ada2ab5f8c7473913f6c34c05d1a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793488"
---
# <a name="writing-a-transactional-application"></a>Zápis transakční aplikace
Jako programátor transakční aplikace můžete využívat výhod dvou programovacích modelů poskytované <xref:System.Transactions> obor názvů umožní vytvořit transakci. Můžete využít explicitní programovacího modelu s použitím <xref:System.Transactions.Transaction> třídy nebo implicitní programovací model, ve kterém transakce jsou automaticky spravuje infrastruktury, s použitím <xref:System.Transactions.TransactionScope> třídy. Doporučujeme použít implicitní transakce model pro vývoj. Další informace o tom, jak použít obor transakce v [implementace implicitní transakce s využitím oboru transakcí](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) tématu.  
  
 Oba modely podporují potvrzení transakcí, když program dosáhne konzistentního stavu. Pokud je potvrzení úspěšné, je transakce trvale potvrzena. Pokud se potvrzení nezdaří, přerušení transakce. Je-li program aplikace nelze úspěšně dokončit transakce, pokusí se přerušit a vrácení transakce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
### <a name="creating-a-transaction"></a>Vytváření transakcí  
 <xref:System.Transactions> Obor názvů poskytuje dva modely pro vytváření transakcí. Tyto modely jsou zahrnuta v následujících tématech.  
  
 [Implementace implicitní transakce s využitím oboru transakcí](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření implicitní transakce pomocí <xref:System.Transactions.TransactionScope> třídy.  
  
 [Implementace explicitní transakce přes CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření explicitní transakce pomocí <xref:System.Transactions.CommittableTransaction> třídy.  
  
### <a name="escalating-transaction-management"></a>Správa eskalaci transakcí  
 Když transakce musí při přístupu k prostředkům v jiné doméně aplikace, nebo pokud chcete zařadit do jiného správce prostředků trvalý, transakce je automaticky eskalován jej lze spravovat pomocí příkaz MSDTC. Eskalace transakce jsou obsaženy v [eskalace správy transakce](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tématu.  
  
### <a name="concurrency"></a>Souběžnost  
 Téma [Správa souběžnosti s DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) ukazuje, jak lze dosáhnout souběžnosti mezi asynchronní úlohy s použitím <xref:System.Transactions.DependentTransaction> třídy.  
  
### <a name="com-interop"></a>Vzájemná funkční spolupráce modelu COM +  
 Téma [interoperabilita se službami Enterprise Services a transakcemi COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) ukazuje, jak můžete provést své distribuované transakce interakci s transakcí modelu COM +.  
  
### <a name="diagnostics"></a>Diagnostika  
 [Diagnostická trasování](../../../../docs/framework/data/transactions/diagnostic-traces.md) popisuje, jak lze pomocí trasovací kódy, které se vygenerovaly <xref:System.Transactions> infrastrukturu pro řešení chyb ve vašich aplikacích.  
  
### <a name="working-within-aspnet"></a>Práce v rámci technologie ASP.NET  
 [System.Transactions v ASP.NET s využitím](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) téma popisuje, jak lze úspěšně pomocí <xref:System.Transactions> uvnitř aplikace technologie ASP.NET.
