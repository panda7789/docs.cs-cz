---
title: Architektura a návrh
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: a4b597c8a62c661ace4485959589823094b9a08f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606851"
---
# <a name="architecture-and-design"></a><span data-ttu-id="89bce-102">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="89bce-102">Architecture and Design</span></span>
<span data-ttu-id="89bce-103">Modul generování SQL v [zprostředkovateli ukázek](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) je implementovaný jako návštěvníky na strom výrazu, který představuje strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="89bce-103">The SQL generation module in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="89bce-104">Generování se provádí v jednom průchodu přes strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="89bce-104">The generation is done in a single pass over the expression tree.</span></span>  
  
 <span data-ttu-id="89bce-105">Uzly stromu jsou zpracovávány zdola nahoru.</span><span class="sxs-lookup"><span data-stu-id="89bce-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="89bce-106">Nejprve je vytvořen zprostředkující struktury: SqlSelectStatement nebo SqlBuilder, obě implementující ISqlFragment.</span><span class="sxs-lookup"><span data-stu-id="89bce-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="89bce-107">V dalším kroku řetězec příkazu SQL je vytvořený z této struktury.</span><span class="sxs-lookup"><span data-stu-id="89bce-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="89bce-108">Existují dva důvody pro zprostředkující strukturu:</span><span class="sxs-lookup"><span data-stu-id="89bce-108">There are two reasons for the intermediate structure:</span></span>  
  
- <span data-ttu-id="89bce-109">Příkaz SELECT se vyplní logicky, mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="89bce-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="89bce-110">Uzly, které jsou součástí v klauzuli FROM jsou zobrazeny před uzly, které jsou součástí WHERE, GROUP BY a ORDER BY – klauzule.</span><span class="sxs-lookup"><span data-stu-id="89bce-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>  
  
- <span data-ttu-id="89bce-111">Přejmenování aliasy, je nutné určit všech použitých aliasy pro zabránění kolizím při přejmenování.</span><span class="sxs-lookup"><span data-stu-id="89bce-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="89bce-112">Přejmenování možnosti v SqlBuilder odložit, představují sloupce, které jsou kandidáty pro přejmenování pomocí symbolu objektů.</span><span class="sxs-lookup"><span data-stu-id="89bce-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>  
  
 <span data-ttu-id="89bce-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="89bce-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>  
  
 <span data-ttu-id="89bce-114">V první fázi při návštěvě stromu výrazů výrazy jsou seskupené do SqlSelectStatements, spojení se sloučí a aliasy spojení se sloučí.</span><span class="sxs-lookup"><span data-stu-id="89bce-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="89bce-115">V této fázi Symbol objekty představují sloupce nebo vstupní aliasy, které mohou být přejmenován.</span><span class="sxs-lookup"><span data-stu-id="89bce-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>  
  
 <span data-ttu-id="89bce-116">V druhé fáze, při vytváření aktuální řetězcovou jsou přejmenované aliasy.</span><span class="sxs-lookup"><span data-stu-id="89bce-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>  
  
## <a name="data-structures"></a><span data-ttu-id="89bce-117">Datové struktury</span><span class="sxs-lookup"><span data-stu-id="89bce-117">Data Structures</span></span>  
 <span data-ttu-id="89bce-118">Tato část popisuje typy používané [zprostředkovateli ukázek](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , který používáte k vytvoření příkazu SQL.</span><span class="sxs-lookup"><span data-stu-id="89bce-118">This section discusses the types used in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) that you use to build a SQL statement.</span></span>  
  
### <a name="isqlfragment"></a><span data-ttu-id="89bce-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="89bce-119">ISqlFragment</span></span>  
 <span data-ttu-id="89bce-120">Tato část popisuje třídy, které implementují rozhraní ISqlFragment, které má dva účely:</span><span class="sxs-lookup"><span data-stu-id="89bce-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>  
  
- <span data-ttu-id="89bce-121">Běžné návratový typ pro všechny metody návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="89bce-121">A common return type for all the visitor methods.</span></span>  
  
