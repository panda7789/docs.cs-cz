---
title: "Vrácení transakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaebbb7fa2e6e0420243c32cb70c64092ea86fa7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-rollback"></a>Vrácení transakce
Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Activities.NativeActivity> který přistupuje k vedlejším <xref:System.Activities.RuntimeTransactionHandle> získat vedlejším transakce a explicitně vrátit zpět.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V pracovním postupu, transakce je automaticky při dokončení krajních <xref:System.Activities.Statements.TransactionScope> nebo <xref:System.ServiceModel.Activities.TransactedReceiveScope> dokončení.  Transakce implicitně zobrazí zpět v případě, že k neošetřené výjimce šíří přes hranice oboru. Však může nastat situace, kdy má smysl explicitně bez nutnosti výjimku vrácení transakce. V takovém případě můžete aktivity vlastní vrácení zpět jako jeden v této ukázce explicitně přerušení vedlejším transakce a zadejte z důvodu výjimky volitelné.  
  
 `RollbackActivity` Je <xref:System.Activities.NativeActivity> jak to vyžaduje přístup k vlastnostem provádění získat vedlejším <xref:System.Activities.RuntimeTransactionHandle>. V `Execute` metoda, získá <xref:System.Activities.RuntimeTransactionHandle> a zkontroluje, zda je `null`, což naznačuje, že aktivita byl použit bez ambientní spuštění transakce. Poté získá transakce, znovu kontrola zda `null` je k dispozici. Je možné, že vedlejším <xref:System.Activities.RuntimeTransactionHandle> bez někdy inicializace spuštění transakce. Nakonec zruší transakce voláním <xref:System.Transactions.Transaction.Rollback%2A> a zadání výjimka zadaný uživatelem nebo obecná výjimka, která uvádí, že aktivita vrátila zpět transakci.  
  
 Ukázkový pracovní postup se skládá z <xref:System.Activities.Statements.TransactionScope> jehož subjekt vytiskne stav transakce před a po `RollbackActivity` provede. Všimněte si, že i když transakce byla vrácena zpět, <xref:System.Activities.Statements.TransactionScope> provede dokončen a není přerušení pracovního postupu, dokud se nedokončí text. Pracovní postup byl přerušen, protože <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> výchozí nastavení vlastnosti `true`.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Spouštění řešení TransactionRollback.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>Viz také  
 [Transakce](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
