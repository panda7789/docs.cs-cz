---
title: Známé problémy v SqlClient pro Entity Framework
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: c1353444415ddd2305a73d14bacf1bb33a931929
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251716"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Známé problémy v SqlClient pro Entity Framework
Tato část popisuje známé problémy související s zprostředkovatele dat .NET Framework pro SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Koncové mezery v řetězcové funkce  
 SQL Server ignoruje koncové mezery v řetězcové hodnoty. Proto předávání koncové mezery v řetězci může vést k nepředvídatelným výsledkům, dokonce i chyby.  
  
 Pokud je třeba mít koncové mezery do řetězce, měli byste zvážit připojení prázdný znak na konci, tak, aby SQL Server není oříznutí řetězce. Pokud koncové mezery nejsou vyžadovány, má být oříznut předtím, než jsou předány dolů kanálu dotazu.  
  
## <a name="right-function"></a>RIGHT – funkce  
 Pokud non -`null` předanou jako první argument a 0 je předána jako druhý argument `RIGHT(nvarchar(max)`, 0`)` nebo `RIGHT(varchar(max)`, 0`)`, `NULL` místo bude vrácena hodnota `empty` řetězec.  
  
## <a name="cross-and-outer-apply-operators"></a>RŮZNÉ a vnější použít operátory  
 RŮZNÉ a operátoru OUTER APPLY operátory byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]. V některých případech může být vytvoření kanálu dotazu příkaz jazyka Transact-SQL, který obsahuje operátory CROSS APPLY a/nebo operátoru OUTER APPLY. Protože někteří poskytovatelé back-end, včetně verze SQL serveru starší než [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], nepodporují tyto operátory, tyto dotazy se nedá spustit na těchto zprostředkovatelů back-endu.  
  
 Následují některé typické scénáře, které by mohly vést k přítomnost CROSS APPLY a/nebo operátoru OUTER APPLY operátory v dotazu výstup:  
  
-   Korelační poddotaz s stránkování.  
  
-   `AnyElement` Přes korelovaný poddotaz, nebo kolekci vytvořenou testovaným navigace.  
  
-   LINQ dotazy, které používají seskupení metody, které přijímají elementu selektor.  
  
-   Dotaz, ve kterém je explicitně zadán CROSS APPLY nebo operátoru OUTER APPLY  
  
-   Vytvořit dotaz, který má DEREF přes konstrukci REF.  
  
## <a name="skip-operator"></a>Operátor SKIP  
 Pokud používáte [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)], pomocí přeskočit s klauzulí ORDER BY v neklíčových sloupců může vrátit nesprávné výsledky. Větší než zadaný počet řádků se možná přeskočí, pokud neklíčový sloupec v sobě obsahuje duplicitní data. Je to kvůli jak SKIP je přeložen pro [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]. Například následující dotaz, více než pět řádků možná přeskočí, pokud `E.NonKeyColumn` obsahují duplicitní hodnoty:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Cílení na verzi serveru SQL správný  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Cíle [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] podle verze systému SQL Server, který je zadaný v dotazu `ProviderManifestToken` atribut schématu elementu v souboru modelu (ssdl) úložiště. Tato verze se může lišit od verze skutečné jste připojeni k serveru SQL. Například, pokud používáte SQL Server 2005 ale vaše `ProviderManifestToken` atribut je nastaven na 2008 generované [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] dotazu nebude možné provést na serveru. Například nebude ve starších verzích systému SQL Server spustit dotaz, který používá typy čas nové datum, které byly zavedeny v systému SQL Server 2008. Pokud používáte SQL Server 2005, ale vaše `ProviderManifestToken` atribut je nastaven na 2000, generované [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] dotaz zřejmě menší optimalizované a může se zobrazit výjimka, která říká, že dotaz se nepodporuje. Další informace najdete v části různé a vnější použít operátory, dříve v tomto tématu.  
  
 Určitého chování, databáze, závisí na nastavení databáze úroveň kompatibility. Pokud vaše `ProviderManifestToken` atribut je nastaven na 2005 a je vaše verze systému SQL Server 2005, ale úroveň kompatibility databáze je nastavený na "80" (SQL Server 2000) vygenerovaný [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] bude cílené na systém SQL Server 2005, ale nebude možné provést z důvodu očekávaným způsobem nastavení úrovně kompatibility. Například můžete přijít pořadí informace pokud název sloupce v seznamu ORDER BY odpovídá názvu sloupce v modulu pro výběr.  
  
## <a name="nested-queries-in-projection"></a>Vnořené dotazy v projekci  
 Vnořené dotazy v klauzuli projekce může získat přeloženy do kartézský součin dotazy na serveru. U některých back-end serverů, včetně serveru SQL Server to může způsobit TempDB tabulka, která má být poměrně velké. To může snížit výkon serveru.  
  
 Následuje příklad vnořeného dotazu v klauzuli projekce:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Server generované hodnoty Identity identifikátor GUID  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Podporuje generovaný serverem identifikátor GUID typu hodnot identity, ale poskytovateli musí podporovat, vrátí hodnotu, generovaný serverem identity po vložila řádek. Od verze SQL Server 2005, může vrátit identifikátor GUID typu generovaný serverem v databázi serveru SQL Server prostřednictvím [klauzuli OUTPUT](https://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Viz také  
 [SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [Známé problémy a aspekty u LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