- <span data-ttu-id="89bce-122">Poskytuje metodu pro zápis konečný řetězec SQL.</span><span class="sxs-lookup"><span data-stu-id="89bce-122">Gives a method to write the final SQL string.</span></span>  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a><span data-ttu-id="89bce-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="89bce-123">SqlBuilder</span></span>  
 <span data-ttu-id="89bce-124">SqlBuilder je shromažďování zařízení pro konečný řetězec SQL, který je podobný StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="89bce-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="89bce-125">Skládá se z řetězců, které tvoří konečné SQL spolu s ISqlFragments, které mohou být převedeny na řetězce.</span><span class="sxs-lookup"><span data-stu-id="89bce-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a><span data-ttu-id="89bce-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="89bce-126">SqlSelectStatement</span></span>  
 <span data-ttu-id="89bce-127">SqlSelectStatement představuje canonical příkazu SQL SELECT tvaru vyberte..."</span><span class="sxs-lookup"><span data-stu-id="89bce-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="89bce-128">Z...</span><span class="sxs-lookup"><span data-stu-id="89bce-128">FROM  ..</span></span> <span data-ttu-id="89bce-129">KDE...</span><span class="sxs-lookup"><span data-stu-id="89bce-129">WHERE …</span></span> <span data-ttu-id="89bce-130">SESKUPIT PODLE...</span><span class="sxs-lookup"><span data-stu-id="89bce-130">GROUP BY …</span></span> <span data-ttu-id="89bce-131">ŘADIT PODLE".</span><span class="sxs-lookup"><span data-stu-id="89bce-131">ORDER BY".</span></span>  
  
 <span data-ttu-id="89bce-132">Každá klauzule SQL je reprezentován StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="89bce-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="89bce-133">Kromě toho sleduje, zda byl zadán Distinct a zda je příkaz nejvyšší.</span><span class="sxs-lookup"><span data-stu-id="89bce-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="89bce-134">Pokud není příkaz nejvyšší, klauzule ORDER by je vynechána, pokud příkaz obsahuje taky klauzuli TOP.</span><span class="sxs-lookup"><span data-stu-id="89bce-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>  
  
 <span data-ttu-id="89bce-135">FromExtents obsahuje seznam vstupů pro příkaz SELECT.</span><span class="sxs-lookup"><span data-stu-id="89bce-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="89bce-136">V tomto obvykle není právě jeden element.</span><span class="sxs-lookup"><span data-stu-id="89bce-136">There is usually just one element in this.</span></span> <span data-ttu-id="89bce-137">Příkazy SELECT pro spojení dočasně může mít více než jeden element.</span><span class="sxs-lookup"><span data-stu-id="89bce-137">SELECT statements for joins may temporarily have more than one element.</span></span>  
  
 <span data-ttu-id="89bce-138">Pokud příkaz SELECT vytvoří připojení k uzlu, SqlSelectStatement udržuje seznam všechny rozsahy, které se sloučí ve spojení v AllJoinExtents.</span><span class="sxs-lookup"><span data-stu-id="89bce-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="89bce-139">OuterExtents představuje vnější odkazy SqlSelectStatement a používá se pro přejmenování vstupní alias.</span><span class="sxs-lookup"><span data-stu-id="89bce-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>  
  
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
  
#### <a name="topclause"></a><span data-ttu-id="89bce-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="89bce-140">TopClause</span></span>  
 <span data-ttu-id="89bce-141">TopClause představuje výraz TOP v SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="89bce-142">Vlastnost TopCount označuje počet prvních řádků by měla být zaškrtnutá.</span><span class="sxs-lookup"><span data-stu-id="89bce-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="89bce-143">Při splnění WithTies TopClause byla vytvořena z DbLimitExpession.</span><span class="sxs-lookup"><span data-stu-id="89bce-143">When WithTies is true, the TopClause was built from a DbLimitExpession.</span></span>  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a><span data-ttu-id="89bce-144">Symboly</span><span class="sxs-lookup"><span data-stu-id="89bce-144">Symbols</span></span>  
 <span data-ttu-id="89bce-145">Třídy související s symbolů a tabulky symbolů provádějí přejmenování vstupní alias, spojení sloučení alias a přejmenování alias sloupce.</span><span class="sxs-lookup"><span data-stu-id="89bce-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>  
  
 <span data-ttu-id="89bce-146">Třída Symbol představuje rozsah, vnořeného příkazu SELECT nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="89bce-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="89bce-147">Používá se místo skutečných alias umožňující přejmenování poté, co bylo použito a taky mají další informace pro artefakt, který představuje (jako je typ).</span><span class="sxs-lookup"><span data-stu-id="89bce-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>  
  
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
  
 <span data-ttu-id="89bce-148">Ukládá název původní alias pro zastoupené v rozsahu, vnořeného příkazu SELECT nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="89bce-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>  
  
 <span data-ttu-id="89bce-149">NewName ukládá alias, který se použije v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="89bce-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="89bce-150">Je původně nastavena na název a přejmenovat pouze v případě potřeby při generování konečný řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="89bce-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>  
  
 <span data-ttu-id="89bce-151">Typ je platný pouze pro symboly představující rozsahy a vnořených příkazů SELECT.</span><span class="sxs-lookup"><span data-stu-id="89bce-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>  
  
#### <a name="symbolpair"></a><span data-ttu-id="89bce-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="89bce-152">SymbolPair</span></span>  
 <span data-ttu-id="89bce-153">Třída SymbolPair řeší záznam sloučení.</span><span class="sxs-lookup"><span data-stu-id="89bce-153">The SymbolPair class addresses record flattening.</span></span>  
  
 <span data-ttu-id="89bce-154">Vezměte v úvahu výraz pro vlastnost D (v, "j3.j2.j1.a.x"), kde je v VarRef, j1, j2, j3 jsou spojení, je v rozsahu a x je sloupce.</span><span class="sxs-lookup"><span data-stu-id="89bce-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>  
  
 <span data-ttu-id="89bce-155">Tato akce nemá nakonec převést na {j'}. {x'}.</span><span class="sxs-lookup"><span data-stu-id="89bce-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="89bce-156">Zdrojové pole představuje nejkrajnější Příkaz_sql představující výrazu join (třeba j2); Toto je vždy symbol spojení.</span><span class="sxs-lookup"><span data-stu-id="89bce-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="89bce-157">Pole sloupce přesune z jeden symbol spojení na další končí na symbol nikoli na spojení.</span><span class="sxs-lookup"><span data-stu-id="89bce-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="89bce-158">To je vrácena při návštěvě DbPropertyExpression, ale nikdy je přidán SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="89bce-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a><span data-ttu-id="89bce-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="89bce-159">JoinSymbol</span></span>  
 <span data-ttu-id="89bce-160">Symbol spojení je Symbol, který představuje vnořeného příkazu SELECT s spojení nebo spojení vstup.</span><span class="sxs-lookup"><span data-stu-id="89bce-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>  
  
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
  
 <span data-ttu-id="89bce-161">Seznam sloupců představuje seznam sloupců v klauzuli SELECT, pokud tento symbol představuje příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="89bce-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="89bce-162">ExtentList je seznam rozsahů v klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="89bce-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="89bce-163">Má-li spojení více rozsahů sloučí na nejvyšší úrovni, sleduje FlattenedExtentList rozsahy k zajištění tohoto rozsahu, v jakém jsou správně přejmenovat aliasy.</span><span class="sxs-lookup"><span data-stu-id="89bce-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>  
  
 <span data-ttu-id="89bce-164">NameToExtent má všechny rozsahy v ExtentList jako slovník.</span><span class="sxs-lookup"><span data-stu-id="89bce-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="89bce-165">IsNestedJoin slouží k určení, zda je JoinSymbol symbol běžné spojení nebo, pokud má odpovídající SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="89bce-166">Všechny seznamy jsou nastavit přesně jednou a pak použít pro vyhledávání nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="89bce-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>  
  
