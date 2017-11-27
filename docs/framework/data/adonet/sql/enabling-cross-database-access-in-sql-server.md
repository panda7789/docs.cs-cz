---
title: "Povolení přístupu mezi databáze v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 720c4c8eecc20b971eb9ecf1abb85da1e72e3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Povolení přístupu mezi databáze v systému SQL Server
Řetězení mezidatabázové vlastnictví nastane, když postup v jedné databáze závisí na objektech v jiné databázi. Řetěz mezidatabázové vlastnictví funguje stejným způsobem jako vlastnictví řetězení v rámci jedné databáze, s tím rozdílem, že řetězce rozděleno vlastnictví vyžaduje, aby všechny vlastníky objektů jsou namapované na stejný účet pro přihlášení. Pokud zdrojový objekt v databázi zdrojové a cílové objekty v cílové databází jsou vlastněny stejný účet pro přihlášení, nekontroluje systém SQL Server oprávnění pro cílové objekty.  
  
## <a name="off-by-default"></a>Ve výchozím nastavení vypnuté  
 Vlastnictví řetězení mezi databázemi je ve výchozím nastavení vypnutý. Společnost Microsoft doporučuje zakázat mezidatabázové vlastnictví řetězení, protože ho budete vystavuje následující rizika zabezpečení:  
  
-   Databáze vlastníků a členy `db_ddladmin` nebo `db_owners` databázové role můžete vytvořit objekty, které vlastní jiní uživatelé. Tyto objekty, můžete vybrat potenciálně objekty v jiných databázích. To znamená, že pokud povolíte mezidatabázové vlastnictví řetězení, je nutné plně důvěřovat tito uživatelé s daty v všechny databáze.  
  
-   Uživatelé s oprávněním Vytvořit databáze můžete vytvářet nové databáze a připojit existující databáze. Pokud mezidatabázové vlastnictví řetězení je povoleno, mohou tito uživatelé přejdou objekty v jiných databázích, které budou pravděpodobně nemá oprávnění z nově vytvořené nebo připojených databází, které vytvoří.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Povolení mezidatabázové vlastnictví řetězení  
 Řetězení mezidatabázové vlastnictví by měl Povolit jenom v prostředích, kde můžete důvěřovat plně vysoce privilegovaných uživatelů. Dá se během instalace pro všechny databáze, nebo selektivně pro konkrétní databáze pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy `sp_configure` a `ALTER DATABASE`.  
  
 Pokud chcete konfigurovat selektivně řetězení mezidatabázové vlastnictví, použijte `sp_configure` k vypnutí serveru. Pak použijte příkaz ALTER DATABASE pomocí nastavení ON DB_CHAINING konfigurace mezidatabázové vlastnictví zřetězení pouze databáze, které je vyžadují.  
  
 Následující příklad se zapne řetězení mezidatabázové vlastnictví pro všechny databáze:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Následující příklad se zapne mezidatabázové vlastnictví řetězení pro konkrétní databáze:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dynamické SQL  
 Řetězení mezidatabázové vlastnictví nefunguje, pokud je v případech, kde jsou provést dynamicky vytvořené příkazy SQL, dokud jeden uživatel existuje v obou databází. Můžete obejít v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] vytvořením uložené procedury, která přistupuje k datům v jiné databázi a podepisování postup s certifikátem, který již existuje v obou databází. To umožňuje uživatelům přístup k databázi prostředky využívané třídou postup bez toho, abyste jim přístup k databázi nebo oprávnění.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Rozšíření databáze zosobnění pomocí EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) a [mezi DB vlastnictví řetězení možnost](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] knihy Online.|Témata popisují postup konfigurace mezidatabázové vlastnictví řetězení pro instanci [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Správa oprávnění pomocí uložené procedury v systému SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Zápis zabezpečené dynamické SQL v systému SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Podepisování uložené procedury v systému SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
