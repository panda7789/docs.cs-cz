---
title: "Obrazec stromy příkazů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3311ac88355ac0d7214ec932719e1445757d9e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="ec11e-102">Obrazec stromy příkazů</span><span class="sxs-lookup"><span data-stu-id="ec11e-102">The Shape of the Command Trees</span></span>
<span data-ttu-id="ec11e-103">Modul generování SQL je zodpovědný za generování back-end konkrétní dotaz SQL na základě výrazu stromu příkaz daný vstupní dotaz.</span><span class="sxs-lookup"><span data-stu-id="ec11e-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="ec11e-104">Tato část popisuje vlastnosti, vlastnosti a struktura stromy příkazů dotazu.</span><span class="sxs-lookup"><span data-stu-id="ec11e-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>  
  
## <a name="query-command-trees-overview"></a><span data-ttu-id="ec11e-105">Přehled stromy příkaz dotazu</span><span class="sxs-lookup"><span data-stu-id="ec11e-105">Query Command Trees Overview</span></span>  
 <span data-ttu-id="ec11e-106">Dotaz stromu příkazů je reprezentaci objektu modelu dotazu.</span><span class="sxs-lookup"><span data-stu-id="ec11e-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="ec11e-107">Dotazů stromy příkazů mají dva účely:</span><span class="sxs-lookup"><span data-stu-id="ec11e-107">Query command trees serve two purposes:</span></span>  
  
-   <span data-ttu-id="ec11e-108">Vyjádřit vstupní dotaz, který je zadaný na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec11e-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="ec11e-109">Chcete-li express dotazu výstup, který je uveden na poskytovatele a popisuje dotazy na back-end.</span><span class="sxs-lookup"><span data-stu-id="ec11e-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>  
  
 <span data-ttu-id="ec11e-110">Dotaz příkaz podporu stromy bohatší sémantiku než SQL:1999 kompatibilní dotazů, včetně podpory pro práci s vnořené kolekce a typ operací, jako je kontrola, zda je entita určitého typu nebo filtrování sady založený na typu.</span><span class="sxs-lookup"><span data-stu-id="ec11e-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>  
  
 <span data-ttu-id="ec11e-111">Vlastnost DBQueryCommandTree.Query je kořenem strom výrazu, která popisuje logiku dotazu.</span><span class="sxs-lookup"><span data-stu-id="ec11e-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="ec11e-112">Vlastnost DBQueryCommandTree.Parameters obsahuje seznam parametrů, které se používají v dotazu.</span><span class="sxs-lookup"><span data-stu-id="ec11e-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="ec11e-113">Strom výrazu se skládá z objekty od objektu DbExpression.</span><span class="sxs-lookup"><span data-stu-id="ec11e-113">The expression tree is composed of DbExpression objects.</span></span>  
  
 <span data-ttu-id="ec11e-114">Objekt DbExpression představuje některé výpočty.</span><span class="sxs-lookup"><span data-stu-id="ec11e-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="ec11e-115">Několik druhů výrazy jsou poskytovány [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro sestavování výrazy dotazů, včetně konstanty, proměnné, funkce, konstruktory a standardní relační operátory jako filtr a připojení.</span><span class="sxs-lookup"><span data-stu-id="ec11e-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="ec11e-116">Každý objekt DbExpression má hodnotu ResultType vlastnost, která představuje typ výsledku vytvořeného tento výraz.</span><span class="sxs-lookup"><span data-stu-id="ec11e-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="ec11e-117">Tento typ je vyjádřen jako TypeUsage.</span><span class="sxs-lookup"><span data-stu-id="ec11e-117">This type is expressed as a TypeUsage.</span></span>  
  
## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="ec11e-118">Tvary strom příkazů výstup dotazu</span><span class="sxs-lookup"><span data-stu-id="ec11e-118">Shapes of the Output Query Command Tree</span></span>  
 <span data-ttu-id="ec11e-119">Stromy příkazů dotazu výstup úzce představují relační dotazy (SQL) a splňovat pravidla mnohem přísnější než ty, které platí pro dotazů stromy příkazů.</span><span class="sxs-lookup"><span data-stu-id="ec11e-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="ec11e-120">Obvykle obsahují konstrukce, které jsou snadno převedeny na SQL.</span><span class="sxs-lookup"><span data-stu-id="ec11e-120">They typically contain constructs that are easily translated to SQL.</span></span>  
  
 <span data-ttu-id="ec11e-121">Vstupní příkaz stromy jsou vyjádřeny proti konceptuální model, který podporuje navigační vlastnosti přidružení mezi entitami a dědičnost.</span><span class="sxs-lookup"><span data-stu-id="ec11e-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="ec11e-122">Výstup příkazu stromy jsou vyjádřeny pro model úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec11e-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="ec11e-123">Zadejte stromy příkazů umožňují projektu vnořené kolekce, ale nechcete stromy příkazů výstup.</span><span class="sxs-lookup"><span data-stu-id="ec11e-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>  
  
 <span data-ttu-id="ec11e-124">Stromy příkazů výstup dotazu jsou vytvořeny pomocí podmnožinu dostupných objektů DbExpression a i některé výrazy v tuto podmnožinu mají omezený využití.</span><span class="sxs-lookup"><span data-stu-id="ec11e-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>  
  
 <span data-ttu-id="ec11e-125">Typ operace, jako je kontrola, zda je daný výraz určitého typu nebo filtrování podle typu, nastaví se nenacházejí v výstup stromy příkazů.</span><span class="sxs-lookup"><span data-stu-id="ec11e-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>  
  
 <span data-ttu-id="ec11e-126">Ve výstupu příkazu stromy používají pouze výrazy, které vracejí logické hodnoty pro projekce a pouze pro predikáty ve výrazech nutnosti predikátu, jako je filtr nebo příkaz case.</span><span class="sxs-lookup"><span data-stu-id="ec11e-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>  
  
 <span data-ttu-id="ec11e-127">Kořenové stromy příkazů výstupu dotazu je objekt DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="ec11e-127">The root of an output query command trees is a DbProjectExpression object.</span></span>  
  
### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="ec11e-128">Typy výrazů není k dispozici v stromy příkazů výstup dotazu</span><span class="sxs-lookup"><span data-stu-id="ec11e-128">Expression Types Not Present in Output Query Command Trees</span></span>  
 <span data-ttu-id="ec11e-129">Následující typy výrazů nejsou platné ve stromu příkazů výstupu dotazu a není potřeba ji zpracovat zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="ec11e-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>  
  
 <span data-ttu-id="ec11e-130">Objekt DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-130">DbDerefExpression</span></span>  
  
 <span data-ttu-id="ec11e-131">Třída DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-131">DbEntityRefExpression</span></span>  
  
 <span data-ttu-id="ec11e-132">Třída DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-132">DbRefKeyExpression</span></span>  
  
 <span data-ttu-id="ec11e-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-133">DbIsOfExpression</span></span>  
  
 <span data-ttu-id="ec11e-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-134">DbOfTypeExpression</span></span>  
  
 <span data-ttu-id="ec11e-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-135">DbRefExpression</span></span>  
  
 <span data-ttu-id="ec11e-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-136">DbRelationshipNavigationExpression</span></span>  
  
 <span data-ttu-id="ec11e-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-137">DbTreatExpression</span></span>  
  
### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="ec11e-138">Výraz omezení a poznámky</span><span class="sxs-lookup"><span data-stu-id="ec11e-138">Expression Restrictions and Notes</span></span>  
 <span data-ttu-id="ec11e-139">Mnoho výrazů lze použít pouze s omezeným přístupem způsobem v stromy příkazů výstup dotazu:</span><span class="sxs-lookup"><span data-stu-id="ec11e-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>  
  
