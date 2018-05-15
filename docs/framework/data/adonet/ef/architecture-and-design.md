---
title: Architektura a návrh
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: c2e8ff5f21a2941d75b21915552e6935a1423978
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="architecture-and-design"></a><span data-ttu-id="e373e-102">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="e373e-102">Architecture and Design</span></span>
<span data-ttu-id="e373e-103">Modul generování SQL v [ukázka zprostředkovatele](http://go.microsoft.com/fwlink/?LinkId=180616) je implementovaný jako návštěvníka na strom výrazu, který představuje strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="e373e-103">The SQL generation module in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="e373e-104">Generování probíhá v jednom průchodu přes strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="e373e-104">The generation is done in a single pass over the expression tree.</span></span>  
  
 <span data-ttu-id="e373e-105">Uzly stromu jsou zpracovávány zdola nahoru.</span><span class="sxs-lookup"><span data-stu-id="e373e-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="e373e-106">Nejprve se vytvářejí zprostředkující struktura: SqlSelectStatement nebo SqlBuilder, obě implementuje ISqlFragment.</span><span class="sxs-lookup"><span data-stu-id="e373e-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="e373e-107">V dalším kroku řetězec příkazu jazyka SQL se vytvářejí z této struktury.</span><span class="sxs-lookup"><span data-stu-id="e373e-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="e373e-108">Existují dva důvody pro zprostředkující strukturu:</span><span class="sxs-lookup"><span data-stu-id="e373e-108">There are two reasons for the intermediate structure:</span></span>  
  
-   <span data-ttu-id="e373e-109">Příkaz SELECT se naplní logicky, mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="e373e-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="e373e-110">Uzly, které jsou součástí klauzule FROM navštívené před uzly, které jsou součástí WHERE, GROUP BY a klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="e373e-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>  
  
-   <span data-ttu-id="e373e-111">Pokud chcete přejmenovat aliasy, musí identifikovat všechny používané aliasy pro zabrání se tím kolizím při přejmenování.</span><span class="sxs-lookup"><span data-stu-id="e373e-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="e373e-112">Symbol objekty odložení přejmenování volbám v SqlBuilder, lze použijte k reprezentaci sloupce, které jsou kandidáty pro přejmenování.</span><span class="sxs-lookup"><span data-stu-id="e373e-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>  
  
 <span data-ttu-id="e373e-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="e373e-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>  
  
 <span data-ttu-id="e373e-114">V první fázi, při návštěvě strom výrazu výrazy jsou seskupené do SqlSelectStatements, se sloučí spojení a aliasy spojení se sloučí.</span><span class="sxs-lookup"><span data-stu-id="e373e-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="e373e-115">V tomto průchodu Symbol objekty představují vstupní aliasy, které může být přejmenován nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="e373e-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>  
  
 <span data-ttu-id="e373e-116">Ve druhé fázi se při vytváření konkrétní řetězec jsou přejmenovány aliasy.</span><span class="sxs-lookup"><span data-stu-id="e373e-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>  
  
## <a name="data-structures"></a><span data-ttu-id="e373e-117">Datové struktury</span><span class="sxs-lookup"><span data-stu-id="e373e-117">Data Structures</span></span>  
 <span data-ttu-id="e373e-118">Tato část popisuje typy používané v [ukázka zprostředkovatele](http://go.microsoft.com/fwlink/?LinkId=180616) používané k vytvoření příkazu SQL.</span><span class="sxs-lookup"><span data-stu-id="e373e-118">This section discusses the types used in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) that you use to build a SQL statement.</span></span>  
  
### <a name="isqlfragment"></a><span data-ttu-id="e373e-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="e373e-119">ISqlFragment</span></span>  
 <span data-ttu-id="e373e-120">Tato část obsahuje třídy, které implementují rozhraní ISqlFragment, která má dva účely:</span><span class="sxs-lookup"><span data-stu-id="e373e-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>  
  
-   <span data-ttu-id="e373e-121">Běžné návratový typ pro všechny metody návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="e373e-121">A common return type for all the visitor methods.</span></span>  
  
-   <span data-ttu-id="e373e-122">Poskytuje metodu pro zápis konečné řetězec SQL.</span><span class="sxs-lookup"><span data-stu-id="e373e-122">Gives a method to write the final SQL string.</span></span>  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a><span data-ttu-id="e373e-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="e373e-123">SqlBuilder</span></span>  
 <span data-ttu-id="e373e-124">SqlBuilder je shromažďování zařízení pro konečné řetězec SQL, podobně jako StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="e373e-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="e373e-125">Skládá se z řetězců, které tvoří konečné SQL, společně s ISqlFragments, kterou můžete převést do řetězce.</span><span class="sxs-lookup"><span data-stu-id="e373e-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a><span data-ttu-id="e373e-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="e373e-126">SqlSelectStatement</span></span>  
 <span data-ttu-id="e373e-127">SqlSelectStatement představuje kanonický příkazu SQL SELECT tvaru vyberte..."</span><span class="sxs-lookup"><span data-stu-id="e373e-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="e373e-128">Z...</span><span class="sxs-lookup"><span data-stu-id="e373e-128">FROM  ..</span></span> <span data-ttu-id="e373e-129">KDE...</span><span class="sxs-lookup"><span data-stu-id="e373e-129">WHERE …</span></span> <span data-ttu-id="e373e-130">SESKUPIT PODLE...</span><span class="sxs-lookup"><span data-stu-id="e373e-130">GROUP BY …</span></span> <span data-ttu-id="e373e-131">ŘADIT PODLE".</span><span class="sxs-lookup"><span data-stu-id="e373e-131">ORDER BY".</span></span>  
  
 <span data-ttu-id="e373e-132">Každý z klauzule SQL je reprezentována StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="e373e-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="e373e-133">Kromě toho sleduje, zda byla zadána klauzule Distinct, a jestli je nejhornější příkaz.</span><span class="sxs-lookup"><span data-stu-id="e373e-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="e373e-134">Pokud příkaz není nejhornější, klauzule ORDER by je vynechán, pokud příkaz také obsahuje klauzuli TOP.</span><span class="sxs-lookup"><span data-stu-id="e373e-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>  
  
 <span data-ttu-id="e373e-135">FromExtents obsahuje seznam vstupy pro příkaz SELECT.</span><span class="sxs-lookup"><span data-stu-id="e373e-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="e373e-136">V tomto obvykle není právě jeden element.</span><span class="sxs-lookup"><span data-stu-id="e373e-136">There is usually just one element in this.</span></span> <span data-ttu-id="e373e-137">Příkazy SELECT pro spojení dočasně může mít více než jeden element.</span><span class="sxs-lookup"><span data-stu-id="e373e-137">SELECT statements for joins may temporarily have more than one element.</span></span>  
  
 <span data-ttu-id="e373e-138">Pokud příkaz SELECT se vytvoří pomocí připojení k uzlu, SqlSelectStatement udržuje seznam všechny rozsahy, které byly průmětu ve spojení v AllJoinExtents.</span><span class="sxs-lookup"><span data-stu-id="e373e-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="e373e-139">OuterExtents představuje vnější odkazů SqlSelectStatement a používá se pro přejmenování vstupní alias.</span><span class="sxs-lookup"><span data-stu-id="e373e-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>  
  
```  
internal sealed class SqlSelectStatement : ISqlFragment {  
   internal bool IsDistinct { get, set };  
   internal bool IsTopMost  
  
   internal List<Symbol> AllJoinExtents { get, set };  
   internal List<Symbol> FromExtents { get};  
   internal Dictionary<Symbol, bool> OuterExtents { get};  
  
   internal TopClause Top { get, set };  
  
   internal SqlBuilder Select {get};  
   internal SqlBuilder From  
   internal SqlBuilder Where  
   internal SqlBuilder GroupBy  
   public SqlBuilder OrderBy  
}  
```  
  
#### <a name="topclause"></a><span data-ttu-id="e373e-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="e373e-140">TopClause</span></span>  
 <span data-ttu-id="e373e-141">TopClause představuje výraz TOP v SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="e373e-142">Vlastnost TopCount Určuje, kolik HORNÍCH řádků měla by být vybrána.</span><span class="sxs-lookup"><span data-stu-id="e373e-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="e373e-143">Pokud WithTies hodnotu true, TopClause byl sestaven z DbLimitExpession.</span><span class="sxs-lookup"><span data-stu-id="e373e-143">When WithTies is true, the TopClause was built from a DbLimitExpession.</span></span>  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a><span data-ttu-id="e373e-144">Symboly</span><span class="sxs-lookup"><span data-stu-id="e373e-144">Symbols</span></span>  
 <span data-ttu-id="e373e-145">Třídy související s Symbol a tabulky symbolů provádění přejmenování vstupní alias, vyrovnání alias spojení a přejmenování alias sloupce.</span><span class="sxs-lookup"><span data-stu-id="e373e-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>  
  
 <span data-ttu-id="e373e-146">Třída Symbol představuje rozsah, vnořené příkazu SELECT nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="e373e-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="e373e-147">Místo skutečného alias se používá k povolení pro přejmenování po byla použita a spojeno také další informace o artefaktu, který představuje (např. typu).</span><span class="sxs-lookup"><span data-stu-id="e373e-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>  
  
```  
class Symbol : ISqlFragment {  
   internal Dictionary<string, Symbol> Columns {get}  
   internal bool NeedsRenaming {get, set}  
   internal bool IsUnnest {get, set}   //not used  
  
   public string Name{get}  
   public string NewName {get,set}  
   internal TypeUsage Type {get, set}  
  
   public Symbol(string name, TypeUsage type)  
}  
```  
  
 <span data-ttu-id="e373e-148">Ukládá název aliasu původní pro reprezentována rozsah, vnořené příkazu SELECT nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="e373e-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>  
  
 <span data-ttu-id="e373e-149">NewName ukládá alias, který se použije v příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="e373e-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="e373e-150">Je původně nastavena na název a přejmenovat pouze v případě potřeby při generování v posledním řetězci dotazu.</span><span class="sxs-lookup"><span data-stu-id="e373e-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>  
  
 <span data-ttu-id="e373e-151">Typ je platný pouze pro symboly představující rozsahy a vnořených příkazů SELECT.</span><span class="sxs-lookup"><span data-stu-id="e373e-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>  
  
#### <a name="symbolpair"></a><span data-ttu-id="e373e-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="e373e-152">SymbolPair</span></span>  
 <span data-ttu-id="e373e-153">Třída SymbolPair řeší záznamů sloučení.</span><span class="sxs-lookup"><span data-stu-id="e373e-153">The SymbolPair class addresses record flattening.</span></span>  
  
 <span data-ttu-id="e373e-154">Vezměte v úvahu výraz vlastnost D (v, "j3.j2.j1.a.x"), kde je v VarRef, j1, j2, j3 jsou spojení, je rozsah a x sloupců.</span><span class="sxs-lookup"><span data-stu-id="e373e-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>  
  
 <span data-ttu-id="e373e-155">Tento postup je nakonec přeložit na </span><span class="sxs-lookup"><span data-stu-id="e373e-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="e373e-156">}. {x'}.Pole zdroje představuje nejkrajnější SqlStatement, představující výraz spojení (například j2); Toto je vždy symbol spojení.</span><span class="sxs-lookup"><span data-stu-id="e373e-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="e373e-157">Pole sloupec přesune z jednoho připojení k symbol na další končí na symbol – připojení k.</span><span class="sxs-lookup"><span data-stu-id="e373e-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="e373e-158">To je vrácena, pokud návštěvou DbPropertyExpression, ale nikdy je přidán do SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="e373e-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a><span data-ttu-id="e373e-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="e373e-159">JoinSymbol</span></span>  
 <span data-ttu-id="e373e-160">Symbol spojení je Symbol, který představuje vnořený příkaz SELECT s spojení nebo spojení vstup.</span><span class="sxs-lookup"><span data-stu-id="e373e-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>  
  
```  
internal sealed class JoinSymbol : Symbol {  
   internal List<Symbol> ColumnList {get, set}  
   internal List<Symbol> ExtentList {get}  
   internal List<Symbol> FlattenedExtentList {get, set}  
   internal Dictionary<string, Symbol> NameToExtent {get}  
   internal bool IsNestedJoin {get, set}  
  
   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)  
}  
```  
  
 <span data-ttu-id="e373e-161">Seznam sloupců představuje seznam sloupců v klauzuli SELECT, pokud tento symbol představuje příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="e373e-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="e373e-162">ExtentList je seznam rozsahů v klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="e373e-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="e373e-163">Pokud připojení k více rozsahů průmětu na nejvyšší úrovni, sleduje FlattenedExtentList rozsahy zajistit této míře, které aliasy jsou přejmenovány správně.</span><span class="sxs-lookup"><span data-stu-id="e373e-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>  
  
 <span data-ttu-id="e373e-164">NameToExtent má všechny rozsahy v ExtentList jako slovník.</span><span class="sxs-lookup"><span data-stu-id="e373e-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="e373e-165">IsNestedJoin slouží k určení, zda je JoinSymbol symbol obyčejnou spojení nebo ten, který má odpovídající SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e373e-166">Všechny seznamy jsou nastavit přesně jednou a pak se použije pro hledání nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="e373e-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>  
  
#### <a name="symboltable"></a><span data-ttu-id="e373e-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="e373e-167">SymbolTable</span></span>  
 <span data-ttu-id="e373e-168">SymbolTable se používá k překladu názvů proměnných na symboly.</span><span class="sxs-lookup"><span data-stu-id="e373e-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="e373e-169">SymbolTable je implementovaný jako zásobníku se nový záznam pro každý obor.</span><span class="sxs-lookup"><span data-stu-id="e373e-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="e373e-170">Hledání vyhledávání z horní části zásobníku k dolnímu dokud nebude nalezen položku.</span><span class="sxs-lookup"><span data-stu-id="e373e-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 <span data-ttu-id="e373e-171">Není k dispozici pouze jeden SymbolTable na jednu instanci modulu generování Sql.</span><span class="sxs-lookup"><span data-stu-id="e373e-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="e373e-172">Zadaný a byl ukončen pro každý uzel relační oborů.</span><span class="sxs-lookup"><span data-stu-id="e373e-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="e373e-173">Všechny symboly v dřívější obory jsou viditelné pro novější obory, pokud není skrytý na základě jiných symbolů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="e373e-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>  
  
### <a name="global-state-for-the-visitor"></a><span data-ttu-id="e373e-174">Globální stav pro návštěvníka</span><span class="sxs-lookup"><span data-stu-id="e373e-174">Global State for the Visitor</span></span>  
 <span data-ttu-id="e373e-175">Jako pomoc při přejmenování aliasy a sloupce, spravovat seznam všechny názvy sloupců (AllColumnNames) a aliasy rozsah (AllExtentNames), které byly použity v první předání přes stromu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e373e-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="e373e-176">Tabulky symbolů přeloží názvy proměnných na symboly.</span><span class="sxs-lookup"><span data-stu-id="e373e-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="e373e-177">IsVarRefSingle se používá pouze pro účely ověření není nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="e373e-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>  
  
 <span data-ttu-id="e373e-178">Dva zásobníky používá prostřednictvím CurrentSelectStatement a IsParentAJoin jsou sloužící k předávání "parametry" z nadřazené do podřízené uzly, vzhledem k tomu, že nám předat parametry neumožňuje vzoru návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="e373e-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>  
  
```  
internal Dictionary<string, int> AllExtentNames {get}  
internal Dictionary<string, int> AllColumnNames {get}  
SymbolTable symbolTable = new SymbolTable();  
bool isVarRefSingle = false;  
  
Stack<SqlSelectStatement> selectStatementStack;  
private SqlSelectStatement CurrentSelectStatement{get}  
  
Stack<bool> isParentAJoinStack;  
private bool IsParentAJoin{get}  
```  
  
## <a name="common-scenarios"></a><span data-ttu-id="e373e-179">Běžné scénáře</span><span class="sxs-lookup"><span data-stu-id="e373e-179">Common Scenarios</span></span>  
 <span data-ttu-id="e373e-180">Tato část popisuje běžné scénáře zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="e373e-180">This section discusses common provider scenarios.</span></span>  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="e373e-181">Seskupování uzlů výraz do SQL příkazy</span><span class="sxs-lookup"><span data-stu-id="e373e-181">Grouping Expression Nodes into SQL Statements</span></span>  
 <span data-ttu-id="e373e-182">SqlSelectStatement se vytvoří při prvním relační uzlu je došlo (obvykle rozsah DbScanExpression) při návštěvě stromu zdola nahoru.</span><span class="sxs-lookup"><span data-stu-id="e373e-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="e373e-183">K vytvoření příkazu SQL SELECT s jako několika vnořené dotazy nejdříve agregační jako řadu svých nadřazených uzlů co možná v tomto SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e373e-184">Rozhodnutí, zda daný uzel (relační) mohou být přidány do aktuální SqlSelectStatement (jeden, vrácena při návštěvě vstup) nebo pokud je třeba spustit nové prohlášení je počítaný metodou IsCompatible a závisí na co se již SqlSelectStatement, což závisí na uzly byly dole daný uzel.</span><span class="sxs-lookup"><span data-stu-id="e373e-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>  
  
 <span data-ttu-id="e373e-185">Obvykle Pokud klauzule příkazu SQL, jsou vyhodnoceny po klauzule kde uzly za ke sloučení nejsou prázdné, uzel nelze přidat do aktuální příkaz.</span><span class="sxs-lookup"><span data-stu-id="e373e-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="e373e-186">Například pokud další uzel je filtr, aby uzel lze začlenit do aktuální SqlSelectStatement pouze v případě, že platí následující:</span><span class="sxs-lookup"><span data-stu-id="e373e-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>  
  
-   <span data-ttu-id="e373e-187">Vyberte seznam je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e373e-187">The SELECT list is empty.</span></span> <span data-ttu-id="e373e-188">Pokud seznamu příkazu SELECT není prázdná, seznamu příkazu select bylo vytvořeno uzel předcházející filtr a predikát může odkazovat na sloupce vyprodukované tohoto seznamu, vyberte možnost.</span><span class="sxs-lookup"><span data-stu-id="e373e-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>  
  
-   <span data-ttu-id="e373e-189">GROUPBY je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e373e-189">The GROUPBY is empty.</span></span> <span data-ttu-id="e373e-190">Pokud GROUPBY není prázdná, přidání filtru znamená filtrování před seskupení, která není správný.</span><span class="sxs-lookup"><span data-stu-id="e373e-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>  
  
-   <span data-ttu-id="e373e-191">Klauzule TOP je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e373e-191">The TOP clause is empty.</span></span> <span data-ttu-id="e373e-192">Když klauzule TOP není prázdná, přidání filtru by totiž filtrování před provedením NAHOŘE, který není správný.</span><span class="sxs-lookup"><span data-stu-id="e373e-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>  
  
 <span data-ttu-id="e373e-193">To neplatí pro nerelační uzly jako DbConstantExpression nebo aritmetických výrazech, protože se jedná vždy součástí existující SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e373e-194">Při zjištění kořenu stromu spojení (připojení k uzlu, který nemá připojení k nadřazené), je spuštěn nový SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="e373e-195">Všechny podřízené spojení levé spine se agregován do tohoto SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e373e-196">Vždy, když se spustí novou SqlSelectStatement a stávající se přidá do vstupní, aktuální SqlSelectStatement může třeba provést přidáním sloupce projekce (klauzuli SELECT), pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e373e-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="e373e-197">To se provádí pomocí metody AddDefaultColumns, který zjistí FromExtents SqlSelectStatement a přidá všechny sloupce, které přináší seznam rozsahů reprezentována FromExtents v oboru do seznamu předpokládané sloupců.</span><span class="sxs-lookup"><span data-stu-id="e373e-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="e373e-198">Důvodem je, protože v tomto okamžiku Neznámý sloupce, které odkazují na jiných uzlech.</span><span class="sxs-lookup"><span data-stu-id="e373e-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="e373e-199">To může být optimalizovaná tak, aby pouze projektu sloupce, které můžete později použít.</span><span class="sxs-lookup"><span data-stu-id="e373e-199">This can be optimized to only project the columns that can later be used.</span></span>  
  
### <a name="join-flattening"></a><span data-ttu-id="e373e-200">Připojení k vyrovnání</span><span class="sxs-lookup"><span data-stu-id="e373e-200">Join Flattening</span></span>  
 <span data-ttu-id="e373e-201">Vlastnost IsParentAJoin pomáhá určit, zda lze vyrovnány dané připojení.</span><span class="sxs-lookup"><span data-stu-id="e373e-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="e373e-202">Konkrétně IsParentAJoin vrátí `true` pouze pro podřízený objekt levé spojení a pro každou DbScanExpression, který je okamžitý vstupní spojení, v takovém případě tento podřízený uzel opětovně používá stejné SqlSelectStatement, nadřazený byste použili později.</span><span class="sxs-lookup"><span data-stu-id="e373e-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="e373e-203">Další informace najdete v tématu "Výrazy připojení".</span><span class="sxs-lookup"><span data-stu-id="e373e-203">For more information, see "Join Expressions".</span></span>  
  
### <a name="input-alias-redirecting"></a><span data-ttu-id="e373e-204">Vstupní Alias přesměrování</span><span class="sxs-lookup"><span data-stu-id="e373e-204">Input Alias Redirecting</span></span>  
 <span data-ttu-id="e373e-205">Přesměrování vstupní alias je provedeno pomocí tabulky symbolů.</span><span class="sxs-lookup"><span data-stu-id="e373e-205">Input alias redirecting is accomplished with the symbol table.</span></span>  
  
 <span data-ttu-id="e373e-206">Vysvětlení, přesměrování vstupní alias, naleznete v prvním příkladu v [generování SQL z stromy příkazů – doporučené postupy](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="e373e-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="e373e-207">Existuje "a" potřeba přesměrovat na "b" v projekci.</span><span class="sxs-lookup"><span data-stu-id="e373e-207">There "a" needed to be redirected to "b" in the projection.</span></span>  
  
 <span data-ttu-id="e373e-208">Když je vytvořen objekt SqlSelectStatement, rozsah, který je vstup uzlu uveden vlastnost From SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="e373e-209">Symbol (< symbol_b >) se vytvoří na základě název vstupní vazby ("b") představují tento rozsah a "AS" + < symbol_b > je připojeno k klauzule From.</span><span class="sxs-lookup"><span data-stu-id="e373e-209">A Symbol (<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " +  <symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="e373e-210">Symbol je taky přidaný ke FromExtents vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e373e-210">The symbol is also added to the FromExtents property.</span></span>  
  
 <span data-ttu-id="e373e-211">Symbol je taky přidaná do tabulky symbolů propojení název vstupní vazby k němu ("b", < symbol_b >).</span><span class="sxs-lookup"><span data-stu-id="e373e-211">The symbol is also added to the symbol table to link the input binding name to it ("b", <symbol_b>).</span></span>  
  
 <span data-ttu-id="e373e-212">Pokud následné uzlu opětovně používá tento SqlSelectStatement, přidá položku do tabulky symbolů propojení její název Vstupní vazba na tento symbol.</span><span class="sxs-lookup"><span data-stu-id="e373e-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="e373e-213">V našem příkladu by opakovaně použít SqlSelectStatement a přidejte DbProjectExpression s názvem Vstupní vazba "a" ("a", \< symbol_b >) do tabulky.</span><span class="sxs-lookup"><span data-stu-id="e373e-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>  
  
 <span data-ttu-id="e373e-214">Když výrazy odkazovat na název vstupní vazby uzlu, který je použití SqlSelectStatement, že je odkaz přeložit pomocí tabulky symbolů na správný přesměrovaného symbol.</span><span class="sxs-lookup"><span data-stu-id="e373e-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="e373e-215">Při "a" z "a.x" vyřešení při návštěvě představující DbVariableReferenceExpression "a" it přeloží na symbol < symbol_b >.</span><span class="sxs-lookup"><span data-stu-id="e373e-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol <symbol_b>.</span></span>  
  
### <a name="join-alias-flattening"></a><span data-ttu-id="e373e-216">Připojení k vyrovnání Alias</span><span class="sxs-lookup"><span data-stu-id="e373e-216">Join Alias Flattening</span></span>  
 <span data-ttu-id="e373e-217">Připojení k vyrovnání alias se dosáhne, když návštěvou DbPropertyExpression, jak je popsáno v části s názvem DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="e373e-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>  
  
### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="e373e-218">Název sloupce a míry Alias přejmenování</span><span class="sxs-lookup"><span data-stu-id="e373e-218">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="e373e-219">Problém název sloupce a míry alias přejmenování je řešit pomocí znaky, které pouze získat nahrazena s aliasy ve druhé fázi generování popsané v části s názvem druhé fáze generování SQL: generování příkaz String.</span><span class="sxs-lookup"><span data-stu-id="e373e-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="e373e-220">První fáze generování SQL: návštěvou strom výrazu</span><span class="sxs-lookup"><span data-stu-id="e373e-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="e373e-221">Tato část popisuje první fáze generování SQL, když je vytvořil výraz představující, které je navštívené dotaz a zprostředkující struktura, buď SqlSelectStatement nebo SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="e373e-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>  
  
 <span data-ttu-id="e373e-222">Tato část popisuje zásad hostujícími jiný výraz uzlu kategorií a podrobnosti hostujících typy konkrétní výrazů.</span><span class="sxs-lookup"><span data-stu-id="e373e-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>  
  
### <a name="relational-non-join-nodes"></a><span data-ttu-id="e373e-223">Relační uzlů (bez připojení k)</span><span class="sxs-lookup"><span data-stu-id="e373e-223">Relational (Non-Join) Nodes</span></span>  
 <span data-ttu-id="e373e-224">Následující typy výrazů podporují – připojení k uzly:</span><span class="sxs-lookup"><span data-stu-id="e373e-224">The following expression types support non-join nodes:</span></span>  
  
-   <span data-ttu-id="e373e-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-225">DbDistinctExpression</span></span>  
  
-   <span data-ttu-id="e373e-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-226">DbFilterExpression</span></span>  
  
-   <span data-ttu-id="e373e-227">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-227">DbGroupByExpression</span></span>  
  
-   <span data-ttu-id="e373e-228">DbLimitExpession</span><span class="sxs-lookup"><span data-stu-id="e373e-228">DbLimitExpession</span></span>  
  
-   <span data-ttu-id="e373e-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-229">DbProjectExpression</span></span>  
  
-   <span data-ttu-id="e373e-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-230">DbSkipExpression</span></span>  
  
-   <span data-ttu-id="e373e-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-231">DbSortExpression</span></span>  
  
 <span data-ttu-id="e373e-232">Kteří navštěvují tyto uzly se následující následující:</span><span class="sxs-lookup"><span data-stu-id="e373e-232">Visiting these nodes follows the following pattern:</span></span>  
  
1.  <span data-ttu-id="e373e-233">Navštivte relační vstupní a získat výsledné SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="e373e-234">Vstup relační uzel může být jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="e373e-234">The input to a relational node could be one of the following:</span></span>  
  
    -   <span data-ttu-id="e373e-235">Relační uzlu, včetně rozsah (DbScanExpression, např.).</span><span class="sxs-lookup"><span data-stu-id="e373e-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="e373e-236">Návštěvou takový uzel vrátí SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-236">Visiting such a node returns a SqlSelectStatement.</span></span>  
  
    -   <span data-ttu-id="e373e-237">Operace výraz sady (UNION ALL, např.).</span><span class="sxs-lookup"><span data-stu-id="e373e-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="e373e-238">Výsledek musí být uzavřen do závorek a put v klauzuli FROM nové SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>  
  
2.  <span data-ttu-id="e373e-239">Zkontrolujte, zda aktuální uzel mohou být přidány do SqlSelectStatement vyprodukované vstupu.</span><span class="sxs-lookup"><span data-stu-id="e373e-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="e373e-240">V části s názvem výrazy seskupení do příkazů SQL popisuje to.</span><span class="sxs-lookup"><span data-stu-id="e373e-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="e373e-241">Pokud ne,</span><span class="sxs-lookup"><span data-stu-id="e373e-241">If not,</span></span>  
  
    -   <span data-ttu-id="e373e-242">Aktuální objekt SqlSelectStatement POP.</span><span class="sxs-lookup"><span data-stu-id="e373e-242">Pop the current SqlSelectStatement object.</span></span>  
  
    -   <span data-ttu-id="e373e-243">Vytvořit nový objekt SqlSelectStatement a přidejte popped SqlSelectStatement jako od nového objektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>  
  
    -   <span data-ttu-id="e373e-244">Uveďte nový objekt nad zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e373e-244">Put the new object on top of the stack.</span></span>  
  
3.  <span data-ttu-id="e373e-245">Přesměrování vazby vstupní výraz na správný symbol ze vstupu.</span><span class="sxs-lookup"><span data-stu-id="e373e-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="e373e-246">Tyto informace se udržuje v SqlSelectStatement objektu.</span><span class="sxs-lookup"><span data-stu-id="e373e-246">This information is maintained in the SqlSelectStatement object.</span></span>  
  
4.  <span data-ttu-id="e373e-247">Přidáte nový obor SymbolTable.</span><span class="sxs-lookup"><span data-stu-id="e373e-247">Add a new SymbolTable scope.</span></span>  
  
5.  <span data-ttu-id="e373e-248">Navštivte pro jiný vstup část výrazu (například projekce a predikát).</span><span class="sxs-lookup"><span data-stu-id="e373e-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>  
  
6.  <span data-ttu-id="e373e-249">POP – všechny objekty přidané do globální zásobníky.</span><span class="sxs-lookup"><span data-stu-id="e373e-249">Pop all the objects added to the global stacks.</span></span>  
  
 <span data-ttu-id="e373e-250">DbSkipExpression nemá přímé ekvivalent v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="e373e-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="e373e-251">Logicky je převeden do:</span><span class="sxs-lookup"><span data-stu-id="e373e-251">Logically, it is translated into:</span></span>  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a><span data-ttu-id="e373e-252">Připojení k výrazy</span><span class="sxs-lookup"><span data-stu-id="e373e-252">Join Expressions</span></span>  
 <span data-ttu-id="e373e-253">Následující jsou zvažovány spojení výrazy a běžné způsobem, jsou zpracovávány metodou VisitJoinExpression:</span><span class="sxs-lookup"><span data-stu-id="e373e-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>  
  
-   <span data-ttu-id="e373e-254">DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-254">DbApplyExpression</span></span>  
  
-   <span data-ttu-id="e373e-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-255">DbJoinExpression</span></span>  
  
-   <span data-ttu-id="e373e-256">Objekt DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-256">DbCrossJoinExpression</span></span>  
  
 <span data-ttu-id="e373e-257">Tady jsou kroky najdete:</span><span class="sxs-lookup"><span data-stu-id="e373e-257">The following are the visit steps:</span></span>  
  
 <span data-ttu-id="e373e-258">Před návštěvou podřízené objekty, je nejprve IsParentAJoin a zkontrolujte, zda připojení k uzlu podřízenou spojení podél levého spine volána.</span><span class="sxs-lookup"><span data-stu-id="e373e-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="e373e-259">Pokud vrátí hodnotu false, nové SqlSelectStatement je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="e373e-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="e373e-260">V tomto smysl spojení navštívené odlišně od zbytku uzly, jako nadřazené (připojení k uzlu) vytvoří SqlSelectStatement pro děti pravděpodobně používat.</span><span class="sxs-lookup"><span data-stu-id="e373e-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>  
  
 <span data-ttu-id="e373e-261">Za druhé zpracovat vstupy jeden najednou.</span><span class="sxs-lookup"><span data-stu-id="e373e-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="e373e-262">Pro každý vstupní:</span><span class="sxs-lookup"><span data-stu-id="e373e-262">For each input:</span></span>  
  
1.  <span data-ttu-id="e373e-263">Navštivte vstupu.</span><span class="sxs-lookup"><span data-stu-id="e373e-263">Visit the input.</span></span>  
  
2.  <span data-ttu-id="e373e-264">Proces POST výsledek hostujících vstup vyvoláním ProcessJoinInputResult, který zodpovídá za údržbu tabulky symbolů po návštěvou podřízenou výraz spojení a pravděpodobně dokončení SqlSelectStatement vyprodukované podřízený objekt.</span><span class="sxs-lookup"><span data-stu-id="e373e-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="e373e-265">Výsledek dítěte může být jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="e373e-265">The child's result could be one of the following:</span></span>  
  
    -   <span data-ttu-id="e373e-266">SqlSelectStatement liší od ten, do které budou přidány nadřazený.</span><span class="sxs-lookup"><span data-stu-id="e373e-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="e373e-267">V takovém případě je třeba provést přidáním sloupce výchozí.</span><span class="sxs-lookup"><span data-stu-id="e373e-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="e373e-268">Pokud tento vstup byl spojení, budete muset vytvořit nový symbol spojení.</span><span class="sxs-lookup"><span data-stu-id="e373e-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="e373e-269">Jinak vytvořte symbol normální.</span><span class="sxs-lookup"><span data-stu-id="e373e-269">Otherwise, create a normal symbol.</span></span>  
  
    -   <span data-ttu-id="e373e-270">Rozsah (DbScanExpression, např.), ve kterém je případ, který je jednoduše přidat do seznamu vstupy nadřazené SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e373e-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>  
  
    -   <span data-ttu-id="e373e-271">Není SqlSelectStatement, ve kterém případu, který je uzavřen do závorky.</span><span class="sxs-lookup"><span data-stu-id="e373e-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>  
  
    -   <span data-ttu-id="e373e-272">Stejné SqlSelectStatement, ke kterému je nadřazená přidána.</span><span class="sxs-lookup"><span data-stu-id="e373e-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="e373e-273">V takovém případě je nutné symboly v seznamu FromExtents nahradit pomocí jednoho nové JoinSymbol představující je všechny.</span><span class="sxs-lookup"><span data-stu-id="e373e-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>  
  
    -   <span data-ttu-id="e373e-274">První tři v případech se nazývá AddFromSymbol přidat klauzuli a aktualizovat tabulky symbolů.</span><span class="sxs-lookup"><span data-stu-id="e373e-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>  
  
 <span data-ttu-id="e373e-275">Třetí je navštívené podmínku připojení (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="e373e-275">Third, the join condition (if any) is visited.</span></span>  
  
### <a name="set-operations"></a><span data-ttu-id="e373e-276">Množinové operace</span><span class="sxs-lookup"><span data-stu-id="e373e-276">Set Operations</span></span>  
 <span data-ttu-id="e373e-277">Množinové operace DbUnionAllExpression, DbExceptExpression a DbIntersectExpression zpracovává metodu VisitSetOpExpression.</span><span class="sxs-lookup"><span data-stu-id="e373e-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="e373e-278">Vytvoří SqlBuilder tvaru</span><span class="sxs-lookup"><span data-stu-id="e373e-278">It creates a SqlBuilder of the shape</span></span>  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 <span data-ttu-id="e373e-279">Kde \<leftSqlSelectStatement > a \<rightSqlSelectStatement > se získala při každé vstupních hodnot, kteří navštěvují SqlSelectStatements a \<setOp > je odpovídající operace (UNION ALL např.).</span><span class="sxs-lookup"><span data-stu-id="e373e-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>  
  
### <a name="dbscanexpression"></a><span data-ttu-id="e373e-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-280">DbScanExpression</span></span>  
 <span data-ttu-id="e373e-281">Pokud navštívené v kontextu připojení (jako vstup pro připojení k, které je levé podřízená jiné připojení), vrátí DbScanExpression SqlBuilder s cílem SQL pro odpovídající cíl, který je definující dotazu, tabulka nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e373e-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="e373e-282">Jinak se vytvoří nový SqlSelectStatement s pole od nastavit tak, aby odpovídaly odpovídající cíl.</span><span class="sxs-lookup"><span data-stu-id="e373e-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>  
  
### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="e373e-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-283">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="e373e-284">Návštěvu DbVariableReferenceExpression vrátí Symbol odpovídající tento výraz odkazu na proměnnou podle vyhledávání v tabulce symbolu.</span><span class="sxs-lookup"><span data-stu-id="e373e-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="e373e-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-285">DbPropertyExpression</span></span>  
 <span data-ttu-id="e373e-286">Vyrovnání alias spojení je identifikovat a zpracování při návštěvě DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="e373e-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>  
  
 <span data-ttu-id="e373e-287">Vlastnost Instance první návštěvě a výsledkem je Symbol, JoinSymbol nebo SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="e373e-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="e373e-288">Tady je způsob zpracování těchto třech případech:</span><span class="sxs-lookup"><span data-stu-id="e373e-288">Here is how these three cases are handled:</span></span>  
  
-   <span data-ttu-id="e373e-289">Pokud je vrácen JoinSymbol, než jeho NameToExtent vlastnost obsahuje symbol pro vlastnost potřebné.</span><span class="sxs-lookup"><span data-stu-id="e373e-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="e373e-290">Pokud je symbol spojení představuje vnořené spojení, se vrátí nový pár Symbol s symbol připojení ke sledování symbol, který se použije jako instance alias a symbol reprezentující skutečné vlastnost pro další řešení.</span><span class="sxs-lookup"><span data-stu-id="e373e-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>  
  
-   <span data-ttu-id="e373e-291">Pokud je vrácen SymbolPair a část sloupec je symbol spojení, znovu vrátí symbol spojení, ale nyní je vlastnost column aktualizovat tak, aby odkazoval na vlastnost vyjádřený výrazem aktuální vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e373e-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="e373e-292">Jinak se vrátí SqlBuilder s zdroji SymbolPair jako alias a symbol pro aktuální vlastnost jako sloupec.</span><span class="sxs-lookup"><span data-stu-id="e373e-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>  
  
-   <span data-ttu-id="e373e-293">Pokud Symbol je vrácena, vrátí metoda návštěvu SqlBuilder metodu s dané instance jako alias a název vlastnosti jako název sloupce.</span><span class="sxs-lookup"><span data-stu-id="e373e-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>  
  
### <a name="dbnewinstanceexpression"></a><span data-ttu-id="e373e-294">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-294">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="e373e-295">Když se použije jako vlastnost projekce DbProjectExpression, DbNewInstanceExpression vytvoří textový soubor s oddělovači seznam argumentů představují předpokládané sloupce.</span><span class="sxs-lookup"><span data-stu-id="e373e-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>  
  
 <span data-ttu-id="e373e-296">Když DbNewInstanceExpression má návratový typ kolekce a definuje novou kolekci výrazů zadané jako argumenty, jsou zpracovávány samostatně následujících třech případech:</span><span class="sxs-lookup"><span data-stu-id="e373e-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>  
  
-   <span data-ttu-id="e373e-297">Pokud DbNewInstanceExpression DbElementExpression jako argument pouze, je přeložit takto:</span><span class="sxs-lookup"><span data-stu-id="e373e-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 <span data-ttu-id="e373e-298">Pokud má DbNewInstanceExpression bez argumentů (prázdná tabulka představuje), DbNewInstanceExpression je přeložit na:</span><span class="sxs-lookup"><span data-stu-id="e373e-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 <span data-ttu-id="e373e-299">V opačném případě DbNewInstanceExpression sestavení union all žebříku argumentů:</span><span class="sxs-lookup"><span data-stu-id="e373e-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a><span data-ttu-id="e373e-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-300">DbFunctionExpression</span></span>  
 <span data-ttu-id="e373e-301">Kanonické a integrované funkce jsou zpracovávány stejným způsobem jako: Pokud potřebují zvláštní zpracování (TRIM(string) k LTRIM(RTRIM(string), např.), je vyvolána příslušnou obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="e373e-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="e373e-302">Jinak jsou převedeny na %{FunctionName/ (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="e373e-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>  
  
 <span data-ttu-id="e373e-303">Slovník slouží k udržování přehledu o funkcích, které potřebují zvláštní zpracování a jejich odpovídající obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="e373e-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>  
  
 <span data-ttu-id="e373e-304">Uživatelem definované funkce jsou tanslated k NamespaceName.FunctionName (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="e373e-304">User-defined functions are tanslated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>  
  
### <a name="dbelementexpression"></a><span data-ttu-id="e373e-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-305">DbElementExpression</span></span>  
 <span data-ttu-id="e373e-306">Metoda, která navštíví DbElementExpression je volána, pouze pro návštěvou DbElementExpression, když se používá k reprezentování skalární poddotazu.</span><span class="sxs-lookup"><span data-stu-id="e373e-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="e373e-307">Proto DbElementExpression překládá do dokončení SqlSelectStatement a přidá hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="e373e-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>  
  
### <a name="dbquantifierexpression"></a><span data-ttu-id="e373e-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-308">DbQuantifierExpression</span></span>  
 <span data-ttu-id="e373e-309">V závislosti na typ výrazu (některé nebo všechny), DbQuantifierExpression přeložit jej jako:</span><span class="sxs-lookup"><span data-stu-id="e373e-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated it as:</span></span>  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a><span data-ttu-id="e373e-310">Třída DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-310">DbNotExpression</span></span>  
 <span data-ttu-id="e373e-311">V některých případech je možné sbalit překlad DbNotExpression s jeho vstupní výraz.</span><span class="sxs-lookup"><span data-stu-id="e373e-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="e373e-312">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e373e-312">For example:</span></span>  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 <span data-ttu-id="e373e-313">Z důvodu, který provádí druhý sbalit totiž nedostatky, které byly zavedeny zprostředkovatelem při překladu DbQuantifierExpression z zadejte všechny.</span><span class="sxs-lookup"><span data-stu-id="e373e-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="e373e-314">Rozhraní Entity Framework proto nelze provést zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="e373e-314">Thus the Entity Framework could not have done the simplification.</span></span>  
  
### <a name="dbisemptyexpression"></a><span data-ttu-id="e373e-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="e373e-315">DbIsEmptyExpression</span></span>  
 <span data-ttu-id="e373e-316">DbIsEmptyExpression je přeložená jako:</span><span class="sxs-lookup"><span data-stu-id="e373e-316">DbIsEmptyExpression is translated as:</span></span>  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="e373e-317">Druhé fáze generování SQL: generování příkaz String</span><span class="sxs-lookup"><span data-stu-id="e373e-317">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="e373e-318">Při generování řetězec příkazu SQL, SqlSelectStatement vytvoří skutečné aliasy pro symboly, které řeší problém název sloupce a míry přejmenování alias.</span><span class="sxs-lookup"><span data-stu-id="e373e-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>  
  
 <span data-ttu-id="e373e-319">Přejmenování alias rozsah dojde při zápisu objektu SqlSelectStatement do řetězce.</span><span class="sxs-lookup"><span data-stu-id="e373e-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="e373e-320">Nejprve vytvořte seznam všechny aliasy používá vnější rozsahy.</span><span class="sxs-lookup"><span data-stu-id="e373e-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="e373e-321">Každý symbol v FromExtents (nebo AllJoinExtents, pokud je jinou hodnotu než null), získá přejmenovat, pokud ji koliduje s žádným z rozsahů vnější.</span><span class="sxs-lookup"><span data-stu-id="e373e-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="e373e-322">V případě potřeby přejmenování ho nebude v konfliktu s žádným z rozsahů shromážděny v AllExtentNames.</span><span class="sxs-lookup"><span data-stu-id="e373e-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>  
  
 <span data-ttu-id="e373e-323">Přejmenování sloupce dojde při zápisu Symbol objekt na řetězec.</span><span class="sxs-lookup"><span data-stu-id="e373e-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="e373e-324">AddDefaultColumns v první fázi určil, pokud symbol některé sloupce musí být přejmenována.</span><span class="sxs-lookup"><span data-stu-id="e373e-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="e373e-325">V druhé fázi dojde pouze přejmenování, a ujistěte se, že název vytvořeného nejsou v konfliktu s libovolným názvem použít v AllColumnNames</span><span class="sxs-lookup"><span data-stu-id="e373e-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>  
  
 <span data-ttu-id="e373e-326">K vytvoření jedinečné názvy pro rozsah aliasy i pro sloupce, použijte _n < existing_name >, kde n je nejmenší alias, který nebyl dosud použit.</span><span class="sxs-lookup"><span data-stu-id="e373e-326">To produce unique names both for extent aliases and for columns, use <existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="e373e-327">Globální seznam všechny aliasy zvyšuje potřebu kaskádových přejmenuje.</span><span class="sxs-lookup"><span data-stu-id="e373e-327">The global list of all aliases increases the need for cascading renames.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e373e-328">Viz také</span><span class="sxs-lookup"><span data-stu-id="e373e-328">See Also</span></span>  
 [<span data-ttu-id="e373e-329">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="e373e-329">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
