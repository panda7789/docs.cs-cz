---
title: Úpravy generování SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: ab0c18473e73b2d6fe9eb45c43e9b47947a55d99
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248577"
---
# <a name="modification-sql-generation"></a>Úpravy generování SQL

Tato část popisuje, jak vytvořit modul SQL pro úpravu úprav pro poskytovatele (databáze kompatibilní s SQL: 1999). Tento modul zodpovídá za překlad stromu příkazů změny do odpovídajících příkazů SQL INSERT, UPDATE nebo DELETE.

Informace o generování SQL pro příkazy SELECT najdete v tématu [generování SQL](sql-generation.md).

## <a name="overview-of-modification-command-trees"></a>Přehled stromů příkazů pro změnu

Modul úprav SQL Generation vygeneruje příkazy SQL změny specifické pro databázi na základě daného vstupního DbModificationCommandTree.

DbModificationCommandTree je reprezentace objektového modelu operace DML změny (operace vložení, aktualizace nebo odstranění), která dědí z DbCommandTree. Existují tři implementace DbModificationCommandTree:

- DbInsertCommandTree

- DbUpdateCommandTree

- DbDeleteCommandTree

DbModificationCommandTree a jeho implementace, které jsou vytvářeny [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vždy, představují operaci s jedním řádkem. Tato část popisuje tyto typy s omezeními v .NET Framework verze 3,5.

![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")

DbModificationCommandTree má cílovou vlastnost, která představuje cílovou sadu pro operaci úpravy. Vlastnost Expression cíle definující vstupní sadu je vždy DbScanExpression.  DbScanExpression může představovat tabulku nebo zobrazení nebo sadu dat, která je definována s dotazem, pokud vlastnost metadat "definující dotaz" cílového objektu nemá hodnotu null.

DbScanExpression, který představuje dotaz, by mohl kontaktovat poskytovatele jako cíl změny, pokud byla sada definována pomocí definičního dotazu v modelu, ale není k dispozici žádná funkce pro odpovídající operaci úprav. Poskytovatelé nemusí být schopni podporovat takový scénář (například není).

DbInsertCommandTree představuje operaci vložení jednoho řádku vyjádřenou jako strom příkazů.

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

DbUpdateCommandTree představuje operaci aktualizace s jedním řádkem, která je vyjádřena jako strom příkazů.

DbDeleteCommandTree představuje operaci odstranění jednoho řádku vyjádřenou jako strom příkazů.

### <a name="restrictions-on-modification-command-tree-properties"></a>Omezení vlastností stromu příkazů pro úpravy

Následující informace a omezení se vztahují na vlastnosti stromu příkazů pro úpravy.

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Vracení v DbInsertCommandTree a DbUpdateCommandTree

Pokud hodnota, která není null, vrátí, že příkaz vrátí čtecí modul. V opačném případě by příkaz měl vracet skalární hodnotu určující počet ovlivněných řádků (vloženo nebo aktualizováno).

Návratová hodnota určuje projekci výsledků, které se mají vrátit na základě vloženého nebo aktualizovaného řádku. Může být pouze typu DbNewInstanceExpression představující řádek, přičemž každý z jeho argumentů je DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree. Vlastnosti reprezentované DbPropertyExpressions použitou ve vlastnosti vracející se vždy ukládají vygenerované nebo počítané hodnoty. V DbInsertCommandTree není vrácení hodnoty null, pokud alespoň jedna vlastnost tabulky, do které je řádek vkládán, je zadána jako vygenerované nebo počítané úložiště (označeno jako StoreGeneratedPattern. identity nebo StoreGeneratedPattern. vypočítané ve SSDL). V DbUpdateCommandTrees není vrácení hodnoty null, pokud alespoň jedna vlastnost tabulky, ve které je řádek aktualizován, je zadána jako vypočtené úložiště (označeno jako StoreGeneratedPattern. vypočítané ve SSDL).

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses v DbInsertCommandTree a DbUpdateCommandTree

SetClauses určuje seznam klauzulí INSERT nebo Update set, které definují operaci INSERT nebo Update.

```
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.
```

Vlastnost určuje vlastnost, která má být aktualizována. Je vždy DbPropertyExpression prostřednictvím DbVariableReferenceExpression, který představuje odkaz na cíl odpovídajícího DbModificationCommandTree.

Hodnota určuje novou hodnotu, se kterou chcete vlastnost aktualizovat. Je to buď typ DbConstantExpression nebo DbNullExpression.

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Predikát v DbUpdateCommandTree a DbDeleteCommandTree

Predikát určuje predikát použitý k určení, které členy cílové kolekce by měly být aktualizovány nebo smazány. Jedná se o strom výrazu sestavený z následující podmnožiny DbExpressions:

- Objekt DbComparisonExpression je rovno, s pravou podřízenou položkou DbPropertyExpression tak, jak je omezená, a levou podřízenou DbConstantExpression.

- DbConstantExpression

- DbIsNullExpression přes DbPropertyExpression na omezenou hodnotu

- DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree.

- DbAndExpression

- DbNotExpression

- DbOrExpression

## <a name="modification-sql-generation-in-the-sample-provider"></a>Úprava generování SQL ve zprostředkovateli vzorků

[Poskytovatel ukázkového Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje komponenty zprostředkovatelů dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Cílí na databázi SQL Server 2005 a implementuje se jako obálka na úrovni System. data. SqlClient ADO.NET 2,0 Zprostředkovatel dat.

Modul úprav SQL pro generování ukázkového poskytovatele (umístěný v souboru SQL Generation\DmlSqlGenerator.cs) přebírá vstupní DbModificationCommandTree a vytvoří jediný příkaz SQL, který je možná následován příkazem SELECT, který vrátí čtenář, pokud je určený parametrem DbModificationCommandTree. Všimněte si, že tvar generovaných příkazů je ovlivněn cílovou SQL Server databází.

### <a name="helper-classes-expressiontranslator"></a>Pomocné třídy: ExpressionTranslator

ExpressionTranslator slouží jako společný odlehčený překladatel pro všechny vlastnosti stromu příkazů pro změnu typu DbExpression. Podporuje převod pouze typů výrazů, pro které jsou vlastnosti stromu příkazů změny omezené a jsou sestaveny s konkrétními omezeními.

Následující informace jsou popsány v tématu návštěvy specifických typů výrazů (uzly s triviálními překlady jsou vynechány).

### <a name="dbcomparisonexpression"></a>DbComparisonExpression

Když je ExpressionTranslator vytvořen pomocí preserveMemberValues = true a pokud je konstanta pravého DbConstantExpression (namísto DbNullExpression), přidružuje levý operand (DbPropertyExpressions) k tomuto DbConstantExpression. Který se používá v případě, že je nutné vygenerovat návratový příkaz SELECT pro identifikaci ovlivněného řádku.

### <a name="dbconstantexpression"></a>DbConstantExpression

Pro každou navštívenou konstantu je vytvořen parametr.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Vzhledem k tomu, že instance DbPropertyExpression vždy představuje vstupní tabulku, pokud generace nevytvořila alias (ke kterému dochází pouze ve scénářích aktualizace při použití proměnné tabulky), není pro vstup nutné zadat žádný alias. překlad je ve výchozím nastavení název vlastnosti.

## <a name="generating-an-insert-sql-command"></a>Generování příkazu INSERT SQL

V případě daného DbInsertCommandTree ve zprostředkovateli ukázky se za generovaným příkazem INSERT používá jedna z následujících dvou šablon pro vložení.

První šablona obsahuje příkaz pro vložení hodnot v seznamu SetClauses a příkaz SELECT, který vrátí vlastnosti zadané ve vlastnosti vracející vloženého řádku, pokud vlastnost vracející nebyla null. Element predikátu "\@ @ROWCOUNT > 0" má hodnotu true, pokud byl řádek vložen. Element predikátu "SCOPE_IDENTITY členi = klíč hodnota &#124; SCOPE_IDENTITY ()" převezme tvar "členi = ()" pouze v případě, že je klíčovým členem klíč generovaný úložištěm, protože SCOPE_IDENTITY () vrátí hodnotu poslední identity vloženou do identity ( sloupec generovaný úložištěm.

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

Druhá šablona je potřebná v případě, že vložení určuje vložení řádku, ve kterém je primární klíč uložen, ale není typu Integer, a proto jej nelze použít s SCOPE_IDENTITY ()). Používá se také v případě, že je k dispozici složený klíč generovaný úložištěm.

```sql
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

Následuje příklad, který používá model, který je součástí poskytovatele ukázek. Vygeneruje příkaz INSERT z DbInsertCommandTree.

Následující kód vloží kategorii:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

Tento kód vytvoří následující strom příkazů, který je předán poskytovateli:

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

Příkaz Store, který generuje vzorový poskytovatel, je následující příkaz SQL:

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a>Generování příkazu Update SQL

Pro daný DbUpdateCommandTree je vygenerovaný příkaz Update založen na následující šabloně:

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

Klauzule SET má nafalešnou klauzuli set (@i = 0), pouze pokud nejsou zadány žádné klauzule SET. K tomu je potřeba zajistit, aby se přepočítaly všechny počítané sloupce v úložišti.

Pouze v případě, že návratová vlastnost nemá hodnotu null, je vygenerován příkaz SELECT, který vrátí vlastnosti zadané ve vlastnosti vráceno.

Následující příklad používá model, který je součástí poskytovatele Sample k vygenerování aktualizačního příkazu.

Následující kód uživatele aktualizuje kategorii:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

Tento uživatelský kód vytvoří následující strom příkazů, který se předává poskytovateli:

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

Ukázkový poskytovatel vytvoří následující příkaz úložiště:

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a>Generování příkazu Delete SQL

Pro daný DbDeleteCommandTree je vygenerovaný příkaz DELETE založen na následující šabloně:

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

Následující příklad používá model, který je součástí poskytovatele Sample k vygenerování příkazu DELETE.

Následující kód uživatele odstraní kategorii:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

Tento uživatelský kód vytvoří následující strom příkazů, který je předán poskytovateli.

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

Následující příkaz pro uložení je vytvořen poskytovatelem ukázky:

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a>Viz také:

- [Zápis zprostředkovatele dat Entity Framework](writing-an-ef-data-provider.md)
