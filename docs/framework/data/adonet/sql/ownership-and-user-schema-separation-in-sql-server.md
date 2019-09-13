---
title: Vlastnictví a oddělení uživatelských schémat na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 5ad3d927bcf3534e134db2c98b79842b0e6148f3
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894434"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Vlastnictví a oddělení uživatelských schémat na SQL Serveru
Základní pojem zabezpečení SQL Server je, že vlastníci objektů mají neodvolatelná oprávnění ke správě. Nemůžete odebrat oprávnění vlastníka objektu a nemůžete vyřadit uživatele z databáze, pokud v ní vlastní objekty.  
  
## <a name="user-schema-separation"></a>Oddělení schématu uživatele  
 Oddělení uživatelsky definovaných schémat zajišťuje větší flexibilitu při správě oprávnění databázových objektů. *Schéma* je pojmenovaný kontejner pro databázové objekty, který umožňuje seskupení objektů do samostatných oborů názvů. Například ukázková databáze AdventureWorks obsahuje schémata pro produkci, prodej a Lidskézdroje.  
  
 Syntaxe názvů čtyř částí pro odkazování na objekty určuje název schématu.  
  
```text
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Vlastníci a oprávnění schématu  
 Schémata může vlastnit libovolný objekt zabezpečení databáze a jeden instanční objekt může mít několik schémat. Můžete použít pravidla zabezpečení pro schéma, které jsou zděděné všemi objekty ve schématu. Po nastavení oprávnění k přístupu pro schéma se tato oprávnění automaticky uplatní, protože do schématu se přidají nové objekty. Uživatelům může být přiřazeno výchozí schéma a více uživatelů databáze může sdílet stejné schéma.  
  
 Ve výchozím nastavení, když vývojáři vytvářejí objekty ve schématu, objekty vlastní objekt zabezpečení, který vlastní schéma, nikoli vývojář. Vlastnictví objektu lze přenést pomocí příkazu ALTER-SQL příkazu ALTER AUTHORIZATION. Schéma může obsahovat také objekty, které jsou vlastněny různými uživateli a mají podrobnější oprávnění než přiřazení ke schématu, i když to nedoporučujeme, protože zvyšuje složitost správy oprávnění. Objekty lze přesouvat mezi schématy a vlastnictví schématu lze přenášet mezi objekty zabezpečení. Uživatele databáze je možné vyřadit, aniž by to ovlivnilo schémata.  
  
### <a name="built-in-schemas"></a>Vestavěná schémata  
 SQL Server se dodává s deseti předem definovanými schématy, které mají stejné názvy jako předdefinované uživatele a role databáze. Existují hlavně pro zpětnou kompatibilitu. Schémata, která mají stejné názvy jako pevné databázové role, můžete odstranit, pokud je nepotřebujete. Nemůžete vyřadit následující schémata:  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 Pokud je z databáze modelů vyřadíte, nebudou se zobrazovat v nových databázích.  
  
> [!NOTE]
> Schémata `sys` a`INFORMATION_SCHEMA` jsou vyhrazena pro systémové objekty. V těchto schématech nemůžete vytvářet objekty a nemůžete je vyřadit.  
  
#### <a name="the-dbo-schema"></a>Schéma dbo  
 `dbo` Schéma je výchozí schéma pro nově vytvořenou databázi. `dbo` Schéma vlastní`dbo` tento uživatelský účet. Ve výchozím nastavení mají `dbo` uživatelé vytvořeni pomocí příkazu Transact-SQL Create User jako výchozí schéma.  
  
 Uživatelé, kteří jsou přiřazeni `dbo` schématu, nedědí oprávnění `dbo` k uživatelskému účtu. Pro uživatele nejsou děděna žádná oprávnění od schématu. objektům databáze obsaženým ve schématu jsou zděděna oprávnění schématu.  
  
> [!NOTE]
> Pokud jsou objekty databáze odkazovány pomocí názvu jedné součásti, SQL Server nejprve vyhledá ve výchozím schématu uživatele. Pokud se objekt nenalezne, SQL Server ve `dbo` schématu dál. Pokud objekt není ve `dbo` schématu, je vrácena chyba.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o vlastnictví objektů a schématech naleznete v následujících zdrojích informací.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Oddělení schématu uživatele](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))|Popisuje změny zavedené oddělením schématu uživatele. Zahrnuje nové chování, jeho dopad na vlastnictví, zobrazení katalogu a oprávnění.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Ověřování v SQL Serveru](authentication-in-sql-server.md)
- [Serverové a databázové role na SQL Serveru](server-and-database-roles-in-sql-server.md)
- [Autorizace a oprávnění na SQL Serveru](authorization-and-permissions-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
