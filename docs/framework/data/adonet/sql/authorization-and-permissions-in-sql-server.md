---
title: "Autorizace a oprávnění v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0916ca83cae40d1deda2e1126fd7b7ebab46a23c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="authorization-and-permissions-in-sql-server"></a>Autorizace a oprávnění v systému SQL Server
Při vytváření databázových objektů, je třeba explicitně udělit oprávnění, aby byly dostupné pro uživatele. Všechny zabezpečitelné objekty má oprávnění, která lze udělit oprávnění příkazy using objekt zabezpečení.  
  
## <a name="the-principle-of-least-privilege"></a>Princip nejnižších nutných oprávnění  
 Vývoj aplikace pomocí přístup účtu (LUA) nejmenší privilegovaných uživatelů je důležitou součástí strategie Obranným, podrobný pro zamezením bezpečnostní hrozby. LUA přístup zajišťuje, že uživatelé použijte Princip nejnižších nutných oprávnění a vždy se přihlásit s omezenou uživatelské účty. Úlohy správy jsou rozdělená za použití role pevného serveru a použití `sysadmin` pevné role serveru je vážně s omezeným přístupem.  
  
 Vždy použijte Princip nejnižších nutných oprávnění při udělování oprávnění uživatelům databáze. Přidělte minimální oprávnění potřebná pro uživatele nebo roli na dané úloze.  
  
> [!IMPORTANT]
>  Vývoj a testování aplikace pomocí LUA přístup přidá určitý stupeň potíže při procesu vývoje. Je snazší vytvářet objekty a napsat kód, když jste přihlášení jako správce systému nebo vlastníka databáze, než je používá účet LUA. Vývoj aplikací pomocí účtu s vysokými oprávněními ale obfuskováním dopad omezené funkčnosti při nejnižšími oprávněními uživatelé pokusí spustit aplikaci, která vyžaduje zvýšená oprávnění, aby bylo možné správně fungovat. Udělení oprávnění nadměrné uživatelům, aby bylo možné znovu načíst ztraceny funkce můžete ponechat, vaše aplikace bude zranitelný vůči útoku. Navrhování, vývoj a testování aplikace s přihlášení s účtem LUA vynucuje určených přístup k plánování zabezpečení, který eliminuje nepříjemným výskyt nečekaných událostí a riziko jako rychlou opravu udělit oprávnění vyšší úrovně. Přihlášení systému SQL Server můžete použít pro testování i v případě, že aplikace je určený k nasazení pomocí ověřování systému Windows.  
  
## <a name="role-based-permissions"></a>Oprávnění na základě rolí  
 Udělení oprávnění k rolím a nikoli na uživatele zjednodušuje správu zabezpečení. Sady oprávnění, které jsou přiřazeny k rolím jsou zdědí všechny členy role. Aby bylo jednodušší přidávat nebo odebírat uživatele z role, než je znovu vytvořit samostatné oprávnění nastaví pro jednotlivé uživatele. Role mohou být vnořené; příliš mnoho úrovní vnoření však může snížit výkon. Můžete také přidat uživatele do pevné databázové role pro zjednodušení přiřazení oprávnění.  
  
 Můžete udělit oprávnění na úrovni schématu. Uživatelé automaticky zdědí oprávnění na všechny nové objekty vytvořené ve schématu; není nutné udělit oprávnění, jako jsou vytvořit nové objekty.  
  
## <a name="permissions-through-procedural-code"></a>Oprávnění prostřednictvím procedurální kódu  
 Zapouzdření přístup k datům prostřednictvím modulů, jako uložené procedury a uživatelem definované funkce poskytuje další úroveň ochrany okolo vaší aplikace. Uživatelům můžete zabránit přímo interakci s objekty databáze tak, že udělíte oprávnění jenom na uložené procedury nebo funkce při odepření oprávnění základní objektů, jako jsou tabulky. SQL Server dosahuje pomocí řetězení vlastnictví.  
  
