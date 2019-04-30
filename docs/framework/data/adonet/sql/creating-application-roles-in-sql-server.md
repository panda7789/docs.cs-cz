---
title: Vytváření rolí aplikací na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: f836fd239eca30d0a1f4a667cddc844446d1d951
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878017"
---
# <a name="creating-application-roles-in-sql-server"></a>Vytváření rolí aplikací na SQL Serveru
Aplikační role poskytují způsob, jak přiřadit oprávnění k aplikaci místo na uživatele nebo role databáze. Uživatelům můžete připojit k databázi, aktivace aplikační role a předpokládají oprávnění udělených aplikaci. Oprávnění udělená aplikaci role jsou platné po dobu trvání připojení.  
  
> [!IMPORTANT]
>  Aplikační role se aktivují, když klientská aplikace poskytne název role aplikace a heslo v připojovacím řetězci. Představují ohrožení zabezpečení v dvouvrstvé aplikace, protože heslo musí být uložen v klientském počítači. V třívrstvé aplikace lze ukládat hesla tak, aby ji nemůže mít přístup uživatelé aplikace.  
  
## <a name="application-role-features"></a>Funkce Role aplikace  
 Aplikační role mají tyto funkce:  
  
- Na rozdíl od databázové role aplikační role obsahovat žádné členy.  
  
- Aplikační role se aktivují, když aplikace poskytuje název role aplikace a hesla `sp_setapprole` systémové uložené procedury.  
  
- Heslo musí být uložen v klientském počítači a zadanou za běhu; aplikační role nejde aktivovat z v rámci služby SQL Server.  
  
- Heslo není šifrována. Parametr hesla se ukládá jako jednocestného algoritmu hash.  
  
- Po aktivaci oprávnění získat prostřednictvím aplikační role, můžou platit ještě dobu trvání připojení.  
  
- Aplikační role dědí oprávnění udělená `public` role.  
  
- Pokud člen `sysadmin` pevné role serveru aktivuje roli aplikace, kontext zabezpečení, které role aplikace přepne po dobu trvání připojení.  
  
- Pokud jste vytvořili `guest` účet v databázi, který má roli aplikace, nepotřebujete k vytvoření uživatelského účtu databáze pro roli v aplikaci nebo pro všechny přihlašovací údaje, které ho vyvolat. Aplikační role mohou přímý přístup k databázi jiného pouze tehdy, pokud `guest` účet existuje v druhé databázi  
  
- Integrované funkce, které vracejí přihlašovací jména, jako je například SYSTEM_USER, vrátí název přihlášení, která vyvolá aplikační role. Integrované funkce, které vrací databáze uživatelská jména vrátí název role aplikace.  
  
### <a name="the-principle-of-least-privilege"></a>Princip nejnižších oprávnění  
 Aplikační role mají udělit pouze požadovaná oprávnění v případě, že dojde k narušení heslo. Oprávnění `public` role mají odvolat v jakékoli databázi pomocí roli aplikace. Zakažte `guest` účet v libovolné databáze nechcete, aby se volajícím role aplikace mají přístup k.  
  
### <a name="application-role-enhancements"></a>Vylepšení Role aplikace  
 Kontext spuštění lze přepnout zpět na původní volajícího až po dokončení aktivace roli aplikace, není potřeba zakázat sdružování připojení. `sp_setapprole` Procedura nemá novou možnost, která vytvoří soubor cookie, který obsahuje kontextové informace o volajícím. Můžete se vrátit relaci voláním `sp_unsetapprole` postupu předáním souboru cookie.  
  
## <a name="application-role-alternatives"></a>Alternativy Role aplikace  
 Aplikační role, závisí na zabezpečení heslo, které představuje potenciální ohrožení zabezpečení. Hesla mohou vystavené se vložený v kódu aplikace nebo uložen na disku.  
  
 Můžete chtít zvažte následující možnosti.  
  
- Použití kontextu přímé přepnutí s EXECUTE AS příkaz s jeho klauzule č vrátit a pomocí souboru COOKIE. Vytvořte účet uživatele v databázi, která není namapován na přihlášení. Pak přiřaďte oprávnění pro tento účet. Pomocí spustit jako přidružit k uživateli bez přihlášení je bezpečnější, protože je na základě oprávnění, ne pomocí hesla. Další informace najdete v tématu [přizpůsobení oprávnění se zosobněním na SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Podepisování uložených procedur s certifikáty, poskytování pouze oprávnění ke spuštění procedury. Další informace najdete v tématu [podepisování uložených procedur na SQL serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Aplikační role](/sql/relational-databases/security/authentication-access/application-roles)|Popisuje, jak vytvořit a používat aplikačních rolí v systému SQL Server 2008.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
