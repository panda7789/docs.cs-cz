---
title: Tvar stromu příkazů
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 8368354049a77a56a5aa54ab500619576f41b0dc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854260"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="d7010-102">Tvar stromu příkazů</span><span class="sxs-lookup"><span data-stu-id="d7010-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="d7010-103">Modul SQL Generation je zodpovědný za generování dotazu SQL specifického pro back-end založeného na daném vstupním výrazu příkazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="d7010-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="d7010-104">Tato část popisuje vlastnosti, vlastnosti a strukturu stromů příkazů dotazu.</span><span class="sxs-lookup"><span data-stu-id="d7010-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="d7010-105">Přehled stromů příkazů dotazů</span><span class="sxs-lookup"><span data-stu-id="d7010-105">Query Command Trees Overview</span></span>

<span data-ttu-id="d7010-106">Strom příkazů dotazu je reprezentace objektového modelu dotazu.</span><span class="sxs-lookup"><span data-stu-id="d7010-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="d7010-107">Stromy příkazů dotazu slouží dvěma účelům:</span><span class="sxs-lookup"><span data-stu-id="d7010-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="d7010-108">Pro vyjádření vstupního dotazu, který je určen pro Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d7010-108">To express an input query that is specified against the Entity Framework.</span></span>

- <span data-ttu-id="d7010-109">Aby bylo možné vyjádřit výstupní dotaz, který je dán poskytovateli, a popisuje dotaz na back-end.</span><span class="sxs-lookup"><span data-stu-id="d7010-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="d7010-110">Stromy příkazů dotazů podporují bohatší sémantiku než dotazy kompatibilní s SQL: 1999, včetně podpory pro práci s vnořenými kolekcemi a operacemi typu, jako je například kontrola, zda entita je určitého typu, nebo filtrování sad založených na typu.</span><span class="sxs-lookup"><span data-stu-id="d7010-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="d7010-111">Vlastnost DBQueryCommandTree. Query je kořenem stromu výrazu, který popisuje logiku dotazu.</span><span class="sxs-lookup"><span data-stu-id="d7010-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="d7010-112">Vlastnost DBQueryCommandTree. Parameters obsahuje seznam parametrů, které se používají v dotazu.</span><span class="sxs-lookup"><span data-stu-id="d7010-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="d7010-113">Strom výrazu se skládá z objektů DbExpression.</span><span class="sxs-lookup"><span data-stu-id="d7010-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="d7010-114">Objekt DbExpression představuje některé výpočty.</span><span class="sxs-lookup"><span data-stu-id="d7010-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="d7010-115">K dispozici Entity Framework je několik druhů výrazů pro vytváření výrazů dotazů, včetně konstant, proměnných, funkcí, konstruktorů a standardních relačních operátorů, jako je filtr a spojení.</span><span class="sxs-lookup"><span data-stu-id="d7010-115">Several kinds of expressions are provided by the Entity Framework for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="d7010-116">Každý objekt DbExpression má vlastnost ResultType, která představuje typ výsledku vytvořeného tímto výrazem.</span><span class="sxs-lookup"><span data-stu-id="d7010-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="d7010-117">Tento typ je vyjádřený jako TypeUsage.</span><span class="sxs-lookup"><span data-stu-id="d7010-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="d7010-118">Tvary stromu příkazů pro výstupní dotaz</span><span class="sxs-lookup"><span data-stu-id="d7010-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="d7010-119">Ve stromech příkazů pro výstupní dotazy se těsně reprezentují relační dotazy (SQL) a dodržují se mnohem přísnějších pravidel, než jsou ta, která se vztahují na stromy příkazů dotazů.</span><span class="sxs-lookup"><span data-stu-id="d7010-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="d7010-120">Obvykle obsahují konstrukce, které jsou snadno přeloženy do jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="d7010-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="d7010-121">Stromy vstupních příkazů jsou vyjádřeny na koncepčním modelu, který podporuje navigační vlastnosti, asociace mezi entitami a dědičnost.</span><span class="sxs-lookup"><span data-stu-id="d7010-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="d7010-122">Stromy příkazů výstupu jsou vyjádřeny na model úložiště.</span><span class="sxs-lookup"><span data-stu-id="d7010-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="d7010-123">Vstupní stromy příkazů umožňují projektovat vnořené kolekce, ale výstupní stromy příkazů ne.</span><span class="sxs-lookup"><span data-stu-id="d7010-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="d7010-124">Stromy příkazů pro výstupní dotazy jsou sestaveny pomocí podmnožiny dostupných objektů DbExpression a dokonce i některých výrazů v této podmnožině mají omezené využití.</span><span class="sxs-lookup"><span data-stu-id="d7010-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="d7010-125">Operace typu, jako je například kontrola, zda je daný výraz z konkrétního typu nebo sady filtrování založené na typu, nejsou přítomny ve stromových příkazech výstupu.</span><span class="sxs-lookup"><span data-stu-id="d7010-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="d7010-126">Ve stromových větvích příkazů jsou pro projekce použity pouze výrazy, které vracejí logické hodnoty, a pouze pro predikáty ve výrazech vyžadujících predikát, jako je filtr nebo příkaz Case.</span><span class="sxs-lookup"><span data-stu-id="d7010-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="d7010-127">Kořen stromů příkazů pro výstupní dotaz je objekt DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="d7010-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="d7010-128">Ve stromech příkazů pro výstupní dotazy nejsou k dispozici typy výrazů.</span><span class="sxs-lookup"><span data-stu-id="d7010-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="d7010-129">Následující typy výrazů nejsou platné ve stromu příkazů výstupního dotazu a nemusíte je zpracovávat poskytovateli:</span><span class="sxs-lookup"><span data-stu-id="d7010-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="d7010-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-130">DbDerefExpression</span></span>