## <a name="permission-statements"></a>Oprávnění – příkazy  
 Tři příkazy jazyka Transact-SQL oprávnění jsou popsané v následující tabulce.  
  
|Příkaz oprávnění|Popis|  
|--------------------------|-----------------|  
|UDĚLENÍ|Uděluje oprávnění.|  
|ODVOLÁNÍ.|Odvolá oprávnění. Toto je výchozí stav nového objektu. Oprávnění odvolává pro uživatele nebo roli stále možné zdědit z jiné skupiny nebo role, ke kterým je přiřazen k objektu zabezpečení.|  
|ODEPŘÍT|ODEPŘÍT odvolá oprávnění tak, aby nelze zdědit. ODEPŘÍT má přednost před všechna oprávnění, kromě ODEPŘÍT se nevztahuje na objekt vlastníky nebo členové `sysadmin`. Pokud ODEPŘETE oprávnění na objekt tak, aby `public` role pro všechny uživatele a role kromě vlastníky objektu se nezdařilo a `sysadmin` členy.|  
  
-   Příkaz GRANT můžete přiřadit oprávnění do skupiny nebo role, která může být zděděn uživatele databáze. ODEPŘÍT příkaz však má přednost před jiné příkazy oprávnění. Proto uživatel, který bylo odepřeno oprávnění nemůže Zdědit ji z jiné role.  
  
> [!NOTE]
>  Členové `sysadmin` role a objekt vlastníků pevného serveru nemůže být odepřeno oprávnění.  
  
## <a name="ownership-chains"></a>Vlastnictví řetězů  
 SQL Server zajišťuje, aby pouze objekty, které bylo uděleno oprávnění, můžete přístup k objekty. Pokud více objektů v databázi přístup k sobě navzájem, sekvenci se označuje jako řetězec. Když na odkazy v řetězu prochází přes SQL Server, vyhodnotí oprávnění jinak než kdyby měla přístup každou položku samostatně. Při přístupu k objektu prostřednictvím řetěz, SQL Server nejprve porovnává vlastníka objektu vlastníka objektu volání (předchozí odkaz v řetězci). Pokud oba objekty mají stejného vlastníka, nejsou zkontrolovat oprávnění na odkazovaného objektu. Vždy, když objekt získá přístup k dalším objektem, který má jiného vlastníka, je porušený řetězec vlastnictví a SQL Server musí zkontrolujte kontext zabezpečení volajícího.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Příklady kódu a vlastnictví řetězení  
 Předpokládejme, že je uživateli uděleno oprávnění ke spouštění na uložené procedury, která vybere položku dat z tabulky. Pokud tabulky a uložené procedury stejného vlastníka, uživatel nemusí být udělena všechna oprávnění v tabulce a můžete i odepřel oprávnění. Však musí SQL Server Pokud tabulky a uložené procedury mít různé vlastníky, zkontrolujte oprávnění uživatele v tabulce před povolením přístupu k datům.  
  
> [!NOTE]
>  Řetězení vlastnictví neplatí v případě dynamických příkazů SQL. K volání procedury, která provede příkaz SQL, volající musí mít uděleno oprávnění pro základní tabulky, a aplikace bude zranitelný vůči útoku Injektáž SQL. SQL Server poskytuje nové mechanismů, například zosobnění a podepisování modulů s certifikáty, které nevyžadují udělení oprávnění pro základní tabulky. Ty můžete použít taky s CLR uložené procedury.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Oprávnění](http://msdn.microsoft.com/library/ms191291.aspx) v Online knihách serveru SQL|Obsahuje témata s popisem oprávnění hierarchie, zobrazení katalogu a oprávnění pevné role serveru a databáze.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací v systému SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Ověřování v systému SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Server a databázových rolí v systému SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Vlastnictví a oddělení schéma uživatele v systému SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
