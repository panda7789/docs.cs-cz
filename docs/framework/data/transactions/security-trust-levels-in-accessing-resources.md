---
title: Úrovně důvěryhodnosti zabezpečení v přístupu k prostředkům
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 847467b964e86f6d13be6ba103162512270fa684
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596760"
---
# <a name="security-trust-levels-in-accessing-resources"></a>Úrovně důvěryhodnosti zabezpečení v přístupu k prostředkům
Toto téma popisuje, jak je omezen přístup na studijních materiálech, které <xref:System.Transactions> zveřejňuje.  
  
 Existují tři hlavní úrovně důvěryhodnosti pro <xref:System.Transactions>. Úrovně důvěryhodnosti jsou definovány v závislosti na studijních materiálech, které <xref:System.Transactions> zpřístupňuje a úroveň vztahu důvěryhodnosti, který je třeba získat přístup k těmto prostředkům. Materiály, <xref:System.Transactions> poskytuje přístup k jsou systémové paměti, sdílený proces wide materiály a široké systémových prostředků. Úrovně jsou:  
  
- **AllowPartiallyTrustedCallers** (APTCA) pro použití transakcí v rámci jedné aplikace domény aplikace.  
  
- **DistributedTransactionPermission** (DTP) pro aplikace, které používají distribuované transakce.  
  
- Úplný vztah důvěryhodnosti pro trvalý zdroje, aplikace pro správu konfigurace a starší definiční aplikace.  
  
> [!NOTE]
>  Neměli volat některý z rozhraní zařazení s zosobněným kontexty.  
  
## <a name="trust-levels"></a>Úrovně důvěryhodnosti  
  
### <a name="aptca-partial-trust"></a>APTCA (částečným vztahem důvěryhodnosti)  
 <xref:System.Transactions> Sestavení lze volat částečně důvěryhodným kódem, protože byla označena atributem **AllowPartiallyTrustedCallers** atribut (APTCA). Tento atribut v podstatě odebere implicitní <xref:System.Security.Permissions.SecurityAction.LinkDemand> pro **FullTrust** oprávnění, který je nastavena opačném případě automaticky umisťovat na každou metodu veřejně dostupný v jednotlivých typů. Nicméně některé typy a členy stále vyžadují bezpečnějších oprávnění.  
  
 Atribut APTCA umožňuje aplikacím používat transakcí v částečným vztahem důvěryhodnosti v rámci jediné doméně aplikace. To umožňuje-eskalován transakce a Nestálá zařazení, které lze použít pro zpracování chyb. Příkladem je tabulka transacted hash a aplikace, která ji používá. Data lze přidat do a odebrán z tabulky hash v rámci jedné transakce. Pokud později transakce vrácena zpět, všechny změny provedené v tabulce hash v rámci dané transakce lze vrátit zpět.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Když <xref:System.Transactions> transakce je eskalován jej lze spravovat pomocí nástroje MSDTC, <xref:System.Transactions> požadavky <xref:System.Transactions.DistributedTransactionPermission> (DTP) k vytvoření distribuované transakce. To znamená, že kód, který způsobí, že transakce se eskalován (například prostřednictvím serializace nebo další trvalé zařazení) by bylo nutné mít udělena DTP. Kód, který původně vytvořil <xref:System.Transactions> transakce nutně nemusí mít toto oprávnění.  
  
### <a name="fulltrust-link-demands"></a>Požadavky na propojení FullTrust  
 Tuto úroveň oprávnění je určena k omezení aplikace, které jsou zápisu do trvalý prostředků. Po selhání aplikace musí být možné obnovit pomocí Správce transakcí k určení konečný výsledek transakce, tak, aby jej můžete aktualizovat trvalá data. Tento typ aplikace, se nazývá trvalý zdroj správce. Klasické příkladem tento typ aplikace je SQL.  
  
 Chcete-li povolit obnovení, tento typ aplikace má možnost trvale spotřebovávat systémové prostředky. Toto je vzhledem k tomu, že správce obnovitelných transakcí musí mějte na paměti, transakcí, které mají potvrzeny, dokud můžete ověřit, že všechny správce trvalý prostředků, které se účastní transakce přijali výsledek. Proto tento typ aplikace vyžaduje plnou důvěryhodnost a by neměl být spuštěn, není-li poskytovaná úroveň vztahu důvěryhodnosti.  
  
 Další informace o trvalý zařazení a obnovení najdete v tématu [uvedení prostředků jako účastníků v transakci](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) a [provádění obnovení](../../../../docs/framework/data/transactions/performing-recovery.md) témata.  
  
 Aplikace, které provádějí starší verze definiční pracovat s modelu COM + jsou také nutné mít plnou důvěryhodnost.  
  
 Následuje seznam typy a členy, které nejsou skriptem částečně důvěryhodný kód, protože jsou vybaveny **FullTrust** atribut deklarativní zabezpečení:  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Jen pro okamžitého volajícího je nutné mít **FullTrust** oprávnění nastavena pro použití výše uvedené typy a metody.
