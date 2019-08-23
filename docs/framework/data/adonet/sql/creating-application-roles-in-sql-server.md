---
title: Vytváření rolí aplikací na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: e7060e1b171ee1791b9986250fe6f2050ec77acd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961170"
---
# <a name="creating-application-roles-in-sql-server"></a>Vytváření rolí aplikací na SQL Serveru
Aplikační role poskytují způsob, jak přiřadit oprávnění k aplikaci místo databázové role nebo uživatele. Uživatelé se mohou připojit k databázi, aktivovat aplikační roli a převzít oprávnění udělená aplikaci. Oprávnění udělená aplikační roli jsou platná po dobu trvání připojení.  
  
> [!IMPORTANT]
> Aplikační role jsou aktivovány, Pokud klientská aplikace poskytuje název aplikační role a heslo v připojovacím řetězci. Představují bezpečnostní chybu v aplikaci se dvěma vrstvami, protože heslo musí být uloženo v klientském počítači. V aplikaci se třemi vrstvami můžete uložit heslo tak, aby k němu uživatelé aplikace nezískali.  
  
## <a name="application-role-features"></a>Funkce aplikační role  
 Aplikační role mají následující funkce:  
  
- Na rozdíl od databázových rolí role aplikace neobsahují žádné členy.  
  
- Aplikační role jsou aktivovány, pokud aplikace poskytuje název aplikační role a heslo k `sp_setapprole` systémové uložené proceduře.  
  
- Heslo musí být uloženo v klientském počítači a zadáno v době běhu. roli aplikace nelze aktivovat v rámci SQL Server.  
  
- Heslo není šifrované. Heslo parametru je uloženo jako jednosměrná hodnota hash.  
  
- Po aktivaci zůstanou oprávnění získaná prostřednictvím aplikační role v platnosti po dobu trvání připojení.  
  
- Aplikační role dědí oprávnění udělená této `public` roli.  
  
- Pokud člen `sysadmin` pevné role serveru aktivuje roli aplikace, přepne se kontext zabezpečení do role aplikace po dobu trvání připojení.  
  
- Pokud vytvoříte `guest` účet v databázi s aplikační rolí, nemusíte vytvářet uživatelský účet databáze pro roli aplikace ani pro jakékoli přihlašovací údaje, které ji vyvolávají. Aplikační role mají přímý přístup k jiné databázi pouze v `guest` případě, že účet existuje v druhé databázi.  
  
- Integrované funkce, které vracejí přihlašovací jména, jako je například SYSTEM_USER, vrátí název přihlášení, který vyvolal aplikační roli. Předdefinované funkce, které vracejí uživatelská jména databáze, vrátí název aplikační role.  
  
### <a name="the-principle-of-least-privilege"></a>Princip nejnižších oprávnění  
 Aplikačním rolím by se měla udělit jenom požadovaná oprávnění pro případ ohrožení zabezpečení hesla. Oprávnění k `public` roli by měla být odvolána v jakékoli databázi pomocí aplikační role. Zakažte `guest` účet v jakékoli databázi, ke které nechcete volajícím role aplikace přistupovat.  
  
### <a name="application-role-enhancements"></a>Vylepšení aplikační role  
 Kontext spuštění lze přepnout zpět na původního volajícího po aktivaci role aplikace a odebrat nutnost zakázat sdružování připojení. `sp_setapprole` Procedura má novou možnost, která vytvoří soubor cookie, který obsahuje kontextové informace o volajícím. Můžete obnovit relaci voláním `sp_unsetapprole` procedury a předáním souboru cookie.  
  
## <a name="application-role-alternatives"></a>Alternativy aplikační role  
 Aplikační role závisí na zabezpečení hesla, které představuje potenciální ohrožení zabezpečení. Hesla můžou být vystavená na základě vložení do kódu aplikace nebo uloženého na disku.  
  
 Možná budete chtít vzít v úvahu následující alternativy.  
  
- Používejte přepínání kontextu pomocí příkazu Spustit jako s klauzulemi NO REVERT a COOKIE. Můžete vytvořit uživatelský účet v databázi, která není namapovaná na přihlášení. Pak k tomuto účtu přiřadíte oprávnění. Použití příkazu Spustit jako s uživatelem bez přihlášení je bezpečnější, protože se jedná o oprávnění, které není založené na heslech. Další informace najdete v tématu [přizpůsobení oprávnění pomocí zosobnění v SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Podepište uložené procedury pomocí certifikátů a přidělíte oprávnění pouze pro provedení těchto postupů. Další informace najdete v tématu [Podepisování uložených procedur v SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Aplikační role](/sql/relational-databases/security/authentication-access/application-roles)|Popisuje, jak vytvořit a použít aplikační role v SQL Server 2008.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
