---
title: "Generování SQL úpravy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0c41f818c554b61dd6e63818627cb494f7c01577
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="modification-sql-generation"></a>Generování SQL úpravy
Tato část popisuje, jak vyvíjet modul úpravy SQL generování pro vaše (SQL:1999 – databáze kompatibilní) zprostředkovatele. Tento modul je zodpovědná za překladu stromu příkazů změny do příslušné příkazy SQL INSERT, UPDATE nebo DELETE.  
  
 Informace o generování SQL pro příkazy select najdete v tématu [generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).  
  
## <a name="overview-of-modification-command-trees"></a>Přehled stromy příkazů změny  
 Modul úpravy SQL generování generuje založené na daný vstupní DbModificationCommandTree úpravy specifické pro databáze SQL příkazy.  
  
 DbModificationCommandTree je reprezentaci objektu modelu změny operace DML (typu vložení, aktualizaci nebo operace odstranění), která dědí z DbCommandTree. Existují tři implementace DbModificationCommandTree:  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree a jeho implementace, které vznikají pomocí funkcí [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vždy představují jeden řádek operaci. Tato část popisuje tyto typy s jejich omezení v rozhraní .NET Framework verze 3.5.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree má vlastnost Target, která představuje cíl nastavit pro modifikační operaci. Vlastnost výrazu cílové složky, která definuje vstupní sadě je vždy DbScanExpression.  DbScanExpression může představovat buď tabulku nebo zobrazení, nebo sadu dat definované pomocí dotazu Pokud je vlastnost metadat "Definování dotaz" jeho cíle nesmí být nulová.  
  
 DbScanExpression, který představuje dotaz mohl pouze dosáhnout poskytovatele jako cíl změny pokud sada byl definován pomocí definující dotazu v modelu, ale žádná funkce byla poskytnuta pro odpovídající modifikační operaci. Zprostředkovatelé nemusí být schopné podporovat takové situaci (SqlClient, například nemá).  
  
 DbInsertCommandTree představuje operace insert jeden řádek, vyjádřené jako strom příkazů.  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree představuje operaci aktualizace jednoho řádku vyjádřené jako strom příkazů.  
  
 DbDeleteCommandTree představuje operaci odstranění jednoho řádku vyjádřené jako strom příkazů.  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>Omezení pro úpravu příkaz stromu vlastnosti  
 Následující informace a omezení platí pro vlastnosti úpravy příkazu stromu.  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Vrácení v DbInsertCommandTree a DbUpdateCommandTree  
 Když jinou hodnotu než null, Returning označuje, že příkaz vrátí čtečka čipových karet. Příkaz, jinak by měl vrátit skalární hodnotu, která určuje počet ovlivněných řádků (Vložit nebo aktualizovat).  
  
 Hodnota Returning určuje projekci výsledků vrácených základě na vložené nebo aktualizované řádek. Je možné ho pouze typu představující řádek, se každý z jeho argumenty DbPropertyExpression příliš DbVariableReferenceExpression, představující odkaz na cíl odpovídající DbModificationCommandTree DbNewInstanceExpression. Vlastnosti reprezentována DbPropertyExpressions použít ve vlastnosti Returning jsou vždy úložiště vygeneruje nebo počítaných hodnot. V DbInsertCommandTree Returning není null při alespoň jednu vlastnost tabulky, ve kterém bude vložen řádku je zadán jako úložiště vygeneruje nebo počítaných (označena jako StoreGeneratedPattern.Identity nebo StoreGeneratedPattern.Computed v ssdl). V DbUpdateCommandTrees, Returning není null. Pokud je zadán parametr alespoň jednu vlastnost tabulky, ve kterém se právě aktualizuje řádek jako úložiště počítaný (označena jako StoreGeneratedPattern.Computed v ssdl).  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses v DbInsertCommandTree a DbUpdateCommandTree  
 SetClauses určuje seznam insert nebo update nastavit klauzule, které definují operace insert nebo update.  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 Vlastnost určuje vlastnost, která by měly být aktualizovány. Vždycky je DbPropertyExpression přes DbVariableReferenceExpression, která představuje odkaz na cíl odpovídající DbModificationCommandTree.  
  
 Hodnota určuje, ke které má být aktualizujte vlastnost novou hodnotu. Je buď typu DbConstantExpression nebo DbNullExpression.  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>V DbUpdateCommandTree a DbDeleteCommandTree predikátem  
 Predikát určuje predikát umožňuje určit, které členy cílové kolekce by měl aktualizovat ani odstranit. Je sestaven z následující podmnožinu DbExpressions strom výrazu:  
  
-   Objekt DbComparisonExpression druhu rovná s správné podřízené se DbPropertyExression s omezeným přístupem níže a levé podřízený objekt DbConstantExpression.  
  
-   DbConstantExpression  
  
-   Objekt DbIsNullExpression přes DbPropertyExpresison s omezeným přístupem níže  
  
-   DbPropertyExpression přes DbVariableReferenceExpression, představující odkaz na cíl odpovídající DbModificationCommandTree.  
  
-   Objekt DbAndExpression  
  
-   Třída DbNotExpression  
  
-   Třída DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>Generování SQL změny ve zprostředkovateli ukázka  
 [Zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) ukazuje součástí zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Jeho cílem databáze systému SQL Server 2005 a je implementovaný jako obálku nad System.Data.SqlClient ADO.NET 2.0 dat zprostředkovatele.  
  
 Modul úpravy SQL generování ukázkového poskytovatele (nachází se v souboru SQL Generation\DmlSqlGenerator.cs) trvá vstupní DbModificationCommandTree a vytvoří jeden úprav příkazu SQL pravděpodobně následovaný příkazem SELECT vrátit čtečka, pokud určeného DbModificationCommandTree. Všimněte si, že tvar příkazy generované ovlivňuje cílová databáze systému SQL Server.  
  
### <a name="helper-classes-expressiontranslator"></a>Pomocné třídy: ExpressionTranslator  
 ExpressionTranslator slouží jako běžné lightweight překladač pro všechny úpravy příkaz stromu vlastnosti typu DbExpression. Podporuje překlad pouze typy výrazů na které jsou omezené vlastnosti strom příkazů úpravy a je integrovaný s konkrétní omezení na paměti.  
  
 Tyto informace se věnuje návštěvou typy konkrétní výrazů (uzly s trivial překlady byly vynechány).  
  
### <a name="dbcomparisonexpression"></a>Objekt DbComparisonExpression  
 Pokud je ExpressionTranslator vytvořený pomocí preserveMemberValues = true, a když konstanta vpravo DbConstantExpression (namísto DbNullExpression) se přidruží levý operand (DbPropertyExpressions), DbConstantExpression. Který se používá, pokud je třeba vytvořit pro identifikaci příslušného řádku vyberte příkaz return.  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 Pro každý navštívené konstanta je vytvořený parametr.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Vzhledem k tomu, že Instance DbPropertyExpression vždy představuje vstupní tabulky, pokud generování vytvořil alias (která se dělá jenom ve scénářích aktualizace Pokud se používá proměnnou tabulky), je třeba zadat pro vstup; žádný alias překlad výchozí název vlastnosti.  
  
## <a name="generating-an-insert-sql-command"></a>Generování příkazu Insert SQL  
 Pro danou DbInsertCommandTree ve zprostředkovateli ukázkové následuje příkaz insert generovaného jednu z níže dvě vložení šablon.  
  
 První šablonu, kterou má příkaz k provedení vložení, na základě hodnot v seznamu SetClauses a vyberte příkaz vrátit vlastnosti zadaná ve vlastnosti Returning vloženého řádku, pokud vlastnost Returning nebyla null. Element predikátem "@@ROWCOUNT > 0" je hodnota true, pokud byl vložit řádek. Element predikátem "keyMemberI = keyValueI &#124; scope_identity() "trvá tvar" keyMemberI = scope_identity() "pouze v případě keyMemeberI je klíč generovaný úložištěm, protože scope_identity() vrátí poslední hodnotu identity, které jsou vloženy do sloupce identity (generovaný úložištěm).  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Druhá šablona je nutný v případě, že úlohy insert určuje vložíte řádek kde primární klíč se generuje úložiště, ale není typu integer a proto jej nelze použít s scope_identity()). Používá se také při složený klíč generovaný úložištěm.  
  
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
  
 Následuje příklad, který používá model, který je součástí ukázkového zprostředkovatele. Příkaz insert vygeneruje z DbInsertCommandTree.  
  
 Následující kód vloží do kategorií:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Tento kód vytvoří následující strom příkazů, které je předána zprostředkovateli:  
  
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
  
 Příkaz úložiště, který vytváří ukázkového zprostředkovatele je následující příkaz SQL:  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>Generování příkazu SQL pro aktualizaci  
 Pro danou DbUpdateCommandTree příkaz generovaného aktualizace podle následující šablony:  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Klauzuli set obsahuje klauzuli falešných set ("@i = 0") pouze v případě, že nejsou zadány žádné klauzule set. To je potřeba zajistit, že žádné úložiště vypočtená jsou přepočítávány sloupce.  
  
 Pouze v případě, že vlastnost Returning není null, se k vrácení vlastností zadaná ve vlastnosti Returning vygeneruje příkazu select.  
  
 Následující příklad používá model, který je součástí zprostředkovatele ukázka ke generování příkazu pro aktualizaci.  
  
 Následující kód uživatele aktualizace kategorie:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 Tento kód uživatele vytváří následující strom příkazů, které je předána zprostředkovateli:  
  
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
  
 Ukázka zprostředkovatele vytváří následující příkaz úložiště:  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>Generování příkazu SQL odstranění  
 Pro danou DbDeleteCommandTree vygenerovaný příkaz DELETE podle následující šablony:  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 Následující příklad používá model, který je součástí zprostředkovatele ukázka ke generování příkaz delete.  
  
 Následující kód uživatel odstraní kategorie:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Tento kód uživatel vytvoří následující strom příkazů, které je předána zprostředkovateli.  
  
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
  
 Následující příkaz úložiště je produkovaný ukázkového zprostředkovatele:  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis poskytovatele dat Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
