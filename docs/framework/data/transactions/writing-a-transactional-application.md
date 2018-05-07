---
title: Zápis transakčních aplikací
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 048df434ff0ada2ab5f8c7473913f6c34c05d1a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="writing-a-transactional-application"></a>Zápis transakčních aplikací
Jako programátor transakční aplikace můžete využívat výhod dvou programovacích modelů poskytované <xref:System.Transactions> obor názvů umožní vytvořit transakci. Můžete použít explicitní programovací model pomocí <xref:System.Transactions.Transaction> třídu nebo implicitní programovací model, ve kterém transakce jsou automaticky spravovány infrastrukturu, pomocí <xref:System.Transactions.TransactionScope> – třída. Doporučujeme použít model implicitní transakci pro vývoj. Můžete najít další informace o tom, jak používat v oboru transakce [implementace implicitní transakci pomocí oboru transakce](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) tématu.  
  
 Oba modely podporují potvrzení transakcí, když program dosáhne konzistentního stavu. Pokud je potvrzení úspěšné, je transakce trvale potvrzena. Pokud se potvrzení nezdaří, přerušení transakce. Je-li program aplikace nelze úspěšně dokončit transakce, pokusí se přerušit a vrácení transakce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
### <a name="creating-a-transaction"></a>Vytváření transakcí  
 <xref:System.Transactions> Obor názvů poskytuje dva modely pro vytváření transakcí. Tyto modely jsou popsané v následujících tématech.  
  
 [Implementace implicitní transakce s využitím oboru transakcí](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření implicitní transakce pomocí <xref:System.Transactions.TransactionScope> třídy.  
  
 [Implementace explicitní transakce přes CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření explicitní transakce pomocí <xref:System.Transactions.CommittableTransaction> třídy.  
  
### <a name="escalating-transaction-management"></a>Správa eskalaci transakcí  
 Když transakce musí při přístupu k prostředkům v jiné doméně aplikace, nebo pokud chcete zařadit do jiného správce prostředků trvalý, transakce je automaticky eskalován jej lze spravovat pomocí příkaz MSDTC. Najdete v článku eskalace transakce [transakce správu eskalace](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tématu.  
  
### <a name="concurrency"></a>Souběžnost  
 V tématu [Správa souběžnosti s DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) ukazuje, jak jde dosáhnout souběžnosti mezi asynchronních úloh pomocí <xref:System.Transactions.DependentTransaction> třídy.  
  
### <a name="com-interop"></a>Vzájemná funkční spolupráce modelu COM +  
 Téma [vzájemná funkční spolupráce s Enterprise služeb a transakcí modelu COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) ukazuje, jak provést vaší distribuovaných transakcí v interakci s transakcí modelu COM +.  
  
### <a name="diagnostics"></a>Diagnostika  
 [Diagnostické trasování](../../../../docs/framework/data/transactions/diagnostic-traces.md) popisuje, jak můžete použít trasování kódy, které jsou generované <xref:System.Transactions> infrastrukturu pro odstraňování chyb ve svých aplikacích.  
  
### <a name="working-within-aspnet"></a>Práce v rámci technologie ASP.NET  
 [System.Transactions pomocí technologie ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) téma popisuje, jak můžete úspěšně použít <xref:System.Transactions> uvnitř aplikace ASP.NET.
