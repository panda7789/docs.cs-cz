---
title: Použití System.Transactions v ASP.NET
description: Použijte System. Transactions uvnitř aplikace ASP.NET. Povolte oprávnění distribuované transakce a pracujte s dynamickou kompilací.
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 48907faf99953e34d045a1e0d79eed8a788187b5
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141641"
---
# <a name="using-systemtransactions-in-aspnet"></a>Použití System.Transactions v ASP.NET
Toto téma popisuje, jak lze úspěšně použít <xref:System.Transactions> v aplikaci ASP.NET.

## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Povolit DistributedTransactionPermission v technologii ASP.NET
 <xref:System.Transactions>podporuje částečně důvěryhodné volající a je označen `AllowPartiallyTrustedCallers` atributem (APTCA). Úrovně důvěryhodnosti pro <xref:System.Transactions> jsou definovány na základě typů prostředků (například systémové paměti, sdílených prostředků v rámci procesu, prostředků v rámci systému a dalších prostředků), které <xref:System.Transactions> zveřejňují a úrovně důvěryhodnosti, které by měly být požadovány pro přístup k těmto prostředkům. V prostředí částečné důvěryhodnosti, můžete použít jiný plně důvěryhodné sestavení pouze transakce v rámci domény aplikace (v takovém případě jediný zdroj chráněn je systémová paměť), pokud má oprávnění <xref:System.Transactions.DistributedTransactionPermission>.

 <xref:System.Transactions.DistributedTransactionPermission>je vydaný na vyžádání pokaždé, když je Správa transakcí eskalacá, aby se spravovala pomocí služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC). Tento druh scénář využívá prostředky celého procesu a zejména globální zdroj, který je vyhrazené místo v protokolu MSDTC. Příklad toto využití je do databáze nebo aplikace, která používá databázi v rámci služeb, které poskytuje klientské části webu.

 ASP.NET má svou vlastní sadu úrovní důvěryhodnosti a přiřazuje konkrétní sadu oprávnění s těmito úrovněmi důvěryhodnosti prostřednictvím souborů zásad. Další informace najdete v tématu [úrovně důvěryhodnosti ASP.NET a soubory zásad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Při první instalaci Windows SDK není k dispozici žádný výchozí soubor zásad pro ASP.NET <xref:System.Transactions.DistributedTransactionPermission> . V takovém případě, když je vaše transakce v aplikaci ASP.NET eskalacá, aby se spravovala pomocí MSDTC, eskalace se nezdařila, a to <xref:System.Security.SecurityException> po náročné <xref:System.Transactions.DistributedTransactionPermission> . Chcete-li povolit eskalaci transakce v prostředí ASP.NET s částečným vztahem důvěryhodnosti, měli byste udělit <xref:System.Transactions.DistributedTransactionPermission> ve stejné výchozí úrovni důvěryhodnosti jako ty z <xref:System.Data.SqlClient.SqlClientPermission> . Můžete buď nakonfigurovat vlastní vlastní úroveň důvěryhodnosti a soubor zásad, nebo můžete upravit výchozí soubory zásad, které jsou **Web_hightrust.config** a **Web_mediumtrust.config**.

 Chcete-li upravit soubory zásad, přidejte `SecurityClass` element pro `DistributedTransactionPermission` `SecurityClasses` element pod `PolicyLevel` element a přidejte odpovídající `IPermission` element pod ASP.NET `NamedPermissionSet` for System. Transactions. Následující konfigurační soubor ukazuje to.

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

 Další informace o zásadách zabezpečení ASP.NET naleznete v tématu [Element securityPolicy (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).

## <a name="dynamic-compilation"></a>Dynamická kompilace
 Pokud chcete importovat a používat <xref:System.Transactions> v aplikaci ASP.NET, která je dynamicky kompilována v přístupu, měli byste umístit odkaz na <xref:System.Transactions> sestavení v konfiguračním souboru. Odkaz konkrétně by měl být přidán do `compilation/assemblies` oddílu výchozího kořenového **Web.config** konfiguračního souboru nebo konkrétního konfiguračního souboru webové aplikace. Následující příklad ukazuje to.

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

 Další informace najdete v tématu [Přidání elementu pro sestavení pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).

## <a name="see-also"></a>Viz také

- [ASP.NET úrovně důvěryhodnosti a soubory zásad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy – element (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Eskalace správy transakce](transaction-management-escalation.md)
