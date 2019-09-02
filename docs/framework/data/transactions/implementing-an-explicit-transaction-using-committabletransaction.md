---
title: Implementace explicitní transakce přes CommittableTransaction
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: 19b62c24d00903d1494a755dbeabb460935cdacd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205937"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>Implementace explicitní transakce přes CommittableTransaction
<xref:System.Transactions.CommittableTransaction> Třída poskytuje explicitní způsob pro použití transakcí, na rozdíl od použití aplikacemi <xref:System.Transactions.TransactionScope> třídy implicitně. Je užitečné pro aplikace, které chcete použít stejnou transakci napříč několika volání funkce nebo více vláken volání. Na rozdíl od <xref:System.Transactions.TransactionScope> třídy pro zápis do aplikace potřebuje konkrétně volat <xref:System.Transactions.CommittableTransaction.Commit%2A> a <xref:System.Transactions.Transaction.Rollback%2A> metody za účelem potvrzení nebo přerušení transakce.  
  
## <a name="overview-of-the-committabletransaction-class"></a>Přehled třídy CommittableTransaction  
 <xref:System.Transactions.CommittableTransaction> Třída odvozena z <xref:System.Transactions.Transaction> třídy, proto poskytuje všechny funkce ten. Je obzvláště užitečná <xref:System.Transactions.Transaction.Rollback%2A> metodu na <xref:System.Transactions.Transaction> třídu, která lze také použít k vrácení zpět <xref:System.Transactions.CommittableTransaction> objektu.  
  
 <xref:System.Transactions.Transaction> Třída je podobně jako <xref:System.Transactions.CommittableTransaction> třídy, ale nenabízí `Commit` metody. To umožňuje předat objekt transakce (nebo klony jeho) do jiné metody (potenciálně na jiných vláknech) při stále řízení při transakce se potvrzeny. Je volána kód je možné zařazení a hlasovat pro transakce, ale pouze tvůrce <xref:System.Transactions.CommittableTransaction> objektu má možnost potvrzení transakce.  
  
 Všimněte si těchto hodnot při práci s <xref:System.Transactions.CommittableTransaction> třídy  
  
- Vytváření <xref:System.Transactions.CommittableTransaction> transakce nenastaví okolí transakce. Je třeba konkrétně nastavena a okolí transakce, ujistěte se, že správci prostředků pracovat v kontextu vpravo transakce v případě potřeby obnovit. Způsob, jak nastavit aktuální okolí transakce je nastavením statické <xref:System.Transactions.Transaction.Current%2A> vlastnost na globální <xref:System.Transactions.Transaction> objektu.  
  
- Objekt <xref:System.Transactions.CommittableTransaction> objektu nelze znovu použít. Jednou <xref:System.Transactions.CommittableTransaction> objektu byla potvrzena nebo vrácena zpět, nelze jej použít znovu v transakci. To znamená nelze jej nastavit jako aktuální kontext okolí transakce.  
  
## <a name="creating-a-committabletransaction"></a>Vytváření CommittableTransaction  
 Následující příklad vytvoří nový <xref:System.Transactions.CommittableTransaction> a potvrdí ji.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 Vytváření instance <xref:System.Transactions.CommittableTransaction> automaticky nenastaví kontext okolí transakce. Proto všechny operace na správce prostředků není součástí této transakce. Statické <xref:System.Transactions.Transaction.Current%2A> vlastnost na globální <xref:System.Transactions.Transaction> objektu se používá k nastavení nebo načtení okolí transakce a aplikace musíte ručně nastavit k zajištění správci prostředků mohou být součástí transakce. Je také vhodné k uložení původní okolí transakce a jeho obnovení po dokončení práce <xref:System.Transactions.CommittableTransaction> objektu.  
  
 Potvrzení transakce, je třeba explicitně volat <xref:System.Transactions.CommittableTransaction.Commit%2A> metody. Pro vrácení zpět transakcí, měli byste zavolat <xref:System.Transactions.Transaction.Rollback%2A> metody. Je důležité si všimněte si, že až <xref:System.Transactions.CommittableTransaction> byl potvrzené nebo vrátit zpět všechny prostředky zahrnuté v tom, že transakce jsou stále uzamčena.  
  
 Objekt <xref:System.Transactions.CommittableTransaction> objekt lze použít v rámci volání funkce a vlákna. Je však až do vývojář aplikace ke zpracování výjimek a konkrétně volání <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> metodu v případě selhání.  
  
## <a name="asynchronous-commit"></a>Asynchronní zápis  
 <xref:System.Transactions.CommittableTransaction> Třída rovněž poskytuje mechanismus pro potvrzení transakce asynchronně. Zápis transakce může trvat značné množství času, jak ji může zahrnovat více přístup k databázi a latence možný sítě. Pokud chcete, aby se zabránilo zablokování v vysoce výkonných aplikací, můžete pomocí asynchronní zápis dokončete transakční pracovní co nejdříve a spustit operaci potvrzení jako pozadí úlohu. <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> a <xref:System.Transactions.CommittableTransaction.EndCommit%2A> metody <xref:System.Transactions.CommittableTransaction> třída umožňuje provést.  
  
 Můžete volat <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> odesláním holdup potvrzení na vlákno z fondu podprocesů. Můžete také volat <xref:System.Transactions.CommittableTransaction.EndCommit%2A> k určení, pokud transakce ve skutečnosti byla. Je-li transakce se nepodařilo zapsat z jakéhokoli důvodu <xref:System.Transactions.CommittableTransaction.EndCommit%2A> vyvolá výjimka transakce. Pokud není v čase ještě potvrzené transakce <xref:System.Transactions.CommittableTransaction.EndCommit%2A> je volána, volajícího bude blokován, dokud nebude transakce potvrzena nebo zrušena.  
  
 Nejjednodušší způsob, jak provést asynchronní zápis je poskytnutím metoda zpětného volání, která se má volat po dokončení potvrzení. Je však třeba volat <xref:System.Transactions.CommittableTransaction.EndCommit%2A> metodu na původní <xref:System.Transactions.CommittableTransaction> objekt použitý k vyvolání volání. Chcete-li získat tento objekt, můžete přetypování parametru *IAsyncResult* metody zpětného volání, protože <xref:System.Transactions.CommittableTransaction> třída implementuje <xref:System.IAsyncResult> třídu.  
  
 Následující příklad ukazuje, jak lze provést asynchronní zápis.  
  
```csharp  
public void DoTransactionalWork()  
{  
     Transaction oldAmbient = Transaction.Current;  
     CommittableTransaction committableTransaction = new CommittableTransaction();  
     Transaction.Current = committableTransaction;  
  
     try  
     {  
          /* Perform transactional work here */  
          // No errors - commit transaction asynchronously  
          committableTransaction.BeginCommit(OnCommitted,null);  
     }  
     finally  
     {  
          //Restore the ambient transaction   
          Transaction.Current = oldAmbient;  
     }  
}  
void OnCommitted(IAsyncResult asyncResult)  
{  
     CommittableTransaction committableTransaction;  
     committableTransaction = asyncResult as CommittableTransaction;     
     Debug.Assert(committableTransaction != null);  
     try  
     {  
          using(committableTransaction)  
          {  
               committableTransaction.EndCommit(asyncResult);  
          }  
     }  
     catch(TransactionException e)  
     {  
          //Handle the failure to commit  
     }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Implementace implicitní transakce s využitím oboru transakcí](implementing-an-implicit-transaction-using-transaction-scope.md)
- [Zpracování transakcí](index.md)