#### <a name="symboltable"></a><span data-ttu-id="89bce-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="89bce-167">SymbolTable</span></span>  
 <span data-ttu-id="89bce-168">SymbolTable se používá k překladu názvů proměnných na symboly.</span><span class="sxs-lookup"><span data-stu-id="89bce-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="89bce-169">SymbolTable je implementovaný jako zásobníku se nový záznam pro každý obor.</span><span class="sxs-lookup"><span data-stu-id="89bce-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="89bce-170">Vyhledávání hledat v horní části zásobníku do dolní části dokud nebude nalezen záznam.</span><span class="sxs-lookup"><span data-stu-id="89bce-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 <span data-ttu-id="89bce-171">Pouze jeden SymbolTable na jednu instanci modulu generování Sql není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="89bce-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="89bce-172">Obory jsou zadané a byla ukončena, pro každý uzel relační.</span><span class="sxs-lookup"><span data-stu-id="89bce-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="89bce-173">Všechny symboly v dřívější obory jsou viditelné pro pozdější obory Pokud skrytý za jiných symbolů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="89bce-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>  
  
### <a name="global-state-for-the-visitor"></a><span data-ttu-id="89bce-174">Globální stav pro návštěvníka</span><span class="sxs-lookup"><span data-stu-id="89bce-174">Global State for the Visitor</span></span>  
 <span data-ttu-id="89bce-175">Při přejmenování aliasy a sloupců, Udržovat seznam všech názvů sloupců (AllColumnNames) a aliasy rozsahu (AllExtentNames), které se používají v prvním připojovat přes stromu dotazu.</span><span class="sxs-lookup"><span data-stu-id="89bce-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="89bce-176">Tabulky symbolů přeloží názvy proměnných na symboly.</span><span class="sxs-lookup"><span data-stu-id="89bce-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="89bce-177">IsVarRefSingle slouží pouze pro účely ověření není nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="89bce-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>  
  
 <span data-ttu-id="89bce-178">Dvě zásobníky použít prostřednictvím CurrentSelectStatement a IsParentAJoin se používají pro předávání "parametrů" z nadřazeného podřízené uzly, protože model návštěvníka neumožňuje pro předání parametrů.</span><span class="sxs-lookup"><span data-stu-id="89bce-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>  
  
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
  
## <a name="common-scenarios"></a><span data-ttu-id="89bce-179">Obvyklé scénáře</span><span class="sxs-lookup"><span data-stu-id="89bce-179">Common Scenarios</span></span>  
 <span data-ttu-id="89bce-180">Tato část popisuje běžné scénáře zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="89bce-180">This section discusses common provider scenarios.</span></span>  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="89bce-181">Seskupování uzlů výraz na příkazy SQL</span><span class="sxs-lookup"><span data-stu-id="89bce-181">Grouping Expression Nodes into SQL Statements</span></span>  
 <span data-ttu-id="89bce-182">SqlSelectStatement se vytvoří při prvním uzlu relační dochází (obvykle DbScanExpression rozsahu) při návštěvě stromové struktuře zdola nahoru.</span><span class="sxs-lookup"><span data-stu-id="89bce-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="89bce-183">Vytvořit příkaz SQL SELECT s jako málo vnořené nejvíce agregační tolik svých nadřazených uzlů je možné tuto SqlSelectStatement dotazy.</span><span class="sxs-lookup"><span data-stu-id="89bce-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="89bce-184">Rozhodnutí, jestli daný uzel (relační) mohou být přidány do aktuálního SqlSelectStatement (ten vrátí při návštěvě vstupu) nebo jestli je potřeba spustit nové prohlášení je vypočítán metodou IsCompatible a závisí na to, co je již v SqlSelectStatement závisí na uzly byly níže daný uzel.</span><span class="sxs-lookup"><span data-stu-id="89bce-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>  
  
 <span data-ttu-id="89bce-185">Obvykle Pokud klauzule příkaz SQL se vyhodnocují po klauzulích, kde nejsou prázdné uzly se nebude zvažovat sloučení, uzel nelze přidat k aktuálnímu příkazu.</span><span class="sxs-lookup"><span data-stu-id="89bce-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="89bce-186">Například pokud další uzel je filtr, takový uzel může být zahrnut do aktuální SqlSelectStatement pouze v případě, že platí následující:</span><span class="sxs-lookup"><span data-stu-id="89bce-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>  
  
- <span data-ttu-id="89bce-187">Vyberte seznam je prázdný.</span><span class="sxs-lookup"><span data-stu-id="89bce-187">The SELECT list is empty.</span></span> <span data-ttu-id="89bce-188">Pokud seznam SELECT není prázdný, seznamu příkazu select se vytvořil parametrem uzlu předchází filtr a predikát mohou odkazovat na sloupce produkované tohoto seznamu výběru.</span><span class="sxs-lookup"><span data-stu-id="89bce-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>  
  
