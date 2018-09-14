---
title: Úpravy generování SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615125"
---
# <a name="modification-sql-generation"></a>Úpravy generování SQL
Tato část popisuje, jak vyvinout úprav modulu generování SQL pro vaše (SQL:1999 – databáze kompatibilní) zprostředkovatele. Tento modul je zodpovědná za překládá úpravy stromu příkazů na příslušné příkazy SQL INSERT, UPDATE nebo DELETE.  
  
 Informace o generování SQL pro příkazy select, naleznete v tématu [generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).  
  
## <a name="overview-of-modification-command-trees"></a>Přehled úprav stromů příkazů  
 Modul generování SQL úpravy vygeneruje úpravu konkrétních databází SQL příkazy podle daného vstupního DbModificationCommandTree.  
  
 Objektová reprezentace modelu úprav operace DML (vložení, aktualizace nebo odstranění), je DbModificationCommandTree dědění z DbCommandTree. Existují tři implementace DbModificationCommandTree:  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree a jeho implementace, které jsou vytvářeny [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vždycky reprezentuje operaci jeden řádek. Tato část popisuje tyto typy s jejich omezení v rozhraní .NET Framework verze 3.5.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree má vlastnost Target, který představuje cíl pro operaci úpravy nastavit. Vlastnost Expression cíle, která definuje vstupní sady je vždy DbScanExpression.  DbScanExpression může představovat tabulku nebo zobrazení nebo sady dat definované pomocí dotazu vlastnost metadat "Definice dotazu" jejím cílem je-li jinou hodnotu než null.  
  
 DbScanExpression, který představuje dotaz mohl pouze dosáhnout zprostředkovatele jako cíl změny pokud sada byl definován pomocí definování dotazů v modelu, ale byla zadána žádná funkce pro odpovídající operaci úprav. Poskytovatelé nemusí být schopni poskytovat podporu takové situaci (SqlClient, například nemá).  
  
 DbInsertCommandTree představuje operaci insert jednoho řádku vyjádřené jako strom příkazů.  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree představuje operaci aktualizace jednoho řádku vyjádřené jako strom příkazů.  
  
 DbDeleteCommandTree představuje operaci odstranění jednoho řádku vyjádřené jako strom příkazů.  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>Omezení vlastnosti stromu příkazu Úpravy  
 Následující informace a omezení platí pro vlastnosti úpravy příkazu stromu.  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Vrací DbInsertCommandTree a DbUpdateCommandTree  
 Pokud není null, Returning označuje, že příkaz vrátí čtečku. Příkaz v opačném případě by měl vrátit skalární hodnotu určující počet ovlivněných řádků (přidají nebo aktualizují).  
  
 Hodnota Returning specifikuje projekci výsledků, který se má vrátit na základě vloženého nebo aktualizovaný řádek. Může být pouze typu představuje řádek, kde každý z jejích argumentů je DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree DbNewInstanceExpression. Vlastnosti reprezentované DbPropertyExpressions používá ve vlastnosti Returning jsou vždy úložiště vygeneruje nebo vypočítané hodnoty. V DbInsertCommandTree Returning není null při alespoň jedné vlastnosti takové tabulky, ve kterém je vložen řádku je zadán jako úložiště vygeneruje nebo vypočítat (označené jako StoreGeneratedPattern.Identity nebo StoreGeneratedPattern.Computed v ssdl). V DbUpdateCommandTrees, Returning není null při alespoň jedné vlastnosti takové tabulky, ve kterém se aktualizuje řádek je zadán jako úložiště vypočítat (označené jako StoreGeneratedPattern.Computed v ssdl).  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses DbInsertCommandTree a DbUpdateCommandTree  
 SetClauses určuje seznam insert nebo update nastavit klauzule, které definují operaci insert nebo update.  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 Vlastnost určuje vlastnost, která by se měla aktualizovat. Je vždy DbPropertyExpression nad DbVariableReferenceExpression, který představuje odkaz na cíl odpovídající DbModificationCommandTree.  
  
 Hodnota určuje novou hodnotu, pomocí kterého se má aktualizovat vlastnost. Je buď typu DbConstantExpression nebo DbNullExpression.  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Predikátu v DbUpdateCommandTree a DbDeleteCommandTree  
 Predikát určuje predikát, který umožňuje určit, které členy cílové kolekce by měl aktualizovat ani odstranit. Strom výrazů, které se skládají z následující dílčí DbExpressions je:  
  
-   Objekt DbComparisonExpression druhu rovná se správné podřízené se DbPropertyExression s omezeným přístupem níže a levém podřízený objekt DbConstantExpression.  
  
-   DbConstantExpression  
  
-   Objekt DbIsNullExpression přes DbPropertyExpresison s omezeným přístupem níže  
  
-   DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree.  
  
-   DbAndExpression  
  
-   Třída DbNotExpression  
  
-   Třída DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>Úpravy generování SQL ve zprostředkovateli ukázek  
 [Ukázka zprostředkovatele Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) ukazuje součástí zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Je zaměřen na databázi systému SQL Server 2005 a je implementovaný jako obálka nad zprostředkovatele dat ADO.NET 2.0 System.Data.SqlClient.  
  
 Modul generování SQL úpravy ukázkového poskytovatele (umístěný v souboru SQL Generation\DmlSqlGenerator.cs) přijímá vstupní DbModificationCommandTree a vytvoří jeden úprav příkazu SQL pravděpodobně následovaný příkazem SELECT se vraťte Čtečka případného DbModificationCommandTree. Všimněte si, že tvar příkazy generované je ovlivněna cílová databáze systému SQL Server.  
  
### <a name="helper-classes-expressiontranslator"></a>Pomocné třídy: ExpressionTranslator  
 ExpressionTranslator slouží jako běžné zjednodušené převaděč pro všechny úpravy příkaz stromu vlastnosti typu DbExpression. Podporuje překlad pouze typy výrazů ke kterým jsou omezeny vlastnosti stromu příkazů úpravy a vytvořené s konkrétní omezení na paměti.  
  
 Následující informace popisují navštívit typy konkrétní výrazů (uzly s triviální překlady jsou vynechány).  
  
### <a name="dbcomparisonexpression"></a>Objekt DbComparisonExpression  
 Když je vytvořený ExpressionTranslator pomocí preserveMemberValues = true, a když konstanty na pravé straně je objekt DbConstantExpression (namísto DbNullExpression), přiřadí levý operand (DbPropertyExpressions) s, který DbConstantExpression. Který se používá, pokud vratky příkazu Select je potřeba vygenerovat k identifikaci ovlivněných řádků.  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 Pro každý navštívených – konstanta se vytvoří parametr.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Vzhledem k tomu, že Instance DbPropertyExpression vždy představuje vstupní tabulky, není-li generování vytvořil alias (která situace nastane pouze ve scénářích aktualizace při se používá proměnnou tabulky), žádný alias musí být zadaná pro vstup; překlad výchozí název vlastnosti.  
  
## <a name="generating-an-insert-sql-command"></a>Generování příkazu Insert SQL  
 Pro daný DbInsertCommandTree ve zprostředkovateli ukázek následuje příkazu insert generované některou ze šablon dvě vložit níže.  
  
 První šablona má příkaz provádět na základě hodnot v seznamu SetClauses insert a příkaz SELECT pro vrácení vlastnosti zadaná ve vlastnosti Returning vloženého řádku, pokud vlastnost Returning nebyl prázdný. Element predikátu "\@ @ROWCOUNT > 0" je hodnota true, pokud byl vložen řádek. Element predikátu "keyMemberI = keyValueI &#124; scope_identity()" má tvar "keyMemberI = scope_identity()" pouze v případě keyMemeberI je klíče generované úložištěm, protože scope_identity() vrátí poslední hodnotu identity, které jsou vloženy do identity ( sloupec generovaných úložištěm).  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Druhá šablona je potřeba, je-li vložit určuje vložení řádku, kde primární klíč se generuje úložiště, ale není typu integer a proto jej nelze použít s scope_identity()). Používá se také při složené klíče generované úložištěm.  
  
