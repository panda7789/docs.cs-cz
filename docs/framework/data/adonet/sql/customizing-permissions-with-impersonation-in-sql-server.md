---
title: Přizpůsobení oprávnění se zosobněním na SQL Serveru
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: dd7fb4c94c5a0a9bca0cd36b8d76864158072d4e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326967"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Přizpůsobení oprávnění se zosobněním na SQL Serveru
Mnoho aplikací používá pro přístup k datům, spoléhat na řetězení vlastnictví můžete omezit přístup k základní tabulky uložené procedury. Můžete udělit oprávnění spouštět na uložené procedury, odvolání nebo odepřením oprávnění u základní tabulky. SQL Server oprávnění volající nekontroluje, pokud uložené procedury a tabulky mají stejné vlastníka. Ale řetězení vlastnictví nefunguje Pokud objekty mají různé vlastníci nebo v případě dynamické SQL.  
  
 Můžete použít EXECUTE AS klauzule v uložené proceduře když volající nemá oprávnění u objektů odkazovaná databáze. Účinek EXECUTE AS klauzule je, že kontextu spuštění přepnutí na uživatele proxy serveru. Veškerý kód, stejně jako všechna volání vnořených uložených procedur a aktivačních událostí, spustí v kontextu zabezpečení uživatele proxy serveru. Kontext spuštění se vrátí zpět na původní volajícího až po provádění procedury nebo při vydání příkazu obnovit.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Kontext přímé přepnutí s EXECUTE AS – příkaz  
 Příkaz umožňuje přepínat kontext spuštění příkazu pomocí zosobnění jiného uživatele přihlášení nebo databáze AS spuštění příkazů jazyka Transact-SQL. To je užitečná technika pro testování dotazů a procedur jako jiný uživatel.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Musíte mít oprávnění k přihlášení nebo uživatele, kterého jsou zosobnění ZOSOBNIT. Toto oprávnění je vyjádřena pro `sysadmin` pro všechny databáze, a `db_owner` členů role v databázích, které vlastní.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Udělení oprávnění EXECUTE AS – klauzule  
 Můžete použít EXECUTE AS klauzuli v definici hlavičky uložené procedury, aktivační události nebo uživatelem definované funkce (s výjimkou vložené funkce vracející tabulku). To způsobí, že postup provést v kontextu uživatelské jméno nebo podle EXECUTE AS – klíčové slovo klauzuli. Můžete vytvořit proxy uživatele v databázi, která není namapován na přihlášení, udělena potřebná oprávnění pouze u objektů procedura přistupuje. Pouze proxy uživatele zadaného v EXECUTE jako klauzule musí mít oprávnění u všech objektů přistupuje modulu.  
  
> [!NOTE]
>  Některé akce, jako je například TRUNCATE TABLE nemají udělitelným oprávnění. Začlenění příkaz v rámci procedury a zadání uživatele proxy serveru, který má oprávnění k příkazu ALTER TABLE, můžete rozšířit oprávnění došlo ke zkrácení tabulky volajícím, kteří mají jenom oprávnění spouštět v postupu.  
  
 Kontext zadaný v EXECUTE jako klauzuli je platný po dobu trvání tento postup, včetně vnořených procedur a aktivačních událostí. Kontext se vrátí volajícímu při spuštění je dokončena nebo je vydán příkaz REVERT.  
  
 Existují tři kroky při použití EXECUTE AS klauzule v postupu.  
  
1. Vytvoření uživatele proxy serveru v databázi, která není namapován na přihlášení. Tento krok není povinný, ale pomáhá při správě oprávnění.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1. Proxy uživateli udělte potřebná oprávnění.  
  
2. Přidat EXECUTE AS klauzule uloženou proceduru nebo uživatelem definované funkce.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  Aplikace, které vyžadují auditování můžete zrušit, protože není zachováno původní kontext zabezpečení volajícího. Integrované funkce, které vracejí identity aktuálního uživatele, jako je například SESSION_USER, uživatele nebo uzivatelske_jmeno, vrátí uživatele přidruženého k EXECUTE AS klauzule, nikoli původní volající.  
  
### <a name="using-execute-as-with-revert"></a>Použití EXECUTE AS s vrácení  
 Příkaz vrátit příkazů jazyka Transact-SQL můžete vrátit na původní kontext spuštění.  
  
 Volitelná klauzule s ne vrátit soubor COOKIE = @variableName, umožňuje přepnout kontext spuštění zpět do volajícího, pokud @variableName proměnná obsahuje platnou hodnotu. To umožňuje jste museli přepínat kontext spuštění zpět volajícímu v prostředích, kde se používá sdružování připojení. Protože hodnota @variableName je znám pouze volajícímu metody EXECUTE AS prohlášení, volající může zaručit, že koncový uživatel, který volá aplikaci nelze změnit kontext spuštění. Když se připojení uzavře, je vrácen do fondu. Další informace o připojení sdružování v ADO.NET, naleznete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Určení kontextu spuštění  
 Kromě zadání uživatele, můžete také použít EXECUTE AS s jakoukoli následující klíčová slova.  
  
-   VOLAJÍCÍ. Spouštění jako VOLAJÍCÍ je výchozí hodnota; Pokud není zadána žádná další možnost, postup spustí v kontextu zabezpečení volajícího.  
  
-   VLASTNÍK. Postup spuštění jako vlastník spustí v kontextu postupu vlastníka. Pokud postupu je vytvořena ve schématu vlastněné `dbo` nebo vlastník databáze postupu budou spouštěny s neomezenými oprávněními.  
  
-   VLASTNÍ. Spuštění jako vlastní spustí v kontextu zabezpečení Tvůrce uložené procedury. Jedná se o ekvivalent spuštění jako určitý uživatel, pokud zadaný uživatel je osoba, vytvoření či změna postup.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Úpravy dat pomocí uložených procedur](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
