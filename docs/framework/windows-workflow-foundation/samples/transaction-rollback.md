---
title: Odvolání transakce
ms.date: 03/30/2017
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
ms.openlocfilehash: 8134623248b072ec5a095ab9b10840e94a09243c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528974"
---
# <a name="transaction-rollback"></a>Odvolání transakce
Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Activities.NativeActivity> , který přistupuje k okolí <xref:System.Activities.RuntimeTransactionHandle> okolí transakce a explicitně ji vrátit zpět.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V pracovním postupu, je automaticky transakce po dokončení nejkrajnější <xref:System.Activities.Statements.TransactionScope> nebo <xref:System.ServiceModel.Activities.TransactedReceiveScope> dokončí.  Transakce implicitně vrátí zpět, když k neošetřené výjimce rozšíří do hranic rozsahu. Ale může nastat situace, kdy je vhodné explicitně vrácení zpět transakcí bez nutnosti vyvolání výjimky. V takovém případě můžete použít aktivitu vlastní vrácení zpět jako jednu v této ukázce je explicitně zrušení okolí transakce a poskytovat z důvodu výjimky volitelné.  
  
 `RollbackActivity` Je <xref:System.Activities.NativeActivity> vyžaduje přístup k vlastnostem spuštění zobrazíte okolí <xref:System.Activities.RuntimeTransactionHandle>. V `Execute` metoda, získá <xref:System.Activities.RuntimeTransactionHandle> a zkontroluje, zda je `null`, což znamená, že aktivity se použil bez okolí transakce za běhu. Potom získá transakci znovu kontroluje, zda `null` je k dispozici. Je možné mít okolí <xref:System.Activities.RuntimeTransactionHandle> bez někdy inicializace běhové transakce. Nakonec zruší transakce voláním <xref:System.Transactions.Transaction.Rollback%2A> a určení výjimky na uživatele nebo obecná výjimka, která uvádí, že aktivita odvolala transakci.  
  
 Ukázkový pracovní postup se skládá z <xref:System.Activities.Statements.TransactionScope> jejíž textové Vypíše stav transakce před a po `RollbackActivity` spustí. Všimněte si, že i v případě, transakce byla vrácena zpět, <xref:System.Activities.Statements.TransactionScope> spustí do konce a není přerušit pracovního postupu, dokud se nedokončí text. Pracovní postup byl přerušen, protože <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> výchozí vlastnost `true`.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načtení řešení TransactionRollback.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3.  Stisknutím kláves CTRL + F5 spusťte aplikaci.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>Viz také  
 [Transakce](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
