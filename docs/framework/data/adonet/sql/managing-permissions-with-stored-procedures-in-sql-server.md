---
title: Správa oprávnění pomocí uložených procedur na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 0688157b45892cacb73f858dffb93836da9fc91d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229989"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Správa oprávnění pomocí uložených procedur na SQL Serveru
Jedním ze způsobů vytvoření více řádků obrany kolem vaše databáze je k implementaci všech přístup k datům pomocí uložených procedur a uživatelem definované funkce. Odvolat nebo odepřít všechna oprávnění pro příslušné objekty, jako jsou tabulky a udělení oprávnění EXECUTE na uložené procedury. Tím se vytvoří efektivně bezpečnostní hraniční sítě kolem dat a databázových objektů.  
  
## <a name="stored-procedure-benefits"></a>Výhody uložené procedury  
 Uložené procedury nabízí tyto výhody:  
  
-   Pravidel pro logiku a obchodní data, lze zapouzdřit tak, aby uživatelé můžete přístup k datům a objekty pouze způsobem, že vývojáři a správci databází.  
  
-   Parametrizované uložené procedury, které byly ověřeny všechny uživatele, je možné zabránit útokům prostřednictvím injektáže SQL. Pokud používáte dynamic SQL, nezapomeňte parametrizovat příkazům a nikdy Nezahrnovat hodnoty parametrů přímo do řetězce dotazu.  
  
-   Ad hoc dotazy a data změny může být zakázáno. To zabrání uživatelům neúmyslně nebo záměrně – došlo k poškození dat nebo provádění dotazů, které zhoršit výkon na serveru nebo v síti.  
  
-   Chyby mohou být zpracovány v kódu procedury bez předávaný přímo do klientské aplikace. To zabrání chybové zprávy se vrátilo, který může pomoci při zjišťování útoku. Protokolování chyb a zpracování na serveru.  
  
-   Uložené procedury lze zapsat jednou a přistupuje mnoho aplikací.  
  
-   Klientské aplikace není nutné znát základní datové struktury. Uložená procedura kódu můžete změnit bez nutnosti změn v klientských aplikacích za předpokladu, změny nemají vliv na seznamy parametrů nebo vrácena datové typy.  
  
-   Uložené procedury může snížit síťový provoz díky kombinaci více operací do jedné protokolu TDS.  
  
## <a name="stored-procedure-execution"></a>Provedení uložené procedury  
 Uložené procedury Využijte výhod vlastnictví řetězení k poskytnutí přístupu k datům tak, aby uživatelé nepotřebují mít explicitní oprávnění pro přístup k databázové objekty. Řetěz vlastnictví existuje, když objekty, které přistupují k sobě navzájem postupně jsou vlastněné stejným uživatelem. Například ostatní uložené procedury lze volat uloženou proceduru nebo uložené procedury lze přistupovat k více tabulek. Pokud mají všechny objekty v řetězu certifikátů spuštění stejného vlastníka, pak SQL Server kontroluje pouze oprávnění ke spuštění pro volající, není volajícího oprávnění na jiné objekty. Proto je nutné udělit pouze oprávnění spouštět na uložené procedury; můžete odvolat nebo odebrat všechna oprávnění k podkladové tabulky.  
  
## <a name="best-practices"></a>Doporučené postupy  
 Jednoduše zápis uložených procedur není dost informací k odpovídajícím způsobem zabezpečení aplikace. Měli byste také zvážit následující možných bezpečnostních děr.  
  
-   Udělení oprávnění EXECUTE na uložené procedury pro databázové role, které chcete mít možnost přístupu k datům.  
  
-   Odvolat či odepřít všechna oprávnění k podkladové tabulky pro všechny role a uživatele v databázi, včetně `public` role. Z veřejné dědí oprávnění všichni uživatelé. Proto odepřením oprávnění `public` znamená to jenom vlastníci a `sysadmin` členové mají přístup; všichni ostatní uživatelé nebudou moci dědit oprávnění z členství v jiných rolích.  
  
-   Bez přidání uživatele nebo role, aby `sysadmin` nebo `db_owner` role. Správci systému a vlastníci databáze můžete přístup ke všem objektům v databázi.  
  
-   Zakažte `guest` účtu. To zabrání anonymním uživatelům s připojením k databázi. Ve výchozím nastavení nové databáze je zakázána účet guest.  
  
-   Implementace chyba zpracování a protokolu chyb.  
  
-   Vytvořte parametrizované uložené procedury, které byly ověřeny všechny uživatelský vstup. Zpracovávat veškerý vstup uživatele jako nedůvěryhodné.  
  
-   Vyhněte dynamic SQL, pokud není nezbytně nutné. Použijte funkci QUOTENAME() příkazů jazyka Transact-SQL k vymezení hodnotu řetězce a escape jakékoli výskyt oddělovače ve vstupním řetězci.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Uložené procedury](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) a [útok prostřednictvím injektáže SQL](https://go.microsoft.com/fwlink/?LinkId=98234) v Online knihách serveru SQL|Témata popisují postup vytvoření uložených procedur a jak funguje útok prostřednictvím injektáže SQL.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [Úpravy dat pomocí uložených procedur](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
