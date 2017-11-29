---
title: "Správa oprávnění pomocí uložené procedury v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 806cd23060dde3f7b466df0d4ce39162353380e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Správa oprávnění pomocí uložené procedury v systému SQL Server
Jedna z metod vytváření více řádků obrany kolem vaše databáze je implementace všechny přístup k datům pomocí uložené procedury nebo funkce definované uživatelem. Odvolání nebo odepřít všechna oprávnění k základní objekty, jako jsou tabulky a udělte oprávnění spouštět na uložené procedury. Tím se vytvoří efektivně zabezpečení hraniční kolem dat a databázových objektů.  
  
## <a name="stored-procedure-benefits"></a>Výhody uložené procedury  
 Uložené procedury mají následující výhody:  
  
-   Data logiku a obchodní pravidla můžete zapouzdřené tak, aby uživatelé můžete přístup k datům a objekty pouze způsoby, které chcete vývojáři a správci databází.  
  
-   Parametrizované uložené procedury, které ověření vstupu všechny uživatele lze zabránit útokům Injektáž SQL. Pokud používáte dynamické SQL, nezapomeňte Parametrizace příkazech a nikdy nezahrne hodnoty parametrů přímo do řetězce dotazu.  
  
-   Ad hoc dotazy a data změny můžete povoleny. To zabrání uživatelům neoprávněnému nebo neúmyslně zničení dat nebo provádění dotazů, které zhoršit výkon na serveru nebo sítě.  
  
-   Můžete zpracování chyb v postupu kódu bez předávány přímo pro klientské aplikace. To brání chybové zprávy vracené, který může pomoci při testování útoku. Protokolování chyb a zpracovat je na serveru.  
  
-   Uložené procedury můžete zapisovat jednou a získat přístup k mnoha aplikacemi.  
  
-   Klienta aplikace není nutné znát základní datové struktury. Uložené procedury kódu můžete změnit bez nutnosti změny v klientských aplikacích tak dlouho, dokud se změny neovlivní seznamy parametrů nebo vrácena datové typy.  
  
-   Uložené procedury může snížit zatížení sítě kombinací více operací do jedné procedury volání.  
  
## <a name="stored-procedure-execution"></a>Spuštění uložené procedury  
 Uložené procedury využívá výhod vlastnictví řetězení zajistit přístup k datům tak, aby uživatelé nemusí mít výslovná oprávnění pro přístup k databázové objekty. Řetězce vlastnictví existuje objekty, které postupně k druhému přistupovat jsou vlastněny stejného uživatele. Například uložené procedury můžete volat jiné uložené procedury nebo uložené procedury lze získat přístup k více tabulek. Pokud mají všechny objekty v řetězu provádění stejného vlastníka, pak systému SQL Server zkontroluje pouze oprávnění ke spuštění pro volající, ne volajícího oprávnění na jiné objekty. Proto musíte udělit pouze oprávnění spouštění na uložené procedury; můžete odvolat nebo odepřít všechna oprávnění pro základní tabulky.  
  
## <a name="best-practices"></a>Doporučené postupy  
 Jednoduše zápis uložených procedur není dost adekvátní zabezpečit vaše aplikace. Měli byste také zvážit následující potenciální bezpečnostní díry.  
  
-   Udělte oprávnění spouštět na uložené procedury pro databázové role, které chcete mít možnost přístupu k datům.  
  
-   Odvolat či odepřít všechna oprávnění na základní tabulky pro všechny role a uživatele v databázi, včetně `public` role. Všichni uživatelé dědí oprávnění od veřejné. Proto odepření oprávnění k `public` znamená to jenom vlastníci a `sysadmin` členové mají přístup; všichni ostatní uživatelé nebudou moci dědí oprávnění od členství v jiné role.  
  
-   Nepřidávejte uživatele nebo role, aby `sysadmin` nebo `db_owner` role. Správci a vlastníci databáze můžete přístup ke všem objektům databáze.  
  
-   Zakažte `guest` účtu. To bude anonymním uživatelům zabránit v připojení k databázi. Ve výchozím nastavení v nových databází vypnutá účet hosta.  
  
-   Implementovat chyba zpracování a protokolu chyb.  
  
-   Vytvořte parametrizované uložené procedury, které ověření vstupu všechny uživatele. Všechny uživatelský vstup považovat za nedůvěryhodný.  
  
-   Vyhnout dynamické SQL, pokud není nezbytně nutné. Použijte funkci QUOTENAME() Transact-SQL a tím vymezit řetězcovou hodnotu vyhnuli kterýkoli z výskytů oddělovače ve vstupním řetězci.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Uložené procedury](http://msdn.microsoft.com/library/ms190782.aspx) a [Injektáž SQL](http://go.microsoft.com/fwlink/?LinkId=98234) v Online knihách serveru SQL|Témata popisují, jak vytvořit uložené procedury a jak funguje Injektáž SQL.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scénáře zabezpečení aplikací v systému SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Zápis zabezpečené dynamické SQL v systému SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Podepisování uložené procedury v systému SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Přizpůsobení oprávnění s zosobnění v systému SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Úprava dat pomocí uložené procedury](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
