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
# <a name="modification-sql-generation"></a><span data-ttu-id="71854-102">Generování SQL úpravy</span><span class="sxs-lookup"><span data-stu-id="71854-102">Modification SQL Generation</span></span>
<span data-ttu-id="71854-103">Tato část popisuje, jak vyvíjet modul úpravy SQL generování pro vaše (SQL:1999 – databáze kompatibilní) zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="71854-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="71854-104">Tento modul je zodpovědná za překladu stromu příkazů změny do příslušné příkazy SQL INSERT, UPDATE nebo DELETE.</span><span class="sxs-lookup"><span data-stu-id="71854-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="71854-105">Informace o generování SQL pro příkazy select najdete v tématu [generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="71854-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="71854-106">Přehled stromy příkazů změny</span><span class="sxs-lookup"><span data-stu-id="71854-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="71854-107">Modul úpravy SQL generování generuje založené na daný vstupní DbModificationCommandTree úpravy specifické pro databáze SQL příkazy.</span><span class="sxs-lookup"><span data-stu-id="71854-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="71854-108">DbModificationCommandTree je reprezentaci objektu modelu změny operace DML (typu vložení, aktualizaci nebo operace odstranění), která dědí z DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="71854-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="71854-109">Existují tři implementace DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="71854-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="71854-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="71854-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="71854-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="71854-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="71854-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="71854-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="71854-113">DbModificationCommandTree a jeho implementace, které vznikají pomocí funkcí [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vždy představují jeden řádek operaci.</span><span class="sxs-lookup"><span data-stu-id="71854-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="71854-114">Tato část popisuje tyto typy s jejich omezení v rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="71854-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="71854-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="71854-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="71854-116">DbModificationCommandTree má vlastnost Target, která představuje cíl nastavit pro modifikační operaci.</span><span class="sxs-lookup"><span data-stu-id="71854-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="71854-117">Vlastnost výrazu cílové složky, která definuje vstupní sadě je vždy DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="71854-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="71854-118">DbScanExpression může představovat buď tabulku nebo zobrazení, nebo sadu dat definované pomocí dotazu Pokud je vlastnost metadat "Definování dotaz" jeho cíle nesmí být nulová.</span><span class="sxs-lookup"><span data-stu-id="71854-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="71854-119">DbScanExpression, který představuje dotaz mohl pouze dosáhnout poskytovatele jako cíl změny pokud sada byl definován pomocí definující dotazu v modelu, ale žádná funkce byla poskytnuta pro odpovídající modifikační operaci.</span><span class="sxs-lookup"><span data-stu-id="71854-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="71854-120">Zprostředkovatelé nemusí být schopné podporovat takové situaci (SqlClient, například nemá).</span><span class="sxs-lookup"><span data-stu-id="71854-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="71854-121">DbInsertCommandTree představuje operace insert jeden řádek, vyjádřené jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="71854-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="71854-122">DbUpdateCommandTree představuje operaci aktualizace jednoho řádku vyjádřené jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="71854-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="71854-123">DbDeleteCommandTree představuje operaci odstranění jednoho řádku vyjádřené jako strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="71854-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="71854-124">Omezení pro úpravu příkaz stromu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="71854-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="71854-125">Následující informace a omezení platí pro vlastnosti úpravy příkazu stromu.</span><span class="sxs-lookup"><span data-stu-id="71854-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="71854-126">Vrácení v DbInsertCommandTree a DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="71854-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="71854-127">Když jinou hodnotu než null, Returning označuje, že příkaz vrátí čtečka čipových karet.</span><span class="sxs-lookup"><span data-stu-id="71854-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="71854-128">Příkaz, jinak by měl vrátit skalární hodnotu, která určuje počet ovlivněných řádků (Vložit nebo aktualizovat).</span><span class="sxs-lookup"><span data-stu-id="71854-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="71854-129">Hodnota Returning určuje projekci výsledků vrácených základě na vložené nebo aktualizované řádek.</span><span class="sxs-lookup"><span data-stu-id="71854-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="71854-130">Je možné ho pouze typu představující řádek, se každý z jeho argumenty DbPropertyExpression příliš DbVariableReferenceExpression, představující odkaz na cíl odpovídající DbModificationCommandTree DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="71854-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="71854-131">Vlastnosti reprezentována DbPropertyExpressions použít ve vlastnosti Returning jsou vždy úložiště vygeneruje nebo počítaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="71854-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="71854-132">V DbInsertCommandTree Returning není null při alespoň jednu vlastnost tabulky, ve kterém bude vložen řádku je zadán jako úložiště vygeneruje nebo počítaných (označena jako StoreGeneratedPattern.Identity nebo StoreGeneratedPattern.Computed v ssdl).</span><span class="sxs-lookup"><span data-stu-id="71854-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="71854-133">V DbUpdateCommandTrees, Returning není null. Pokud je zadán parametr alespoň jednu vlastnost tabulky, ve kterém se právě aktualizuje řádek jako úložiště počítaný (označena jako StoreGeneratedPattern.Computed v ssdl).</span><span class="sxs-lookup"><span data-stu-id="71854-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="71854-134">SetClauses v DbInsertCommandTree a DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="71854-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="71854-135">SetClauses určuje seznam insert nebo update nastavit klauzule, které definují operace insert nebo update.</span><span class="sxs-lookup"><span data-stu-id="71854-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="71854-136">Vlastnost určuje vlastnost, která by měly být aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="71854-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="71854-137">Vždycky je DbPropertyExpression přes DbVariableReferenceExpression, která představuje odkaz na cíl odpovídající DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="71854-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="71854-138">Hodnota určuje, ke které má být aktualizujte vlastnost novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71854-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="71854-139">Je buď typu DbConstantExpression nebo DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="71854-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="71854-140">V DbUpdateCommandTree a DbDeleteCommandTree predikátem</span><span class="sxs-lookup"><span data-stu-id="71854-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="71854-141">Predikát určuje predikát umožňuje určit, které členy cílové kolekce by měl aktualizovat ani odstranit.</span><span class="sxs-lookup"><span data-stu-id="71854-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="71854-142">Je sestaven z následující podmnožinu DbExpressions strom výrazu:</span><span class="sxs-lookup"><span data-stu-id="71854-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="71854-143">Objekt DbComparisonExpression druhu rovná s správné podřízené se DbPropertyExression s omezeným přístupem níže a levé podřízený objekt DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="71854-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="71854-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="71854-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="71854-145">Objekt DbIsNullExpression přes DbPropertyExpresison s omezeným přístupem níže</span><span class="sxs-lookup"><span data-stu-id="71854-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="71854-146">DbPropertyExpression přes DbVariableReferenceExpression, představující odkaz na cíl odpovídající DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="71854-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="71854-147">Objekt DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="71854-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="71854-148">Třída DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="71854-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="71854-149">Třída DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="71854-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="71854-150">Generování SQL změny ve zprostředkovateli ukázka</span><span class="sxs-lookup"><span data-stu-id="71854-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="71854-151">[Zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) ukazuje součástí zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71854-151">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="71854-152">Jeho cílem databáze systému SQL Server 2005 a je implementovaný jako obálku nad System.Data.SqlClient ADO.NET 2.0 dat zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="71854-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="71854-153">Modul úpravy SQL generování ukázkového poskytovatele (nachází se v souboru SQL Generation\DmlSqlGenerator.cs) trvá vstupní DbModificationCommandTree a vytvoří jeden úprav příkazu SQL pravděpodobně následovaný příkazem SELECT vrátit čtečka, pokud určeného DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="71854-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="71854-154">Všimněte si, že tvar příkazy generované ovlivňuje cílová databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="71854-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="71854-155">Pomocné třídy: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="71854-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="71854-156">ExpressionTranslator slouží jako běžné lightweight překladač pro všechny úpravy příkaz stromu vlastnosti typu DbExpression.</span><span class="sxs-lookup"><span data-stu-id="71854-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="71854-157">Podporuje překlad pouze typy výrazů na které jsou omezené vlastnosti strom příkazů úpravy a je integrovaný s konkrétní omezení na paměti.</span><span class="sxs-lookup"><span data-stu-id="71854-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="71854-158">Tyto informace se věnuje návštěvou typy konkrétní výrazů (uzly s trivial překlady byly vynechány).</span><span class="sxs-lookup"><span data-stu-id="71854-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="71854-159">Objekt DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="71854-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="71854-160">Pokud je ExpressionTranslator vytvořený pomocí preserveMemberValues = true, a když konstanta vpravo DbConstantExpression (namísto DbNullExpression) se přidruží levý operand (DbPropertyExpressions), DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="71854-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="71854-161">Který se používá, pokud je třeba vytvořit pro identifikaci příslušného řádku vyberte příkaz return.</span><span class="sxs-lookup"><span data-stu-id="71854-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="71854-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="71854-162">DbConstantExpression</span></span>  
 <span data-ttu-id="71854-163">Pro každý navštívené konstanta je vytvořený parametr.</span><span class="sxs-lookup"><span data-stu-id="71854-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="71854-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="71854-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="71854-165">Vzhledem k tomu, že Instance DbPropertyExpression vždy představuje vstupní tabulky, pokud generování vytvořil alias (která se dělá jenom ve scénářích aktualizace Pokud se používá proměnnou tabulky), je třeba zadat pro vstup; žádný alias překlad výchozí název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="71854-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="71854-166">Generování příkazu Insert SQL</span><span class="sxs-lookup"><span data-stu-id="71854-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="71854-167">Pro danou DbInsertCommandTree ve zprostředkovateli ukázkové následuje příkaz insert generovaného jednu z níže dvě vložení šablon.</span><span class="sxs-lookup"><span data-stu-id="71854-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="71854-168">První šablonu, kterou má příkaz k provedení vložení, na základě hodnot v seznamu SetClauses a vyberte příkaz vrátit vlastnosti zadaná ve vlastnosti Returning vloženého řádku, pokud vlastnost Returning nebyla null.</span><span class="sxs-lookup"><span data-stu-id="71854-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="71854-169">Element predikátem "@@ROWCOUNT > 0" je hodnota true, pokud byl vložit řádek.</span><span class="sxs-lookup"><span data-stu-id="71854-169">The predicate element "@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="71854-170">Element predikátem "keyMemberI = keyValueI &#124; scope_identity() "trvá tvar" keyMemberI = scope_identity() "pouze v případě keyMemeberI je klíč generovaný úložištěm, protože scope_identity() vrátí poslední hodnotu identity, které jsou vloženy do sloupce identity (generovaný úložištěm).</span><span class="sxs-lookup"><span data-stu-id="71854-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="71854-171">Druhá šablona je nutný v případě, že úlohy insert určuje vložíte řádek kde primární klíč se generuje úložiště, ale není typu integer a proto jej nelze použít s scope_identity()).</span><span class="sxs-lookup"><span data-stu-id="71854-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="71854-172">Používá se také při složený klíč generovaný úložištěm.</span><span class="sxs-lookup"><span data-stu-id="71854-172">It is also used if there is a compound store-generated key.</span></span>  
  
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
  
 <span data-ttu-id="71854-173">Následuje příklad, který používá model, který je součástí ukázkového zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="71854-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="71854-174">Příkaz insert vygeneruje z DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="71854-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="71854-175">Následující kód vloží do kategorií:</span><span class="sxs-lookup"><span data-stu-id="71854-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="71854-176">Tento kód vytvoří následující strom příkazů, které je předána zprostředkovateli:</span><span class="sxs-lookup"><span data-stu-id="71854-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="71854-177">Příkaz úložiště, který vytváří ukázkového zprostředkovatele je následující příkaz SQL:</span><span class="sxs-lookup"><span data-stu-id="71854-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="71854-178">Generování příkazu SQL pro aktualizaci</span><span class="sxs-lookup"><span data-stu-id="71854-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="71854-179">Pro danou DbUpdateCommandTree příkaz generovaného aktualizace podle následující šablony:</span><span class="sxs-lookup"><span data-stu-id="71854-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="71854-180">Klauzuli set obsahuje klauzuli falešných set ("@i = 0") pouze v případě, že nejsou zadány žádné klauzule set.</span><span class="sxs-lookup"><span data-stu-id="71854-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="71854-181">To je potřeba zajistit, že žádné úložiště vypočtená jsou přepočítávány sloupce.</span><span class="sxs-lookup"><span data-stu-id="71854-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="71854-182">Pouze v případě, že vlastnost Returning není null, se k vrácení vlastností zadaná ve vlastnosti Returning vygeneruje příkazu select.</span><span class="sxs-lookup"><span data-stu-id="71854-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="71854-183">Následující příklad používá model, který je součástí zprostředkovatele ukázka ke generování příkazu pro aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="71854-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="71854-184">Následující kód uživatele aktualizace kategorie:</span><span class="sxs-lookup"><span data-stu-id="71854-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="71854-185">Tento kód uživatele vytváří následující strom příkazů, které je předána zprostředkovateli:</span><span class="sxs-lookup"><span data-stu-id="71854-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="71854-186">Ukázka zprostředkovatele vytváří následující příkaz úložiště:</span><span class="sxs-lookup"><span data-stu-id="71854-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="71854-187">Generování příkazu SQL odstranění</span><span class="sxs-lookup"><span data-stu-id="71854-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="71854-188">Pro danou DbDeleteCommandTree vygenerovaný příkaz DELETE podle následující šablony:</span><span class="sxs-lookup"><span data-stu-id="71854-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="71854-189">Následující příklad používá model, který je součástí zprostředkovatele ukázka ke generování příkaz delete.</span><span class="sxs-lookup"><span data-stu-id="71854-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="71854-190">Následující kód uživatel odstraní kategorie:</span><span class="sxs-lookup"><span data-stu-id="71854-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="71854-191">Tento kód uživatel vytvoří následující strom příkazů, které je předána zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="71854-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
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
  
 <span data-ttu-id="71854-192">Následující příkaz úložiště je produkovaný ukázkového zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="71854-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="71854-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="71854-193">See Also</span></span>  
 [<span data-ttu-id="71854-194">Zápis poskytovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="71854-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
