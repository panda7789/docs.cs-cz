---
title: Zápis zabezpečené dynamické SQL v systému SQL Server
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5fdf41353e1772eab46e2e6b8f16ad7bfdf7a72f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Zápis zabezpečené dynamické SQL v systému SQL Server
Injektáž SQL je proces, pomocí kterého uživatel se zlými úmysly zadá příkazy jazyka Transact-SQL místo platný vstup. Pokud vstup je předán přímo k serveru bez ověřování a aplikace nechtěně spustí kód vložený, se útoku může dojít k poškození nebo zničení data.  
  
 Všechny příkazy SQL procedury měla být kontrolována chyb zabezpečení, vkládání, protože SQL Server provede všechny syntakticky dotazy, které obdrží. Zkušený a určené útočník smí uživatel manipulovat i parametrizované data. Pokud používáte dynamické SQL, nezapomeňte Parametrizace příkazech a nikdy nezahrne hodnoty parametrů přímo do řetězce dotazu.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomie útok prostřednictvím injektáže SQL  
 Proces vkládání funguje tak, že předčasně ukončení textový řetězec a připojení nového příkazu. Protože vložení příkazu může mít další řetězce, přidá se k němu předtím, než se spustí, malefactor ukončí vloženého řetězec s komentář označte "–". Následující text je ignorován v době provedení. Můžete vložit více příkazů pomocí středníkem (;) oddělovač.  
  
 Tak dlouho, dokud vloženého kódu SQL je syntakticky správný, manipulaci nelze zjistit prostřednictvím kódu programu. Proto musíte ověřit všechny vstup uživatele a pečlivě zkontrolujte kód, který spouští sestavené příkazy SQL na serveru, který používáte. Nikdy řetězení vstup uživatele, který není ověřen. Zřetězení řetězců je primární bod položky skriptu.  
  
 Zde jsou některé užitečné pokyny:  
  
-   Nikdy sestavení příkazy jazyka Transact-SQL přímo z vstup uživatele; pomocí uložených procedur ověření vstupu uživatele.  
  
-   Ověřte vstup uživatele tak, že testování typ, délku, formát a rozsah. Abyste se vyhnuli názvy systému nebo funkce REPLACE(), abyste se vyhnuli libovolný znak v řetězci, použijte funkci QUOTENAME() Transact-SQL.  
  
-   Implementujte několik vrstev ověření v jednotlivých vrstvách vaší aplikace.  
  
-   Testování velikosti a datový typ vstupu a vynutit odpovídající omezení. To může pomoct zabránit záměrné přetečení zásobníku.  
  
-   Zkušební obsah proměnných řetězce a přijímat pouze očekávaných hodnot. Odmítněte položky, které obsahují binární data, řídicí sekvence a komentář znaky.  
  
-   Při práci s dokumenty XML, ověřte všechna data pro její schéma, jak je zadán.  
  
-   V prostředích s víceúrovňových by měla být ověřena všechna data před jejich příchodu do zóny důvěryhodných serverů.  
  
-   Nepřijímají následujících řetězců v polích, ze které souboru názvy konstruovat: AUX, CLOCK$, COM1 až COM8, CON, konfigurace$, LPT1 LPT8, NUL a PRN.  
  
-   Použití <xref:System.Data.SqlClient.SqlParameter> objektů pomocí uložené procedury a příkazy pro ověřování typu kontrolu a délka.  
  
-   Použití <xref:System.Text.RegularExpressions.Regex> výrazy v kódu klienta pro filtrování neplatné znaky.  
  
## <a name="dynamic-sql-strategies"></a>Strategie dynamické SQL  
 Provádění dynamicky vytvoří příkazů SQL v vaší procedurální kód zalomení řetězu vlastnictví způsobuje systému SQL Server zkontrolujte oprávnění volajícího u těchto objektů přistupuje dynamické SQL.  
  
 Metody pro uživatelům udělen přístup k datům pomocí uložené procedury a uživatelem definované funkce, které jsou spouštěny dynamické SQL má systém SQL Server.  
  
-   Pomocí jazyka Transact-SQL AS provést zosobnění klauzule, jak je popsáno v [přizpůsobení oprávnění s zosobnění v systému SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Podepisování uložené procedury s certifikáty, jak je popsáno v [podepisování uložené procedury v systému SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>SPUŠTĚNÍ AS  
 Spustit jako klauzule nahradí oprávnění volajícího s od uživatele zadané v EXECUTE AS klauzule. Vnořené uložené procedury nebo aktivační události spustit v kontextu zabezpečení uživatele proxy serveru. To může dojít k narušení aplikace, které spoléhají na zabezpečení na úrovni řádků nebo vyžadovat auditování. Některé funkce, které vrátí identitu uživatele, vrátí uživatele zadaného v EXECUTE AS klauzule, není původní volající. Kontext spuštění je vrátit zpět na původní volající pouze po spuštění procedury nebo při vydání příkazu vrátit.  
  
### <a name="certificate-signing"></a>Podepisování certifikátu  
 Když provede uložené procedury, která má byla podepsána pomocí certifikátu, oprávnění udělená uživateli certifikát jsou sloučeny s těmi, která volajícího. Kontext spuštění zůstává stejná; Uživatel certifikát není zosobnit volající. Podepisování uložené procedury, vyžaduje několik kroků k implementaci. Pokaždé, když se mění podle postupu, musí být znovu podepisovat.  
  
### <a name="cross-database-access"></a>Mezi přístup k databázi  
 Řetězení mezidatabázové vlastnictví nefunguje, pokud je v případech, kde jsou vykonány dynamicky vytvořený příkazů SQL. Vám může tento problém vyřešit v systému SQL Server vytváření uložené procedury, která přistupuje k datům v jiné databázi a podepisování postup s certifikátem, který již existuje v obou databází. To umožňuje uživatelům přístup k databázi prostředky využívané třídou postup bez toho, abyste jim přístup k databázi nebo oprávnění.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Uložené procedury](http://go.microsoft.com/fwlink/?LinkId=98233) a [Injektáž SQL](http://go.microsoft.com/fwlink/?LinkId=98234) v Online knihách serveru SQL|Témata popisují, jak vytvořit uložené procedury a jak funguje Injektáž SQL.|  
|[Nové útoky zkrácení SQL a jak se vyhnout jejich](http://msdn.microsoft.com/msdnmag/issues/06/11/SQLSecurity/) v časopise MSDN.|Popisuje, jak lze omezit znaky a řetězce, Injektáž SQL a úpravy pomocí zkrácení útoky.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Přizpůsobení oprávnění se zosobněním na SQL Serveru](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
