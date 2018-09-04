---
title: Autorizace a oprávnění na SQL serveru
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: bdf5112e3f0e2cada4885b0b66adf248f0ffe808
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661931"
---
# <a name="authorization-and-permissions-in-sql-server"></a>Autorizace a oprávnění na SQL serveru
Při vytváření databázových objektů, je nutné explicitně udělit oprávnění, aby byly přístupné uživatelům. Všechny zabezpečitelné objekty má oprávnění, která lze udělit pomocí příkazů oprávnění objektu zabezpečení.  
  
## <a name="the-principle-of-least-privilege"></a>Princip nejnižších oprávnění  
 Vývoj aplikace pomocí přístup založený na uživatele nejméně privilegovaný účet (LUA) je důležitou součástí strategie obranné a podrobné pro zamezením bezpečnostní hrozby. Přístup LUA zajišťuje, že uživatelé postupovat podle principu nejnižší úrovně oprávnění a vždy se přihlásit s omezenými uživatelskými účty. Úlohy správy jsou rozdělená pomocí role pevného serveru a použití `sysadmin` pevné role serveru je vážně s omezeným přístupem.  
  
 Vždy postupujte podle principu nejnižší úrovně oprávnění při udělování oprávnění pro uživatele databáze. Udělte minimální potřebná oprávnění pro uživatele nebo roli k provedení dané úlohy.  
  
> [!IMPORTANT]
>  Vývoj a testování aplikace pomocí LUA přístup přidá určitý stupeň potíže do procesu vývoje. Je snazší vytvářet objekty a napsat kód, když jste přihlášení jako správce nebo vlastníka databáze, než účet LUA. Vývoj aplikace pomocí vysoce privilegovaný účet však obfuskaci dopadu omezenou funkčnost při nejméně privilegovaní uživatelé pokusí spustit aplikaci, která vyžaduje zvýšenou úroveň oprávnění, aby bylo možné správně fungovat. Udělení nadměrná oprávnění uživatelům, aby bylo možné znovu načíst ke ztrátě funkčnosti můžete nechat, vaše aplikace snadno napadnutelný. Navrhování, vývoj a testování vaší aplikace přihlášení s účtem LUA vynucuje disciplinovaný přístup k plánování zabezpečení, které předchází nepříjemným překvapením a pokušení k udělení oprávnění vyšší úrovně jako rychlou opravu. Přihlašovací jméno SQL serveru můžete použít pro testování i v případě, že vaše aplikace je určena k nasazení pomocí ověřování Windows.  
  
## <a name="role-based-permissions"></a>Oprávnění na základě rolí  
 Udělení oprávnění rolím, nikoli uživatelům zjednodušuje správu zabezpečení. Sady oprávnění, která jsou přiřazená rolím jsou děděné všichni členové role. Je snazší přidat nebo odebrat uživatele z role, než je znovu vytvořit samostatné oprávnění nastaví pro jednotlivé uživatele. Role mohou být vnořené; příliš mnoho úrovní vnoření, může ale snížit výkon. Můžete také přidat uživatele do pevné databázové role pro zjednodušení přiřazování oprávnění.  
  
 Můžete udělit oprávnění na úrovni schématu. Uživatelé automaticky dědí oprávnění pro všechny nové objekty vytvořené ve schématu; nemusíte při vytváření nových objektů se udělit oprávnění.  
  
## <a name="permissions-through-procedural-code"></a>Oprávnění prostřednictvím kódu procedury  
 Zapouzdření přístup k datům prostřednictvím modulů, jako uložených procedur a uživatelsky definovaných funkcí poskytuje další úroveň ochrany okolo vaší aplikace. Uživatelům můžete zabránit přímo interakci s databázovými objekty tak, že udělíte oprávnění jenom pro uložené procedury nebo funkce při odepření oprávnění pro příslušné objekty, jako jsou tabulky. SQL Server dosahuje řetězení vlastnictví.  
  
## <a name="permission-statements"></a>Příkazy oprávnění  
 Tři příkazy jazyka Transact-SQL oprávnění jsou popsány v následující tabulce.  
  
|Oprávnění – příkaz|Popis|  
|--------------------------|-----------------|  
|UDĚLENÍ|Udělí oprávnění.|  
|ODVOLAT|Odvolá oprávnění. Toto je výchozí stav nového objektu. Oprávnění odvolána uživatele nebo roli je stále možné zdědit z jiných skupin nebo role, ke kterým je přiřazen objekt zabezpečení.|  
|ODEPŘÍT|ODEPŘÍT odvolá oprávnění tak, že nelze dědit. ODEPŘÍT má přednost před všechna oprávnění, kromě ODEPŘÍT se nevztahují na vlastníky objektu nebo členům `sysadmin`. Pokud třeba ODEPŘETE oprávnění u objektu `public` role se nezdařilo pro všechny uživatele a role s výjimkou objektu vlastníci a `sysadmin` členy.|  
  
-   Příkaz udělení oprávnění můžete přiřadit skupiny nebo role, která mohou být zděděny uživatele databáze s. ODEPŘÍT příkaz však má přednost před všechny ostatní příkazy oprávnění. Proto uživatel, který se zamítla oprávnění nemůže dědit ji z jiné role.  
  
> [!NOTE]
>  Členové `sysadmin` vlastníky role a objekt serveru nemůže být odepřeno oprávnění.  
  
## <a name="ownership-chains"></a>Vlastnictví řetězců  
 SQL Server zajišťuje, že pouze objekty, které bylo uděleno oprávnění přístup objekty. V případě několika databázových objektů přístup k sobě navzájem, sekvence se označuje jako řetězec. Pokud SQL Server prochází odkazů v řetězu certifikátů, je vyhodnocen jako oprávnění jinak než kdyby získávali přístup každá položka samostatně. Při přístupu k objektu pomocí řetězce, SQL Server nejprve porovnává vlastníka objektu vlastníkovi objektem neúčastnícím se volání (předchozí článek v řetězci). Pokud oba objekty stejné vlastníka, nebudou kontrolovány oprávnění na odkazovaném objektu. Pokaždé, když se objekt má přístup k dalším objektem, který má jiného vlastníka, je porušený řetězec vlastnictví a systému SQL Server musíte zaškrtnout kontext zabezpečení volajícího.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Kódu procedury a řetězení vlastnictví  
 Předpokládejme, že uživatel udělil oprávnění ke spouštění na uložené procedury, která vybere data z tabulky. Pokud uložené procedury a tabulky mají stejné vlastníka, uživatel nemusí být udělena všechna oprávnění v tabulce a může dokonce odepřena oprávnění. Však musí SQL Server Pokud uložené procedury a tabulky mít různé vlastníky, zkontrolujte oprávnění uživatele pro tabulku před povolením přístupu k datům.  
  
> [!NOTE]
>  Řetězení vlastnictví nelze použít v případě dynamických příkazů SQL. Volání procedury, která provede příkaz SQL, volající musí být uděleno oprávnění k podkladové tabulky byste museli opustit aplikaci zranitelný vůči útoku prostřednictvím injektáže SQL. SQL Server poskytuje nové mechanismy, jako je například zosobnění a podepisování moduly s certifikáty, které nevyžadují udělení oprávnění pro základní tabulky. Ty lze také s CLR uložené procedury.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v tématu následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Oprávnění](/sql/relational-databases/security/permissions-database-engine)|Obsahuje témata popisující oprávnění hierarchie, zobrazení katalogu a oprávnění pevné role serveru a databáze.|
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serverové a databázové role na SQL Serveru](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
