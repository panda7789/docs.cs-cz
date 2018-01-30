---
title: "Podepisování uložené procedury v systému SQL Server"
ms.custom: 
ms.date: 01/05/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 15771cc214ee17bc2c98bab2423013483d1355f1
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a>Podepisování uložené procedury v systému SQL Server
 Digitální podpis je šifrovaný privátní klíč podepisující ověřování algoritmem digest data. Privátní klíč zajišťuje, že digitální podpis jedinečné pro jeho nosiče nebo vlastníka. Můžete si uložené procedury, funkce (s výjimkou vložené funkce vracející tabulku), aktivační události a sestavení.  
  
 Uložená procedura s certifikát nebo asymetrický klíč můžete přihlásit. To je určen pro scénáře, když prostřednictvím vlastnictví řetězení nelze zdědit oprávnění nebo když je porušený, jako je například dynamická SQL řetězec vlastnictví. Potom můžete vytvořit uživatele namapované na certifikát, udělení uživatelských oprávnění u objektů, které uloženou proceduru potřebuje pro přístup k certifikátu.  

 Také vytvořit přihlášení namapované na stejný certifikát a potom můžete udělit všechny potřebné oprávnění na úrovni serveru na tomto přihlášení nebo přidejte přihlášení na jeden nebo více rolí pevného serveru. To slouží k nedoporučujeme povolovat `TRUSTWORTHY` databáze nastavení pro scénáře, ve kterých jsou potřeba vyšší úroveň oprávnění.  
  
 Při spuštění uložené procedury systému SQL Server kombinuje oprávnění certifikát uživatele a/nebo přihlášení s těmi, která volajícího. Na rozdíl od `EXECUTE AS` klauzuli nezmění kontext provádění procedury. Integrované funkce této návratový přihlášení a uživatelská jména vrátí název volajícího, není certifikát uživatelské jméno.  
  
## <a name="creating-certificates"></a>Vytváření certifikátů  
 Při přihlašování uložená procedura s certifikát nebo asymetrický klíč, algoritmus digest dat, který se skládá z šifrované hodnoty hash uložené procedury kódu, společně s execute-jako uživatel, je vytvořený pomocí soukromého klíče. V době běhu je data digest dešifrovat pomocí veřejného klíče a porovná s hodnotou hash uložené procedury. Změna execute-jako uživatel zruší platnost hodnota hash tak, aby už odpovídá digitální podpis. Úprava uloženou proceduru zahodí podpis úplně, aby se zabránilo někoho, kdo nemá přístup k privátnímu klíči z Změna kódu uložené procedury. V obou případech musíte znovu podepsat postup pokaždé, když změníte kód nebo execute-jako uživatel.  
  
 Se účastní podepisování modul dvě požadované kroky:  
  
1.  Vytvoření certifikátu pomocí jazyka Transact-SQL `CREATE CERTIFICATE [certificateName]` příkaz. Tento příkaz má několik možností pro nastavení počáteční a koncové datum a heslo. Výchozí datum vypršení platnosti je jeden rok.  
  
1.  Podepsat certifikát pomocí jazyka Transact-SQL postup `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` příkaz.  

Jakmile modul byl podepsán, jeden nebo více objektů musí být vytvořen aby udržení další oprávnění, které by měly být přidruženy s certifikátem.  

Pokud modul potřebuje další oprávnění na úrovni databáze:  
  
1.  Vytvořit databázi uživatele přidruženého k certifikátu pomocí jazyka Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` příkaz. Tohoto uživatele existuje pouze v databázi a nejsou spojené s přihlašovacími údaji, pokud přihlášení také byly vytvořeny z tohoto stejný certifikát.  
  
1.  Udělte certifikátu vyžaduje oprávnění na úrovni databáze.  
  
Pokud modul potřebuje další oprávnění na úrovni serveru:  
  
1.  Zkopírujte certifikát, který chcete `master` databáze.  
 
1.  Vytvořte přihlašovací údaje související s certifikátu pomocí jazyka Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` příkaz.  
  
1.  Udělte přihlášení certifikát požadovaná oprávnění na úrovni serveru.  
  
> [!NOTE]  
>  Certifikát nelze udělit oprávnění pro uživatele, kterého se použila oprávnění odvolat pomocí příkazu ODEPŘÍT. ODEPŘÍT vždy má přednost před udělení, brání volající dědění oprávnění udělená uživateli certifikát.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Modul podepsání](http://go.microsoft.com/fwlink/?LinkId=98590) v Online knihách serveru SQL|Popisuje modul podepisování, zadání vzorový scénář a odkazy na související témata Transact-SQL.|  
|[Uložené procedury s certifikátem podepisování](http://msdn.microsoft.com/library/bb283630.aspx) v Online knihách serveru SQL|Kurz k podepisování uložené procedury s certifikátem.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Úpravy dat pomocí uložených procedur](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
