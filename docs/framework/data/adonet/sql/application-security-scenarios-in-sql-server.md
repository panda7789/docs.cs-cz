---
title: Scénáře zabezpečení aplikací v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 1239715678bda648bc962f9b23667b954b540e3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="application-security-scenarios-in-sql-server"></a>Scénáře zabezpečení aplikací v systému SQL Server
Neexistuje žádný jeden správný způsob, jak vytvořit zabezpečený klientskou aplikaci SQL Server. Každá aplikace je jedinečné v jeho požadavky na prostředí pro nasazení a počet uživatelů. Aplikace, která je přiměřeně zabezpečen po počátečním nasazení se může stát méně zabezpečené v čase. Není možné předpovědět žádné přesnost co hrozeb můžou vznikat v budoucnu.  
  
 SQL Server, jako produkt, má vyvinuly prostřednictvím mnoha verzí začlenit nejnovější funkce zabezpečení, které umožňují vývojářům vytvářet aplikace zabezpečené databáze. Ale nepřejde do stavu zabezpečení v poli; To vyžaduje potom monitorování a aktualizace.  
  
## <a name="common-threats"></a>Běžné hrozeb  
 Vývojáři musí porozumět bezpečnostní hrozby, nástrojů pro čítače a jak se vyhnout samo celistvosti. Zabezpečení můžete nejlépe představit jako řetězec, kde zalomení v jeden odkaz ohrožuje sílu celek. Následující seznam obsahuje některé běžné bezpečnostních hrozeb, které jsou popsány podrobněji v tématech v této části.  
  
### <a name="sql-injection"></a>Injektáž SQL  
 Injektáž SQL je proces, pomocí kterého uživatel se zlými úmysly zadá příkazy jazyka Transact-SQL místo platný vstup. Pokud vstup je předán přímo k serveru bez ověřování a aplikace nechtěně spustí kód vložený, útoku se může dojít k poškození nebo zničení data. Můžete zabránit SQL Server vkládání útoky pomocí uložené procedury a příkazy s parametry, vyhnout dynamické SQL a omezení oprávnění pro všechny uživatele.  
  
### <a name="elevation-of-privilege"></a>Zvýšení oprávnění  
 Zvýšení úrovně oprávnění útoky nastane, když má uživatel přístup předpokládat, že oprávnění důvěryhodného účtu, jako je například roli vlastníka nebo správce. Vždy spustit pod nejméně privilegovaným uživatelské účty a přiřaďte pouze potřebná oprávnění. Vyhněte se použití správce nebo vlastníka účty pro provádění kódu. Toto omezení velikosti škody, které může dojít, pokud se podaří útoku. Při provádění úlohy, které vyžadují další oprávnění, použijte postup podepisování nebo zosobnění pouze po dobu trvání úlohy. Můžete přihlásit uložené procedury s certifikáty nebo použít zosobnění dočasně přiřadit oprávnění.  
  
### <a name="probing-and-intelligent-observation"></a>Testování a inteligentní pozorování  
 Útoku testování můžete chybové zprávy generované aplikací hledat pro chyby zabezpečení. Implementace zpracování chyb v všechny procedurální kód, aby se zabránilo informace o chybě systému SQL Server nebyl vrácen pro koncového uživatele.  
  
### <a name="authentication"></a>Ověřování  
 Útok prostřednictvím injektáže řetězec připojení může dojít, když pomocí přihlášení serveru SQL, pokud připojovací řetězec založený na vstup uživatele vytvořeným za běhu. Pokud připojovací řetězec není zaškrtnuté pro dvojice platný – klíčové slovo, útočník můžete vložit další znaky, potenciálně přístup k citlivým datům nebo jiným prostředkům na serveru. Pokud je to možné, použijte ověřování systému Windows. Pokud musíte použít přihlášení serveru SQL, použijte <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytvoření a ověření připojovací řetězce v době běhu.  
  
### <a name="passwords"></a>Hesla  
 Řada útoků úspěšné, protože bylo možné získat nebo uhodnout heslo pro privilegovaných uživatelů útočníka. Hesla jsou vaše první linií obrany před neoprávněným uživatelům, takže nastavení spolehlivého hesla je důležité pro zabezpečení vašeho systému. Vytvořte a vynutit zásady hesel pro smíšený režim ověřování.  
  
 Vždy přiřazujte silné heslo, které `sa` účtu, i když se používá ověřování systému Windows.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Popisuje, jak spravovat oprávnění a řídit přístup k datům pomocí uložených procedur. Použití uložených procedur je efektivní způsob, jak reagovat na mnoho bezpečnostní hrozby.  
  
 [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Popisuje postupy pro psaní zabezpečené dynamické SQL pomocí uložené procedury.  
  
 [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Popisuje, jak se přihlásit pomocí certifikátu umožňuje uživatelům pracovat s daty, které nemají přímý přístup k uložené procedury. To umožňuje uložené procedury k provádění operací, které volající nemá oprávnění k provedení přímo.  
  
 [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Popisuje způsob použití EXECUTE AS klauzule zosobňovat jiného uživatele. Zosobnění přepínačů kontext provádění volající, který má zadaný uživatel.  
  
 [Udělení oprávnění na úrovni řádků na SQL Serveru](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Popisuje, jak implementovat oprávnění na úrovni řádku omezit přístup k datům.  
  
 [Vytváření rolí aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Popisuje funkce a funkce aplikační role.  
  
 [Povolení přístupu mezi databázemi na SQL Serveru](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Popisuje, jak povolit přístup k databázi mezi bez ohrožující zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server – zabezpečení](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
