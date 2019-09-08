---
title: Scénáře zabezpečení aplikací na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: bf844f35a3504af52cdb6bf745862ad5098dfc5f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782689"
---
# <a name="application-security-scenarios-in-sql-server"></a>Scénáře zabezpečení aplikací na SQL Serveru
Neexistuje žádný jednoduchý způsob, jak vytvořit zabezpečenou SQL Server klientskou aplikaci. Každá aplikace je jedinečná ve svých požadavcích, prostředí nasazení a naplnění uživatelů. Aplikace, která je po počátečním nasazení dostatečně zabezpečená, může v průběhu času dojít k méně bezpečnému zabezpečení. Není možné předpovědět žádnou přesnost, které mohou být v budoucnu hrozby.  
  
 SQL Server jako produkt se vyvinulo v mnoha verzích, aby zahrnovaly nejnovější funkce zabezpečení, které vývojářům umožňují vytvářet zabezpečené databázové aplikace. Zabezpečení ale nepřichází v krabici. vyžaduje nepřetržité monitorování a aktualizaci.  
  
## <a name="common-threats"></a>Běžné hrozby  
 Vývojáři potřebují porozumět bezpečnostním hrozbám, nástrojům pro jejich čítače a tomu, jak se vyhnout bezpečnostním otvorům, které samy způsobili. Zabezpečení je možné nejlépe představit jako řetěz, kde přerušení na jednom spojení ohrožuje sílu celého celku. Následující seznam obsahuje některé běžné bezpečnostní hrozby, které jsou podrobněji popsány v tématech v této části.  
  
### <a name="sql-injection"></a>Injektáže SQL  
 Injektáže SQL je proces, pomocí kterého uživatel se zlými úmysly zadá příkazy jazyka Transact-SQL místo platného vstupu. Pokud je vstup předán přímo serveru bez ověření a pokud aplikace neúmyslně spouští vložený kód, pak útok může poškodit nebo zničit data. Můžete SQL Server vzdoruje útoky prostřednictvím injektáže pomocí uložených procedur a parametrizovaných příkazů, zabránit dynamickému SQL a omezit oprávnění pro všechny uživatele.  
  
### <a name="elevation-of-privilege"></a>Zvýšení oprávnění  
 Zvýšení oprávnění k útokům se projeví, když uživatel může převzít oprávnění důvěryhodného účtu, jako je třeba vlastník nebo správce. Vždy spouštějte pod minimálními uživatelskými účty, které mají oprávnění, a přiřaďte pouze potřebná oprávnění. Nepoužívejte účty pro správu nebo vlastníka ke spouštění kódu. Tím se omezí množství škod, ke kterým může dojít, pokud se útok nezdaří. Při provádění úloh, které vyžadují další oprávnění, použijte podepisování procedur nebo zosobnění pouze po dobu trvání úkolu. Uložené procedury můžete podepsat pomocí certifikátů nebo je použít zosobnění k dočasnému přiřazení oprávnění.  
  
### <a name="probing-and-intelligent-observation"></a>Zjišťování a inteligentní sledování  
 Útok na zjišťování může použít chybové zprávy generované aplikací pro hledání slabých míst zabezpečení. Implementujte zpracování chyb ve všech procedurální kód, aby se zabránilo vrácení informací SQL Server koncovému uživateli.  
  
### <a name="authentication"></a>Ověřování  
 Útok injektáže připojovacího řetězce může nastat při použití SQL Server přihlášení, pokud je v době běhu vytvořen připojovací řetězec založený na vstupu uživatele. Pokud není v připojovacím řetězci zaškrtnuto platné páry klíčového slova, může útočník vložit nadbytečné znaky, potenciálně získat přístup k citlivým datům nebo jiným prostředkům na serveru. Ověřování systému Windows používejte všude, kde je to možné. Pokud je nutné použít SQL Server přihlašovacích údajů, použijte <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytvoření a ověření připojovacích řetězců v době běhu.  
  
### <a name="passwords"></a>Hesel  
 Mnoho útoků je úspěšné, protože narušitel byl schopný získat nebo uhodnout heslo pro privilegovaného uživatele. Hesla představují první linii obrany proti narušitelům, takže nastavení silných hesel je nezbytné pro zabezpečení vašeho systému. Vytvořte a vyvynuťte zásady hesel pro ověřování ve smíšeném režimu.  
  
 Pro `sa` účet vždy přiřaďte silné heslo, a to i při použití ověřování systému Windows.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](managing-permissions-with-stored-procedures-in-sql-server.md)  
 Popisuje, jak pomocí uložených procedur spravovat oprávnění a řídit přístup k datům. Použití uložených procedur je účinný způsob, jak reagovat na mnoho bezpečnostních hrozeb.  
  
 [Zápis zabezpečené dynamické SQL na SQL Serveru](writing-secure-dynamic-sql-in-sql-server.md)  
 Popisuje techniky pro psaní zabezpečeného dynamického SQL pomocí uložených procedur.  
  
 [Podepisování uložených procedur na SQL Serveru](signing-stored-procedures-in-sql-server.md)  
 Popisuje, jak podepsat uloženou proceduru certifikátem, aby uživatelé mohli pracovat s daty, ke kterým nemají přímý přístup. Tím umožníte, aby uložené procedury prováděly operace, které volající nemá oprávnění k přímému provádění.  
  
 [Přizpůsobení oprávnění se zosobněním na SQL Serveru](customizing-permissions-with-impersonation-in-sql-server.md)  
 Popisuje způsob použití klauzule EXECUTE AS k zosobnění jiného uživatele. Zosobnění přepíná kontext spuštění od volajícího k zadanému uživateli.  
  
 [Udělení oprávnění na úrovni řádků na SQL Serveru](granting-row-level-permissions-in-sql-server.md)  
 Popisuje, jak implementovat oprávnění na úrovni řádků pro omezení přístupu k datům.  
  
 [Vytváření rolí aplikací na SQL Serveru](creating-application-roles-in-sql-server.md)  
 Popisuje funkce a funkce aplikačních rolí.  
  
 [Povolení přístupu mezi databázemi na SQL Serveru](enabling-cross-database-access-in-sql-server.md)  
 Popisuje, jak povolit přístup mezi databázemi bez ohrožených zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [SQL Server – zabezpečení](sql-server-security.md)
- [Přehled zabezpečení SQL Serveru](overview-of-sql-server-security.md)
- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Přehled ADO.NET](../ado-net-overview.md)
