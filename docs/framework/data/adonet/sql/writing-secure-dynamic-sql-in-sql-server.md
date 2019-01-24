---
title: Zápis zabezpečené dynamické SQL na serveru SQL Server
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: 446a9f6a49b376f04d1c82d45463d567d89116d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745607"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Zápis zabezpečené dynamické SQL na serveru SQL Server
Útok prostřednictvím injektáže SQL je proces, pomocí kterého uživatel se zlými úmysly zadá příkazů jazyka Transact-SQL místo platný vstup. Pokud vstup je předána přímo na server bez ověřování, a pokud aplikace provádí neúmyslně vloženého kódu, útoku hrozí riziko poškození nebo zničení data.  
  
 Vkládání chyb zabezpečení byste měli zkontrolovat všechny procedury, které sestavují SQL příkazy, protože SQL Server spustí všechny syntakticky platné dotazy, které obdrží. Útočník zkušený a vzhledem k lze ovládat i parametrizované data. Pokud používáte dynamic SQL, nezapomeňte parametrizovat příkazům a nikdy Nezahrnovat hodnoty parametrů přímo do řetězce dotazu.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomie útok prostřednictvím injektáže SQL  
 Proces vkládání funguje díky předčasné ukončení textový řetězec a připojení nového příkazu. Protože vložený příkaz může mít další řetězce připojí k němu předtím, než se spustí, ukončí malefactor vložený řetězec s označením komentář "--". Následující text je ignorován v době spuštění. Více příkazů může být vložen středník (;) pomocí oddělovače.  
  
 Vložený kód SQL je syntakticky správný, úmyslné poškozování nelze zjistit prostřednictvím kódu programu. Proto musíte ověřit všechny vstup uživatele a pečlivě revize kódu, který spouští konstruovaný příkazy jazyka SQL na serveru, kterou používáte. Nikdy zřetězit uživatelský vstup, který není ověřený. Zřetězení řetězců je primární bod zadání injektáži skriptu.  
  
 Tady jsou některé užitečné pokyny:  
  
-   Příkazy jazyka Transact-SQL přímo ze vstupu uživatele; nikdy sestavení uložené procedury slouží k ověření vstupu uživatele.  
  
-   Ověření vstupu uživatele při testování typ, délku, formátu a rozsah. Použijte funkci QUOTENAME() příkazů jazyka Transact-SQL k uvození názvy systému nebo funkce REPLACE() k uvození libovolného znaku v řetězci.  
  
-   Implementujte několik úrovní ověření v jednotlivých vrstvách vaší aplikace.  
  
-   Testování velikosti a datový typ vstupu a vynucovat odpovídající omezení. To může pomoci zabránit přetečení vyrovnávací paměti rozhodnout vědomě a záměrně.  
  
-   Testovací obsah proměnných řetězce a přijmout jenom očekávané hodnoty. Odmítnutí položky, které obsahují binárních dat, řídicích sekvencí a znaky komentáře.  
  
-   Při práci s dokumenty XML ověřte jako se zadají všechna data pro jeho schéma.  
  
-   V prostředích s více vrstvé by měl být ověřen všechna data před jejich příchodu do zóny důvěryhodných serverů.  
  
-   Nepřijmout následujících řetězců v polích, ze kterých lze zkonstruovat názvy souborů: AUX, CLOCK$, COM1 prostřednictvím COM8, CON, CONFIG$, LPT1, LPT8, NUL a PRN.  
  
-   Použití <xref:System.Data.SqlClient.SqlParameter> objekty s uloženými procedurami a příkazy, které poskytují kontrolu a délka ověření typu.  
  
-   Použití <xref:System.Text.RegularExpressions.Regex> výrazy v klientském kódu k filtrování neplatné znaky.  
  
## <a name="dynamic-sql-strategies"></a>Strategie dynamické SQL  
 Provádění dynamicky vytvoří příkazy SQL v vašeho kódu procedury konce řetězce vlastnictví, způsobí systému SQL Server ke kontrole oprávnění volajícího u těchto objektů přistupuje dynamické SQL.  
  
 SQL Server má metody pro uživatelům udělíte přístup k datům pomocí uložených procedur a uživatelem definovaných funkcí, které jsou spouštěny dynamické SQL.  
  
-   Použití zosobnění se příkazů jazyka Transact-SQL spustit jako klauzuli, jak je popsáno v [přizpůsobení oprávnění se zosobněním na SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Podepisování uložených procedur s certifikáty, jak je popsáno v [podepisování uložených procedur na SQL serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>SPUSTIT JAKO  
 Spustit jako se nahradí klauzule oprávnění volající s ním uživatel zadaný v EXECUTE AS klauzuli. Vnořené uložených procedur a aktivačních událostí spuštění v kontextu zabezpečení uživatele proxy serveru. Toto může rozbít aplikace, které využívají zabezpečení na úrovní řádků nebo vyžadován audit. Některé funkce, které vrátí identitu uživatele, vrátí uživatele zadaného v EXECUTE AS klauzule, nikoli původní volající. Kontext spuštění se vrátí zpět na původní volajícího až po provádění procedury nebo při vydání příkazu obnovit.  
  
### <a name="certificate-signing"></a>Podepisování certifikátu  
 Když Spustí uloženou proceduru, která byla podepsána pomocí certifikátu, oprávnění udělená uživatelského certifikátu jsou sloučeny s ty volajícího. Kontext spuštění zůstává stejné. Uživatel certifikát není zosobňují volajícího. Podepisování uložených procedur, vyžaduje několik kroků k implementaci. Pokaždé, když se změní podle postupu, je třeba jej znovu podepsat.  
  
### <a name="cross-database-access"></a>Různé přístup k databázi  
 Vlastnictví mezidatabázové řetězení nebude fungovat v případech, ve kterých se spouští dynamicky vytvořené příkazy SQL. Můžete obejít tím v systému SQL Server vytvořením uloženou proceduru, která přistupuje k datům v jiné databázi a podepisování postup certifikátem, který existuje v databázi i databázi. To poskytuje uživatelům přístup k databázi prostředky využívané třídou postupu bez nutnosti přidělit jim přístup k databázi nebo oprávnění.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Uložené procedury](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) a [útok prostřednictvím injektáže SQL](/sql/relational-databases/security/sql-injection) v Online knihách serveru SQL|Témata popisují postup vytvoření uložených procedur a jak funguje útok prostřednictvím injektáže SQL.|  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
