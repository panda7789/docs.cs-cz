---
title: "Podepisování uložené procedury v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b3d90579e28fde40d461bdb511d797e5d7f6f179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="signing-stored-procedures-in-sql-server"></a>Podepisování uložené procedury v systému SQL Server
Uložená procedura s certifikát nebo asymetrický klíč můžete přihlásit. To je určen pro scénáře, když prostřednictvím vlastnictví řetězení nelze zdědit oprávnění nebo když je porušený, jako je například dynamická SQL řetězec vlastnictví. Potom vytvoření uživatele namapované na certifikát, udělení uživatelských oprávnění u objektů, které uloženou proceduru potřebuje pro přístup k certifikátu.  
  
 Při spuštění uložené procedury systému SQL Server kombinuje oprávnění uživatele certifikát s těmi, která volajícího. Na rozdíl od EXECUTE KLAUZULI, kontext provádění procedury nemění. Integrované funkce této návratový přihlášení a uživatelská jména vrátí název volajícího, není certifikát uživatelské jméno.  
  
 Digitální podpis je šifrovaný privátní klíč podepisující ověřování algoritmem digest data. Privátní klíč zajišťuje, že digitální podpis jedinečné pro jeho nosiče nebo vlastníka. Můžete si uložené procedury, funkce nebo aktivační události.  
  
> [!NOTE]
>  Certifikát můžete vytvořit v hlavní databázi, a udělit oprávnění na úrovni serveru.  
  
## <a name="creating-certificates"></a>Vytváření certifikátů  
 Když se přihlásíte uložené procedury s certifikátem, algoritmus digest dat skládající se z šifrované hodnoty hash kód uložené procedury je vytvořený pomocí soukromého klíče. V době běhu je data digest dešifrovat pomocí veřejného klíče a porovná s hodnotou hash uložené procedury. Úprava uloženou proceduru zruší platnost hodnota hash, tak, aby už odpovídá digitální podpis. Tím se zabrání někoho, kdo nemá přístup k privátnímu klíči z Změna kódu uložené procedury. Proto musíte znovu podepsat postup pokaždé, když upravíte ji.  
  
 Se účastní podepisování modul čtyři kroky:  
  
1.  Vytvoření certifikátu pomocí jazyka Transact-SQL `CREATE CERTIFICATE [certificateName]` příkaz. Tento příkaz má několik možností pro nastavení počáteční a koncové datum a heslo. Výchozí datum vypršení platnosti je jeden rok  
  
2.  Vytvořit databázi uživatele přidruženého k certifikátu pomocí jazyka Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` příkaz. Tohoto uživatele existuje pouze v databázi a nejsou spojené s přihlášením.  
  
3.  Udělte certifikát požadovaná oprávnění pro databázové objekty.  
  
> [!NOTE]
>  Certifikát nelze udělit oprávnění pro uživatele, kterého se použila oprávnění odvolat pomocí příkazu ODEPŘÍT. ODEPŘÍT vždy má přednost před udělení, brání volající dědění oprávnění udělená uživateli certifikát.  
  
1.  Podepsat certifikát pomocí jazyka Transact-SQL postup `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` příkaz.  
  
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
