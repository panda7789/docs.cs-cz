---
title: Použití System.Transactions v ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 866d7b69fa6c18f6edfb48655b213e140a095a28
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880224"
---
# <a name="using-systemtransactions-in-aspnet"></a>Použití System.Transactions v ASP.NET
Toto téma popisuje, jak lze úspěšně pomocí <xref:System.Transactions> uvnitř aplikace technologie ASP.NET.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Povolit DistributedTransactionPermission v technologii ASP.NET  
 <xref:System.Transactions> podporuje částečně důvěryhodných volajících a je označený **AllowPartiallyTrustedCallers** atribut (APTCA). Vztah důvěryhodnosti úrovní pro <xref:System.Transactions> jsou definovány v závislosti na typy prostředků (pro příklad, systémová paměť, sdílené prostředky celého procesu, systémové prostředky a další materiály), který <xref:System.Transactions> zpřístupňuje a úroveň vztahu důvěryhodnosti, který je třeba získat přístup k těmto prostředkům. V prostředí částečné důvěryhodnosti, můžete použít jiný plně důvěryhodné sestavení pouze transakce v rámci domény aplikace (v takovém případě jediný zdroj chráněn je systémová paměť), pokud má oprávnění <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission> je požadováno vždy, když je Správa transakcí eskalován jej lze spravovat pomocí Microsoft distribuované transakce koordinátor (MSDTC). Tento druh scénář využívá prostředky celého procesu a zejména globální zdroj, který je vyhrazené místo v protokolu MSDTC. Příklad toto využití je do databáze nebo aplikace, která používá databázi v rámci služeb, které poskytuje klientské části webu.  
  
 Technologie ASP.NET má svou vlastní sadu úrovně důvěryhodnosti a přidruží konkrétní sadu oprávnění tyto úrovně důvěryhodnosti prostřednictvím soubory zásad. Další informace najdete v tématu [úrovně důvěryhodnosti technologie ASP.NET a soubory zásad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Po počáteční instalaci sadu Windows SDK, žádný výchozí zásady soubory ASP.NET jsou přidružené k <xref:System.Transactions.DistributedTransactionPermission>. Proto když vaši transakci v aplikaci technologie ASP.NET je eskalován jej lze spravovat pomocí příkaz MSDTC, eskalace nezdaří a zobrazí se <xref:System.Security.SecurityException> při náročných <xref:System.Transactions.DistributedTransactionPermission>. Chcete-li povolit eskalace transakce v částečném vztahu důvěryhodnosti prostředí ASP.NET, byste měli udělit <xref:System.Transactions.DistributedTransactionPermission> ve stejné úrovně důvěryhodnosti výchozí jako <xref:System.Data.SqlClient.SqlClientPermission>. Můžete buď nakonfigurovat vlastní soubor vlastní důvěryhodnosti úroveň a zásady pro podporu tohoto, nebo můžete upravit výchozí zásady soubory, které jsou **Web_hightrust.config** a **Web_mediumtrust.config**.  
  
 Chcete-li upravit zásady souborů, přidejte **SecurityClass** – element pro **DistributedTransactionPermission** k **SecurityClasses** element v rámci  **PolicyLevel, který** elementu a přidejte odpovídající **IPermission** element v rámci technologie ASP.NET **NamedPermissionSet** pro System.Transactions. Následující konfigurační soubor ukazuje to.  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 Další informace o zásadách zabezpečení technologie ASP.NET najdete v tématu [securityPolicy – Element (schéma nastavení technologie ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).  
  
## <a name="dynamic-compilation"></a>Dynamická kompilace  
 Pokud chcete importovat a používat <xref:System.Transactions> v aplikaci ASP.NET, která je dynamicky zkompilován přístupu, měli byste umístit odkaz na <xref:System.Transactions> sestavení v konfiguračním souboru. Konkrétně odkaz by měl vloženou **kompilace**/**sestavení** část výchozí kořen **Web.config** konfigurační soubor, nebo konfigurační soubor konkrétní webové aplikace. Následující příklad ukazuje to.  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 Další informace najdete v tématu [přidat Element pro sestavení compilation (schéma nastavení technologie ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [Úrovně důvěryhodnosti technologie ASP.NET a zásady souborů](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy – Element (schéma nastavení technologie ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Eskalace správy transakce](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
