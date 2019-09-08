---
title: Autorizace a oprávnění na SQL Serveru
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: c9b041a078494cd29d6cab5297728d233dafa236
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782597"
---
# <a name="authorization-and-permissions-in-sql-server"></a>Autorizace a oprávnění na SQL Serveru
Při vytváření databázových objektů musíte explicitně udělit oprávnění, aby je bylo možné uživatelům zpřístupnit. Každý zabezpečitelný objekt má oprávnění, která lze udělit objektu zabezpečení pomocí příkazů oprávnění.  
  
## <a name="the-principle-of-least-privilege"></a>Princip nejnižších oprávnění  
 Vývoj aplikace s využitím přístupu s minimálním privilegovaným uživatelským účtem (LUA) je důležitou součástí obrannou linií a podrobné strategie pro vytváření čítačů bezpečnostních hrozeb. Přístup LUA zajišťuje, aby uživatelé dodržovali princip minimálního oprávnění a vždy se přihlásili pomocí omezených uživatelských účtů. Úlohy správy jsou rozděleny pomocí pevných rolí serveru a používání `sysadmin` pevné role serveru je u sebe vážně omezené.  
  
 Při udělování oprávnění uživatelům databáze vždy postupujte podle principu nejnižší oprávnění. Udělení minimálních oprávnění potřebných pro uživatele nebo roli k provedení daného úkolu.  
  
> [!IMPORTANT]
> Vývoj a testování aplikace pomocí přístupu LUA přičítá ke procesu vývoje stupeň potíží. Vytváření objektů a psaní kódu je snazší, pokud jste přihlášeni jako správce systému nebo jako vlastník databáze, než používá účet LUA. Vývoj aplikací pomocí vysoce privilegovaného účtu ale může vymezit dopad omezených funkcí, když se nejméně privilegované uživatele pokusí spustit aplikaci, která vyžaduje zvýšená oprávnění, aby fungovala správně. Udělení nadměrných oprávnění uživatelům, aby bylo možné znovu získat ztracené funkce, může způsobit, že vaše aplikace bude zranitelná vůči útokům. Návrh, vývoj a testování vaší aplikace přihlášené pomocí účtu LUA vynutily oborové postupy pro plánování zabezpečení, které eliminují nepříjem překvapením a pokušení pro udělení zvýšených oprávnění jako Rychlá oprava. Můžete použít SQL Server přihlašovací údaje pro testování i v případě, že je vaše aplikace určena k nasazení pomocí ověřování systému Windows.  
  
## <a name="role-based-permissions"></a>Oprávnění na základě rolí  
 Udělení oprávnění rolím, nikoli uživatelům, zjednodušuje správu zabezpečení. Sady oprávnění, které jsou přiřazeny rolím, dědí všichni členové této role. Je snazší přidat nebo odebrat uživatele z role, než aby bylo možné znovu vytvořit samostatné sady oprávnění pro jednotlivé uživatele. Role můžou být vnořené. příliš mnoho úrovní vnoření ale může snížit výkon. Můžete taky přidat uživatele k pevným databázovým rolím, abyste zjednodušili přiřazování oprávnění.  
  
 Můžete udělit oprávnění na úrovni schématu. Uživatelé automaticky převezmou oprávnění pro všechny nové objekty vytvořené ve schématu. Při vytváření nových objektů nemusíte udělovat oprávnění.  
  
## <a name="permissions-through-procedural-code"></a>Oprávnění prostřednictvím kódu procedurální  
 Zapouzdření přístupu k datům prostřednictvím modulů, jako jsou uložené procedury a uživatelsky definované funkce, poskytuje další vrstvu ochrany kolem vaší aplikace. Uživatelům můžete zabránit přímo v interakci s databázovými objekty tím, že udělíte oprávnění pouze k uloženým procedurám nebo funkcím a odepřete oprávnění podkladovým objektům, jako jsou tabulky. SQL Server dosahuje pomocí zřetězení vlastnictví.  
  
