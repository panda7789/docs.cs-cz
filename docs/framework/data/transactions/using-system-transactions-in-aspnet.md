---
title: System.Transactions – pomocí technologie ASP.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c20905c8eafb1ac31702a46878e517ac090e484
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="using-systemtransactions-in-aspnet"></a>System.Transactions – pomocí technologie ASP.NET
Toto téma popisuje, jak lze úspěšně pomocí <xref:System.Transactions> v rámci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Povolit DistributedTransactionPermission v technologii ASP.NET  
 <xref:System.Transactions> podporuje částečně důvěryhodné volající a je označené **AllowPartiallyTrustedCallers** atribut (APTCA). Vztah důvěryhodnosti úrovní pro <xref:System.Transactions> jsou definovány v závislosti na typy prostředků (pro příklad, systémová paměť, sdílené prostředky celého procesu, systémové prostředky a další materiály), který <xref:System.Transactions> zpřístupňuje a úroveň vztahu důvěryhodnosti, který je třeba získat přístup k těmto prostředkům. V prostředí částečné důvěryhodnosti, můžete použít jiný plně důvěryhodné sestavení pouze transakce v rámci domény aplikace (v takovém případě jediný zdroj chráněn je systémová paměť), pokud má oprávnění <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission>je požadováno vždy, když je Správa transakcí eskalován jej lze spravovat pomocí Microsoft distribuované transakce koordinátor MSDTC (). Tento druh scénář využívá prostředky celého procesu a zejména globální zdroj, který je vyhrazené místo v protokolu MSDTC. Příklad toto využití je do databáze nebo aplikace, která používá databázi v rámci služeb, které poskytuje klientské části webu.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]obsahuje vlastní sadu úrovně důvěryhodnosti a přidruží konkrétní sadu oprávnění tyto úrovně důvěryhodnosti prostřednictvím soubory zásad. Další informace najdete v tématu [úrovně důvěryhodnosti ASP.NET a soubory zásad](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1). Při počáteční instalaci sadu Windows SDK, žádná výchozí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] soubory zásad jsou přidruženy <xref:System.Transactions.DistributedTransactionPermission>. Jako takové, když vaši transakci v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace je eskalován jej lze spravovat pomocí příkaz MSDTC, eskalace nezdaří a zobrazí se <xref:System.Security.SecurityException> při náročných <xref:System.Transactions.DistributedTransactionPermission>. Chcete-li povolit eskalace transakce v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] prostředí částečným vztahem důvěryhodnosti, byste měli udělit <xref:System.Transactions.DistributedTransactionPermission> ve stejné úrovně důvěryhodnosti výchozí jako <xref:System.Data.SqlClient.SqlClientPermission>. Buď můžete nakonfigurovat svůj vlastní soubor vlastní důvěryhodnosti úroveň a zásady pro podporu tohoto, nebo můžete upravit výchozí zásady soubory, které jsou **Web_hightrust.config** a **Web_mediumtrust.config**.  
  
 Chcete-li upravit soubory zásad, přidejte **SecurityClass** element pro **DistributedTransactionPermission** k **SecurityClasses** prvek v rámci  **PolicyLevel, který** prvek a přidat odpovídající **IPermission** prvek v rámci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** pro System.Transactions. Následující konfigurační soubor ukazuje to.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zásady zabezpečení, najdete v části [securityPolicy – Element (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).  
  
## <a name="dynamic-compilation"></a>Dynamická kompilace  
 Pokud chcete importovat a používat <xref:System.Transactions> v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikaci, která je dynamicky zkompilován přístupu, měli byste umístit odkaz <xref:System.Transactions> sestavení v konfiguračním souboru. Konkrétně by měl být odkaz na přidají pod **kompilace**/**sestavení** část kořenové výchozí **Web.config** konfigurační soubor, nebo konfigurační soubor konkrétní webové aplikace. Následující příklad ukazuje to.  
  
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
  
 Další informace najdete v tématu [add – Element pro sestavení pro kompilaci (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).  
  
## <a name="see-also"></a>Viz také  
 [Úrovně důvěryhodnosti ASP.NET a soubory zásad](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [securityPolicy – Element (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [Eskalace správy transakce](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
