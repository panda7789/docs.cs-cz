---
title: Vytváření rolí aplikací na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: 212bda6f64829792e965dd6714428a05b30c995b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794273"
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
  
- Používejte přepínání kontextu pomocí příkazu Spustit jako s klauzulemi NO REVERT a COOKIE. Můžete vytvořit uživatelský účet v databázi, která není namapovaná na přihlášení. Pak k tomuto účtu přiřadíte oprávnění. Použití příkazu Spustit jako s uživatelem bez přihlášení je bezpečnější, protože se jedná o oprávnění, které není založené na heslech. Další informace najdete v tématu [přizpůsobení oprávnění pomocí zosobnění v SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Podepište uložené procedury pomocí certifikátů a přidělíte oprávnění pouze pro provedení těchto postupů. Další informace najdete v tématu [Podepisování uložených procedur v SQL Server](signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Aplikační role](/sql/relational-databases/security/authentication-access/application-roles)|Popisuje, jak vytvořit a použít aplikační role v SQL Server 2008.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](overview-of-sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