- <span data-ttu-id="d7010-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="d7010-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="d7010-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-133">DbIsOfExpression</span></span>

- <span data-ttu-id="d7010-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="d7010-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-135">DbRefExpression</span></span>

- <span data-ttu-id="d7010-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="d7010-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="d7010-138">Omezení výrazů a poznámky</span><span class="sxs-lookup"><span data-stu-id="d7010-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="d7010-139">Mnoho výrazů lze použít pouze ve stromových strukturách příkazů pro výstup dotazování v omezeném počtu:</span><span class="sxs-lookup"><span data-stu-id="d7010-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="d7010-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-140">DbFunctionExpression</span></span>

<span data-ttu-id="d7010-141">Lze předat následující typy funkcí:</span><span class="sxs-lookup"><span data-stu-id="d7010-141">The following function types can be passed:</span></span>

- <span data-ttu-id="d7010-142">Kanonické funkce, které jsou rozpoznávány oborem názvů EDM.</span><span class="sxs-lookup"><span data-stu-id="d7010-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="d7010-143">Integrované funkce (úložiště), které jsou rozpoznávány BuiltInAttribute.</span><span class="sxs-lookup"><span data-stu-id="d7010-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="d7010-144">Uživatelsky definované funkce.</span><span class="sxs-lookup"><span data-stu-id="d7010-144">User-defined functions.</span></span>

<span data-ttu-id="d7010-145">Kanonické funkce (viz [kanonické funkce](./language-reference/canonical-functions.md) pro další informace) jsou určeny jako součást Entity Framework a poskytovatelé by měli poskytovat implementace pro kanonické funkce na základě těchto specifikací.</span><span class="sxs-lookup"><span data-stu-id="d7010-145">Canonical functions (see [Canonical Functions](./language-reference/canonical-functions.md) for more information) are specified as part of the Entity Framework, and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="d7010-146">Funkce úložiště jsou založeny na specifikacích v příslušném manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d7010-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="d7010-147">Uživatelsky definované funkce jsou založeny na specifikacích ve SSDL.</span><span class="sxs-lookup"><span data-stu-id="d7010-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="d7010-148">Také funkce s atributem NiladicFunction nemají žádné argumenty a měly by být přeloženy bez závorek na konci.</span><span class="sxs-lookup"><span data-stu-id="d7010-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="d7010-149">To znamená pro  *\<funkci*  *\<> místo funkce > ()* .</span><span class="sxs-lookup"><span data-stu-id="d7010-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="d7010-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="d7010-151">DbNewInstanceExpression může probíhat pouze v následujících dvou případech:</span><span class="sxs-lookup"><span data-stu-id="d7010-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="d7010-152">Jako vlastnost projekce DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="d7010-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="d7010-153">Při použití následujících omezení platí:</span><span class="sxs-lookup"><span data-stu-id="d7010-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="d7010-154">Výsledný typ musí být typ řádku.</span><span class="sxs-lookup"><span data-stu-id="d7010-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="d7010-155">Každý z jeho argumentů je výraz, který vytváří výsledek s primitivním typem.</span><span class="sxs-lookup"><span data-stu-id="d7010-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="d7010-156">Každý argument je typicky skalární výraz, jako je například PropertyExpression přes DbVariableReferenceExpression, vyvolání funkce nebo aritmetický výpočet DbPropertyExpressiony prostřednictvím DbVariableReferenceExpression nebo vyvolání funkce. .</span><span class="sxs-lookup"><span data-stu-id="d7010-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="d7010-157">Výraz reprezentující skalární poddotaz ale může také nastat v seznamu argumentů pro DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="d7010-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="d7010-158">Výraz reprezentující skalární poddotaz je strom výrazů, který představuje poddotaz, který vrací přesně jeden řádek a jeden sloupec primitivního typu s kořenem objektu DbElementExpression.</span><span class="sxs-lookup"><span data-stu-id="d7010-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="d7010-159">S typem vrácené kolekce, v takovém případě definuje novou kolekci výrazů poskytovaných jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="d7010-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="d7010-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="d7010-161">DbVariableReferenceExpression musí být podřízeným uzlem uzlu DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="d7010-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="d7010-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-162">DbGroupByExpression</span></span>