- <span data-ttu-id="89bce-189">GROUPBY je prázdný.</span><span class="sxs-lookup"><span data-stu-id="89bce-189">The GROUPBY is empty.</span></span> <span data-ttu-id="89bce-190">Pokud funkce GROUPBY není prázdná, přidání filtru by znamenal filtrování před seskupení, který není správný.</span><span class="sxs-lookup"><span data-stu-id="89bce-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>  
  
- <span data-ttu-id="89bce-191">Klauzule TOP je prázdný.</span><span class="sxs-lookup"><span data-stu-id="89bce-191">The TOP clause is empty.</span></span> <span data-ttu-id="89bce-192">Pokud klauzule TOP není prázdná, přidání filtru by znamenal filtrování než přistoupíte k horní části, který není správný.</span><span class="sxs-lookup"><span data-stu-id="89bce-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>  
  
 <span data-ttu-id="89bce-193">To se nevztahují na nerelačních uzlů jako DbConstantExpression nebo aritmetických výrazů, protože jsou vždy součástí existující SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="89bce-194">Při zjištění kořen stromu join (připojení k uzlu, který nemá připojení k nadřazené), je spuštěn nový SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="89bce-195">Všechny jeho podřízené objekty levém hřbetu spojení se agregují do této SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="89bce-196">Pokaždé, když je spuštěn nový SqlSelectStatement a tu se přidá do vstupní, může aktuální SqlSelectStatement musíte provést přidáním sloupce projekce (klauzule SELECT), pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="89bce-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="89bce-197">To se provádí pomocí metody AddDefaultColumns, která prohledá FromExtents SqlSelectStatement a přidá všechny sloupce, které seznamu rozsahů reprezentována FromExtents přináší v rozsahu do seznamu předpokládané sloupců.</span><span class="sxs-lookup"><span data-stu-id="89bce-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="89bce-198">Je to, protože v tomto okamžiku Neznámý sloupce, které odkazují jiných uzlech.</span><span class="sxs-lookup"><span data-stu-id="89bce-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="89bce-199">To lze optimalizovat do projektu pouze sloupce, které mohou být později použity.</span><span class="sxs-lookup"><span data-stu-id="89bce-199">This can be optimized to only project the columns that can later be used.</span></span>  
  
### <a name="join-flattening"></a><span data-ttu-id="89bce-200">Připojte se k vyrovnání</span><span class="sxs-lookup"><span data-stu-id="89bce-200">Join Flattening</span></span>  
 <span data-ttu-id="89bce-201">Vlastnost IsParentAJoin pomáhá určit, zda lze plochý dané připojení.</span><span class="sxs-lookup"><span data-stu-id="89bce-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="89bce-202">Konkrétně se vrátí IsParentAJoin `true` pouze pro vstupní levé podřízené spojení a pro každý DbScanExpression, který je ihned k připojení k, v takovém případě tento podřízený uzel opakovaně používá stejnou SqlSelectStatement nadřazené by tu používat.</span><span class="sxs-lookup"><span data-stu-id="89bce-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="89bce-203">Další informace najdete v tématu "Join Expressions".</span><span class="sxs-lookup"><span data-stu-id="89bce-203">For more information, see "Join Expressions".</span></span>  
  