```  
-- second insert template  
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)  
  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys  
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES  
  
[SELECT <returning_over_t>   
 FROM @generated_keys  AS g  
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN  
 WHERE @@ROWCOUNT > 0  
```  
  
 Následuje příklad, který používá model, který je součástí ukázkového zprostředkovatele. Generuje příkazu k vložení z DbInsertCommandTree.  
  
 Následující kód vloží kategorii:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Tento kód vytvoří následující stromu příkazů, který se předá do zprostředkovatele:  
  
```  
DbInsertCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).CategoryName  
| | |_Value  
| |   |_'Test Category'  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).Description  
| | |_Value  
| |   |_'A new category for testing'  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).Picture  
|   |_Value  
|     |_null  
|_Returning  
  |_NewInstance : Record['CategoryID'=Edm.Int32]  
    |_Column : 'CategoryID'  
      |_Var(target).CategoryID  
```  
  
 Příkaz úložiště, který vytváří zprostředkovateli ukázek je následující příkaz SQL:  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>Generování SQL příkazu k aktualizaci  
 Pro daný DbUpdateCommandTree příkazu generované aktualizace podle následující šablony:  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Klauzule set je klauzule set falešné ("@i = 0") pouze v případě, že jsou zadány bez klauzule set. Tím je zajištěno, že žádné úložiště počítané sloupce jsou přepočítány.  
  
 Pouze v případě, že vlastnost Returning není null, vyberte příkaz vygeneruje se vraťte se do vlastností zadaná ve vlastnosti Returning.  
  
 Následující příklad používá model, který je součástí ukázkového zprostředkovatele k vygenerování příkazu k aktualizaci.  
  
 Následující kód uživatele aktualizuje kategorii:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 Tento uživatelský kód vytvoří následující stromu příkazů, který se předá do zprostředkovatele:  
  
```  
DbUpdateCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).CategoryName  
|   |_Value  
|     |_'New test name'  
|_Predicate  
| |_  
|   |_Var(target).CategoryID  
|   |_=  
|   |_10  
|_Returning   
```  
  
 Ukázka zprostředkovatele vytvoří následující příkaz úložiště:  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>Generování SQL příkazu Delete  
 Pro daný DbDeleteCommandTree generované příkazem k odstranění podle následující šablony:  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 Následující příklad používá model, který je součástí ukázkového zprostředkovatele k vygenerování příkazu pro odstranění.  
  
 Následující kód uživatele odstraní kategorie:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Tento uživatelský kód vytvoří následující stromu příkazů, která je předána zprostředkovateli.  
  
```  
DbDeleteCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_Predicate  
  |_  
    |_Var(target).CategoryID  
    |_=  
    |_10  
```  
  
 Následující příkaz úložiště je vytvořen poskytovatelem vzorku:  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis zprostředkovatele dat Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
