---
title: Použití System.Transactions v ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 6f88a4b06a9a83cf920601b7abe887d8b5fa7839
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774152"
---
# <a name="using-systemtransactions-in-aspnet"></a>Použití System.Transactions v ASP.NET
Toto téma popisuje, jak můžete úspěšně použít <xref:System.Transactions> v rámci aplikace ASP.NET.

## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Povolit DistributedTransactionPermission v technologii ASP.NET
 <xref:System.Transactions> podporuje částečně důvěryhodné volající a je označen atributem **AllowPartiallyTrustedCallers** (APTCA). Úrovně důvěryhodnosti pro <xref:System.Transactions> jsou definované na základě typů prostředků (například systémové paměti, sdílených prostředků v rámci procesu, prostředků v rámci systému a dalších prostředků), které <xref:System.Transactions> zveřejňuje a úroveň důvěryhodnosti, která by se měla vyžadovat pro přístup k těmto funkcím. prostředky. V prostředí částečné důvěryhodnosti, můžete použít jiný plně důvěryhodné sestavení pouze transakce v rámci domény aplikace (v takovém případě jediný zdroj chráněn je systémová paměť), pokud má oprávnění <xref:System.Transactions.DistributedTransactionPermission>.

 <xref:System.Transactions.DistributedTransactionPermission> je vyžádané při každém zvýšení správy transakcí, aby je bylo možné spravovat pomocí Microsoft DTC (Distributed Transaction Coordinator) (MSDTC). Tento druh scénář využívá prostředky celého procesu a zejména globální zdroj, který je vyhrazené místo v protokolu MSDTC. Příklad toto využití je do databáze nebo aplikace, která používá databázi v rámci služeb, které poskytuje klientské části webu.

 ASP.NET má svou vlastní sadu úrovní důvěryhodnosti a přiřazuje konkrétní sadu oprávnění s těmito úrovněmi důvěryhodnosti prostřednictvím souborů zásad. Další informace najdete v tématu [úrovně důvěryhodnosti ASP.NET a soubory zásad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Při první instalaci Windows SDK nejsou k <xref:System.Transactions.DistributedTransactionPermission>přidruženy žádné výchozí soubory zásad ASP.NET. V takovém případě, když je vaše transakce v aplikaci ASP.NET eskalacá, aby se spravovala pomocí služby MSDTC, eskalace se nezdařila s <xref:System.Security.SecurityException>em při náročné <xref:System.Transactions.DistributedTransactionPermission>. Chcete-li povolit eskalaci transakce v prostředí ASP.NET s částečným vztahem důvěryhodnosti, je třeba udělit <xref:System.Transactions.DistributedTransactionPermission> ve stejné výchozí úrovni důvěryhodnosti jako <xref:System.Data.SqlClient.SqlClientPermission>. Můžete buď nakonfigurovat vlastní vlastní úroveň důvěryhodnosti a soubor zásad pro podporu, nebo můžete upravit výchozí soubory zásad, které jsou **Web_hightrust. config** a **web_mediumtrust. config**.

 Chcete-li upravit soubory zásad, přidejte element **SecurityClass** pro **DistributedTransactionPermission** do elementu **SecurityClasses** pod prvkem **PolicyLevel** a přidejte odpovídající prvek **IPermission** pod ASP.NET **parametru NamedPermissionSet** pro System. Transactions. Následující konfigurační soubor ukazuje to.

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
 Pokud chcete importovat a používat <xref:System.Transactions> v aplikaci ASP.NET, která je dynamicky kompilována v přístupu, měli byste umístit odkaz na <xref:System.Transactions> sestavení v konfiguračním souboru. Odkaz konkrétně by měl být přidán do oddílu **kompilace**/**sestavení** výchozího kořenového konfiguračního souboru **Web. config** nebo do konkrétního konfiguračního souboru webové aplikace. Následující příklad ukazuje to.

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

## <a name="see-also"></a>Viz také:

- [ASP.NET úrovně důvěryhodnosti a soubory zásad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy – element (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Eskalace správy transakce](transaction-management-escalation.md)
