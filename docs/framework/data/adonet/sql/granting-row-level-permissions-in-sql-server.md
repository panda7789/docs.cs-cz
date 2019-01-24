---
title: Udělení oprávnění na úrovni řádků na SQL serveru
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 28e552e005cdfa0b4c69ff95927b938fa3898193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553764"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Udělení oprávnění na úrovni řádků na SQL serveru
V některých případech je potřeba řídit přístup k datům na podrobnější úrovni, než jaké jednoduše udělení, odvolání nebo odepření oprávnění poskytuje. Nemocnice databázové aplikace může například vyžadovat jednotlivé lékařů omezit přístup k informacím o související s pouze pacientů. Podobné požadavky nejsou v mnoha prostředích, včetně finance, zákonem, government a aplikacím armády. K řešení scénářů, SQL Server 2016 poskytuje [zabezpečení na úrovní řádků](https://msdn.microsoft.com/library/dn765131.aspx) funkce, která zjednodušuje a centralizuje logiky přístupu na úrovni řádku v zásadách zabezpečení. U starších verzí systému SQL Server můžete dosáhnout podobné funkce vydává filtrování na úrovni řádků pomocí zobrazení.  
  
## <a name="implementing-row-level-filtering"></a>Implementace filtrování na úrovni řádků  
 Filtrování na úrovni řádků slouží k ukládání informací o do jedné tabulky jako v předchozím příkladu nemocnice aplikací. K implementaci na úrovni řádků filtrování každý řádek obsahuje sloupce, který definuje odlišující parametr, jako je například uživatelské jméno, popisek nebo jiný identifikátor. Vytvoření zásad zabezpečení nebo zobrazení v tabulce, který filtruje řádky, které má uživatel přístup. Pak vytvoříte parametrizované uložené procedury, které řídit typy dotazů, které uživatel může spustit.  
  
 Následující příklad popisuje, jak nakonfigurovat filtrování na úrovni řádků na základě názvu uživatele nebo přihlášení:  
  
-   Vytvořte tabulku, přidání sloupce pro uložení názvu.  
  
-   Povolte filtrování na úrovni řádků:  
  
    -   Pokud používáte SQL Server 2016 nebo novější, nebo [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), vytvořte zásadu zabezpečení, která přidá predikát pro tabulku omezení řádků vrácena na ty, které odpovídají jednomu aktuálního uživatele databáze (pomocí CURRENT_USER() Integrovaná funkce) nebo aktuální přihlašovací jméno (pomocí předdefinované funkci SUSER_SNAME()):  
  
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
  
    -   Pokud používáte verzi systému SQL Server 2016, můžete dosáhnout použitím zobrazení podobné funkce:  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   Vytvořte uložené procedury k výběru, vložit, aktualizovat a odstranit data. Pokud filtrování budou přijaty zásady zabezpečení, uložené procedury by měl provádět tyto operace v základní tabulce přímo. v opačném případě Pokud filtrování budou přijaty ve zobrazení, uložené procedury místo toho pracovat na zobrazení. Zásady zabezpečení nebo zobrazení bude automaticky filtrovat řádky instance vrátí, nebo upravit dotazy uživatelů a uložené procedury bude poskytovat obtížnější hranice zabezpečení úspěšně spuštění dotazů, které dokážou odvodit moct uživatelé s přístupem přímých dotazů existence filtrovaná data.  
  
-   Pro uložené procedury, které vkládají data zachytit pomocí stejné funkce určené v zásadách zabezpečení nebo uživatelské jméno a vložte tuto hodnotu do sloupce uživatelské jméno.  
  
-   Zakázat všechna oprávnění pro tabulky (a zobrazení, pokud je k dispozici) na `public` role. Uživatelé nebudou mít dědění oprávnění z jiné databázové role, protože predikát filtru je založena na uživatele nebo přihlašovací jména, ne na role.  
  
-   Udělení spustit na uložené procedury pro databázové role. Data mohou uživatelé přistupovat pouze prostřednictvím uložené procedury, které jsou k dispozici.  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení na úrovní řádků](https://msdn.microsoft.com/library/dn765131.aspx)
- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
