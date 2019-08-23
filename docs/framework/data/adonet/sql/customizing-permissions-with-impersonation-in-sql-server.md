---
title: Přizpůsobení oprávnění se zosobněním na SQL Serveru
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: 52e11bd983a8c9155d90659834df03dea6449a8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961114"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Přizpůsobení oprávnění se zosobněním na SQL Serveru
Mnoho aplikací používá pro přístup k datům uložené procedury, které se spoléhají na zřetězení vlastnictví, aby se omezil přístup k základním tabulkám. Můžete udělit oprávnění pro spouštění uložených procedur, odvolat nebo odepřít oprávnění pro základní tabulky. SQL Server nekontrolují oprávnění volajícího, pokud má uložená procedura a tabulky stejného vlastníka. Řetězení vlastnictví ale nefunguje, pokud objekty mají různé vlastníky nebo v případě dynamického SQL.  
  
 V uložené proceduře můžete použít klauzuli EXECUTE AS, pokud volající nemá oprávnění k objektům odkazované databáze. Výsledkem klauzule EXECUTE AS je přepnutí kontextu spuštění na uživatele proxy serveru. Veškerý kód, stejně jako všechna volání vnořených uložených procedur nebo triggerů, se spustí v kontextu zabezpečení uživatele proxy serveru. Kontext spuštění se vrátí původnímu volajícímu až po provedení procedury nebo při vydání příkazu REVERT.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Přepínání kontextu pomocí příkazu Spustit jako  
 Příkaz Transact-SQL EXECUTE AS umožňuje přepnout kontext provádění příkazu zosobněním jiného uživatele nebo uživatele databáze. Toto je užitečnou technikou pro testování dotazů a postupů jako jiný uživatel.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Musíte mít oprávnění k ZOSOBNĚNí nebo k zosobnění uživatele. Toto oprávnění je odvozené pro `sysadmin` všechny databáze a `db_owner` členy rolí v databázích, které vlastní.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Udělování oprávnění s klauzulí EXECUTE AS  
 Můžete použít klauzuli EXECUTE AS v hlavičce definice uložené procedury, triggeru nebo uživatelsky definované funkce (s výjimkou vložených funkcí vracející tabulky). To způsobí, že se procedura spustí v kontextu uživatelského jména nebo klíčového slova zadaného v klauzuli EXECUTE AS. Můžete vytvořit uživatele proxy v databázi, která není namapována na přihlašovací údaje, a udělit tak pouze potřebná oprávnění k objektům, ke kterým má přístup tento postup. Jenom uživatel proxy, který je zadaný v klauzuli spustit jako, musí mít oprávnění pro všechny objekty, ke kterým přistupoval modul.  
  
> [!NOTE]
> Některé akce, například TRUNCATE TABLE, nemají udělená oprávnění. Zahrnutím příkazu v rámci procedury a zadáním uživatele proxy, který má oprávnění ALTER TABLE, můžete oprávnění zkrátit pro zkrácení tabulky na volající, kteří mají pouze oprávnění k provedení procedury.  
  
 Kontext zadaný v klauzuli EXECUTE AS je platný po dobu trvání procedury, včetně vnořených procedur a triggerů. Kontext se vrátí volajícímu, pokud je spuštění dokončeno nebo je vydán příkaz REVERT.  
  
 Existují tři kroky, které se týkají použití klauzule EXECUTE AS v proceduře.  
  
1. Vytvořte uživatele proxy v databázi, která není namapovaná na přihlašovací jméno. To není povinné, ale pomáhá při správě oprávnění.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1. Udělte uživateli proxy potřebná oprávnění.  
  
2. Přidejte klauzuli EXECUTE AS do uložené procedury nebo uživatelsky definované funkce.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
> Aplikace, které vyžadují auditování, můžou přerušit, protože původní kontext zabezpečení volajícího se nezachová. Integrované funkce, které vracejí identitu aktuálního uživatele, jako je SESSION_USER, uživatel nebo uživatelské_jméno, vrátí uživatele přidruženého k klauzuli EXECUTE AS, nikoli původnímu volajícímu.  
  
### <a name="using-execute-as-with-revert"></a>Použití příkazu Spustit jako s příkazem REVERT  
 Pomocí příkazu Transact-SQL REVERT se můžete vrátit k původnímu kontextu spuštění.  
  
 Volitelná klauzule bez revertu souborů cookie @variableName= umožňuje přepnout kontext spuštění zpět na volajícího, @variableName Pokud proměnná obsahuje správnou hodnotu. To umožňuje přepnout kontext spuštění zpět na volající v prostředích, kde se používá sdružování připojení. Vzhledem k tomu, @variableName že hodnota je známa pouze volajícímu příkazu Spustit jako, volající může zaručit, že kontext spuštění nemůže být změněn koncovým uživatelem, který aplikaci vyvolá. Po zavření připojení se vrátí do fondu. Další informace o sdružování připojení v ADO.NET najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Určení kontextu spuštění  
 Kromě určení uživatele můžete také použít příkaz Spustit jako s některým z následujících klíčových slov.  
  
- VOLAJÍCÍ. Spuštění jako volající je výchozí. Pokud není zadána žádná jiná možnost, pak se procedura provede v kontextu zabezpečení volajícího.  
  
- OWNER. Spuštění jako vlastník provede proceduru v kontextu vlastníka procedury. Pokud je procedura vytvořena ve schématu vlastněném nástrojem `dbo` nebo vlastníkem databáze, postup bude proveden s neomezenými oprávněními.  
  
- SAMOROZBALUJÍCÍ. Spouští se jako samostatně spouštěné v kontextu zabezpečení tvůrce uložené procedury. Jedná se o ekvivalentní spuštění jako zadaný uživatel, kde zadaný uživatel je osoba, která tuto proceduru vytvořila nebo mění.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Úpravy dat pomocí uložených procedur](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
