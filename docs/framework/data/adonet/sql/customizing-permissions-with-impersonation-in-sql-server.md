---
title: "Přizpůsobení oprávnění s zosobnění v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fbd5aa34fa9e90df972e718c28d0ba97287c3d8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Přizpůsobení oprávnění s zosobnění v systému SQL Server
Mnoho aplikací pomocí uložené procedury pro přístup k datům, spoléhat na vlastnictví řetězení omezit přístup k základní tabulky. Můžete udělit oprávnění pro spouštění na uložené procedury, odvolání nebo odmítnout oprávnění u základní tabulky. SQL Server oprávnění volajícího nekontroluje, pokud se uložené procedury a tabulky mít stejného vlastníka. Ale vlastnictví řetězení nefunguje Pokud objekty mají různé vlastníci, nebo v případě dynamických SQL.  
  
 Můžete použít EXECUTE AS klauzule v uložené proceduře při volající nemá oprávnění pro odkazované databázové objekty. Účinek klauzule EXECUTE as je, že kontextu spuštění je přepnutá na uživatele proxy serveru. Všechny kódu, stejně jako libovolný volání vnořené uložené procedury nebo aktivační události, spustí v kontextu zabezpečení uživatele proxy serveru. Kontext spuštění je vrátit zpět na původní volající pouze po spuštění procedury nebo při vydání příkazu vrátit.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Kontext přepínání s EXECUTE AS – příkaz  
 Příkaz umožňuje přepínačem kontext provádění příkazu zosobnění jiného uživatele přihlášení nebo databáze provést AS jazyka Transact-SQL. To je užitečné pro testování dotazů a postupy jako jiný uživatel.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Musí mít oprávnění ZOSOBNIT na přihlášení nebo uživateli, které jsou zosobnění. Toto oprávnění je implicitní pro `sysadmin` pro všechny databáze, a `db_owner` členy role v databázích, které vlastní.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Udělení oprávnění s EXECUTE AS – klauzule  
 Můžete použít EXECUTE AS klauzule v hlavičce definice uložené procedury, aktivační události nebo uživatelem definovanou funkci (s výjimkou vložené funkce vracející tabulku). To způsobí, že postup spuštěn v kontextu uživatelské jméno nebo zadaný v EXECUTE AS – klíčové slovo klauzule. Vytvořit uživatele proxy serveru v databázi, která není namapován na přihlášení, udělení ho jenom nezbytná oprávnění u objektů přístup procedurou. Pouze proxy uživatel zadaný v EXECUTE jako klauzule musí mít oprávnění pro přístup k modulu pro všechny objekty.  
  
> [!NOTE]
>  Některé akce, jako je TRUNCATE TABLE nemají udělitelný oprávnění. Zařadit příkaz v rámci procedury a zadání uživatele proxy serveru, který má oprávnění k příkazu ALTER TABLE, můžete rozšířit oprávnění ke zkrácení tabulky pro volající, kteří mají oprávnění provést jen v postupu.  
  
 Kontext, zadaný v EXECUTE jako klauzule je platný po dobu trvání procesu, včetně vnořené procedur a triggerů. Po dokončení provádění nebo příkaz REVERT se objeví, vrátí kontext volajícímu.  
  
 Existují tři kroky potřebné při používání EXECUTE AS klauzule v postupu.  
  
1.  Vytvořte uživatele proxy serveru v databázi, která není namapován na přihlášení. Tento krok není povinný, ale pomáhá při správě oprávnění.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1.  Udělte nezbytná oprávnění uživatele proxy serveru.  
  
2.  Přidat EXECUTE AS klauzule uložená procedura nebo uživatelem definované funkce.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  Aplikace, které vyžadují auditování možné zrušit, protože původní kontext zabezpečení volajícího nezůstanou zachovány. Integrované funkce, které vrátí identitu aktuálního uživatele, jako je například SESSION_USER, uživatele nebo uživatelské_jméno, vrátí uživatele přidruženého k EXECUTE AS klauzule, není původní volající.  
  
### <a name="using-execute-as-with-revert"></a>Pomocí vrátit EXECUTE AS  
 Příkaz vrátit Transact-SQL můžete obnovit původní kontextu spuštění.  
  
 Klauzuli volitelné, s ne vrátit COOKIE = @variableName, umožňuje Pokud přepnete zpět do volající kontext provádění @variableName proměnná obsahuje správnou hodnotu. Umožňuje přepnout kontext provádění volající v prostředích, kde se používá sdružování připojení. Protože hodnota @variableName známý pouze volající EXECUTE AS prohlášení, volající může zaručit, že kontextu spuštění nelze změnit koncovým uživatelem, která volá aplikaci. Když se připojení uzavře, je vrácen do fondu. Další informace o připojení sdružování v ADO.NET, najdete v části [SQL sdružování připojení serveru (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Určení kontextu spuštění  
 Kromě určení uživatele, můžete také použít EXECUTE AS s žádným z následujících klíčových slov.  
  
-   VOLAJÍCÍ. Provádění jako VOLAJÍCÍ je výchozí; Pokud není zadána žádná další možnost, postup spustí v kontextu zabezpečení volajícího.  
  
-   VLASTNÍK. Postup spuštění jako vlastník provede v rámci postupu vlastníka. Pokud se ve schématu vlastníkem vytvoří postup `dbo` nebo vlastník databáze postup bude vykonán neomezená oprávnění.  
  
-   SÁM SEBOU. Provádění jako vlastní spustí v kontextu zabezpečení Tvůrce uložené procedury. Jde o ekvivalent spuštění jako zadaného uživatele, pokud zadaný uživatel osobou vytvoření či změna postupu.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Přepínání kontextu](http://msdn.microsoft.com/library/ms188268.aspx) v Online knihách serveru SQL|Obsahuje odkazy na témata s popisem použití EXECUTE AS klauzule.|  
|[Pro vytvoření vlastní sadu oprávnění pomocí EXECUTE AS](http://msdn.microsoft.com/library/ms190384.aspx) a [pomocí EXECUTE AS v modulech](http://msdn.microsoft.com/library/ms178106.aspx) v Online knihách serveru SQL|Témata popisují, jak používat EXECUTE AS klauzule.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Úpravy dat pomocí uložených procedur](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
