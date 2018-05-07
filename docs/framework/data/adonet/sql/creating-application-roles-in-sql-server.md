---
title: Vytváření aplikací rolí v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: cb3bcb08877d8a17ea40ea48440c1d71560d0e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-application-roles-in-sql-server"></a>Vytváření aplikací rolí v systému SQL Server
Role aplikace poskytují způsob, jak přiřadit oprávnění k aplikaci místo databázové role nebo uživatele. Uživatele můžete připojit k databázi, aktivujte roli aplikace a předpokládá oprávnění udělená aplikaci. Oprávnění udělená role aplikace jsou platné po dobu trvání připojení.  
  
> [!IMPORTANT]
>  Aplikační role jsou aktivovat, pokud klientská aplikace poskytuje název role aplikace a heslo v připojovacím řetězci. Vzhledem k tomu, že heslo musí být uložen v klientském počítači nepředstavují ohrožení zabezpečení v dvouvrstvé aplikace. V třívrstvá aplikace můžete uložit heslo, aby ho nemůže mít přístup uživatelé aplikace.  
  
## <a name="application-role-features"></a>Funkce Role aplikací  
 Role aplikací mít následující funkce:  
  
-   Na rozdíl od databázové role aplikační role obsahovat žádné členy.  
  
-   Aplikační role jsou aktivované, když aplikace poskytuje název role aplikace a heslo k `sp_setapprole` systémové uložené procedury.  
  
-   Heslo musí být uložen v klientském počítači a zadaný v době běhu; aplikační role nelze aktivovat z uvnitř systému SQL Server.  
  
-   Heslo není šifrován. Parametr hesla se ukládají jako jednocestného algoritmu hash.  
  
-   Po aktivaci, oprávnění získané prostřednictvím aplikační role zůstávají platná po dobu trvání připojení.  
  
-   Aplikační role dědí oprávnění udělená `public` role.  
  
-   Pokud se členem `sysadmin` pevné role serveru aktivuje aplikační role, kontext zabezpečení se přepne do, aplikační role po dobu trvání připojení.  
  
-   Pokud vytvoříte `guest` účtu v databázi, která má aplikační role, není nutné k vytvoření účtu uživatele databáze pro aplikační role ani pro žádný z přihlášení, které vyvolají ho. Aplikační role mohou přímý přístup k jiné databázi, pouze pokud `guest` účet existuje v databázi druhý  
  
-   Integrované funkce, které vracejí přihlašovacích jmen, jako je například SYSTEM_USER, vrátí název přihlášení, která volá aplikační role. Integrované funkce, které vracejí databáze uživatelská jména vrátí název role aplikace.  
  
### <a name="the-principle-of-least-privilege"></a>Princip nejnižších nutných oprávnění  
 Aplikační role je třeba poskytnout jenom požadovaná oprávnění, v případě, že dojde k ohrožení bezpečnosti heslo. Oprávnění k `public` role měli zrušený za všechny databáze pomocí aplikační role. Zakažte `guest` účet v libovolné databázi nechcete volající role aplikací mít přístup k.  
  
### <a name="application-role-enhancements"></a>Vylepšení Role aplikace  
 Kontext spuštění je možné přepnout zpět na původní volající po aktivaci role aplikačního, nemusíte zakázat sdružování připojení. `sp_setapprole` Procedura nemá novou možnost, která vytvoří soubor cookie, který obsahuje kontextové informace o volajícím. Můžete obnovit relace voláním `sp_unsetapprole` postupu předání souboru cookie.  
  
## <a name="application-role-alternatives"></a>Aplikace Role alternativy  
 Aplikační role závisí na zabezpečení hesla, které představuje potenciální ohrožení zabezpečení. Hesla mohou vystavené jeho vkládání do kódu aplikace nebo uložit na disk.  
  
 Můžete chtít zvažte následující možnosti.  
  
-   Použití kontext přepínání s EXECUTE AS příkaz s jeho klauzule NO REVERT a pomocí souboru COOKIE. Můžete vytvořit účet uživatele v databázi, která není namapován na přihlášení. Pak přiřaďte oprávnění k tomuto účtu. Pomocí provést AS s bez přihlášení uživatele je bezpečnější, protože je na základě oprávnění, není založené na heslech. Další informace najdete v tématu [přizpůsobení oprávnění s zosobnění v systému SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Zaregistrujte uložené procedury s certifikáty, udělení pouze oprávnění k provedení postupy. Další informace najdete v tématu [podepisování uložené procedury v systému SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Aplikační role](http://msdn.microsoft.com/library/ms190998.aspx) v Online knihách serveru SQL|Popisuje postup vytvoření a používání aplikace rolí v systému SQL Server 2008.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
