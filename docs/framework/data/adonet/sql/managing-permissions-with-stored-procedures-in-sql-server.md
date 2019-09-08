---
title: Správa oprávnění pomocí uložených procedur na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 412d2a0a292e2ac83e6c42cf721c83e63633408c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780949"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Správa oprávnění pomocí uložených procedur na SQL Serveru
Jednou z metod vytvoření více řádků obrany v databázi je implementace veškerého přístupu k datům pomocí uložených procedur nebo uživatelsky definovaných funkcí. Odvoláte nebo odepřete všechna oprávnění k podkladovým objektům, jako jsou tabulky, a udělte oprávnění k provádění uložených procedur. Tím se efektivně vytvoří hraniční zabezpečení kolem vašich dat a databázových objektů.  
  
## <a name="stored-procedure-benefits"></a>Výhody uložených procedur  
 Uložené procedury mají následující výhody:  
  
- Data logiky a podnikových pravidel je možné zapouzdřit, aby uživatelé měli přístup k datům a objektům pouze způsobem, který mají vývojáři a správci databází v úmyslu.  
  
- Parametrizované uložené procedury, které ověřují všechny vstupy uživatelů, se dají použít k vzdoruje útoku prostřednictvím injektáže SQL. Použijete-li Dynamic SQL, nezapomeňte příkazy parametrizovat a nikdy Nezahrnovat hodnoty parametrů přímo do řetězce dotazu.  
  
- Je možné, že se nepovolí ad hoc dotazy a změny dat. To zabrání uživatelům v škodlivých nebo neúmyslném zničení dat nebo provádění dotazů, které mají vliv na výkon serveru nebo sítě.  
  
- Chyby lze zpracovat v kódu procedury bez předání přímo klientským aplikacím. To brání tomu, aby se vracely chybové zprávy, které by mohly pomoci při útoku na zjišťování. Protokoluje chyby a zpracuje je na serveru.  
  
- Uložené procedury lze zapsat jednou a k nim mají pøístup mnoho aplikací.  
  
- Klientské aplikace nepotřebují znát žádné informace o podkladových datových strukturách. Uložený kód procedury lze změnit bez nutnosti změny v klientských aplikacích, pokud změny neovlivňují seznamy parametrů ani vrácené datové typy.  
  
- Uložené procedury mohou snížit zatížení sítě kombinací více operací do jednoho volání procedury.  
  
## <a name="stored-procedure-execution"></a>Spuštění uložené procedury  
 Uložené procedury využívají výhod zřetězení vlastnictví k poskytnutí přístupu k datům, aby uživatelé nemuseli mít explicitní oprávnění k přístupu k databázovým objektům. Řetěz vlastnictví existuje, pokud objekty, které jsou na sobě navzájemně přistupují, jsou vlastněny stejným uživatelem. Například uložená procedura může volat jiné uložené procedury nebo uložená procedura může získat přístup k několika tabulkám. Pokud mají všechny objekty v řetězci spuštění stejný vlastník, pak SQL Server pouze kontroluje oprávnění EXECUTE pro volajícího, nikoli oprávnění volajícího pro jiné objekty. Proto musíte pro uložené procedury udělit pouze oprávnění ke spouštění. v podkladových tabulkách můžete odvolat nebo odepřít všechna oprávnění.  
  
## <a name="best-practices"></a>Doporučené postupy  
 Pouhým zápisem uložených procedur nestačí dostatečně zabezpečit svoji aplikaci. Měli byste také zvážit následující potenciální bezpečnostní otvory.  
  
- Udělte oprávnění EXECUTE pro uložené procedury databázových rolí, které chcete mít přístup k datům.  
  
- Odvolat nebo odepřít všechna oprávnění k podkladovým tabulkám pro všechny role a uživatele v databázi, včetně `public` role. Všichni uživatelé dědí oprávnění z veřejného. Proto odepření oprávnění `public` znamená, že mají přístup pouze `sysadmin` vlastníci a členové; všichni ostatní uživatelé nebudou moci dědit oprávnění z členství v jiných rolích.  
  
- Nepřidávejte uživatele nebo role do `sysadmin` rolí nebo. `db_owner` Správci systému a vlastníci databází mají přístup ke všem databázovým objektům.  
  
- Zakažte `guest` účet. Tato akce zabrání anonymním uživatelům v připojení k databázi. Účet hosta je ve výchozím nastavení v nových databázích zakázán.  
  
- Implementuje zpracování chyb a protokolování chyb.  
  
- Vytvořte parametrizované uložené procedury, které ověřují všechny vstupy uživatele. Považovat všechny vstupy uživatelů za nedůvěryhodné.  
  
- Vyhněte se dynamickému SQL, pokud není nezbytně nutné. Použijte funkci Transact-SQL QUOTa () k vymezení řetězcové hodnoty a řídicího znaku ve vstupním řetězci.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Uložené procedury](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) a [injektáže SQL](https://go.microsoft.com/fwlink/?LinkId=98234) na SQL Server Knihy online|Témata popisují postup vytvoření uložených procedur a způsobu, jakým funguje injektáže SQL.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](writing-secure-dynamic-sql-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](signing-stored-procedures-in-sql-server.md)
- [Přizpůsobení oprávnění se zosobněním na SQL Serveru](customizing-permissions-with-impersonation-in-sql-server.md)
- [Úpravy dat pomocí uložených procedur](../modifying-data-with-stored-procedures.md)
- [Přehled ADO.NET](../ado-net-overview.md)
