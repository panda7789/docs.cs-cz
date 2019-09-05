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
# <a name="modification-sql-generation"></a><span data-ttu-id="a3c7c-102">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="a3c7c-102">Modification SQL Generation</span></span>

<span data-ttu-id="a3c7c-103">Tato část popisuje, jak vytvořit modul SQL pro úpravu úprav pro poskytovatele (databáze kompatibilní s SQL: 1999).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="a3c7c-104">Tento modul zodpovídá za překlad stromu příkazů změny do odpovídajících příkazů SQL INSERT, UPDATE nebo DELETE.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>

<span data-ttu-id="a3c7c-105">Informace o generování SQL pro příkazy SELECT najdete v tématu [generování SQL](sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-105">For information about SQL generation for select statements, see [SQL Generation](sql-generation.md).</span></span>

## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="a3c7c-106">Přehled stromů příkazů pro změnu</span><span class="sxs-lookup"><span data-stu-id="a3c7c-106">Overview of Modification Command Trees</span></span>

<span data-ttu-id="a3c7c-107">Modul úprav SQL Generation vygeneruje příkazy SQL změny specifické pro databázi na základě daného vstupního DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>

<span data-ttu-id="a3c7c-108">DbModificationCommandTree je reprezentace objektového modelu operace DML změny (operace vložení, aktualizace nebo odstranění), která dědí z DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="a3c7c-109">Existují tři implementace DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-109">There are three implementations of DbModificationCommandTree:</span></span>

- <span data-ttu-id="a3c7c-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="a3c7c-110">DbInsertCommandTree</span></span>

- <span data-ttu-id="a3c7c-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="a3c7c-111">DbUpdateCommandTree</span></span>

- <span data-ttu-id="a3c7c-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="a3c7c-112">DbDeleteCommandTree</span></span>

<span data-ttu-id="a3c7c-113">DbModificationCommandTree a jeho implementace, které jsou vytvářeny [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vždy, představují operaci s jedním řádkem.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="a3c7c-114">Tato část popisuje tyto typy s omezeními v .NET Framework verze 3,5.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>

<span data-ttu-id="a3c7c-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="a3c7c-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>

<span data-ttu-id="a3c7c-116">DbModificationCommandTree má cílovou vlastnost, která představuje cílovou sadu pro operaci úpravy.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="a3c7c-117">Vlastnost Expression cíle definující vstupní sadu je vždy DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="a3c7c-118">DbScanExpression může představovat tabulku nebo zobrazení nebo sadu dat, která je definována s dotazem, pokud vlastnost metadat "definující dotaz" cílového objektu nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>

<span data-ttu-id="a3c7c-119">DbScanExpression, který představuje dotaz, by mohl kontaktovat poskytovatele jako cíl změny, pokud byla sada definována pomocí definičního dotazu v modelu, ale není k dispozici žádná funkce pro odpovídající operaci úprav.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="a3c7c-120">Poskytovatelé nemusí být schopni podporovat takový scénář (například není).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>

<span data-ttu-id="a3c7c-121">DbInsertCommandTree představuje operaci vložení jednoho řádku vyjádřenou jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

<span data-ttu-id="a3c7c-122">DbUpdateCommandTree představuje operaci aktualizace s jedním řádkem, která je vyjádřena jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>

<span data-ttu-id="a3c7c-123">DbDeleteCommandTree představuje operaci odstranění jednoho řádku vyjádřenou jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>

### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="a3c7c-124">Omezení vlastností stromu příkazů pro úpravy</span><span class="sxs-lookup"><span data-stu-id="a3c7c-124">Restrictions on Modification Command Tree Properties</span></span>

<span data-ttu-id="a3c7c-125">Následující informace a omezení se vztahují na vlastnosti stromu příkazů pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-125">The following information and restrictions apply to the modification command tree properties.</span></span>

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="a3c7c-126">Vracení v DbInsertCommandTree a DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="a3c7c-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="a3c7c-127">Pokud hodnota, která není null, vrátí, že příkaz vrátí čtecí modul.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="a3c7c-128">V opačném případě by příkaz měl vracet skalární hodnotu určující počet ovlivněných řádků (vloženo nebo aktualizováno).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>

<span data-ttu-id="a3c7c-129">Návratová hodnota určuje projekci výsledků, které se mají vrátit na základě vloženého nebo aktualizovaného řádku.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="a3c7c-130">Může být pouze typu DbNewInstanceExpression představující řádek, přičemž každý z jeho argumentů je DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="a3c7c-131">Vlastnosti reprezentované DbPropertyExpressions použitou ve vlastnosti vracející se vždy ukládají vygenerované nebo počítané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="a3c7c-132">V DbInsertCommandTree není vrácení hodnoty null, pokud alespoň jedna vlastnost tabulky, do které je řádek vkládán, je zadána jako vygenerované nebo počítané úložiště (označeno jako StoreGeneratedPattern. identity nebo StoreGeneratedPattern. vypočítané ve SSDL).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="a3c7c-133">V DbUpdateCommandTrees není vrácení hodnoty null, pokud alespoň jedna vlastnost tabulky, ve které je řádek aktualizován, je zadána jako vypočtené úložiště (označeno jako StoreGeneratedPattern. vypočítané ve SSDL).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="a3c7c-134">SetClauses v DbInsertCommandTree a DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="a3c7c-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="a3c7c-135">SetClauses určuje seznam klauzulí INSERT nebo Update set, které definují operaci INSERT nebo Update.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>

```
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.
```

<span data-ttu-id="a3c7c-136">Vlastnost určuje vlastnost, která má být aktualizována.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="a3c7c-137">Je vždy DbPropertyExpression prostřednictvím DbVariableReferenceExpression, který představuje odkaz na cíl odpovídajícího DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

<span data-ttu-id="a3c7c-138">Hodnota určuje novou hodnotu, se kterou chcete vlastnost aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="a3c7c-139">Je to buď typ DbConstantExpression nebo DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="a3c7c-140">Predikát v DbUpdateCommandTree a DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="a3c7c-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>

<span data-ttu-id="a3c7c-141">Predikát určuje predikát použitý k určení, které členy cílové kolekce by měly být aktualizovány nebo smazány.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="a3c7c-142">Jedná se o strom výrazu sestavený z následující podmnožiny DbExpressions:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-142">It is an expression tree built of the following subset of DbExpressions:</span></span>

- <span data-ttu-id="a3c7c-143">Objekt DbComparisonExpression je rovno, s pravou podřízenou položkou DbPropertyExpression tak, jak je omezená, a levou podřízenou DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExpression as restricted below and the left child a DbConstantExpression.</span></span>

- <span data-ttu-id="a3c7c-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="a3c7c-144">DbConstantExpression</span></span>

- <span data-ttu-id="a3c7c-145">DbIsNullExpression přes DbPropertyExpression na omezenou hodnotu</span><span class="sxs-lookup"><span data-stu-id="a3c7c-145">DbIsNullExpression over a DbPropertyExpression as restricted below</span></span>

- <span data-ttu-id="a3c7c-146">DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

- <span data-ttu-id="a3c7c-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="a3c7c-147">DbAndExpression</span></span>

- <span data-ttu-id="a3c7c-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="a3c7c-148">DbNotExpression</span></span>

- <span data-ttu-id="a3c7c-149">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="a3c7c-149">DbOrExpression</span></span>

## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="a3c7c-150">Úprava generování SQL ve zprostředkovateli vzorků</span><span class="sxs-lookup"><span data-stu-id="a3c7c-150">Modification SQL Generation in the Sample Provider</span></span>

<span data-ttu-id="a3c7c-151">[Poskytovatel ukázkového Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje komponenty zprostředkovatelů dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3c7c-151">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="a3c7c-152">Cílí na databázi SQL Server 2005 a implementuje se jako obálka na úrovni System. data. SqlClient ADO.NET 2,0 Zprostředkovatel dat.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>

<span data-ttu-id="a3c7c-153">Modul úprav SQL pro generování ukázkového poskytovatele (umístěný v souboru SQL Generation\DmlSqlGenerator.cs) přebírá vstupní DbModificationCommandTree a vytvoří jediný příkaz SQL, který je možná následován příkazem SELECT, který vrátí čtenář, pokud je určený parametrem DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="a3c7c-154">Všimněte si, že tvar generovaných příkazů je ovlivněn cílovou SQL Server databází.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>

### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="a3c7c-155">Pomocné třídy: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="a3c7c-155">Helper Classes: ExpressionTranslator</span></span>

<span data-ttu-id="a3c7c-156">ExpressionTranslator slouží jako společný odlehčený překladatel pro všechny vlastnosti stromu příkazů pro změnu typu DbExpression.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="a3c7c-157">Podporuje převod pouze typů výrazů, pro které jsou vlastnosti stromu příkazů změny omezené a jsou sestaveny s konkrétními omezeními.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>

<span data-ttu-id="a3c7c-158">Následující informace jsou popsány v tématu návštěvy specifických typů výrazů (uzly s triviálními překlady jsou vynechány).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>

### <a name="dbcomparisonexpression"></a><span data-ttu-id="a3c7c-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="a3c7c-159">DbComparisonExpression</span></span>

<span data-ttu-id="a3c7c-160">Když je ExpressionTranslator vytvořen pomocí preserveMemberValues = true a pokud je konstanta pravého DbConstantExpression (namísto DbNullExpression), přidružuje levý operand (DbPropertyExpressions) k tomuto DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="a3c7c-161">Který se používá v případě, že je nutné vygenerovat návratový příkaz SELECT pro identifikaci ovlivněného řádku.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>

### <a name="dbconstantexpression"></a><span data-ttu-id="a3c7c-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="a3c7c-162">DbConstantExpression</span></span>

<span data-ttu-id="a3c7c-163">Pro každou navštívenou konstantu je vytvořen parametr.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-163">For each visited constant a parameter is created.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="a3c7c-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="a3c7c-164">DbPropertyExpression</span></span>

<span data-ttu-id="a3c7c-165">Vzhledem k tomu, že instance DbPropertyExpression vždy představuje vstupní tabulku, pokud generace nevytvořila alias (ke kterému dochází pouze ve scénářích aktualizace při použití proměnné tabulky), není pro vstup nutné zadat žádný alias. překlad je ve výchozím nastavení název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>

## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="a3c7c-166">Generování příkazu INSERT SQL</span><span class="sxs-lookup"><span data-stu-id="a3c7c-166">Generating an Insert SQL Command</span></span>

<span data-ttu-id="a3c7c-167">V případě daného DbInsertCommandTree ve zprostředkovateli ukázky se za generovaným příkazem INSERT používá jedna z následujících dvou šablon pro vložení.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>

<span data-ttu-id="a3c7c-168">První šablona obsahuje příkaz pro vložení hodnot v seznamu SetClauses a příkaz SELECT, který vrátí vlastnosti zadané ve vlastnosti vracející vloženého řádku, pokud vlastnost vracející nebyla null.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="a3c7c-169">Element predikátu "\@ @ROWCOUNT > 0" má hodnotu true, pokud byl řádek vložen.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-169">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="a3c7c-170">Element predikátu "SCOPE_IDENTITY členi = klíč hodnota &#124; SCOPE_IDENTITY ()" převezme tvar "členi = ()" pouze v případě, že je klíčovým členem klíč generovaný úložištěm, protože SCOPE_IDENTITY () vrátí hodnotu poslední identity vloženou do identity ( sloupec generovaný úložištěm.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="a3c7c-171">Druhá šablona je potřebná v případě, že vložení určuje vložení řádku, ve kterém je primární klíč uložen, ale není typu Integer, a proto jej nelze použít s SCOPE_IDENTITY ()).</span><span class="sxs-lookup"><span data-stu-id="a3c7c-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="a3c7c-172">Používá se také v případě, že je k dispozici složený klíč generovaný úložištěm.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-172">It is also used if there is a compound store-generated key.</span></span>

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

<span data-ttu-id="a3c7c-173">Následuje příklad, který používá model, který je součástí poskytovatele ukázek.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="a3c7c-174">Vygeneruje příkaz INSERT z DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-174">It generates an insert command from a DbInsertCommandTree.</span></span>

<span data-ttu-id="a3c7c-175">Následující kód vloží kategorii:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-175">The following code inserts a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="a3c7c-176">Tento kód vytvoří následující strom příkazů, který je předán poskytovateli:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-176">This code produces the following command tree, which is passed to the provider:</span></span>

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

<span data-ttu-id="a3c7c-177">Příkaz Store, který generuje vzorový poskytovatel, je následující příkaz SQL:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-177">The store command that the sample provider produces is the following SQL statement:</span></span>

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a><span data-ttu-id="a3c7c-178">Generování příkazu Update SQL</span><span class="sxs-lookup"><span data-stu-id="a3c7c-178">Generating an Update SQL Command</span></span>

<span data-ttu-id="a3c7c-179">Pro daný DbUpdateCommandTree je vygenerovaný příkaz Update založen na následující šabloně:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="a3c7c-180">Klauzule SET má nafalešnou klauzuli set (@i = 0), pouze pokud nejsou zadány žádné klauzule SET.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="a3c7c-181">K tomu je potřeba zajistit, aby se přepočítaly všechny počítané sloupce v úložišti.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-181">This is to ensure that any store-computed columns are recomputed.</span></span>

<span data-ttu-id="a3c7c-182">Pouze v případě, že návratová vlastnost nemá hodnotu null, je vygenerován příkaz SELECT, který vrátí vlastnosti zadané ve vlastnosti vráceno.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>

<span data-ttu-id="a3c7c-183">Následující příklad používá model, který je součástí poskytovatele Sample k vygenerování aktualizačního příkazu.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>

<span data-ttu-id="a3c7c-184">Následující kód uživatele aktualizuje kategorii:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-184">The following user code updates a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="a3c7c-185">Tento uživatelský kód vytvoří následující strom příkazů, který se předává poskytovateli:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-185">This user code produces the following command tree, which is passed to the provider:</span></span>

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

<span data-ttu-id="a3c7c-186">Ukázkový poskytovatel vytvoří následující příkaz úložiště:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-186">The sample provider produces the following store command:</span></span>

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="a3c7c-187">Generování příkazu Delete SQL</span><span class="sxs-lookup"><span data-stu-id="a3c7c-187">Generating a Delete SQL Command</span></span>

<span data-ttu-id="a3c7c-188">Pro daný DbDeleteCommandTree je vygenerovaný příkaz DELETE založen na následující šabloně:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

<span data-ttu-id="a3c7c-189">Následující příklad používá model, který je součástí poskytovatele Sample k vygenerování příkazu DELETE.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>

<span data-ttu-id="a3c7c-190">Následující kód uživatele odstraní kategorii:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-190">The following user code deletes a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="a3c7c-191">Tento uživatelský kód vytvoří následující strom příkazů, který je předán poskytovateli.</span><span class="sxs-lookup"><span data-stu-id="a3c7c-191">This user code produces the following command tree, which is passed to the provider.</span></span>

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

<span data-ttu-id="a3c7c-192">Následující příkaz pro uložení je vytvořen poskytovatelem ukázky:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-192">The following store command is produced by the sample provider:</span></span>

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a><span data-ttu-id="a3c7c-193">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3c7c-193">See also</span></span>

- [<span data-ttu-id="a3c7c-194">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a3c7c-194">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
