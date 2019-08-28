---
title: Podepisování uložených procedur na SQL Serveru
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: a30b5e28263c9f36e80c4e6b848033d5095b830b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043934"
---
# <a name="signing-stored-procedures-in-sql-server"></a>Podepisování uložených procedur na SQL Serveru

Digitální podpis je datový výtah zašifrovaný pomocí privátního klíče podepsaného. Privátní klíč zajišťuje, aby byl digitální podpis jedinečný pro jeho nosič nebo vlastníka. Uložené procedury, funkce (s výjimkou vložených funkcí vracející tabulky), triggery a sestavení můžete podepsat.

Uloženou proceduru můžete podepsat pomocí certifikátu nebo asymetrického klíče. To je určené pro scénáře, kdy oprávnění nejde dědit pomocí zřetězení vlastnictví nebo když je řetěz vlastnictví poškozený, jako je například dynamický SQL. Pak můžete vytvořit uživatele namapovaného na certifikát a udělit mu oprávnění k přístupu k objektům, ke kterým musí mít uložená procedura přístup.

Můžete také vytvořit přihlašovací údaje namapované na stejný certifikát a pak každému přihlašovacímu jménu udělit potřebná oprávnění na úrovni serveru nebo přidat přihlašovací údaje k jedné nebo více pevným rolím serveru. To je navrženo tak, aby `TRUSTWORTHY` nedocházelo k povolení nastavení databáze pro scénáře, ve kterých jsou potřeba oprávnění vyšší úrovně.

Když je uložená procedura spuštěná, SQL Server kombinuje oprávnění uživatele certifikátu a/nebo přihlášení s volajícími. Na rozdíl od `EXECUTE AS` klauzule nemění kontext provádění procedury. Integrované funkce, které vracejí přihlašovací jméno a uživatelská jména, vracejí jméno volajícího, nikoli uživatelské jméno certifikátu.

## <a name="creating-certificates"></a>Vytváření certifikátů

Když podepíšete uloženou proceduru pomocí certifikátu nebo asymetrického klíče, vytvoří se pomocí privátního klíče datový výtah, který se skládá z šifrované hodnoty hash kódu uložené procedury, společně s příkazem spustit jako uživatel. V době běhu je data Digest dešifrována pomocí veřejného klíče a porovnána s hodnotou hash uložené procedury. Změna příkazu Spustit jako uživatel neověřuje hodnotu hash, aby se digitální podpis už neshodoval. Úpravou uložené procedury se signatura úplně zruší, což zabrání někomu, kdo nemá přístup k privátnímu klíči, ve změně kódu uložené procedury. V obou případech je nutné znovu podepsat proceduru pokaždé, když změníte kód nebo spustím jako uživatel.

Při podepisování modulu je potřeba mít dva požadované kroky:

1. Pomocí příkazu Transact-SQL `CREATE CERTIFICATE [certificateName]` vytvořte certifikát. Tento příkaz má několik možností nastavení počátečního a koncového data a hesla. Výchozí datum vypršení platnosti je jeden rok.

1. Pomocí příkazu Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` podepište tuto proceduru pomocí certifikátu.

Jakmile je modul podepsán, je třeba vytvořit jeden nebo více objektů zabezpečení, aby bylo možné uchovávat další oprávnění, která by měla být přidružena k certifikátu.

Pokud modul potřebuje další oprávnění na úrovni databáze:

1. Pomocí příkazu Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` vytvořte uživatele databáze přidružené k tomuto certifikátu. Tento uživatel existuje pouze v databázi a není přidružen k účtu, pokud nebylo vytvořeno také přihlášení ze stejného certifikátu.

1. Udělte uživateli certifikátu požadovaná oprávnění na úrovni databáze.

Pokud modul potřebuje další oprávnění na úrovni serveru:

1. Zkopírujte certifikát do `master` databáze.

1. Pomocí příkazu Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` vytvořte přihlášení přidružené k tomuto certifikátu.

1. Udělte přihlašovacímu účtu požadovaná oprávnění na úrovni serveru.

> [!NOTE]
> Certifikát nemůže udělit oprávnění uživateli, který má oprávnění k odvolání pomocí příkazu DENY. ZAMÍTNUTí vždycky má přednost před udělením a brání volajícímu v dědění oprávnění udělených uživateli certifikátu.

## <a name="external-resources"></a>Externí zdroje

Další informace najdete v následujících materiálech.

|Resource|Popis|
|--------------|-----------------|
|[Přihlášení modulu](https://go.microsoft.com/fwlink/?LinkId=98590) SQL Server Knihy online|Popisuje podepisování modulů a poskytuje ukázkový scénář a odkazy na související témata jazyka Transact-SQL.|
|[Podepisování uložených procedur s certifikátem](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate) v SQL Server Knihy online|V této části najdete kurz pro podepsání uložené procedury pomocí certifikátu.|

## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [Úpravy dat pomocí uložených procedur](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
