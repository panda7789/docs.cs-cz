---
title: Udělení oprávnění na úrovni řádků na SQL Serveru
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: df5fcb4a6c73e12bec2ab17501fdfb02cf672324
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782363"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Udělení oprávnění na úrovni řádků na SQL Serveru

V některých scénářích je potřeba řídit přístup k datům na podrobnější úrovni, než jaká oprávnění nabízí jenom udělování, odvolávání nebo odepření. Například databázová aplikace v nemocnicích může vyžadovat, aby jednotliví lékaři omezili přístup k informacím, které se týkají pouze svých pacientů. Podobné požadavky existují v mnoha prostředích, včetně finančních, zákonných, státních a vojenských aplikací. Aby bylo možné tyto scénáře vyřešit, SQL Server 2016 poskytuje funkci [zabezpečení na úrovni řádků](/sql/relational-databases/security/row-level-security) , která zjednodušuje a centralizovat logiku přístupu na úrovni řádků v zásadách zabezpečení. Pro starší verze SQL Server lze dosáhnout podobných funkcí pomocí zobrazení k přijetí filtrování na úrovni řádků.

## <a name="implementing-row-level-filtering"></a>Implementace filtrování na úrovni řádků

Filtrování na úrovni řádků se používá pro aplikace, které ukládají informace v jedné tabulce, jako je třeba výše uvedený příklad nemocnice. Pro implementaci filtrování na úrovni řádků každý řádek má sloupec, který definuje rozdílový parametr, jako je například uživatelské jméno, popisek nebo jiný identifikátor. Vytvoříte buď zásadu zabezpečení, nebo zobrazení v tabulce, které filtruje řádky, ke kterým má uživatel přístup. Pak vytvoříte parametrizované uložené procedury, které řídí typy dotazů, které může uživatel provádět.

Následující příklad popisuje, jak nakonfigurovat filtrování na úrovni řádků na základě uživatelského jména nebo přihlašovacího jména:

- Vytvořte tabulku a přidejte do ní sloupec pro uložení názvu.

- Povolit filtrování na úrovni řádků:

  - Pokud používáte SQL Server 2016 nebo vyšší nebo [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), vytvořte zásadu zabezpečení, která přidá predikát do tabulky s omezením počtu vrácených řádků na ty, které odpovídají buď aktuálnímu uživateli databáze (pomocí integrované funkce CURRENT_USER ()), nebo aktuální přihlašovací jméno (pomocí předdefinované funkce SUSER_SNAME ():

      ```sql
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

  - Pokud používáte verzi SQL Server před 2016, můžete dosáhnout podobných funkcí pomocí zobrazení:

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- Vytvořte uložené procedury pro výběr, vložení, aktualizaci a odstranění dat. Pokud je filtrování vydaných zásadami zabezpečení, měly by tyto operace provádět přímo v základní tabulce. v opačném případě, pokud je filtrování vydaným zobrazením, by místo toho měly být uložené procedury použity pro zobrazení. Pomocí zásad zabezpečení nebo zobrazení budou automaticky filtrovány řádky vracené nebo upravené uživatelskými dotazy a uložený postup bude poskytovat těžší hranici zabezpečení, která uživatelům brání v úspěšném spuštění dotazů, které mohou odvodit existence filtrovaných dat.

- U uložených procedur, které vkládají data, Zachyťte uživatelské jméno pomocí stejné funkce zadané v zásadách nebo zobrazení zabezpečení a vložte tuto hodnotu do sloupce UserName (uživatelské jméno).

- Odepřít všechna oprávnění k tabulkám (a zobrazením, pokud jsou k dispozici) pro `public` roli. Uživatelé nebudou moci dědit oprávnění z jiných databázových rolí, protože predikát filtru je založen na uživatelských nebo přihlašovacích jménech a nikoli na rolích.

- Udělte spuštění na uložených procedurách databázovým rolím. Uživatelé můžou k datům přistupovat jenom prostřednictvím poskytnutých uložených procedur.

## <a name="see-also"></a>Viz také:

- [Zabezpečení na úrovni řádků](/sql/relational-databases/security/row-level-security)
- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](writing-secure-dynamic-sql-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
