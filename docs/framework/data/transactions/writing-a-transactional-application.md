---
title: "Zápis transakčních aplikací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c988f5ab5a342ad3282414634ca3bfc21f481ea5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="writing-a-transactional-application"></a>Zápis transakčních aplikací
Jako programátor transakční aplikace můžete využívat výhod dvou programovacích modelů poskytované <xref:System.Transactions> obor názvů umožní vytvořit transakci. Můžete použít explicitní programovací model pomocí <xref:System.Transactions.Transaction> třídu nebo implicitní programovací model, ve kterém transakce jsou automaticky spravovány infrastrukturu, pomocí <xref:System.Transactions.TransactionScope> – třída. Doporučujeme použít model implicitní transakci pro vývoj. Můžete najít další informace o tom, jak používat v oboru transakce [implementace implicitní transakci pomocí oboru transakce](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) tématu.  
  
 Oba modely podporují potvrzení transakcí, když program dosáhne konzistentního stavu. Pokud je potvrzení úspěšné, je transakce trvale potvrzena. Pokud se potvrzení nezdaří, přerušení transakce. Je-li program aplikace nelze úspěšně dokončit transakce, pokusí se přerušit a vrácení transakce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
### <a name="creating-a-transaction"></a>Vytváření transakcí  
 <xref:System.Transactions> Obor názvů poskytuje dva modely pro vytváření transakcí. Tyto modely jsou popsané v následujících tématech.  
  
 [Implementace implicitní transakci pomocí oboru transakce](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Popisuje, jak <xref:System.Transactions> obor názvů podporuje vytváření implicitní transakce pomocí <xref:System.Transactions.TransactionScope> třídy.  
  
 [Implementace explicitní transakce pomocí CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
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
