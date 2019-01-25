---
title: Podepisování uložených procedur na SQL serveru
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: da7b21d725d301006288245c940e4367c3ce8568
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606819"
---
# <a name="signing-stored-procedures-in-sql-server"></a>Podepisování uložených procedur na SQL serveru
 Digitální podpis je algoritmu digest data zašifrovaná pomocí soukromého klíče podpisu. Privátní klíč zajistí, že digitální podpis je jedinečné pro jeho nosiče nebo vlastníka. Uložené procedury, funkce (s výjimkou vložené funkce vracející tabulku), aktivační události a sestavení se můžete přihlásit.  
  
 Uložená procedura s certifikátem nebo asymetrickým klíčem se můžete přihlásit. To je určen pro scénáře, když nelze dědit oprávnění prostřednictvím řetězení vlastnictví nebo když řetězce vlastnictví bylo přerušeno, jako je například dynamické SQL. Pak vytvoříte uživatele mapovat na certifikát, udělení uživatelských oprávnění na objekty, které uloženou proceduru potřebuje přístup k certifikátu.  

 Je můžete také vytvořit přihlašovací jméno mapované na stejný certifikát a pak udělit všechna nezbytná oprávnění na úrovni serveru na tomto přihlášení nebo přidat přihlášení na jeden nebo více rolí serveru. To je navržená tak, aby povolení `TRUSTWORTHY` databáze nastavení pro scénáře, ve kterých jsou potřeba oprávnění vyšší úrovně.  
  
 Při spuštění uložené procedury kombinuje SQL Server oprávnění certifikátů uživatele a/nebo přihlášení s těmi volajícího. Na rozdíl od `EXECUTE AS` klauzule nezmění kontext provádění procedury. Integrované funkce tento návratový přihlašovací a uživatelská jména vrátí jméno volajícího, není certifikát uživatelské jméno.  
  
## <a name="creating-certificates"></a>Vytváření certifikátů  
 Při přihlašování uloženou proceduru s certifikátem nebo asymentrickým klíčem, algoritmus digest dat skládající se z šifrované hodnoty hash uloženou proceduru kódu, společně s execute – jako uživatel, se vytvoří pomocí soukromého klíče. V době běhu je ověřování algoritmem digest data dešifrovat pomocí veřejného klíče a ve srovnání s hodnotou hash uloženou proceduru. Změna execute – jako uživatel zruší platnost hodnoty hash tak, aby už neodpovídá digitální podpis. Úprava uloženou proceduru zahodí podpis zcela, což zabraňuje někoho, kdo nemá přístup k privátnímu klíči možnost měnit kód uloženou proceduru. V obou případech musíte znovu podepsat postup při každé změně kódu nebo execute – jako uživatel.  
  
 Při podepisování modulu jsou dva kroky:  
  
1.  Vytvořit certifikát pomocí příkazů jazyka Transact-SQL `CREATE CERTIFICATE [certificateName]` příkazu. Tento příkaz obsahuje celou řadu možností pro nastavení počáteční a koncové datum a heslo. Výchozí datum vypršení platnosti je 1 rok.  
  
1.  Podepsat certifikát s použitím příkazů jazyka Transact-SQL postupu `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` příkazu.  

Jakmile modul byl podepsán, jeden nebo více objektů zabezpečení je potřeba vytvořit, aby bylo možné obsahovat další oprávnění, které by měly být přidruženy s certifikátem.  

Pokud je nutné modul další oprávnění na úrovni databáze:  
  
1.  Vytvořte uživatele databáze spojené s použitím příkazů jazyka Transact-SQL certifikátu `CREATE USER [userName] FROM CERTIFICATE [certificateName]` příkazu. Tohoto uživatele existuje pouze v databázi a není přidružen k přihlášení, pokud přihlášení také byly vytvořeny z tohoto stejného certifikátu.  
  
1.  Certifikát uživateli udělte požadované oprávnění na úrovni databáze.  
  
Pokud je nutné modul další oprávnění na úrovni serveru:  
  
1.  Zkopírujte certifikát, který `master` databáze.  
 
1.  Vytvořte přihlašovací údaje související s použitím příkazů jazyka Transact-SQL certifikátu `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` příkazu.  
  
1.  Udělte požadovaná oprávnění na úrovni serveru přihlášení certifikátu.  
  
> [!NOTE]  
>  Certifikát nelze udělit oprávnění uživateli, který má určitá oprávnění odvolat ODEPŘÍT příkaz using. ODEPŘÍT vždy přednost udělení, brání volajícímu dědí oprávnění udělená uživatelského certifikátu.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Modul podepsání](https://go.microsoft.com/fwlink/?LinkId=98590) v Online knihách serveru SQL|Popisuje modul podepisování, vzorový scénář a odkazy na relevantní témata příkazů jazyka Transact-SQL.|  
|[Podepisování uložených procedur s certifikátem](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate) v Online knihách serveru SQL|Poskytuje návod pro podepisování certifikátem uloženou proceduru.|  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [Úpravy dat pomocí uložených procedur](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
