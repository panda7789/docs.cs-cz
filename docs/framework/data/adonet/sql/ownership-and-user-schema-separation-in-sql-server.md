---
title: Vlastnictví a oddělení uživatelských schémat na SQL serveru
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 7b1cda211fdc89732afa8eed1eaaf2c98309a969
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741914"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Vlastnictví a oddělení uživatelských schémat na SQL serveru
Základním konceptem zabezpečení SQL serveru je, že vlastníci objekty mají neodvolatelnou oprávnění ke správě je. Nelze odebrat oprávnění z objektu vlastníka a z databáze nelze vyřadit uživatele, pokud vlastní objekty v ní.  
  
## <a name="user-schema-separation"></a>Oddělení uživatelských schémat  
 Oddělení uživatelských schémat umožňuje větší flexibilitu při správě oprávnění objektu databáze. A *schématu* je pojmenovaný kontejner pro databázové objekty, což vám umožní do objektů skupiny do samostatných oborů názvů. Například ukázkové databáze AdventureWorks obsahuje schémata pro produkci, prodej a lidských zdrojů.  
  
 Složené ze čtyř částí názvů syntaxe pro odkazování na objekty Určuje název schématu.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Vlastníci schématu a oprávnění  
 Schémata může být vlastněn libovolný objekt zabezpečení databáze, a vytvoří se jeden objekt může vlastnit více schémat. Pravidla lze použít zabezpečení na schéma, které dědí všechny objekty ve schématu. Až nastavíte přístupová oprávnění pro schéma, tato oprávnění se automaticky použijí jako nové objekty jsou přidány do schématu. Uživatelům je možné přiřadit výchozí schéma a více uživatelů databáze můžete sdílet stejné schéma.  
  
 Ve výchozím nastavení když vývojáři vytvářet objekty ve schématu, objekty jsou vlastněny objektu zabezpečení, který vlastní schéma není pro vývojáře. Pomocí příkazu ALTER AUTORIZACE Transact-SQL lze přenést vlastnictví objektu. Schéma může také obsahovat objekty, které jsou vlastněny různých uživatelů a oprávnění podrobnější než přiřazené do schématu, i když se to nedoporučuje, protože přispějete ke složitosti správy oprávnění. Objekty lze přesunout mezi schémata a schéma vlastnictví, dají se přenášet mezi objekty zabezpečení. Uživatelé databáze můžete vyřadit bez ovlivnění schémata.  
  
### <a name="built-in-schemas"></a>Předdefinovaných schémat  
 SQL Server se dodává s deset předem definovaná schémata, které mají stejné názvy jako integrované databáze uživatelů a rolí. Existují především z důvodu zpětné kompatibility. Schémata, která mají stejné názvy jako pevné databázové role, pokud je nepotřebujete, můžete zrušit. Nelze vyřadit následující schémata:  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 Pokud je vyřadit z databáze modelu, nezobrazí se v nové databáze.  
  
> [!NOTE]
>  `sys` a `INFORMATION_SCHEMA` schémata jsou rezervované pro systémové objekty. Nemůže vytvořit objekty v těchto schématech a nelze je vyřadit.  
  
#### <a name="the-dbo-schema"></a>Dbo schématu  
 `dbo` Schéma je výchozí schéma pro nově vytvořenou databázi. `dbo` Vlastní schéma `dbo` uživatelský účet. Ve výchozím nastavení, mají uživatelé vytvoření pomocí příkazu Vytvořit uživatele příkazů jazyka Transact-SQL `dbo` jako jejich výchozí schéma.  
  
 Uživatelé, kteří jsou přiřazeni `dbo` schématu nedědí oprávnění `dbo` uživatelský účet. Žádná oprávnění jsou zděděny z schématu uživatelů. oprávnění schématu jsou děděné databázové objekty obsažené ve schématu.  
  
> [!NOTE]
>  Databázové objekty je odkazováno pomocí názvu jednu část, SQL Server nejprve hledá v výchozí schéma uživatele. Pokud se objekt nenajde existuje, hledá dále v systému SQL Server `dbo` schématu. Pokud není v objektu `dbo` schéma, je vrácena chyba.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o vlastnictví objektu a schémat najdete v následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Oddělení uživatelských schémat](https://msdn.microsoft.com/library/ms190387.aspx) v Online knihách serveru SQL|Jsou zde popsány změny zavedené oddělení uživatelských schémat. Zahrnuje nové chování, jeho dopad na vlastnictví, zobrazení katalogu a oprávnění.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serverové a databázové role na SQL Serveru](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