<span data-ttu-id="d7010-163">Vlastnost Aggregates třídy DbGroupAggregate může mít pouze elementy typu DbFunctionAggregate.</span><span class="sxs-lookup"><span data-stu-id="d7010-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="d7010-164">Neexistují žádné další agregované typy.</span><span class="sxs-lookup"><span data-stu-id="d7010-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="d7010-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-165">DbLimitExpression</span></span>

<span data-ttu-id="d7010-166">Omezení vlastnosti může být pouze DbConstantExpression nebo DbParameterReferenceExpression.</span><span class="sxs-lookup"><span data-stu-id="d7010-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="d7010-167">Vlastnost WithTies je také vždy false jako verze 3,5 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7010-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="d7010-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="d7010-168">DbScanExpression</span></span>

<span data-ttu-id="d7010-169">Při použití ve výstupních stromových příkazech představuje DbScanExpression efektivně kontrolu nad tabulkou, zobrazením nebo dotazem úložiště, reprezentovaným EntitySetBase:: Target.</span><span class="sxs-lookup"><span data-stu-id="d7010-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="d7010-170">Pokud vlastnost metadat "definující dotaz" cílového typu není null, představuje dotaz, který je k dispozici v dané vlastnosti metadat v konkrétním jazyku poskytovatele (nebo dialektu), jak je uvedeno v definici schématu úložiště.</span><span class="sxs-lookup"><span data-stu-id="d7010-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="d7010-171">V opačném případě cíl představuje tabulku nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="d7010-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="d7010-172">Jeho předpona schématu je buď ve vlastnosti metadata schématu, pokud není null, jinak je název kontejneru entity.</span><span class="sxs-lookup"><span data-stu-id="d7010-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="d7010-173">Název tabulky nebo zobrazení je buď vlastnost "Table" (metadata), pokud není null, jinak vlastnost Name základu sady entit.</span><span class="sxs-lookup"><span data-stu-id="d7010-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="d7010-174">Všechny tyto vlastnosti pocházejí z definice odpovídajícího objektu EntitySet v souboru definice schématu úložiště (SSDL).</span><span class="sxs-lookup"><span data-stu-id="d7010-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="d7010-175">Používání primitivních typů</span><span class="sxs-lookup"><span data-stu-id="d7010-175">Using Primitive Types</span></span>

<span data-ttu-id="d7010-176">Při odkazování primitivních typů ve výstupních stromových příkazech jsou obvykle odkazovány v primitivních typech koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="d7010-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="d7010-177">Pro určité výrazy ale poskytovatelé potřebují odpovídající primitivní typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="d7010-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="d7010-178">Příklady takových výrazů zahrnují DbCastExpression a případně DbNullExpression, pokud poskytovatel potřebuje přetypovat hodnotu null na odpovídající typ.</span><span class="sxs-lookup"><span data-stu-id="d7010-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="d7010-179">V těchto případech by poskytovatelé měli provést mapování na typ poskytovatele na základě primitivního typu a jeho omezujících vlastností.</span><span class="sxs-lookup"><span data-stu-id="d7010-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7010-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7010-180">See also</span></span>

- [<span data-ttu-id="d7010-181">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="d7010-181">SQL Generation</span></span>](sql-generation.md)
