---
title: Potvrzení transakce v jedné fázi a více fázích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: cbe00fb792ab5f2a7586a958ddbe5bdf004656dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875963"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Potvrzení transakce v jedné fázi a více fázích
Každý prostředek, který používá v transakci spravuje správce prostředků (SV), jejichž akce jsou koordinovaný správcem transakcí (TM). [Uvedení prostředků jako účastníků v transakci](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) téma popisuje, jak prostředek (nebo více zdrojů) může být uveden v transakci. Toto téma popisuje, jak lze koordinovat mezi zařazených prostředků částku transakce.  
  
 Na konci transakce aplikace požádá o transakce, které má být buď potvrzené nebo vrátit zpět. Správce transakcí musí odstranění ohrožení, jako je někteří správci prostředků hlasování se zapsat while ostatním uživatelům hlasování se navrátit transakci.  
  
 Pokud vaše transakce zahrnuje více než jeden prostředek, je nutné provést dvoufázového potvrzení (2PC). Protokol dvoufázového potvrzení (fáze prepare a potvrzovací fáze) zajišťuje, že při transakci skončí, všechny změny na všechny zdroje jsou buď zcela potvrzené nebo plně vrácena zpět. Všichni účastníci jsou pak informováni o konečný výsledek. Podrobné informace o protokolu dvoufázového potvrzení, naleznete v příručce "*zpracování transakcí: Koncepty a techniky (Nováková Kaufmann řady ve systémů pro správu dat) ISBN: 1558601902*"podle Jima šedá.  
  
 Můžete také optimalizovat vaši transakci výkon provedením součást v protokolu jedné fáze potvrzení. Další informace najdete v tématu [optimalizace pomocí Jednofázového potvrzení a možné zařazení Jednofázového oznámení](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 Pokud jste právě chcete být informováni o výsledek transakce a nechcete, aby se účastnit programu hlasování, byste měli zaregistrovat pro <xref:System.Transactions.Transaction.TransactionCompleted> události.  
  
## <a name="two-phase-commit-2pc"></a>Bezdrátové potvrzení (2PC)  
 V první fázi transakce dotazuje správce transakcí každý zdroj k určení, zda transakce potvrzena nebo vrácena zpět. Správce transakcí upozorní ve druhé fázi transakce každý zdroj výsledku své dotazy, díky kterému jej provést všechny potřebné vyčištění.  
  
 K účasti v tento druh transakce, musí implementovat správce prostředků <xref:System.Transactions.IEnlistmentNotification> rozhraní, které poskytuje metody, jež jsou volány správce TM jako oznámení během 2PC.  Následující příklad ukazuje příklad tohoto provádění.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Připravit fáze (fáze 1)  
 Při přijímání <xref:System.Transactions.CommittableTransaction.Commit%2A> požadavků z aplikace, správce transakcí začíná Příprava fáze zařazených účastníci voláním <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metodu na každý zapsán prostředku, za účelem získání hlas každý zdroj v transakci.  
  
 Váš správce prostředků, který implementuje <xref:System.Transactions.IEnlistmentNotification> by měl první implementaci rozhraní <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> jako následující jednoduchý příklad ukazuje metodu.  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 Pokud správce prostředků trvalý obdrží toto volání, ji má protokolovat informace o obnovení transakce (k dispozici načtením <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> vlastnost) a libovolné informace, které jsou nezbytné pro dokončení transakce na potvrzení. Toto není nutné provádět v rámci <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metoda vzhledem k tomu, že správce prostředků to lze provést v pracovní podproces.  
  
 Pokud správce prostředků dokončil jeho připravit pracovní, by měl hlasovat potvrzení nebo vrátit zpět voláním <xref:System.Transactions.PreparingEnlistment.Prepared%2A> nebo <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> metody. Všimněte si, že <xref:System.Transactions.PreparingEnlistment> třída dědí <xref:System.Transactions.Enlistment.Done%2A> metody z <xref:System.Transactions.Enlistment> třídy. Pokud tuto metodu lze volat na <xref:System.Transactions.PreparingEnlistment> zpětného volání ve fázi Prepare, informuje správce TM, je jen pro čtení zařazení (to znamená, že správce prostředků, které může číst, ale ochranou transakcí data nelze aktualizovat) a správce prostředků obdrží žádné další oznámení z správce transakcí tak, aby výsledek transakce ve fázi 2.  
  
 Aplikace je oznámen úspěšné úsilí transakce po hlasovat, že všechny správce prostředků <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.  
  
### <a name="commit-phase-phase-2"></a>Potvrzení fáze (fáze 2)  
 Ve druhém fáze transakce, pokud správce transakcí přijme úspěšné připraví z všechny správce prostředků (uplatnit všechny správce prostředků <xref:System.Transactions.PreparingEnlistment.Prepared%2A> na konci fáze 1), vyvolá <xref:System.Transactions.IEnlistmentNotification.Commit%2A> metodu pro každého správce prostředků. Správci prostředků můžete provést změny trvalý a dokončení potvrzení.  
  
 Pokud některý správce prostředků nahlášena chyba připravit ve fázi 1, vyvolá správce transakcí <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> metodu pro každého správce prostředků a které identifikuje selhání potvrzení do aplikace.  
  
 Váš správce prostředků tedy měli používat následující metody.  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 Správce prostředků by měl provádět každé dílo, které jsou nezbytné pro dokončení transakce v závislosti na typu oznámení a informovat TM, který byl dokončen voláním <xref:System.Transactions.Enlistment.Done%2A> metodu na <xref:System.Transactions.Enlistment> parametru. Tato práce lze provést na pracovní podproces. Všimněte si, že oznámení fáze 2 může dojít, vložený ve stejném vlákně, který volal <xref:System.Transactions.PreparingEnlistment.Prepared%2A> metoda ve fázi 1. Jako takové neměli byste každé dílo po <xref:System.Transactions.PreparingEnlistment.Prepared%2A> volání (například uvolňující uzamčení), které očekáváte dokončili před přijímala oznámení fáze 2.  
  
### <a name="implementing-indoubt"></a>Implementace InDoubt  
 A konečně, měli byste implementovat <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> metody pro správce těkavých prostředků. Tato metoda je volána, pokud správce transakcí ztratí kontaktu s jedním nebo více účastníky, tak jejich stav není znám. V takovém případě je zapotřebí přihlásit tuto skutečnost tak, aby si můžete později zjistit, zda některé z účastníci transakce byla ponechána v nekonzistentním stavu.  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Optimalizace potvrzení jedna fáze  
 Vzhledem k tomu, že všechny aktualizace jsou provedeno bez explicitního koordinace je efektivnější v době běhu protokol jedné fáze potvrzení. Další informace o tomto protokolu naleznete v tématu [optimalizace pomocí Jednofázového potvrzení a možné zařazení Jednofázového oznámení](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Viz také:

- [Optimalizace pomocí jednofázového potvrzení a možné zařazení jednofázového oznámení](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)
- [Uvedení prostředků jako účastníků v transakci](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
