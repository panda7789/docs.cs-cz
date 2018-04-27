---
title: Známé problémy v SqlClient rozhraní Entity Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 8d5363ede9735ea805284638f795af67f2415ad0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Známé problémy v SqlClient rozhraní Entity Framework
Tato část popisuje známé problémy související s zprostředkovatele dat .NET Framework pro SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Koncové mezery řetězcové funkce  
 SQL Server ignoruje koncové mezery v řetězcové hodnoty. Proto předávání koncové mezery v řetězci může vést k vést k neočekávaným výsledkům, i selhání.  
  
 Pokud máte tak, aby měl koncové mezery ve vašem řetězci, měli byste zvážit připojování prázdný znak na konci, tak, aby SQL Server není oříznout řetězec. Pokud koncové mezery nejsou vyžadovány, má být oříznut předtím, než jsou předávány dolů kanálu dotazu.  
  
## <a name="right-function"></a>RIGHT – funkce  
 Pokud jinou hodnotu než`null` byla předána hodnota jako první argument a 0 je předána jako druhý argument `RIGHT(nvarchar(max)`, 0`)` nebo `RIGHT(varchar(max)`, 0`)`, `NULL` bude vrácena hodnota místo `empty` řetězec.  
  
## <a name="cross-and-outer-apply-operators"></a>MEZI a vnější použít operátory  
 MEZI a operátoru OUTER APPLY operátory byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]. V některých případech může vytvořit kanál dotazu příkazu Transact-SQL, který obsahuje operátory křížové použít nebo operátoru OUTER APPLY. Protože někteří poskytovatelé back-end, včetně verze systému SQL Server starších než [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], nepodporují tyto operátory, takové dotazy se nedá spustit na tyto zprostředkovatele back-end.  
  
 Tady jsou některé typické scénáře, které mohou vést k přítomnost mezi použít nebo operátoru OUTER APPLY operátory v dotazu výstup:  
  
-   Korelační poddotaz s stránkování.  
  
-   `AnyElement` Přes korelační poddotazu nebo přes kolekci vyprodukované navigace.  
  
-   LINQ dotazy, které používají seskupování metody, které přijímají selektorem elementu.  
  
-   Dotaz, ve kterém je explicitně zadaný křížové použít nebo operátoru OUTER APPLY  
  
-   Vytvořit dotaz, který má DEREF přes REF konstrukce.  
  
## <a name="skip-operator"></a>SKIP – operátor  
 Pokud používáte [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)], pomocí přeskočit s klauzulí ORDER BY v neklíčových sloupců může vrátit nesprávné výsledky. Více než zadaný počet řádků může přeskočen. Pokud neklíčový sloupec obsahuje duplicitní data v ní. Je to z důvodu jak SKIP je přeložená pro [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]. Například v následujícím dotazu, více než pět řádků může být přeskočeno `E.NonKeyColumn` obsahuje duplicitní hodnoty:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Cílení na verzi serveru SQL správný  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Cíle [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] podle verze systému SQL Server, který je uveden v dotazu `ProviderManifestToken` atribut elementu schématu v souboru modelu (ssdl) úložiště. Tato verze může lišit od verze skutečné jste připojeni k serveru SQL. Například, pokud používáte SQL Server 2005 ale vaše `ProviderManifestToken` je atribut nastaven na 2008, vygenerovaného [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] dotaz nemusí spustit na serveru. Například nebude v dřívějších verzích systému SQL Server spustit dotaz, který používá nové datum čas typy, které byly zavedeny v systému SQL Server 2008. Pokud používáte SQL Server 2005, ale vaše `ProviderManifestToken` je atribut nastaven na 2000 vygenerovaného [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] dotazu může být menší optimalizované nebo výjimku, která uvádí, že dotaz není podporovaný, může získat. Další informace najdete v tématu mezi vnější použít operátory části a dříve v tomto tématu.  
  
 Určitého chování databáze závisí na úroveň kompatibility nastaveno na databázi. Pokud vaše `ProviderManifestToken` 2005 nastavený atribut a je vaší verze systému SQL Server 2005, ale úroveň kompatibility databáze je nastavena na "80" (SQL Server 2000), vygenerovaného [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] bude cílené na SQL Server 2005, ale nemusí provést podle očekávání kvůli nastavení úrovně kompatibility. Například může ztratit řazení informace, pokud název sloupce v seznamu ORDER BY odpovídá název sloupce v modulu pro výběr.  
  
## <a name="nested-queries-in-projection"></a>Vnořené dotazy v projekci  
 Vnořené dotazy v klauzuli projekce může získat přeložit na kartézský součin dotazy na serveru. Na některých serverech back-end, včetně serveru SQL Server to může způsobit v tabulce databáze TempDB získat poměrně velké. To může snížit výkon serveru.  
  
 Následuje příklad vnořený dotaz v klauzuli projekce:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Hodnoty Identity GUID generovaný serverem  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Podporuje hodnoty generované serverem GUID typ identity, ale zprostředkovatel musí podporovat vrácení hodnoty generované serverem identity po vložení řádku. Od verze systému SQL Server 2005, můžete se vrátit na typ GUID generované serverem v databázi systému SQL Server prostřednictvím [klauzuli OUTPUT](http://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Viz také  
 [SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [Známé problémy a aspekty u LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
