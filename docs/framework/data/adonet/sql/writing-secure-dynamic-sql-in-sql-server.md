---
title: Zápis zabezpečené dynamické SQL na SQL Serveru
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: c02455ba8798df1de1d52f6b4db3426d41b95daf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791419"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Zápis zabezpečené dynamické SQL na SQL Serveru
Injektáže SQL je proces, pomocí kterého uživatel se zlými úmysly zadá příkazy jazyka Transact-SQL místo platného vstupu. Pokud je vstup předán přímo serveru bez ověření a pokud aplikace neúmyslně spouští vložený kód, může útok způsobit poškození nebo zničení dat.  
  
 Všechny postupy, které tvoří příkazy SQL, by měly být přezkoumány pro chyby zabezpečení injektáže, protože SQL Server spustí všechny syntakticky platné dotazy, které obdrží. Dokonce i Parametrizovaná data může manipulovat kvalifikovaným a určeným útočníkem. Použijete-li Dynamic SQL, nezapomeňte příkazy parametrizovat a nikdy Nezahrnovat hodnoty parametrů přímo do řetězce dotazu.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomie útoku prostřednictvím injektáže SQL  
 Proces vkládání funguje pomocí předčasného ukončení textového řetězce a připojení nového příkazu. Vzhledem k tomu, že vložený příkaz do něj může před provedením připojit další řetězce, malefactor ukončí vložený řetězec s označením komentáře "--". Následný text se v době spuštění ignoruje. Pomocí středníku lze vložit více příkazů (;) oddělovač.  
  
 Pokud je vložený kód SQL syntakticky správný, nelze programově detekovat manipulace. Proto je nutné ověřit všechny vstupy uživatelů a pečlivě zkontrolovat kód, který spouští vytvořené příkazy SQL na serveru, který používáte. Nikdy nezřetězí vstup uživatele, který není ověřený. Zřetězení řetězců je primárním bodem záznamu pro vkládání skriptu.  
  
 Tady je několik užitečných pokynů:  
  
- Nikdy nevytvářejte příkazy jazyka Transact-SQL přímo ze vstupu uživatele; pomocí uložených procedur ověřte vstup uživatele.  
  
- Ověřte vstup uživatele pomocí testování typu, délky, formátu a rozsahu. Použijte funkci Transact-SQL QUOTa () pro řídicí názvy systému nebo funkci Replace () pro řídicí znak v řetězci.  
  
- Implementujte více vrstev ověřování v každé úrovni aplikace.  
  
- Otestujte velikost a datový typ vstupu a vynuťte příslušná omezení. To může přispět k tomu, aby se předešlo přetečení úmyslné vyrovnávací paměti.  
  
- Otestujte obsah proměnných řetězce a přijměte pouze očekávané hodnoty. Zamítnout položky, které obsahují binární data, řídicí sekvence a znaky komentáře.  
  
- Při práci s dokumenty XML ověří všechna data proti schématu, jak je zadáno.  
  
- V prostředích s více vrstvami musí být všechna data ověřena před příchodem do důvěryhodné zóny.  
  
- V polích, ze kterých lze sestavit názvy souborů, nepřijímejte následující řetězce: AUX, CLOCK $, COM1 až COM8, CON, CONFIG $, LPT1 až LPT8, NUL a PRN.  
  
- Pomocí <xref:System.Data.SqlClient.SqlParameter> objektů s uloženými procedurami a příkazy poskytněte kontrolu typu a délku ověřování.  
  
- Použijte <xref:System.Text.RegularExpressions.Regex> výrazy v kódu klienta k filtrování neplatných znaků.  
  
## <a name="dynamic-sql-strategies"></a>Dynamické strategie SQL  
 Provádění dynamicky vytvořených příkazů SQL v procedurálním kódu ruší řetěz vlastnictví, což způsobilo, že SQL Server kontrolovat oprávnění volajícího proti objektům, ke kterým se přistupuje dynamickým SQL.  
  
 SQL Server má metody pro udělení přístupu uživatelům k datům pomocí uložených procedur a uživatelsky definovaných funkcí, které spouštějí dynamické SQL.  
  
- Použití zosobnění s klauzulí spustit jako v jazyce Transact-SQL, jak je popsáno v tématu [přizpůsobení oprávnění k zosobnění v SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Podepisování uložených procedur pomocí certifikátů, jak je popsáno v tématu [Podepisování uložených procedur v SQL Server](signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>SPUSTIT JAKO  
 Klauzule EXECUTE AS nahrazuje oprávnění volajícího pro uživatele zadaného v klauzuli EXECUTE AS. Vnořené uložené procedury nebo triggery se spouštějí v kontextu zabezpečení uživatele proxy serveru. To může poškodit aplikace, které spoléhají na zabezpečení na úrovni řádků, nebo vyžadují auditování. Některé funkce, které vracejí identitu uživatele, vrátí uživatele zadaného v klauzuli EXECUTE AS, nikoli původního volajícího. Kontext spuštění se vrátí původnímu volajícímu až po provedení procedury nebo při vydání příkazu REVERT.  
  
### <a name="certificate-signing"></a>Podepisování certifikátu  
 Když se spustí uložená procedura podepsaná certifikátem, sloučí se oprávnění udělená uživateli certifikátu s oprávněními volajícího. Kontext spuštění zůstává stejný; uživatel certifikátu nezosobňuje volajícího. Podepisování uložených procedur vyžaduje provedení několika kroků. Pokaždé, když je procedura upravena, musí být znovu podepsána.  
  
### <a name="cross-database-access"></a>Přístup k více databázím  
 Řetězení vlastnictví mezi databázemi nefunguje v případech, kdy jsou spouštěny dynamicky vytvořené příkazy SQL. Tuto možnost můžete v SQL Server obejít tak, že vytvoříte uloženou proceduru, která přistupuje k datům v jiné databázi a podepíše postup s certifikátem, který existuje v obou databázích. Uživatelé tak budou mít přístup k prostředkům databáze použitým postupem bez udělení přístupu k databázi nebo oprávnění.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Uložené procedury](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) a [injektáže SQL](/sql/relational-databases/security/sql-injection) na SQL Server Knihy online|Témata popisují postup vytvoření uložených procedur a způsobu, jakým funguje injektáže SQL.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](signing-stored-procedures-in-sql-server.md)
- [Přizpůsobení oprávnění se zosobněním na SQL Serveru](customizing-permissions-with-impersonation-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
