---
title: Zápis transakční aplikace
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 318771c83a5b7ebc0f3fb2bb8c59240269a2dea9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205820"
---
# <a name="writing-a-transactional-application"></a>Zápis transakční aplikace
Jako programátor transakční aplikace můžete využívat výhod dvou programovacích modelů poskytované <xref:System.Transactions> obor názvů umožní vytvořit transakci. Můžete využít explicitní programovací model pomocí <xref:System.Transactions.Transaction> třídy nebo implicitní programovací model, ve kterém jsou transakce automaticky spravovány infrastrukturou, <xref:System.Transactions.TransactionScope> pomocí třídy. Doporučujeme použít implicitní model transakce pro vývoj. Další informace o tom, jak používat obor transakce v tématu [implementace implicitní transakce pomocí oboru transakce](implementing-an-implicit-transaction-using-transaction-scope.md) , najdete v tématu.  
  
 Oba modely podporují potvrzení transakcí, když program dosáhne konzistentního stavu. Pokud je potvrzení úspěšné, je transakce trvale potvrzena. Pokud se potvrzení nezdaří, přerušení transakce. Je-li program aplikace nelze úspěšně dokončit transakce, pokusí se přerušit a vrácení transakce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
### <a name="creating-a-transaction"></a>Vytváření transakcí  
 <xref:System.Transactions> Obor názvů poskytuje dva modely pro vytváření transakcí. Tyto modely jsou pokryté v následujících tématech.  
  
 [Implementace implicitní transakce s využitím oboru transakcí](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření implicitní transakce pomocí <xref:System.Transactions.TransactionScope> třídy.  
  
 [Implementace explicitní transakce přes CommittableTransaction](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření explicitní transakce pomocí <xref:System.Transactions.CommittableTransaction> třídy.  
  
### <a name="escalating-transaction-management"></a>Správa eskalaci transakcí  
 Když transakce musí při přístupu k prostředkům v jiné doméně aplikace, nebo pokud chcete zařadit do jiného správce prostředků trvalý, transakce je automaticky eskalován jej lze spravovat pomocí příkaz MSDTC. Eskalace transakce je zahrnuta v tématu [Eskalace správy transakcí](transaction-management-escalation.md) .  
  
### <a name="concurrency"></a>Souběžnost  
 Téma [Správa souběžnosti s funkce DependentTransaction](managing-concurrency-with-dependenttransaction.md) ukazuje, jak lze dosáhnout souběžnosti mezi asynchronními úlohami pomocí <xref:System.Transactions.DependentTransaction> třídy.  
  
### <a name="com-interop"></a>Vzájemná funkční spolupráce modelu COM +  
 Téma [interoperabilita se službami Enterprise Services a transakcemi modelu COM+](interoperability-with-enterprise-services-and-com-transactions.md) znázorňuje, jak můžete distribuované transakce pracovat s transakcemi modelu COM+.  
  
### <a name="diagnostics"></a>Diagnostika  
 [Diagnostické trasování](diagnostic-traces.md) popisuje, jak můžete použít kódy trasování, které jsou generovány <xref:System.Transactions> infrastrukturou, k řešení chyb ve vašich aplikacích.  
  
### <a name="working-within-aspnet"></a>Práce v rámci technologie ASP.NET  
 Téma [using System. Transactions v ASP.NET](using-system-transactions-in-aspnet.md) popisuje, jak lze úspěšně použít <xref:System.Transactions> v rámci aplikace ASP.NET.