### <a name="input-alias-redirecting"></a><span data-ttu-id="89bce-204">Vstupní Alias přesměrování</span><span class="sxs-lookup"><span data-stu-id="89bce-204">Input Alias Redirecting</span></span>  
 <span data-ttu-id="89bce-205">Přesměrování vstupní alias se provádí s tabulkou symbolů.</span><span class="sxs-lookup"><span data-stu-id="89bce-205">Input alias redirecting is accomplished with the symbol table.</span></span>  
  
 <span data-ttu-id="89bce-206">Abychom vysvětlili, přesměrování vstupní alias, najdete v prvním příkladu v [generování SQL ze stromů příkazů – osvědčené postupy](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="89bce-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="89bce-207">Existuje "a" potřeba přesměrovat na "b" v projekci.</span><span class="sxs-lookup"><span data-stu-id="89bce-207">There "a" needed to be redirected to "b" in the projection.</span></span>  
  
 <span data-ttu-id="89bce-208">Když je vytvořen objekt SqlSelectStatement, rozsah, který je vstupem uzlu je umístěn ve vlastnosti From SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="89bce-209">Symbol (< symbol_b >) je vytvořen na základě názvu vstupní vazby ("b") pro reprezentaci této míře a "AS" + < symbol_b > připojí se k němu klauzule From.</span><span class="sxs-lookup"><span data-stu-id="89bce-209">A Symbol (<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " +  <symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="89bce-210">Symbol je taky přidaný ke FromExtents vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89bce-210">The symbol is also added to the FromExtents property.</span></span>  
  
 <span data-ttu-id="89bce-211">Symbol je taky přidaný do tabulky symbolů pro propojení názvu Vstupní vazba k němu ("b", < symbol_b >).</span><span class="sxs-lookup"><span data-stu-id="89bce-211">The symbol is also added to the symbol table to link the input binding name to it ("b", <symbol_b>).</span></span>  
  
 <span data-ttu-id="89bce-212">Pokud následné uzel opětovně používá tento SqlSelectStatement, přidá položku do tabulky symbolů pro propojení názvu Vstupní vazba na tento symbol.</span><span class="sxs-lookup"><span data-stu-id="89bce-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="89bce-213">V našem příkladu by opakovaně používat SqlSelectStatement a přidejte DbProjectExpression vstupní vazby názvem "a" ("a", \< symbol_b >) do tabulky.</span><span class="sxs-lookup"><span data-stu-id="89bce-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>  
  
 <span data-ttu-id="89bce-214">Když výrazy odkazovat na název vstupní vazby uzlu, který je použití SqlSelectStatement, odkaz je přeložit pomocí tabulky symbolů správné přesměrovaného symbol.</span><span class="sxs-lookup"><span data-stu-id="89bce-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="89bce-215">Až se "a" z "a.x" vyřeší při návštěvě DbVariableReferenceExpression představující "a" it vyřeší symbol < symbol_b >.</span><span class="sxs-lookup"><span data-stu-id="89bce-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol <symbol_b>.</span></span>  
  
### <a name="join-alias-flattening"></a><span data-ttu-id="89bce-216">Připojte se k vyrovnání Alias</span><span class="sxs-lookup"><span data-stu-id="89bce-216">Join Alias Flattening</span></span>  
 <span data-ttu-id="89bce-217">Připojení k vyrovnání alias se dosáhne, když návštěv DbPropertyExpression, jak je popsáno v části s názvem DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="89bce-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>  
  
### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="89bce-218">Název sloupce a míry Alias přejmenování</span><span class="sxs-lookup"><span data-stu-id="89bce-218">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="89bce-219">Problém název sloupce a míry přejmenování alias je určeno pomocí symbolů, které pouze získat nahrazeny s aliasy ve druhé fázi generování je popsáno v části s názvem druhou fázi generování SQL: Generování příkazu řetězec.</span><span class="sxs-lookup"><span data-stu-id="89bce-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="89bce-220">První fáze generování SQL: Navštívit stromu výrazů</span><span class="sxs-lookup"><span data-stu-id="89bce-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="89bce-221">Tato část popisuje první fázi generování SQL, když je vytvořen představující výraz, který navštívil dotaz a zprostředkujících strukturu, buď SqlSelectStatement nebo SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="89bce-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>  
  
 <span data-ttu-id="89bce-222">Tato část popisuje zásady hostujícími kategorie uzlu jiný výraz a podrobnosti hostujících typy konkrétní výrazů.</span><span class="sxs-lookup"><span data-stu-id="89bce-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>  
  
### <a name="relational-non-join-nodes"></a><span data-ttu-id="89bce-223">Relační uzly (nikoli na spojení)</span><span class="sxs-lookup"><span data-stu-id="89bce-223">Relational (Non-Join) Nodes</span></span>  
 <span data-ttu-id="89bce-224">Následující typy výrazů podporují – připojení k uzlům:</span><span class="sxs-lookup"><span data-stu-id="89bce-224">The following expression types support non-join nodes:</span></span>  
  
- <span data-ttu-id="89bce-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-225">DbDistinctExpression</span></span>  
  
- <span data-ttu-id="89bce-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-226">DbFilterExpression</span></span>  
  
- <span data-ttu-id="89bce-227">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-227">DbGroupByExpression</span></span>  
  
- <span data-ttu-id="89bce-228">DbLimitExpession</span><span class="sxs-lookup"><span data-stu-id="89bce-228">DbLimitExpession</span></span>  
  
- <span data-ttu-id="89bce-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-229">DbProjectExpression</span></span>  
  
- <span data-ttu-id="89bce-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-230">DbSkipExpression</span></span>  
  
- <span data-ttu-id="89bce-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-231">DbSortExpression</span></span>  
  
 <span data-ttu-id="89bce-232">Navštívit tyto uzly následuje následujícímu vzoru:</span><span class="sxs-lookup"><span data-stu-id="89bce-232">Visiting these nodes follows the following pattern:</span></span>  
  
1. <span data-ttu-id="89bce-233">Navštivte relační vstupní a získat výsledný SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="89bce-234">Vstup do relační uzlu může být jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="89bce-234">The input to a relational node could be one of the following:</span></span>  
  
    - <span data-ttu-id="89bce-235">Relační uzlu, včetně rozsahu (DbScanExpression, například).</span><span class="sxs-lookup"><span data-stu-id="89bce-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="89bce-236">Navštívit takový uzel vrátí SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-236">Visiting such a node returns a SqlSelectStatement.</span></span>  
  
    - <span data-ttu-id="89bce-237">Operace výraz sady (UNION ALL, například).</span><span class="sxs-lookup"><span data-stu-id="89bce-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="89bce-238">Výsledek musí být zabalené v hranatých závorkách a put v klauzuli FROM nové SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>  
  
2. <span data-ttu-id="89bce-239">Zkontrolujte, zda aktuální uzel, mohou být přidány do SqlSelectStatement vytvářených vstupu.</span><span class="sxs-lookup"><span data-stu-id="89bce-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="89bce-240">V části s názvem výrazy seskupování na příkazy SQL popisuje to.</span><span class="sxs-lookup"><span data-stu-id="89bce-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="89bce-241">Pokud ne,</span><span class="sxs-lookup"><span data-stu-id="89bce-241">If not,</span></span>  
  
    - <span data-ttu-id="89bce-242">Aktuální objekt SqlSelectStatement POP.</span><span class="sxs-lookup"><span data-stu-id="89bce-242">Pop the current SqlSelectStatement object.</span></span>  
  
    - <span data-ttu-id="89bce-243">Vytvořit nový objekt SqlSelectStatement a přidejte popped SqlSelectStatement jako z nového objektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>  
  
    - <span data-ttu-id="89bce-244">Vložte nový objekt vrcholu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="89bce-244">Put the new object on top of the stack.</span></span>  
  
3. <span data-ttu-id="89bce-245">Přesměrování vazby vstupní výraz na správném symbolu ze vstupu.</span><span class="sxs-lookup"><span data-stu-id="89bce-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="89bce-246">Tyto informace se udržuje v SqlSelectStatement objektu.</span><span class="sxs-lookup"><span data-stu-id="89bce-246">This information is maintained in the SqlSelectStatement object.</span></span>  
  
4. <span data-ttu-id="89bce-247">Přidáte nový obor SymbolTable.</span><span class="sxs-lookup"><span data-stu-id="89bce-247">Add a new SymbolTable scope.</span></span>  
  
5. <span data-ttu-id="89bce-248">Získáte součást bez zadání výrazu (například projekce a predikát).</span><span class="sxs-lookup"><span data-stu-id="89bce-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>  
  
6. <span data-ttu-id="89bce-249">Vyvolat přes POP všechny objekty přidávané do globální zásobníků.</span><span class="sxs-lookup"><span data-stu-id="89bce-249">Pop all the objects added to the global stacks.</span></span>  
  
 <span data-ttu-id="89bce-250">DbSkipExpression nemají přímý ekvivalent v SQL.</span><span class="sxs-lookup"><span data-stu-id="89bce-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="89bce-251">Logicky je přeložen do:</span><span class="sxs-lookup"><span data-stu-id="89bce-251">Logically, it is translated into:</span></span>  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a><span data-ttu-id="89bce-252">Připojte se k výrazy</span><span class="sxs-lookup"><span data-stu-id="89bce-252">Join Expressions</span></span>  
 <span data-ttu-id="89bce-253">Následující považují spojení výrazů a jejich zpracování v běžným způsobem metodou VisitJoinExpression:</span><span class="sxs-lookup"><span data-stu-id="89bce-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>  
  
- <span data-ttu-id="89bce-254">DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-254">DbApplyExpression</span></span>  
  
- <span data-ttu-id="89bce-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-255">DbJoinExpression</span></span>  
  
- <span data-ttu-id="89bce-256">DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-256">DbCrossJoinExpression</span></span>  
  
 <span data-ttu-id="89bce-257">Tady jsou kroky najdete:</span><span class="sxs-lookup"><span data-stu-id="89bce-257">The following are the visit steps:</span></span>  
  
 <span data-ttu-id="89bce-258">Nejprve před podřízené objekty, je vyvolána IsParentAJoin ke kontrole, jestli je spojení uzel potomka spojení podél levém hřbetu.</span><span class="sxs-lookup"><span data-stu-id="89bce-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="89bce-259">Pokud vrátí hodnotu false, je spuštěn nový SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="89bce-260">V tomto smyslu spojení navštívené jinak zbývající uzly, jako nadřazený (připojení k uzlu) vytvoří SqlSelectStatement pro děti pravděpodobně používat.</span><span class="sxs-lookup"><span data-stu-id="89bce-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>  
  
 <span data-ttu-id="89bce-261">Za druhé zpracovávat vstupy jeden najednou.</span><span class="sxs-lookup"><span data-stu-id="89bce-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="89bce-262">Pro každý vstupní:</span><span class="sxs-lookup"><span data-stu-id="89bce-262">For each input:</span></span>  
  
1. <span data-ttu-id="89bce-263">Navštivte vstupu.</span><span class="sxs-lookup"><span data-stu-id="89bce-263">Visit the input.</span></span>  
  
2. <span data-ttu-id="89bce-264">Proces příspěvek výsledek hostujících vstup vyvoláním ProcessJoinInputResult, která zodpovídá za údržbu tabulky symbolů po navštívit podřízený výrazu spojení a pravděpodobně dokončení SqlSelectStatement vytvářených podřízené.</span><span class="sxs-lookup"><span data-stu-id="89bce-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="89bce-265">Dítěte výsledkem může být jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="89bce-265">The child's result could be one of the following:</span></span>  
  
    - <span data-ttu-id="89bce-266">SqlSelectStatement jinak než ke které se přidají nadřazené.</span><span class="sxs-lookup"><span data-stu-id="89bce-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="89bce-267">V takovém případě bude pravděpodobně nutné dokončit tak, že přidáte výchozí sloupce.</span><span class="sxs-lookup"><span data-stu-id="89bce-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="89bce-268">Pokud tento vstup byl spojení, musíte vytvořit nový symbol spojení.</span><span class="sxs-lookup"><span data-stu-id="89bce-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="89bce-269">V opačném případě vytvořte symbol normální.</span><span class="sxs-lookup"><span data-stu-id="89bce-269">Otherwise, create a normal symbol.</span></span>  
  
    - <span data-ttu-id="89bce-270">Rozsah (DbScanExpression, například), ve kterém v takovém případě se jednoduše přidá na seznam vstupů nadřazené SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="89bce-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>  
  
    - <span data-ttu-id="89bce-271">Není SqlSelectStatement, ve kterém složené závorky případu, které je zabalena.</span><span class="sxs-lookup"><span data-stu-id="89bce-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>  
  
    - <span data-ttu-id="89bce-272">Stejné SqlSelectStatement, ke kterému se přidá nadřazené.</span><span class="sxs-lookup"><span data-stu-id="89bce-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="89bce-273">V takovém případě potřebujete symboly v seznamu FromExtents nahradit jednu novou JoinSymbol představující všechny.</span><span class="sxs-lookup"><span data-stu-id="89bce-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>  
  
    - <span data-ttu-id="89bce-274">Pro první tři případy se nazývá AddFromSymbol přidejte klauzuli AS a aktualizovat tabulky symbolů.</span><span class="sxs-lookup"><span data-stu-id="89bce-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>  
  
 <span data-ttu-id="89bce-275">Třetí je zobrazeny jako podmínku připojení (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="89bce-275">Third, the join condition (if any) is visited.</span></span>  
  
### <a name="set-operations"></a><span data-ttu-id="89bce-276">Množinové operace</span><span class="sxs-lookup"><span data-stu-id="89bce-276">Set Operations</span></span>  
 <span data-ttu-id="89bce-277">Množinové operace DbUnionAllExpression DbExceptExpression a DbIntersectExpression jsou zpracovány metoda VisitSetOpExpression.</span><span class="sxs-lookup"><span data-stu-id="89bce-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="89bce-278">Vytvoří SqlBuilder tvaru</span><span class="sxs-lookup"><span data-stu-id="89bce-278">It creates a SqlBuilder of the shape</span></span>  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 <span data-ttu-id="89bce-279">Kde \<leftSqlSelectStatement > a \<rightSqlSelectStatement > jsou SqlSelectStatements získali na jednotlivých vstupních hodnot, a \<setOp > je odpovídající operace (UNION ALL příkladu).</span><span class="sxs-lookup"><span data-stu-id="89bce-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>  
  
### <a name="dbscanexpression"></a><span data-ttu-id="89bce-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-280">DbScanExpression</span></span>  
 <span data-ttu-id="89bce-281">Je-li zobrazeny v kontextu spojení (jako vstup do spojení, která je levého potomka jiné připojení), vrátí DbScanExpression SqlBuilder s cílem SQL pro odpovídající cíl, který definuje dotaz, tabulka nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="89bce-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="89bce-282">V opačném případě nová SqlSelectStatement se vytvoří s pole FROM nastavit tak, aby odpovídaly odpovídající cíle.</span><span class="sxs-lookup"><span data-stu-id="89bce-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>  
  
### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="89bce-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-283">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="89bce-284">Navštivte DbVariableReferenceExpression vrátí Symbol odpovídající tento výraz odkazu na proměnnou podle pohled nahoru v tabulce symbolů.</span><span class="sxs-lookup"><span data-stu-id="89bce-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="89bce-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-285">DbPropertyExpression</span></span>  
 <span data-ttu-id="89bce-286">Spojení sloučení alias je identifikovat a zpracovány při návštěvě DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="89bce-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>  
  
 <span data-ttu-id="89bce-287">Vlastnost Instance je nejprve nenavštívil a výsledkem je Symbol, JoinSymbol nebo SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="89bce-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="89bce-288">Tady je způsob zpracování těchto třech případech:</span><span class="sxs-lookup"><span data-stu-id="89bce-288">Here is how these three cases are handled:</span></span>  
  
- <span data-ttu-id="89bce-289">Pokud se vrátí JoinSymbol, než jeho NameToExtent vlastnost obsahuje symbol pro vlastnost potřebné.</span><span class="sxs-lookup"><span data-stu-id="89bce-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="89bce-290">Pokud spojení symbol představuje vnořené spojení, vrátí se nový pár Symbol symbolem spojení ke sledování symbol, který se použije jako instance alias a symbol představující skutečný vlastnost pro další řešení.</span><span class="sxs-lookup"><span data-stu-id="89bce-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>  
  
- <span data-ttu-id="89bce-291">Pokud se vrátí SymbolPair a části sloupce je symbol, spojení, znovu vrátí symbol spojení, ale nyní je vlastnost sloupec aktualizovat tak, aby odkazoval na vlastnost reprezentována výrazem aktuální vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89bce-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="89bce-292">Jinak se vrátí SqlBuilder zdrojem SymbolPair jako alias a symbolů pro aktuální vlastnost jako sloupec.</span><span class="sxs-lookup"><span data-stu-id="89bce-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>  
  
- <span data-ttu-id="89bce-293">Pokud je Symbol, navštivte metoda vrátí SqlBuilder metodou instance jako alias a název jako název sloupce.</span><span class="sxs-lookup"><span data-stu-id="89bce-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>  
  
### <a name="dbnewinstanceexpression"></a><span data-ttu-id="89bce-294">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-294">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="89bce-295">Při použití jako vlastnost DbProjectExpression projekce DbNewInstanceExpression vytváří čárkou oddělený seznam argumentů pro reprezentaci předpokládané sloupce.</span><span class="sxs-lookup"><span data-stu-id="89bce-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>  
  
 <span data-ttu-id="89bce-296">Pokud DbNewInstanceExpression má návratový typ kolekce a definuje novou kolekci výrazů ve formě argumentů, následující tři případy se řeší samostatně:</span><span class="sxs-lookup"><span data-stu-id="89bce-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>  
  
- <span data-ttu-id="89bce-297">Pokud DbNewInstanceExpression DbElementExpression jako jediný argument, je přeložen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="89bce-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 <span data-ttu-id="89bce-298">Pokud DbNewInstanceExpression nemá žádné argumenty (představuje prázdné tabulky), DbNewInstanceExpression je přeložit na:</span><span class="sxs-lookup"><span data-stu-id="89bce-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 <span data-ttu-id="89bce-299">V opačném případě DbNewInstanceExpression sestavení žebříku sjednocení všech argumentů:</span><span class="sxs-lookup"><span data-stu-id="89bce-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a><span data-ttu-id="89bce-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-300">DbFunctionExpression</span></span>  
 <span data-ttu-id="89bce-301">Canonical a integrované funkce jsou zpracovány stejně: Pokud se vyžadují speciální zacházení (TRIM(string) k LTRIM(RTRIM(string), například), je vyvolána odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="89bce-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="89bce-302">V opačném případě jsou přeloženy na FunctionName (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="89bce-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>  
  
 <span data-ttu-id="89bce-303">Slovníky se používají k udržovat přehled o funkcích, které potřebují zvláštní zacházení a jejich odpovídající obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="89bce-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>  
  
 <span data-ttu-id="89bce-304">Uživatelem definované funkce jsou tanslated k NamespaceName.FunctionName (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="89bce-304">User-defined functions are tanslated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>  
  
### <a name="dbelementexpression"></a><span data-ttu-id="89bce-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-305">DbElementExpression</span></span>  
 <span data-ttu-id="89bce-306">Metoda, která se navštíví DbElementExpression se vyvolá pouze navštívili DbElementExpression, když se používá k reprezentování skalární poddotaz.</span><span class="sxs-lookup"><span data-stu-id="89bce-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="89bce-307">Proto DbElementExpression překládá do dokončení SqlSelectStatement a přidá závorky kolem něj.</span><span class="sxs-lookup"><span data-stu-id="89bce-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>  
  
### <a name="dbquantifierexpression"></a><span data-ttu-id="89bce-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-308">DbQuantifierExpression</span></span>  
 <span data-ttu-id="89bce-309">V závislosti na typu výrazu (některé nebo všechny), je přeložen DbQuantifierExpression jako:</span><span class="sxs-lookup"><span data-stu-id="89bce-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated it as:</span></span>  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a><span data-ttu-id="89bce-310">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-310">DbNotExpression</span></span>  
 <span data-ttu-id="89bce-311">V některých případech je možné sbalit překladu třída DbNotExpression s jeho vstupní výraz.</span><span class="sxs-lookup"><span data-stu-id="89bce-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="89bce-312">Příklad:</span><span class="sxs-lookup"><span data-stu-id="89bce-312">For example:</span></span>  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 <span data-ttu-id="89bce-313">Z důvodů, proč se provádí druhý sbalit totiž nedostatečnou zavedených zprostředkovatelem překladu DbQuantifierExpression z type All.</span><span class="sxs-lookup"><span data-stu-id="89bce-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="89bce-314">Entity Framework proto nelze provést zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="89bce-314">Thus the Entity Framework could not have done the simplification.</span></span>  
  
### <a name="dbisemptyexpression"></a><span data-ttu-id="89bce-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="89bce-315">DbIsEmptyExpression</span></span>  
 <span data-ttu-id="89bce-316">DbIsEmptyExpression je přeložen jako:</span><span class="sxs-lookup"><span data-stu-id="89bce-316">DbIsEmptyExpression is translated as:</span></span>  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="89bce-317">Druhá fáze generování SQL: Generování příkazu řetězec</span><span class="sxs-lookup"><span data-stu-id="89bce-317">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="89bce-318">Při generování řetězec příkazu SQL, SqlSelectStatement vytvoří skutečné aliasy pro symboly, které řeší problém název sloupce a míry přejmenování alias.</span><span class="sxs-lookup"><span data-stu-id="89bce-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>  
  
 <span data-ttu-id="89bce-319">Přejmenování alias rozsahu vyvolá se při zápisu objektu SqlSelectStatement do řetězce.</span><span class="sxs-lookup"><span data-stu-id="89bce-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="89bce-320">Nejprve vytvořte seznam všechny aliasy, které používá vnější rozsah.</span><span class="sxs-lookup"><span data-stu-id="89bce-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="89bce-321">Pokud koliduje s žádným z rozsahů vnější, získá každý symbol FromExtents (nebo AllJoinExtents, pokud je jiná než null), přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="89bce-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="89bce-322">V případě potřeby přejmenování to nebude v konfliktu s žádným z rozsahů shromážděných v AllExtentNames.</span><span class="sxs-lookup"><span data-stu-id="89bce-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>  
  
 <span data-ttu-id="89bce-323">Přejmenování sloupců, nastane při zápisu Symbol – objekt na řetězec.</span><span class="sxs-lookup"><span data-stu-id="89bce-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="89bce-324">AddDefaultColumns v první fázi určil, pokud symbol určité sloupce musí být přejmenována.</span><span class="sxs-lookup"><span data-stu-id="89bce-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="89bce-325">Ve druhé fázi dochází pouze přejmenovat a ujistěte se, že název vytvořeného není v konfliktu s používán AllColumnNames</span><span class="sxs-lookup"><span data-stu-id="89bce-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>  
  
 <span data-ttu-id="89bce-326">Vytvořit jedinečné názvy pro aliasy rozsahu a pro sloupce, použijte _n < existing_name >, kde n je nejmenší alias, který nebyl dosud použit.</span><span class="sxs-lookup"><span data-stu-id="89bce-326">To produce unique names both for extent aliases and for columns, use <existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="89bce-327">Globální seznam všechny aliasy zvyšuje potřebu kaskádové přejmenuje.</span><span class="sxs-lookup"><span data-stu-id="89bce-327">The global list of all aliases increases the need for cascading renames.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89bce-328">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89bce-328">See also</span></span>

- [<span data-ttu-id="89bce-329">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="89bce-329">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
