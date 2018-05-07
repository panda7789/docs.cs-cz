---
title: Povolení přístupu mezi databáze v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 22fa2b48d795fb81b4740ce882f9bff632deabbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 Řetězení mezidatabázové vlastnictví nefunguje, pokud je v případech, kde jsou provést dynamicky vytvořené příkazy SQL, dokud jeden uživatel existuje v obou databází. Vám může tento problém vyřešit v systému SQL Server vytváření uložené procedury, která přistupuje k datům v jiné databázi a podepisování postup s certifikátem, který již existuje v obou databází. To umožňuje uživatelům přístup k databázi prostředky využívané třídou postup bez toho, abyste jim přístup k databázi nebo oprávnění.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Rozšíření databáze zosobnění pomocí EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) a [mezi DB vlastnictví řetězení možnost](http://msdn.microsoft.com/library/ms188694.aspx)příruček SQL Server Books Online.|Témata popisují postup konfigurace mezidatabázové vlastnictví řetězení pro instanci systému SQL Server.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
