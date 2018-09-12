---
title: Scénáře zabezpečení aplikací v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: bf4f4adfd5f49bd210026e40bd5fa4e67da10d75
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699108"
---
# <a name="application-security-scenarios-in-sql-server"></a>Scénáře zabezpečení aplikací v systému SQL Server
Neexistuje žádný jeden správný způsob, jak vytvořit zabezpečené klientské aplikace SQL Server. Každá aplikace je jedinečný v jeho požadavky na nasazení prostředí a uživatelům. Aplikace, který je přiměřeně zabezpečené při prvotním nasazení může být méně zabezpečené v čase. Není možné předpovědět jakékoli přesnost co hrozeb mohou vzniknout v budoucnu.  
  
 SQL Server, produkt, se průběžně vyvíjel mnoho verzí začlenit nejnovější funkce zabezpečení, které vývojářům umožňují vytvářet zabezpečené databázových aplikací. Ale zabezpečení nepřejde do pole. vyžaduje nepřetržité monitorování a aktualizace.  
  
## <a name="common-threats"></a>Běžné hrozby  
 Vývojáři potřebují k pochopení bezpečnostních hrozeb, nástroje poskytované čítači a jak se vyhnout poškozují bezpečnostní díry. Zabezpečení můžete nejlépe představit jako řetězce, kde odmlky v jakékoli jedno propojení ohrožuje sílu celku. Následující seznam obsahuje některé běžné hrozby zabezpečení, které jsou popsány podrobněji v tématech v této části.  
  
### <a name="sql-injection"></a>Útok prostřednictvím injektáže SQL  
 Útok prostřednictvím injektáže SQL je proces, pomocí kterého uživatel se zlými úmysly zadá příkazů jazyka Transact-SQL místo platný vstup. Pokud vstup je předána přímo na server bez ověřování, a pokud aplikace provádí neúmyslně vloženého kódu, útoku hrozí riziko poškození nebo zničení data. Můžete zamezit SQL Server prostřednictvím injektáže útoky pomocí uložené procedury a příkazy s parametry, jak se vyhnout dynamické SQL a omezení oprávnění pro všechny uživatele.  
  
### <a name="elevation-of-privilege"></a>Zvýšení oprávnění  
 Zvýšení úrovně oprávnění pro útoky zajistěte dojít, když je uživatel měl předpokládat oprávnění důvěryhodný účet, jako je například roli vlastníka nebo správce. Vždy spustit pod nejnižší úrovní oprávnění uživatelské účty a přiřaďte pouze potřebná oprávnění. Vyhněte se použití správce nebo vlastníka pro účty pro spouštění kódu. To omezuje množství škody, které může dojít, pokud bude úspěšné útoku. Při provádění úlohy, které vyžadují další oprávnění, použijte proceduru podepisování nebo zosobnění pouze po dobu trvání úlohy. Můžete se přihlásit uložené procedury s certifikáty nebo použití zosobnění se dočasně přiřadit oprávnění.  
  
### <a name="probing-and-intelligent-observation"></a>Zjišťování a inteligentního zjišťování  
 Útok zjišťování můžete použít chybové zprávy generované aplikace pro hledání ohrožení zabezpečení. Implementace zpracování chyb v kódu všechny procedury zabránit informace o chybě systému SQL Server nebyl vrácen pro koncového uživatele.  
  
### <a name="authentication"></a>Ověřování  
 Útok prostřednictvím injektáže řetězec připojení může dojít, když pomocí přihlášení serveru SQL Server, pokud připojovací řetězec založený na vstupu uživatele je vytvořen v době běhu. Pokud připojovací řetězec není možnost zaškrtnuta, pro páry platný – klíčové slovo, útočník může vložit nadbytečné znaky, potenciálně přístup k citlivým datům ani další prostředky na serveru. Kdykoli je to možné, použijte ověřování Windows. Pokud je nutné použít přihlašovací údaje SQL serveru, použijte <xref:System.Data.SqlClient.SqlConnectionStringBuilder> vytvářet a ověřovat připojovací řetězce v době běhu.  
  
### <a name="passwords"></a>Hesla  
 Mnoho útoků úspěšná, protože neoprávněný bylo možné získat nebo uhodnout heslo pro privilegovaných uživatelů. Hesla jsou vaše první linie obrany proti případné útočníky, takže nastavení spolehlivého hesla je důležité pro zabezpečení vašeho systému. Vytvořit a vynucovat zásady pro hesla pro ověřování ve smíšeném režimu.  
  
 Vždy přiřaďte silné heslo, které `sa` účtu, i když se používá ověřování Windows.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Popisuje, jak spravovat oprávnění a řízení přístupu k datům pomocí uložených procedur. Použití uložených procedur je účinný způsob, jak reagovat na mnoho bezpečnostní hrozby.  
  
 [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Popisuje postupy pro zápis zabezpečené dynamické SQL pomocí uložených procedur.  
  
 [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Popisuje, jak podepsat pomocí certifikátu umožňující uživatelům pracovat s daty, která nemají přímý přístup k uložené procedury. To umožňuje uložené procedury k provedení operace, které volající nemá oprávnění provést přímo.  
  
 [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Popisuje způsob použití EXECUTE AS klauzule zosobňovat jiného uživatele. Zosobnění se změní kontext provádění od volajícího pro určitého uživatele.  
  
 [Udělení oprávnění na úrovni řádků na SQL Serveru](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Popisuje, jak implementovat oprávnění na úrovni řádků pro omezení přístupu k datům.  
  
 [Vytváření rolí aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Popisuje funkce a funkce z aplikační role.  
  
 [Povolení přístupu mezi databázemi na SQL Serveru](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Popisuje postup povolení přístupu mezi databázemi bez ohrožující zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server – zabezpečení](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
