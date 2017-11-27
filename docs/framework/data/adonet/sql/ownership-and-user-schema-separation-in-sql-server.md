---
title: "Vlastnictví a oddělení schéma uživatele v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 168eaf9bc0bbac80cbd1e2bb0538aab89d262a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Vlastnictví a oddělení schéma uživatele v systému SQL Server
Koncept základní zabezpečení systému SQL Server je, že vlastníky objektů mít neodvolatelný oprávnění ke správě je. Oprávnění nelze odstranit z objektu vlastníka a z databáze nelze vyřadit uživatele, pokud vlastní objekty v něm.  
  
## <a name="user-schema-separation"></a>Schéma uživatele oddělení  
 Oddělení schéma uživatele umožňuje větší flexibilitu při správě oprávnění objektu databáze. A *schématu* je pojmenované kontejner pro databázové objekty, které vám umožní do objektů skupiny do samostatné obory názvů. Například ukázkovou databázi AdventureWorks obsahuje schémata pro produkční, prodej a Lidskézdroje.  
  
 Odkazy na objekty sestávající ze čtyř částí pojmenování syntaxe Určuje název schématu.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Vlastníci schématu a oprávnění  
 Schémata můžete vlastnit žádné objekt zabezpečení databáze, a jeden objekt může vlastní více schématy. Můžete použít pravidla zabezpečení na schéma, které jsou zdědí všechny objekty ve schématu. Až nastavíte přístupová oprávnění pro schéma, tato oprávnění budou automaticky použita jako schématu se přidají nové objekty. Uživatelé se dají přiřadit výchozí schéma a více uživatelů databáze můžete sdílet stejné schéma.  
  
 Ve výchozím nastavení když vývojáři vytvářet objekty ve schématu, objekty jsou vlastněny objekt zabezpečení, která vlastní schéma, není vývojář. Vlastnictví objektů lze převést pomocí příkazu ALTER AUTORIZACE Transact-SQL. Schéma může také obsahovat objekty, které jsou vlastněny různým uživatelům a podrobnější oprávnění než ty, které jsou přiřazené k schématu, i když se to nedoporučuje, protože přidá složitost správy oprávnění. Objekty lze přesunout mezi schémata a schéma vlastnictví, dají se přenášet mezi objekty zabezpečení. Uživatelé databáze můžete vyřadit, aniž by to ovlivnilo schémat.  
  
### <a name="built-in-schemas"></a>Předdefinovaných schémat.  
 SQL Server se dodává s deset předdefinovaných schémat, které mají stejné názvy jako integrovanou databází uživatelů a rolí. Tyto existovat především z důvodu zpětné kompatibility. Můžete vložit schémat, které mají stejné názvy jako pevné databázové role, pokud je nepotřebujete. Nelze vyřadit následujících schémat:  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 Pokud je vyřadit z modelová databáze, nezobrazí se v nové databáze.  
  
> [!NOTE]
>  `sys` a `INFORMATION_SCHEMA` schémata jsou vyhrazené pro systémové objekty. Nelze vytvořit objekty v těchto schémata a nelze vyřadit, je.  
  
#### <a name="the-dbo-schema"></a>Dbo schématu  
 `dbo` Schéma je výchozí schéma pro nově vytvořené databáze. `dbo` Schématu je vlastníkem `dbo` uživatelský účet. Ve výchozím nastavení, mají uživatelé byla vytvořena pomocí příkazu Vytvořit uživateli Transact-SQL `dbo` jako jejich výchozí schéma.  
  
 Uživatelé, kteří jsou přiřazeny `dbo` schématu nedědí oprávnění `dbo` uživatelský účet. Žádné oprávnění zdědí ze schématu uživatelé; oprávnění schématu jsou zděděny databázové objekty obsažené ve schématu.  
  
> [!NOTE]
>  Když jsou databázové objekty pomocí názvu složené z jedné části, SQL Server nejprve hledá v výchozí schéma uživatele. Pokud objekt existuje nenajde, podívá do systému SQL Server `dbo` schématu. Pokud objekt se nenachází `dbo` schématu, je vrácena chyba.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o vlastnictví objektů a schémat najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Schéma uživatele oddělení](http://msdn.microsoft.com/library/ms190387.aspx) v Online knihách serveru SQL|Popisuje změny zavedené oddělení schéma uživatele. Zahrnuje nové chování, jeho dopad na vlastnictví, zobrazení katalogu a oprávnění.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací v systému SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Ověřování v systému SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Server a databázových rolí v systému SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Autorizace a oprávnění v systému SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
