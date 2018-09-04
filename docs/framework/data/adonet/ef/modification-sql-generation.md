---
title: Úpravy generování SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560753"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="7549f-102">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="7549f-102">Modification SQL Generation</span></span>
<span data-ttu-id="7549f-103">Tato část popisuje, jak vyvinout úprav modulu generování SQL pro vaše (SQL:1999 – databáze kompatibilní) zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7549f-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="7549f-104">Tento modul je zodpovědná za překládá úpravy stromu příkazů na příslušné příkazy SQL INSERT, UPDATE nebo DELETE.</span><span class="sxs-lookup"><span data-stu-id="7549f-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="7549f-105">Informace o generování SQL pro příkazy select, naleznete v tématu [generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="7549f-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="7549f-106">Přehled úprav stromů příkazů</span><span class="sxs-lookup"><span data-stu-id="7549f-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="7549f-107">Modul generování SQL úpravy vygeneruje úpravu konkrétních databází SQL příkazy podle daného vstupního DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="7549f-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="7549f-108">Objektová reprezentace modelu úprav operace DML (vložení, aktualizace nebo odstranění), je DbModificationCommandTree dědění z DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="7549f-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="7549f-109">Existují tři implementace DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="7549f-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="7549f-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="7549f-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="7549f-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="7549f-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="7549f-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="7549f-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="7549f-113">DbModificationCommandTree a jeho implementace, které jsou vytvářeny [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vždycky reprezentuje operaci jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="7549f-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="7549f-114">Tato část popisuje tyto typy s jejich omezení v rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="7549f-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="7549f-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="7549f-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="7549f-116">DbModificationCommandTree má vlastnost Target, který představuje cíl pro operaci úpravy nastavit.</span><span class="sxs-lookup"><span data-stu-id="7549f-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="7549f-117">Vlastnost Expression cíle, která definuje vstupní sady je vždy DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="7549f-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="7549f-118">DbScanExpression může představovat tabulku nebo zobrazení nebo sady dat definované pomocí dotazu vlastnost metadat "Definice dotazu" jejím cílem je-li jinou hodnotu než null.</span><span class="sxs-lookup"><span data-stu-id="7549f-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="7549f-119">DbScanExpression, který představuje dotaz mohl pouze dosáhnout zprostředkovatele jako cíl změny pokud sada byl definován pomocí definování dotazů v modelu, ale byla zadána žádná funkce pro odpovídající operaci úprav.</span><span class="sxs-lookup"><span data-stu-id="7549f-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="7549f-120">Poskytovatelé nemusí být schopni poskytovat podporu takové situaci (SqlClient, například nemá).</span><span class="sxs-lookup"><span data-stu-id="7549f-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="7549f-121">DbInsertCommandTree představuje operaci insert jednoho řádku vyjádřené jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="7549f-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="7549f-122">DbUpdateCommandTree představuje operaci aktualizace jednoho řádku vyjádřené jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="7549f-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="7549f-123">DbDeleteCommandTree představuje operaci odstranění jednoho řádku vyjádřené jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="7549f-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="7549f-124">Omezení vlastnosti stromu příkazu Úpravy</span><span class="sxs-lookup"><span data-stu-id="7549f-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="7549f-125">Následující informace a omezení platí pro vlastnosti úpravy příkazu stromu.</span><span class="sxs-lookup"><span data-stu-id="7549f-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="7549f-126">Vrací DbInsertCommandTree a DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="7549f-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="7549f-127">Pokud není null, Returning označuje, že příkaz vrátí čtečku.</span><span class="sxs-lookup"><span data-stu-id="7549f-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="7549f-128">Příkaz v opačném případě by měl vrátit skalární hodnotu určující počet ovlivněných řádků (přidají nebo aktualizují).</span><span class="sxs-lookup"><span data-stu-id="7549f-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="7549f-129">Hodnota Returning specifikuje projekci výsledků, který se má vrátit na základě vloženého nebo aktualizovaný řádek.</span><span class="sxs-lookup"><span data-stu-id="7549f-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="7549f-130">Může být pouze typu představuje řádek, kde každý z jejích argumentů je DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="7549f-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="7549f-131">Vlastnosti reprezentované DbPropertyExpressions používá ve vlastnosti Returning jsou vždy úložiště vygeneruje nebo vypočítané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7549f-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="7549f-132">V DbInsertCommandTree Returning není null při alespoň jedné vlastnosti takové tabulky, ve kterém je vložen řádku je zadán jako úložiště vygeneruje nebo vypočítat (označené jako StoreGeneratedPattern.Identity nebo StoreGeneratedPattern.Computed v ssdl).</span><span class="sxs-lookup"><span data-stu-id="7549f-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="7549f-133">V DbUpdateCommandTrees, Returning není null při alespoň jedné vlastnosti takové tabulky, ve kterém se aktualizuje řádek je zadán jako úložiště vypočítat (označené jako StoreGeneratedPattern.Computed v ssdl).</span><span class="sxs-lookup"><span data-stu-id="7549f-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="7549f-134">SetClauses DbInsertCommandTree a DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="7549f-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="7549f-135">SetClauses určuje seznam insert nebo update nastavit klauzule, které definují operaci insert nebo update.</span><span class="sxs-lookup"><span data-stu-id="7549f-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="7549f-136">Vlastnost určuje vlastnost, která by se měla aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="7549f-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="7549f-137">Je vždy DbPropertyExpression nad DbVariableReferenceExpression, který představuje odkaz na cíl odpovídající DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="7549f-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="7549f-138">Hodnota určuje novou hodnotu, pomocí kterého se má aktualizovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7549f-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="7549f-139">Je buď typu DbConstantExpression nebo DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="7549f-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="7549f-140">Predikátu v DbUpdateCommandTree a DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="7549f-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="7549f-141">Predikát určuje predikát, který umožňuje určit, které členy cílové kolekce by měl aktualizovat ani odstranit.</span><span class="sxs-lookup"><span data-stu-id="7549f-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="7549f-142">Strom výrazů, které se skládají z následující dílčí DbExpressions je:</span><span class="sxs-lookup"><span data-stu-id="7549f-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="7549f-143">Objekt DbComparisonExpression druhu rovná se správné podřízené se DbPropertyExression s omezeným přístupem níže a levém podřízený objekt DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="7549f-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="7549f-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="7549f-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="7549f-145">Objekt DbIsNullExpression přes DbPropertyExpresison s omezeným přístupem níže</span><span class="sxs-lookup"><span data-stu-id="7549f-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="7549f-146">DbPropertyExpression přes DbVariableReferenceExpression představující odkaz na cíl odpovídající DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="7549f-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="7549f-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="7549f-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="7549f-148">Třída DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="7549f-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="7549f-149">Třída DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="7549f-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="7549f-150">Úpravy generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="7549f-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="7549f-151">[Ukázka zprostředkovatele Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) ukazuje součástí zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7549f-151">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="7549f-152">Je zaměřen na databázi systému SQL Server 2005 a je implementovaný jako obálka nad zprostředkovatele dat ADO.NET 2.0 System.Data.SqlClient.</span><span class="sxs-lookup"><span data-stu-id="7549f-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="7549f-153">Modul generování SQL úpravy ukázkového poskytovatele (umístěný v souboru SQL Generation\DmlSqlGenerator.cs) přijímá vstupní DbModificationCommandTree a vytvoří jeden úprav příkazu SQL pravděpodobně následovaný příkazem SELECT se vraťte Čtečka případného DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="7549f-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="7549f-154">Všimněte si, že tvar příkazy generované je ovlivněna cílová databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7549f-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="7549f-155">Pomocné třídy: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="7549f-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="7549f-156">ExpressionTranslator slouží jako běžné zjednodušené převaděč pro všechny úpravy příkaz stromu vlastnosti typu DbExpression.</span><span class="sxs-lookup"><span data-stu-id="7549f-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="7549f-157">Podporuje překlad pouze typy výrazů ke kterým jsou omezeny vlastnosti stromu příkazů úpravy a vytvořené s konkrétní omezení na paměti.</span><span class="sxs-lookup"><span data-stu-id="7549f-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="7549f-158">Následující informace popisují navštívit typy konkrétní výrazů (uzly s triviální překlady jsou vynechány).</span><span class="sxs-lookup"><span data-stu-id="7549f-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="7549f-159">Objekt DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="7549f-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="7549f-160">Když je vytvořený ExpressionTranslator pomocí preserveMemberValues = true, a když konstanty na pravé straně je objekt DbConstantExpression (namísto DbNullExpression), přiřadí levý operand (DbPropertyExpressions) s, který DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="7549f-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="7549f-161">Který se používá, pokud vratky příkazu Select je potřeba vygenerovat k identifikaci ovlivněných řádků.</span><span class="sxs-lookup"><span data-stu-id="7549f-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="7549f-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="7549f-162">DbConstantExpression</span></span>  
 <span data-ttu-id="7549f-163">Pro každý navštívených – konstanta se vytvoří parametr.</span><span class="sxs-lookup"><span data-stu-id="7549f-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="7549f-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="7549f-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="7549f-165">Vzhledem k tomu, že Instance DbPropertyExpression vždy představuje vstupní tabulky, není-li generování vytvořil alias (která situace nastane pouze ve scénářích aktualizace při se používá proměnnou tabulky), žádný alias musí být zadaná pro vstup; překlad výchozí název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7549f-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="7549f-166">Generování příkazu Insert SQL</span><span class="sxs-lookup"><span data-stu-id="7549f-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="7549f-167">Pro daný DbInsertCommandTree ve zprostředkovateli ukázek následuje příkazu insert generované některou ze šablon dvě vložit níže.</span><span class="sxs-lookup"><span data-stu-id="7549f-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="7549f-168">První šablona má příkaz provádět na základě hodnot v seznamu SetClauses insert a příkaz SELECT pro vrácení vlastnosti zadaná ve vlastnosti Returning vloženého řádku, pokud vlastnost Returning nebyl prázdný.</span><span class="sxs-lookup"><span data-stu-id="7549f-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="7549f-169">Element predikátu "\@ @ROWCOUNT > 0" je hodnota true, pokud byl vložen řádek.</span><span class="sxs-lookup"><span data-stu-id="7549f-169">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="7549f-170">Element predikátu "keyMemberI = keyValueI &#124; scope_identity()" má tvar "keyMemberI = scope_identity()" pouze v případě keyMemeberI je klíče generované úložištěm, protože scope_identity() vrátí poslední hodnotu identity, které jsou vloženy do identity ( sloupec generovaných úložištěm).</span><span class="sxs-lookup"><span data-stu-id="7549f-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="7549f-171">Druhá šablona je potřeba, je-li vložit určuje vložení řádku, kde primární klíč se generuje úložiště, ale není typu integer a proto jej nelze použít s scope_identity()).</span><span class="sxs-lookup"><span data-stu-id="7549f-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="7549f-172">Používá se také při složené klíče generované úložištěm.</span><span class="sxs-lookup"><span data-stu-id="7549f-172">It is also used if there is a compound store-generated key.</span></span>  
  
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
  
 <span data-ttu-id="7549f-173">Následuje příklad, který používá model, který je součástí ukázkového zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7549f-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="7549f-174">Generuje příkazu k vložení z DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="7549f-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="7549f-175">Následující kód vloží kategorii:</span><span class="sxs-lookup"><span data-stu-id="7549f-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="7549f-176">Tento kód vytvoří následující stromu příkazů, který se předá do zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="7549f-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="7549f-177">Příkaz úložiště, který vytváří zprostředkovateli ukázek je následující příkaz SQL:</span><span class="sxs-lookup"><span data-stu-id="7549f-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="7549f-178">Generování SQL příkazu k aktualizaci</span><span class="sxs-lookup"><span data-stu-id="7549f-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="7549f-179">Pro daný DbUpdateCommandTree příkazu generované aktualizace podle následující šablony:</span><span class="sxs-lookup"><span data-stu-id="7549f-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="7549f-180">Klauzule set je klauzule set falešné ("@i = 0") pouze v případě, že jsou zadány bez klauzule set.</span><span class="sxs-lookup"><span data-stu-id="7549f-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="7549f-181">Tím je zajištěno, že žádné úložiště počítané sloupce jsou přepočítány.</span><span class="sxs-lookup"><span data-stu-id="7549f-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="7549f-182">Pouze v případě, že vlastnost Returning není null, vyberte příkaz vygeneruje se vraťte se do vlastností zadaná ve vlastnosti Returning.</span><span class="sxs-lookup"><span data-stu-id="7549f-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="7549f-183">Následující příklad používá model, který je součástí ukázkového zprostředkovatele k vygenerování příkazu k aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="7549f-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="7549f-184">Následující kód uživatele aktualizuje kategorii:</span><span class="sxs-lookup"><span data-stu-id="7549f-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="7549f-185">Tento uživatelský kód vytvoří následující stromu příkazů, který se předá do zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="7549f-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="7549f-186">Ukázka zprostředkovatele vytvoří následující příkaz úložiště:</span><span class="sxs-lookup"><span data-stu-id="7549f-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="7549f-187">Generování SQL příkazu Delete</span><span class="sxs-lookup"><span data-stu-id="7549f-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="7549f-188">Pro daný DbDeleteCommandTree generované příkazem k odstranění podle následující šablony:</span><span class="sxs-lookup"><span data-stu-id="7549f-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="7549f-189">Následující příklad používá model, který je součástí ukázkového zprostředkovatele k vygenerování příkazu pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="7549f-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="7549f-190">Následující kód uživatele odstraní kategorie:</span><span class="sxs-lookup"><span data-stu-id="7549f-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="7549f-191">Tento uživatelský kód vytvoří následující stromu příkazů, která je předána zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="7549f-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
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
  
 <span data-ttu-id="7549f-192">Následující příkaz úložiště je vytvořen poskytovatelem vzorku:</span><span class="sxs-lookup"><span data-stu-id="7549f-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="7549f-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="7549f-193">See Also</span></span>  
 [<span data-ttu-id="7549f-194">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="7549f-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