## <a name="permission-statements"></a>Příkazy oprávnění  
 Tři příkazy pro oprávnění Transact-SQL jsou popsány v následující tabulce.  
  
|Příkaz oprávnění|Popis|  
|--------------------------|-----------------|  
|UDĚLIT|Udělí oprávnění.|  
|ODVOLAT|Odvolá oprávnění. Toto je výchozí stav nového objektu. Oprávnění odvolaných uživatelem nebo rolí může být stále děděno z jiných skupin nebo rolí, ke kterým je objekt zabezpečení přiřazen.|  
|ODMÍTNOUT|DENY odvolá oprávnění, aby ho nebylo možné dědit. ZAMÍTNUTí má přednost před všemi oprávněními, s výjimkou ODEPŘENí se nevztahuje na vlastníky `sysadmin`objektu nebo členy. Pokud odepřete oprávnění objektu k `public` roli, je odepřen všem uživatelům a rolím s výjimkou vlastníků a `sysadmin` členů objektu.|  
  
- Příkaz GRANT může přiřadit oprávnění pro skupinu nebo roli, které mohou být děděny uživateli databáze. Nicméně příkaz Odepřít má přednost před všemi ostatními příkazy oprávnění. Proto uživatel, který byl odepřen oprávnění, nemůže dědit z jiné role.  
  
> [!NOTE]
> `sysadmin` Členové pevné role serveru a vlastníci objektu nelze odepřít oprávnění.  
  
## <a name="ownership-chains"></a>Řetězení vlastnictví  
 SQL Server zajistí, že přístup k objektům mají jenom objekty zabezpečení, které mají udělená oprávnění. Pokud k sobě navzájem přistupuje více databázových objektů, sekvence je označována jako řetězec. Pokud SQL Server prochází odkazy v řetězu, vyhodnocuje oprávnění jinak, než by byla v případě, že k jednotlivým položkám přistupuje samostatně. Když je objekt otevřen prostřednictvím řetězce, SQL Server Nejprve porovná vlastníka objektu s vlastníkem volajícího objektu (předchozí odkaz v řetězci). Pokud mají oba objekty stejného vlastníka, oprávnění k odkazovanému objektu nejsou zaškrtnuta. Pokaždé, když objekt přistupuje k jinému objektu, který má jiného vlastníka, řetěz vlastnictví je přerušen a SQL Server musí kontrolovat kontext zabezpečení volajícího.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Procedurální Code a vlastnictví řetězení  
 Předpokládejme, že uživateli je uděleno oprávnění ke spouštění pro uloženou proceduru, která vybírá data z tabulky. Pokud má úložná procedura a tabulka stejného vlastníka, není nutné, aby uživatel měl udělena žádná oprávnění k tabulce a může dokonce být odepřen oprávnění. Pokud však uložená procedura a tabulka mají různé vlastníky, SQL Server musí před povolením přístupu k datům kontrolovat oprávnění uživatele v tabulce.  
  
> [!NOTE]
> Řetězení vlastnictví nelze použít v případě dynamických příkazů SQL. Chcete-li zavolat proceduru, která spustí příkaz SQL, volajícímu musí být uděleno oprávnění k podkladovým tabulkám a aplikace zůstane zranitelná vůči útokům prostřednictvím injektáže SQL. SQL Server poskytuje nové mechanismy, jako jsou zosobnění a podepisování modulů pomocí certifikátů, které nevyžadují udělení oprávnění pro podkladové tabulky. Lze je také použít s uloženými procedurami CLR.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Oprávnění](/sql/relational-databases/security/permissions-database-engine)|Obsahuje témata popisující hierarchii oprávnění, zobrazení katalogu a oprávnění k pevnému serveru a databázovým rolím.|
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Ověřování v SQL Serveru](authentication-in-sql-server.md)
- [Serverové a databázové role na SQL Serveru](server-and-database-roles-in-sql-server.md)
- [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](ownership-and-user-schema-separation-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
