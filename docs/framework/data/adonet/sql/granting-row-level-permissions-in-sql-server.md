---
title: "Udělení oprávnění na úrovni řádků v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a42c8d24a2817fb0a4118927722e7ac1887517a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Udělení oprávnění na úrovni řádků v systému SQL Server
V některých případech je potřeba řízení přístupu k datům na podrobnější úrovni, než jaké jednoduše udělení, odvolání nebo odepření oprávnění poskytuje. Databázové aplikace měla nemocnice například může vyžadovat jednotlivých lékařů být omezený přístup k informacím o související se pouze jejich pacientů. Podobné požadavky nejsou do mnoha prostředí, včetně finance, zákonem, vládních a vojenský aplikace. Aby vám budou snadněji řešit tyto scénáře, SQL Server 2016 poskytuje [zabezpečení na úrovni řádků](https://msdn.microsoft.com/library/dn765131.aspx) funkce, která zjednodušuje a centralizuje logiku přístup na úrovni řádku v zásadách zabezpečení. U starších verzí systému SQL Server můžete dosáhnout podobné funkce pomocí zobrazení na úrovni řádků filtrování uplatní.  
  
## <a name="implementing-row-level-filtering"></a>Implementace filtrování na úrovni řádků  
 Filtrování na úrovni řádků se používá pro ukládání informací o do jedné tabulky jako v předchozím příkladu měla nemocnice aplikace. K implementaci nízkoúrovňové filtrování každý řádek má sloupec, který definuje rozdílné parametr, jako je například uživatelské jméno, popisek nebo jiné identifikátor. Můžete vytvořit zásady zabezpečení nebo zobrazení v tabulce, která filtruje řádky, na které má uživatel přístup. Pak vytvořte parametrizované uložené procedury, které řídit typy dotazů, které může spustit uživatel.  
  
 Následující příklad popisuje, jak nakonfigurovat filtrování na základě názvu uživatele nebo přihlášení na úrovni řádků:  
  
-   Umožňuje vytvořte tabulku, přidání sloupce pro uložení název.  
  
-   Povolte filtrování na úrovni řádků:  
  
    -   Pokud používáte SQL Server 2016 nebo novější, nebo [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), vytvořte zásadu zabezpečení, která přidá vrátil predikát pro tabulku omezení řádky na ty, které odpovídají buď aktuální databáze uživatel (pomocí CURRENT_USER() Integrovaná funkce) nebo aktuální přihlašovací jméno (s použitím předdefinované funkci SUSER_SNAME()):  
  
        ```tsql  
        CREATE SCHEMA Security  
        GO  
  
        CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)  
            RETURNS TABLE  
            WITH SCHEMABINDING  
        AS  
            RETURN SELECT 1 AS accessResult  
            WHERE @UserName = SUSER_SNAME()  
        GO  
  
        CREATE SECURITY POLICY Security.userAccessPolicy  
            ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,  
            ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable  
        GO  
        ```  
  
    -   Pokud používáte verzi systému SQL Server před 2016, můžete dosáhnout podobné funkce pomocí zobrazení:  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   Vytvořte uložené procedury vybrat, vložit, aktualizovat a odstranit data. Pokud filtrování budou přijaty pomocí zásad zabezpečení, uložené procedury měli provádět tyto operace u základní tabulky přímo. jinak Pokud filtrování budou přijaty zobrazení, uložené procedury místo pracovat na zobrazení. Zásady zabezpečení nebo zobrazení bude automaticky filtrovat řádků vrácena nebo upraveném uživatelských dotazů a uložené procedury budou poskytovat těžší hranice zabezpečení nebudou moct uživatelé s přístupem přímý dotaz úspěšně spouštět dotazy, které lze odvodit existence filtrovaných dat.  
  
-   Pro uložené procedury, které vkládání dat, zaznamenat uživatelské jméno pomocí stejné funkce určené zásady zabezpečení nebo zobrazení a vložte tuto hodnotu do sloupce uživatelské jméno.  
  
-   Zakázat všechna oprávnění v tabulkách (a zobrazení, pokud je k dispozici) na `public` role. Uživatelé nebudou moci dědí oprávnění od jiných rolí databáze, protože predikát filtru je založena na uživatele nebo přihlašovací jména, nikoli na role.  
  
-   Udělení provést uložené procedury pro databázové role. Data mohou uživatelé přistupovat pouze prostřednictvím uložené postupy uvedené.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujícím zdroji.  
  
|||  
|-|-|  
|[Implementace zabezpečení na úrovni řádku a buňky v klasifikovaný databáze pomocí systému SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) na webu TechCenter pro SQL Server lokality.|Popisuje, jak pomocí zabezpečení na úrovni řádku a buňky splňovat požadavky zabezpečení klasifikovaný databáze.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení na úrovni řádků](https://msdn.microsoft.com/library/dn765131.aspx)  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