#### <a name="dbfunctionexpression"></a><span data-ttu-id="ec11e-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-140">DbFunctionExpression</span></span>  
 <span data-ttu-id="ec11e-141">Následující typy funkce se dá předat:</span><span class="sxs-lookup"><span data-stu-id="ec11e-141">The following function types can be passed:</span></span>  
  
-   <span data-ttu-id="ec11e-142">Kanonické funkce, které jsou rozpoznány podle oboru názvů Edm.</span><span class="sxs-lookup"><span data-stu-id="ec11e-142">Canonical functions that are recognized by the Edm namespace.</span></span>  
  
-   <span data-ttu-id="ec11e-143">Funkce integrované (úložiště), které rozpoznává BuiltInAttribute.</span><span class="sxs-lookup"><span data-stu-id="ec11e-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>  
  
-   <span data-ttu-id="ec11e-144">Uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="ec11e-144">User-defined functions.</span></span>  
  
 <span data-ttu-id="ec11e-145">Kanonické funkce (najdete v části [kanonické funkce](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) informace) jsou určené jako součást [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], a poskytovatelé měli zadat implementace pro kanonické funkce na základě těchto specifikací.</span><span class="sxs-lookup"><span data-stu-id="ec11e-145">Canonical functions (see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="ec11e-146">Funkce úložiště jsou založená na specifikacích v manifestu zprostředkovatele, odpovídající.</span><span class="sxs-lookup"><span data-stu-id="ec11e-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="ec11e-147">Uživatelem definované funkce jsou založená na specifikacích v SSDL.</span><span class="sxs-lookup"><span data-stu-id="ec11e-147">User defined functions are based on specifications in the SSDL.</span></span>  
  
 <span data-ttu-id="ec11e-148">Také funkce s atribut NiladicFunction nemají žádné argumenty a by měl přeložit bez závorek na konci.</span><span class="sxs-lookup"><span data-stu-id="ec11e-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="ec11e-149">To znamená, do  *\<%{FunctionName/ >* místo  *\<%{FunctionName/ > ()*.</span><span class="sxs-lookup"><span data-stu-id="ec11e-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>  
  
#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="ec11e-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-150">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="ec11e-151">DbNewInstanceExpression může dojít pouze v těchto dvou případů:</span><span class="sxs-lookup"><span data-stu-id="ec11e-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>  
  
-   <span data-ttu-id="ec11e-152">Jako vlastnost projekce DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="ec11e-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="ec11e-153">Pokud se používá jako takový platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="ec11e-153">When used as such the following restrictions apply:</span></span>  
  
    -   <span data-ttu-id="ec11e-154">Výsledný typ musí být typ řádku.</span><span class="sxs-lookup"><span data-stu-id="ec11e-154">The result type must be a row type.</span></span>  
  
    -   <span data-ttu-id="ec11e-155">Každá jeho argumentů je výraz, který vytvoří výsledek s primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="ec11e-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="ec11e-156">Obvykle je každý argument skalární výraz, jako je PropertyExpression přes DbVariableReferenceExpression, volání funkce nebo aritmetické výpočet DbPropertyExpression přes DbVariableReferenceExpression nebo volání funkce .</span><span class="sxs-lookup"><span data-stu-id="ec11e-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="ec11e-157">Výraz představující skalární poddotazu může také dojít v seznamu argumentů DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="ec11e-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="ec11e-158">Výraz, který reprezentuje skalární poddotazu je představující poddotaz, který vrátí přesně jeden řádek a jeden sloupec s kořenové objekt DbElementExperession primitivního typu strom výrazu</span><span class="sxs-lookup"><span data-stu-id="ec11e-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExperession object root</span></span>  
  
-   <span data-ttu-id="ec11e-159">S návratovým typem kolekce v takovém případě definuje novou kolekci výrazů zadané jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="ec11e-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>  
  
#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="ec11e-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-160">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="ec11e-161">DbVariableReferenceExpression musí být podřízenou DbPropertyExpression uzlu.</span><span class="sxs-lookup"><span data-stu-id="ec11e-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>  
  
#### <a name="dbgroupbyexpression"></a><span data-ttu-id="ec11e-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-162">DbGroupByExpression</span></span>  
 <span data-ttu-id="ec11e-163">Vlastnost agregací pro DbGroupByExpression může mít pouze elementy typu DbFunctionAggregate.</span><span class="sxs-lookup"><span data-stu-id="ec11e-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="ec11e-164">Nejsou žádné jiné agregované typy.</span><span class="sxs-lookup"><span data-stu-id="ec11e-164">There are no other aggregate types.</span></span>  
  
#### <a name="dblimitexpression"></a><span data-ttu-id="ec11e-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-165">DbLimitExpression</span></span>  
 <span data-ttu-id="ec11e-166">Vlastnost omezení lze pouze objekt DbConstantExpression nebo DbParameterReferenceExpression.</span><span class="sxs-lookup"><span data-stu-id="ec11e-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="ec11e-167">Také vlastnost WithTies je vždy false od verze rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="ec11e-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>  
  
#### <a name="dbscanexpression"></a><span data-ttu-id="ec11e-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="ec11e-168">DbScanExpression</span></span>  
 <span data-ttu-id="ec11e-169">Při použití ve výstupu příkazu stromy, DbScanExpression efektivně představuje kontrolu nad tabulky, zobrazení nebo dotaz úložiště, reprezentována EnitySetBase::Target.</span><span class="sxs-lookup"><span data-stu-id="ec11e-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EnitySetBase::Target.</span></span>  
  
 <span data-ttu-id="ec11e-170">Pokud vlastnost metadat "Definování dotaz" cíle jinou hodnotu než null, reprezentuje dotazu, text dotazu, pro který je součástí tuto vlastnost metadata v konkrétní jazyk poskytovatele (nebo dialektu) jako zadaný v definici schématu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec11e-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>  
  
 <span data-ttu-id="ec11e-171">Cíl, jinak hodnota představuje tabulku nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ec11e-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="ec11e-172">Předponu jeho schématu je buď ve vlastnosti metadat "Schématu", pokud nejsou null, jinak je název kontejneru entit.</span><span class="sxs-lookup"><span data-stu-id="ec11e-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="ec11e-173">Název tabulky nebo zobrazení je buď vlastnost metadat "Tabulka", pokud nejsou null, jinak hodnota nastavený základní vlastnost název entity.</span><span class="sxs-lookup"><span data-stu-id="ec11e-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>  
  
 <span data-ttu-id="ec11e-174">Tyto vlastnosti pocházejí z definice odpovídající EntitySet v souboru definice schéma úložiště (SSDL).</span><span class="sxs-lookup"><span data-stu-id="ec11e-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>  
  
### <a name="using-primitive-types"></a><span data-ttu-id="ec11e-175">Pomocí primitivní typy</span><span class="sxs-lookup"><span data-stu-id="ec11e-175">Using Primitive Types</span></span>  
 <span data-ttu-id="ec11e-176">Když jsou ve výstupu příkazu stromech primitivní typy, jsou obvykle odkazovat v primitivních typech konceptuální model.</span><span class="sxs-lookup"><span data-stu-id="ec11e-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="ec11e-177">Pro určité výrazy potřebovat zprostředkovatelé primitivní typ odpovídající úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec11e-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="ec11e-178">Tyto příklady výrazů DbCastExpression a případně DbNullExpression, pokud je potřeba převést hodnotu null na odpovídající typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="ec11e-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="ec11e-179">V těchto případech by měl zprostředkovatelé udělat mapování, aby na základě typu primitivní typ a jeho omezující vlastnosti typu poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="ec11e-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec11e-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec11e-180">See Also</span></span>  
 [<span data-ttu-id="ec11e-181">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="ec11e-181">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
