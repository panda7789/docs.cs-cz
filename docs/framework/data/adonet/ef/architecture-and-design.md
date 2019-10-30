---
title: Architektura a návrh
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 35fbc39db23a2b08ab926e122d2f1eb1806a369b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040028"
---
# <a name="architecture-and-design"></a><span data-ttu-id="9d34e-102">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="9d34e-102">Architecture and Design</span></span>

<span data-ttu-id="9d34e-103">Modul pro generování SQL ve [vzorovém poskytovateli](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) je implementován jako návštěvník ve stromu výrazů, který představuje strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="9d34e-103">The SQL generation module in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="9d34e-104">Generování se provádí v rámci jednoho průchodu ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-104">The generation is done in a single pass over the expression tree.</span></span>

<span data-ttu-id="9d34e-105">Uzly stromu jsou zpracovávány zdola nahoru.</span><span class="sxs-lookup"><span data-stu-id="9d34e-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="9d34e-106">Nejprve je vytvořena zprostředkující struktura: SqlSelectStatement nebo SqlBuilder, jak implementace ISqlFragment.</span><span class="sxs-lookup"><span data-stu-id="9d34e-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="9d34e-107">Dále je příkaz String jazyka SQL vytvořen z této struktury.</span><span class="sxs-lookup"><span data-stu-id="9d34e-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="9d34e-108">Existují dva důvody pro mezilehlé struktury:</span><span class="sxs-lookup"><span data-stu-id="9d34e-108">There are two reasons for the intermediate structure:</span></span>

- <span data-ttu-id="9d34e-109">Logicky se vyplní příkaz SQL SELECT mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="9d34e-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="9d34e-110">Uzly, které jsou součástí klauzule FROM, jsou navštíveny před uzly, které jsou součástí klauzule WHERE, GROUP BY a ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="9d34e-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>

- <span data-ttu-id="9d34e-111">Chcete-li přejmenovat aliasy, je nutné identifikovat všechny použité aliasy, abyste se vyhnuli kolizím při přejmenování.</span><span class="sxs-lookup"><span data-stu-id="9d34e-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="9d34e-112">Chcete-li odložit možnosti přejmenování v SqlBuilder, použijte objekty symbolů pro reprezentaci sloupců, které jsou kandidáty k přejmenování.</span><span class="sxs-lookup"><span data-stu-id="9d34e-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>

<span data-ttu-id="9d34e-113">![Znázorňuje](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="9d34e-113">![Diagram](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>

<span data-ttu-id="9d34e-114">V první fázi při návštěvě stromu výrazů jsou výrazy seskupeny do SqlSelectStatements, spojení jsou shrnuty a jsou shrnuty aliasy.</span><span class="sxs-lookup"><span data-stu-id="9d34e-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="9d34e-115">Během tohoto průchodu objekty symbolů reprezentují sloupce nebo vstupní aliasy, které mohou být přejmenovány.</span><span class="sxs-lookup"><span data-stu-id="9d34e-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>

<span data-ttu-id="9d34e-116">Ve druhé fázi se při vytváření skutečného řetězce přejmenují aliasy.</span><span class="sxs-lookup"><span data-stu-id="9d34e-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>

## <a name="data-structures"></a><span data-ttu-id="9d34e-117">Datové struktury</span><span class="sxs-lookup"><span data-stu-id="9d34e-117">Data Structures</span></span>

<span data-ttu-id="9d34e-118">Tato část popisuje typy používané v [ukázkovém poskytovateli](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , který používáte k vytvoření příkazu SQL.</span><span class="sxs-lookup"><span data-stu-id="9d34e-118">This section discusses the types used in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) that you use to build a SQL statement.</span></span>

### <a name="isqlfragment"></a><span data-ttu-id="9d34e-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="9d34e-119">ISqlFragment</span></span>

<span data-ttu-id="9d34e-120">Tato část se zabývá třídami, které implementují rozhraní ISqlFragment, které slouží ke dvěma účelům:</span><span class="sxs-lookup"><span data-stu-id="9d34e-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>

- <span data-ttu-id="9d34e-121">Společný návratový typ pro všechny metody návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="9d34e-121">A common return type for all the visitor methods.</span></span>

- <span data-ttu-id="9d34e-122">Poskytuje metodu pro zápis konečného řetězce SQL.</span><span class="sxs-lookup"><span data-stu-id="9d34e-122">Gives a method to write the final SQL string.</span></span>

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a><span data-ttu-id="9d34e-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="9d34e-123">SqlBuilder</span></span>

<span data-ttu-id="9d34e-124">SqlBuilder je shromáždění zařízení pro finální řetězec SQL, podobně jako StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="9d34e-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="9d34e-125">Skládá se z řetězců, které tvoří finální SQL, spolu s ISqlFragments, které je možné převést do řetězců.</span><span class="sxs-lookup"><span data-stu-id="9d34e-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a><span data-ttu-id="9d34e-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="9d34e-126">SqlSelectStatement</span></span>

<span data-ttu-id="9d34e-127">SqlSelectStatement představuje kanonický příkaz SQL SELECT obrazce "vybrat...</span><span class="sxs-lookup"><span data-stu-id="9d34e-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="9d34e-128">Z..</span><span class="sxs-lookup"><span data-stu-id="9d34e-128">FROM  ..</span></span> <span data-ttu-id="9d34e-129">KDE...</span><span class="sxs-lookup"><span data-stu-id="9d34e-129">WHERE …</span></span> <span data-ttu-id="9d34e-130">SESKUPIT PODLE...</span><span class="sxs-lookup"><span data-stu-id="9d34e-130">GROUP BY …</span></span> <span data-ttu-id="9d34e-131">ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="9d34e-131">ORDER BY".</span></span>

<span data-ttu-id="9d34e-132">Jednotlivé klauzule jazyka SQL jsou reprezentovány pomocí StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="9d34e-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="9d34e-133">Kromě toho sleduje, zda je zadána odlišná a zda je příkaz zcela na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="9d34e-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="9d34e-134">Pokud příkaz není zcela na nejvyšší úrovni, klauzule ORDER BY je vynechána, pokud příkaz nemá také klauzuli TOP.</span><span class="sxs-lookup"><span data-stu-id="9d34e-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>

<span data-ttu-id="9d34e-135">FromExtents obsahuje seznam vstupů pro příkaz SELECT.</span><span class="sxs-lookup"><span data-stu-id="9d34e-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="9d34e-136">V tomto případě je obvykle pouze jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="9d34e-136">There is usually just one element in this.</span></span> <span data-ttu-id="9d34e-137">Příkazy SELECT pro spojení mohou dočasně mít více než jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="9d34e-137">SELECT statements for joins may temporarily have more than one element.</span></span>

<span data-ttu-id="9d34e-138">Pokud je příkaz SELECT vytvořen pomocí uzlu JOIN, SqlSelectStatement udržuje seznam všech rozsahů, které byly shrnuty v JOIN v AllJoinExtents.</span><span class="sxs-lookup"><span data-stu-id="9d34e-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="9d34e-139">OuterExtents představuje vnější odkazy na SqlSelectStatement a používá se pro přejmenování vstupního aliasu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>

```csharp
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

#### <a name="topclause"></a><span data-ttu-id="9d34e-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="9d34e-140">TopClause</span></span>

<span data-ttu-id="9d34e-141">TopClause představuje výraz TOP v SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="9d34e-142">Vlastnost TopCount určuje, kolik HORNÍch řádků by mělo být vybráno.</span><span class="sxs-lookup"><span data-stu-id="9d34e-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="9d34e-143">Pokud má WithTies hodnotu true, TopClause byl sestaven z DbLimitExpression.</span><span class="sxs-lookup"><span data-stu-id="9d34e-143">When WithTies is true, the TopClause was built from a DbLimitExpression.</span></span>

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a><span data-ttu-id="9d34e-144">Symboly</span><span class="sxs-lookup"><span data-stu-id="9d34e-144">Symbols</span></span>

<span data-ttu-id="9d34e-145">Třídy související s symboly a tabulka symbolů provádějí přejmenování vstupního aliasu, sloučení aliasů a přejmenování aliasu sloupce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>

<span data-ttu-id="9d34e-146">Třída symbol reprezentuje rozsah, vnořený výběrový příkaz nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="9d34e-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="9d34e-147">Používá se místo skutečného aliasu pro povolení přejmenování po jeho použití a také další informace pro artefakt, který představuje (například typ).</span><span class="sxs-lookup"><span data-stu-id="9d34e-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>

```csharp
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

<span data-ttu-id="9d34e-148">Název ukládá původní alias pro zastoupený rozsah, vnořený příkaz SELECT nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="9d34e-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>

<span data-ttu-id="9d34e-149">NewName ukládá alias, který se použije v příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="9d34e-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="9d34e-150">Je původně nastavené na název a v případě potřeby je přejmenovaná, pokud se generuje finální dotaz řetězce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>

<span data-ttu-id="9d34e-151">Typ je vhodný pouze pro symboly představující rozsahy a vnořené příkazy SELECT.</span><span class="sxs-lookup"><span data-stu-id="9d34e-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>

#### <a name="symbolpair"></a><span data-ttu-id="9d34e-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="9d34e-152">SymbolPair</span></span>

<span data-ttu-id="9d34e-153">Třída SymbolPair řeší sloučení záznamů.</span><span class="sxs-lookup"><span data-stu-id="9d34e-153">The SymbolPair class addresses record flattening.</span></span>

<span data-ttu-id="9d34e-154">Vezměte v úvahu výraz vlastnosti D (v, "J3. J2. J1. a. x"), kde v je VarRef, J1, J2, J3, je rozsah a x je sloupce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>

<span data-ttu-id="9d34e-155">To je třeba přeložit do {j}. {x}.</span><span class="sxs-lookup"><span data-stu-id="9d34e-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="9d34e-156">Zdrojové pole představuje nejvzdálenější SqlStatement, představující výraz Join (řekněme J2); Toto je vždy symbol spojení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="9d34e-157">Sloupcové pole se přesune z jednoho symbolu spojení na další, dokud se nezastaví na symbolu bez spojení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="9d34e-158">Tato zpráva se vrátí při návštěvě DbPropertyExpression, ale nikdy se nepřidá do SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="9d34e-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a><span data-ttu-id="9d34e-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="9d34e-159">JoinSymbol</span></span>

<span data-ttu-id="9d34e-160">Symbol spojení je symbol, který představuje vnořený příkaz SELECT s připojením nebo vstupem spojení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>

```csharp
internal sealed class JoinSymbol : Symbol {
   internal List<Symbol> ColumnList {get, set}
   internal List<Symbol> ExtentList {get}
   internal List<Symbol> FlattenedExtentList {get, set}
   internal Dictionary<string, Symbol> NameToExtent {get}
   internal bool IsNestedJoin {get, set}

   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)
}
```

<span data-ttu-id="9d34e-161">ColumnList představuje seznam sloupců v klauzuli SELECT, pokud tento symbol představuje příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="9d34e-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="9d34e-162">ExtentList je seznam rozsahů v klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="9d34e-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="9d34e-163">Pokud je spojení více rozsahů shrnuto na nejvyšší úrovni, FlattenedExtentList sleduje rozsahy, aby bylo zajištěno, že se aliasy rozsahu přejmenují správně.</span><span class="sxs-lookup"><span data-stu-id="9d34e-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>

<span data-ttu-id="9d34e-164">NameToExtent má všechny rozsahy v ExtentList jako slovník.</span><span class="sxs-lookup"><span data-stu-id="9d34e-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="9d34e-165">IsNestedJoin se používá k určení, zda je JoinSymbol běžným spojovacím symbolem nebo s odpovídajícím SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>

<span data-ttu-id="9d34e-166">Všechny seznamy jsou nastavené přesně jednou a pak se použijí pro vyhledávání nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="9d34e-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>

#### <a name="symboltable"></a><span data-ttu-id="9d34e-167">Symbolová</span><span class="sxs-lookup"><span data-stu-id="9d34e-167">SymbolTable</span></span>

<span data-ttu-id="9d34e-168">Symbolová proměnná se používá k překladu názvů proměnných na symboly.</span><span class="sxs-lookup"><span data-stu-id="9d34e-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="9d34e-169">Symbolová sada je implementována jako zásobník s novou položkou pro každý obor.</span><span class="sxs-lookup"><span data-stu-id="9d34e-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="9d34e-170">Vyhledávání vyhledá v horní části zásobníku do dolní části, dokud se nenajde položka.</span><span class="sxs-lookup"><span data-stu-id="9d34e-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

<span data-ttu-id="9d34e-171">Pro jednu instanci modulu SQL Generation existuje pouze jedna pole typu symbol.</span><span class="sxs-lookup"><span data-stu-id="9d34e-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="9d34e-172">Obory se zadávají a ukončí pro každý relační uzel.</span><span class="sxs-lookup"><span data-stu-id="9d34e-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="9d34e-173">Všechny symboly v dřívějších oborech jsou viditelné pro pozdější obory, pokud nejsou skryté jinými symboly se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="9d34e-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>

### <a name="global-state-for-the-visitor"></a><span data-ttu-id="9d34e-174">Globální stav návštěvníka</span><span class="sxs-lookup"><span data-stu-id="9d34e-174">Global State for the Visitor</span></span>

<span data-ttu-id="9d34e-175">Chcete-li pomoct při přejmenování aliasů a sloupců, udržujte seznam všech názvů sloupců (AllColumnNames) a aliasy rozsahu (AllExtentNames), které byly použity v prvním průchodu ve stromu dotazu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="9d34e-176">Tabulka symbolů překládá názvy proměnných na symboly.</span><span class="sxs-lookup"><span data-stu-id="9d34e-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="9d34e-177">IsVarRefSingle se používá jenom pro účely ověření, není to bezpodmínečně nutné.</span><span class="sxs-lookup"><span data-stu-id="9d34e-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>

<span data-ttu-id="9d34e-178">Dvě zásobníky používané přes CurrentSelectStatement a IsParentAJoin se používají k předání "parametrů" z nadřazených uzlů do podřízených uzlů, protože vzor návštěvníka nám neumožňuje předat parametry.</span><span class="sxs-lookup"><span data-stu-id="9d34e-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>

```csharp
internal Dictionary<string, int> AllExtentNames {get}
internal Dictionary<string, int> AllColumnNames {get}
SymbolTable symbolTable = new SymbolTable();
bool isVarRefSingle = false;

Stack<SqlSelectStatement> selectStatementStack;
private SqlSelectStatement CurrentSelectStatement{get}

Stack<bool> isParentAJoinStack;
private bool IsParentAJoin{get}
```

## <a name="common-scenarios"></a><span data-ttu-id="9d34e-179">Běžné scénáře</span><span class="sxs-lookup"><span data-stu-id="9d34e-179">Common Scenarios</span></span>

<span data-ttu-id="9d34e-180">Tato část se zabývá běžnými scénáři poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="9d34e-180">This section discusses common provider scenarios.</span></span>

### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="9d34e-181">Seskupení uzlů výrazů do příkazů SQL</span><span class="sxs-lookup"><span data-stu-id="9d34e-181">Grouping Expression Nodes into SQL Statements</span></span>

<span data-ttu-id="9d34e-182">SqlSelectStatement se vytvoří při zjištění prvního relačního uzlu (obvykle DbScanExpression) při návštěvě stromu od dolní části.</span><span class="sxs-lookup"><span data-stu-id="9d34e-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="9d34e-183">Chcete-li vytvořit příkaz SQL SELECT s co nejmenším počtem vnořených dotazů, můžete agregovat tolik svých nadřazených uzlů, kolik je možné v tomto SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>

<span data-ttu-id="9d34e-184">Rozhodnutí o tom, zda daný (relační) uzel lze přidat do aktuálního SqlSelectStatement (který byl vrácen při návštěvě vstupu), nebo pokud je nutné spustit nový příkaz, je vypočítán metodou kompatibilní a závisí na tom, co je již v SqlSelectStatement, která závisí na tom, jaké uzly byly pod daným uzlem.</span><span class="sxs-lookup"><span data-stu-id="9d34e-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>

<span data-ttu-id="9d34e-185">V případě, že jsou klauzule příkazů SQL vyhodnocovány po klauzulích, kde jsou uzly zvažovány pro sloučení prázdné, uzel nelze do aktuálního příkazu přidat.</span><span class="sxs-lookup"><span data-stu-id="9d34e-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="9d34e-186">Pokud je například dalším uzlem filtr, tento uzel lze do aktuálního SqlSelectStatement začlenit pouze v případě, že platí následující:</span><span class="sxs-lookup"><span data-stu-id="9d34e-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>

- <span data-ttu-id="9d34e-187">Seznam pro výběr je prázdný.</span><span class="sxs-lookup"><span data-stu-id="9d34e-187">The SELECT list is empty.</span></span> <span data-ttu-id="9d34e-188">Pokud seznam SELECT není prázdný, seznam Select byl vytvořen uzlem před filtrem a predikát může odkazovat na sloupce vytvářené tímto seznamem SELECT.</span><span class="sxs-lookup"><span data-stu-id="9d34e-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>

- <span data-ttu-id="9d34e-189">GROUPBY je prázdný.</span><span class="sxs-lookup"><span data-stu-id="9d34e-189">The GROUPBY is empty.</span></span> <span data-ttu-id="9d34e-190">Pokud GROUPBY není prázdné, přidání filtru by znamenalo filtrování před seskupením, což není správné.</span><span class="sxs-lookup"><span data-stu-id="9d34e-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>

- <span data-ttu-id="9d34e-191">Klauzule TOP je prázdná.</span><span class="sxs-lookup"><span data-stu-id="9d34e-191">The TOP clause is empty.</span></span> <span data-ttu-id="9d34e-192">Pokud klauzule TOP není prázdná, přidání filtru by znamenalo filtrování před provedením HORNÍch, což není správné.</span><span class="sxs-lookup"><span data-stu-id="9d34e-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>

<span data-ttu-id="9d34e-193">To se nevztahuje na nerelační uzly, jako je DbConstantExpression nebo aritmetické výrazy, protože jsou vždycky zahrnuté jako součást existující SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>

<span data-ttu-id="9d34e-194">Také při zjištění kořene stromu spojení (spojovací uzel, který nemá nadřazený objekt JOIN) je spuštěn nový SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="9d34e-195">Všechna jeho levá hřbet – děti jsou shrnuty do tohoto SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>

<span data-ttu-id="9d34e-196">Když se spustí nový SqlSelectStatement a do vstupu se přidá aktuální SqlSelectStatement, může se stát, že aktuální se musí dokončit přidáním sloupců projekce (klauzule SELECT), pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="9d34e-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="9d34e-197">To se provádí s metodou AddDefaultColumns, která se zabývá FromExtentsem SqlSelectStatement a přidává všechny sloupce, které seznam rozsahů reprezentovaných FromExtents přináší v oboru do seznamu projektových sloupců.</span><span class="sxs-lookup"><span data-stu-id="9d34e-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="9d34e-198">To je provedeno, protože v tomto okamžiku není známo, na které sloupce odkazují jiné uzly.</span><span class="sxs-lookup"><span data-stu-id="9d34e-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="9d34e-199">To může být optimalizováno pouze na projekt, který lze později použít.</span><span class="sxs-lookup"><span data-stu-id="9d34e-199">This can be optimized to only project the columns that can later be used.</span></span>

### <a name="join-flattening"></a><span data-ttu-id="9d34e-200">Spojit sloučení</span><span class="sxs-lookup"><span data-stu-id="9d34e-200">Join Flattening</span></span>

<span data-ttu-id="9d34e-201">Vlastnost IsParentAJoin pomáhá určit, zda lze dané spojení Sloučit.</span><span class="sxs-lookup"><span data-stu-id="9d34e-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="9d34e-202">Konkrétně IsParentAJoin vrací `true` pouze pro levý podřízený objekt JOIN a pro každý DbScanExpression, který je okamžitým vstupem ke spojení. v takovém případě bude podřízený uzel znovu používat stejný SqlSelectStatement, který by měl nadřazený objekt později použít.</span><span class="sxs-lookup"><span data-stu-id="9d34e-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="9d34e-203">Další informace najdete v tématu výrazy JOIN.</span><span class="sxs-lookup"><span data-stu-id="9d34e-203">For more information, see "Join Expressions".</span></span>

### <a name="input-alias-redirecting"></a><span data-ttu-id="9d34e-204">Přesměrování vstupního aliasu</span><span class="sxs-lookup"><span data-stu-id="9d34e-204">Input Alias Redirecting</span></span>

<span data-ttu-id="9d34e-205">Přesměrování vstupního aliasu je provedeno s tabulkou symbolů.</span><span class="sxs-lookup"><span data-stu-id="9d34e-205">Input alias redirecting is accomplished with the symbol table.</span></span>

<span data-ttu-id="9d34e-206">Chcete-li vysvětlit přesměrování vstupního aliasu, podívejte se na první příklad v tématu [generování SQL z příkazových stromů – osvědčené postupy](generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="9d34e-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="9d34e-207">V projekci je potřeba přesměrovat "a" na "b".</span><span class="sxs-lookup"><span data-stu-id="9d34e-207">There "a" needed to be redirected to "b" in the projection.</span></span>

<span data-ttu-id="9d34e-208">Když je vytvořen objekt SqlSelectStatement, rozsah, který je vstupem do uzlu, je umístěn do vlastnosti from třídy SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="9d34e-209">Symbol (\<symbol_b >) se vytvoří na základě názvu vstupní vazby ("b"), který bude představovat tento rozsah, a > se k klauzuli FROM připojí \<symbol_b.</span><span class="sxs-lookup"><span data-stu-id="9d34e-209">A Symbol (\<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " + \<symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="9d34e-210">Symbol je také přidán do vlastnosti FromExtents.</span><span class="sxs-lookup"><span data-stu-id="9d34e-210">The symbol is also added to the FromExtents property.</span></span>

<span data-ttu-id="9d34e-211">Symbol je také přidán do tabulky symbolů, aby propojí název vstupní vazby s ním ("b", \<symbol_b >).</span><span class="sxs-lookup"><span data-stu-id="9d34e-211">The symbol is also added to the symbol table to link the input binding name to it ("b", \<symbol_b>).</span></span>

<span data-ttu-id="9d34e-212">Pokud následující uzel znovu použije tuto SqlSelectStatement, přidá položku do tabulky symbolů, aby propojí svůj název vstupní vazby s tímto symbolem.</span><span class="sxs-lookup"><span data-stu-id="9d34e-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="9d34e-213">V našem příkladu DbProjectExpression s názvem vstupní vazby "a" by znovu použil SqlSelectStatement a přidat ("a", \< symbol_b >) do tabulky.</span><span class="sxs-lookup"><span data-stu-id="9d34e-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>

<span data-ttu-id="9d34e-214">Když výrazy odkazují na název vstupní vazby uzlu, který znovu používá SqlSelectStatement, tento odkaz se vyřeší pomocí tabulky symbolů do správného přesměrovaného symbolu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="9d34e-215">Při řešení "a" z "a. x" při návštěvě DbVariableReferenceExpression představujícího "a" se přeloží na symbol \<symbol_b >.</span><span class="sxs-lookup"><span data-stu-id="9d34e-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol \<symbol_b>.</span></span>

### <a name="join-alias-flattening"></a><span data-ttu-id="9d34e-216">Spojit sloučení aliasů</span><span class="sxs-lookup"><span data-stu-id="9d34e-216">Join Alias Flattening</span></span>

<span data-ttu-id="9d34e-217">Sloučení aliasu JOIN se dosáhne při návštěvě DbPropertyExpression, jak je popsáno v části s názvem DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="9d34e-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>

### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="9d34e-218">Název sloupce a přejmenování aliasu rozsahu</span><span class="sxs-lookup"><span data-stu-id="9d34e-218">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="9d34e-219">Problémy s názvem sloupce a přejmenováním aliasu rozsahu jsou adresovány pomocí symbolů, které nahradí pouze aliasy ve druhé fázi generování popsané v části s názvem druhá fáze generování kódu SQL: vygenerování příkazu řetězce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="9d34e-220">První fáze generování SQL: návštěvy stromu výrazů</span><span class="sxs-lookup"><span data-stu-id="9d34e-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="9d34e-221">Tato část popisuje první fázi generování kódu SQL, pokud je výraz reprezentující dotaz navštíven a je vytvořena zprostředkující struktura, buď SqlSelectStatement nebo SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="9d34e-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>

<span data-ttu-id="9d34e-222">Tato část popisuje principy navštívení různých kategorií uzlů výrazů a podrobnosti o návštěvě specifických typů výrazů.</span><span class="sxs-lookup"><span data-stu-id="9d34e-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>

### <a name="relational-non-join-nodes"></a><span data-ttu-id="9d34e-223">Relační uzly (bez spojení)</span><span class="sxs-lookup"><span data-stu-id="9d34e-223">Relational (Non-Join) Nodes</span></span>

<span data-ttu-id="9d34e-224">Následující typy výrazů podporují uzly bez připojení:</span><span class="sxs-lookup"><span data-stu-id="9d34e-224">The following expression types support non-join nodes:</span></span>

- <span data-ttu-id="9d34e-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-225">DbDistinctExpression</span></span>

- <span data-ttu-id="9d34e-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-226">DbFilterExpression</span></span>

- <span data-ttu-id="9d34e-227">DbGroupAggregate</span><span class="sxs-lookup"><span data-stu-id="9d34e-227">DbGroupByExpression</span></span>

- <span data-ttu-id="9d34e-228">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-228">DbLimitExpression</span></span>

- <span data-ttu-id="9d34e-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-229">DbProjectExpression</span></span>

- <span data-ttu-id="9d34e-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-230">DbSkipExpression</span></span>

- <span data-ttu-id="9d34e-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-231">DbSortExpression</span></span>

<span data-ttu-id="9d34e-232">Návštěvy těchto uzlů se řídí následujícím vzorem:</span><span class="sxs-lookup"><span data-stu-id="9d34e-232">Visiting these nodes follows the following pattern:</span></span>

1. <span data-ttu-id="9d34e-233">Přejděte na relační vstup a získejte výsledný SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="9d34e-234">Vstup do relačního uzlu může být jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="9d34e-234">The input to a relational node could be one of the following:</span></span>

    - <span data-ttu-id="9d34e-235">Relační uzel, včetně rozsahu (například DbScanExpression).</span><span class="sxs-lookup"><span data-stu-id="9d34e-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="9d34e-236">Návštěvy takového uzlu vrátí SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-236">Visiting such a node returns a SqlSelectStatement.</span></span>

    - <span data-ttu-id="9d34e-237">Výraz operace set (například UNION ALL).</span><span class="sxs-lookup"><span data-stu-id="9d34e-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="9d34e-238">Výsledek musí být zabalen do závorek a musí být vložen do klauzule FROM nového SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>

2. <span data-ttu-id="9d34e-239">Ověřte, zda je možné přidat aktuální uzel do SqlSelectStatement vyprodukovaného vstupem.</span><span class="sxs-lookup"><span data-stu-id="9d34e-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="9d34e-240">Popisuje oddíl s názvem výrazy seskupení do příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="9d34e-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="9d34e-241">Pokud ne,</span><span class="sxs-lookup"><span data-stu-id="9d34e-241">If not,</span></span>

    - <span data-ttu-id="9d34e-242">Byl automaticky zobrazen aktuální objekt SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-242">Pop the current SqlSelectStatement object.</span></span>

    - <span data-ttu-id="9d34e-243">Vytvořte nový objekt SqlSelectStatement a přidejte jako z nového objektu SqlSelectStatement SqlSelectStatementy se systémem.</span><span class="sxs-lookup"><span data-stu-id="9d34e-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>

    - <span data-ttu-id="9d34e-244">Vložte nový objekt nad zásobník.</span><span class="sxs-lookup"><span data-stu-id="9d34e-244">Put the new object on top of the stack.</span></span>

3. <span data-ttu-id="9d34e-245">Přesměruje vazbu vstupního výrazu na správný symbol ze vstupu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="9d34e-246">Tyto informace jsou uchovávány v objektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-246">This information is maintained in the SqlSelectStatement object.</span></span>

4. <span data-ttu-id="9d34e-247">Přidejte nový obor typu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-247">Add a new SymbolTable scope.</span></span>

5. <span data-ttu-id="9d34e-248">Navštivte nevstupní část výrazu (například projekce a predikát).</span><span class="sxs-lookup"><span data-stu-id="9d34e-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>

6. <span data-ttu-id="9d34e-249">Všechny objekty přidané do globálních zásobníků.</span><span class="sxs-lookup"><span data-stu-id="9d34e-249">Pop all the objects added to the global stacks.</span></span>

 <span data-ttu-id="9d34e-250">DbSkipExpression nemá přímý ekvivalent v SQL.</span><span class="sxs-lookup"><span data-stu-id="9d34e-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="9d34e-251">Logicky je přeložena do:</span><span class="sxs-lookup"><span data-stu-id="9d34e-251">Logically, it is translated into:</span></span>

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a><span data-ttu-id="9d34e-252">Výrazy JOIN</span><span class="sxs-lookup"><span data-stu-id="9d34e-252">Join Expressions</span></span>

<span data-ttu-id="9d34e-253">Následující jsou považovány za výrazy JOIN a jsou zpracovávány běžným způsobem pomocí metody VisitJoinExpression:</span><span class="sxs-lookup"><span data-stu-id="9d34e-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>

- <span data-ttu-id="9d34e-254">Argumenty DbApplyExpression pro</span><span class="sxs-lookup"><span data-stu-id="9d34e-254">DbApplyExpression</span></span>

- <span data-ttu-id="9d34e-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-255">DbJoinExpression</span></span>

- <span data-ttu-id="9d34e-256">DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-256">DbCrossJoinExpression</span></span>

<span data-ttu-id="9d34e-257">Postup najdete v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="9d34e-257">The following are the visit steps:</span></span>

<span data-ttu-id="9d34e-258">Nejdřív se před návštěvou podřízených objektů vyvolá IsParentAJoin, aby se zkontrolovalo, jestli je uzel spojení podřízeným objektem JOIN podél levé hřbety.</span><span class="sxs-lookup"><span data-stu-id="9d34e-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="9d34e-259">Pokud vrátí hodnotu false, spustí se nový SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="9d34e-260">V takovém smyslu jsou spojení navštívena odlišně ze zbývajících uzlů, protože nadřazený objekt (spojovací uzel) vytvoří SqlSelectStatement pro podřízené objekty, které mohou být použity.</span><span class="sxs-lookup"><span data-stu-id="9d34e-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>

<span data-ttu-id="9d34e-261">Za druhé zpracujte vstupy v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="9d34e-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="9d34e-262">Pro každý vstup:</span><span class="sxs-lookup"><span data-stu-id="9d34e-262">For each input:</span></span>

1. <span data-ttu-id="9d34e-263">Přejděte na vstup.</span><span class="sxs-lookup"><span data-stu-id="9d34e-263">Visit the input.</span></span>

2. <span data-ttu-id="9d34e-264">Post Process výsledek návštěvy vstupu vyvoláním ProcessJoinInputResult, který zodpovídá za údržbu tabulky symbolů po navštívení podřízeného výrazu JOIN a případně dokončí SqlSelectStatement vyprodukovaný podřízenou položkou.</span><span class="sxs-lookup"><span data-stu-id="9d34e-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="9d34e-265">Výsledkem podřízeného objektu může být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="9d34e-265">The child's result could be one of the following:</span></span>

    - <span data-ttu-id="9d34e-266">SqlSelectStatement se liší od, ke kterému bude přidán nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="9d34e-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="9d34e-267">V takovém případě může být nutné provést Přidání výchozích sloupců.</span><span class="sxs-lookup"><span data-stu-id="9d34e-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="9d34e-268">Pokud byl vstup připojen, je nutné vytvořit nový symbol spojení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="9d34e-269">V opačném případě vytvořte normální symbol.</span><span class="sxs-lookup"><span data-stu-id="9d34e-269">Otherwise, create a normal symbol.</span></span>

    - <span data-ttu-id="9d34e-270">Rozsah (například DbScanExpression), kdy se v takovém případě jednoduše přidá do seznamu vstupů nadřazeného objektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="9d34e-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>

    - <span data-ttu-id="9d34e-271">Nejedná se o SqlSelectStatement. v takovém případě je zabalený pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="9d34e-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>

    - <span data-ttu-id="9d34e-272">Stejný SqlSelectStatement, ke kterému je přidán nadřazený prvek.</span><span class="sxs-lookup"><span data-stu-id="9d34e-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="9d34e-273">V takovém případě je třeba symboly v seznamu FromExtents nahradit jediným novým JoinSymbol, které jim představují všechny.</span><span class="sxs-lookup"><span data-stu-id="9d34e-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>

    - <span data-ttu-id="9d34e-274">Pro první tři případy je volána metoda AddFromSymbol, aby přidala klauzuli AS a aktualizovala tabulku symbolů.</span><span class="sxs-lookup"><span data-stu-id="9d34e-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>

<span data-ttu-id="9d34e-275">Třetí, podmínka spojení (pokud existuje) se navštíví.</span><span class="sxs-lookup"><span data-stu-id="9d34e-275">Third, the join condition (if any) is visited.</span></span>

### <a name="set-operations"></a><span data-ttu-id="9d34e-276">Množinové operace</span><span class="sxs-lookup"><span data-stu-id="9d34e-276">Set Operations</span></span>

<span data-ttu-id="9d34e-277">Množina operací DbUnionAllExpression, DbExceptExpression a DbIntersectExpression se zpracovává metodou VisitSetOpExpression.</span><span class="sxs-lookup"><span data-stu-id="9d34e-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="9d34e-278">Vytvoří SqlBuilder obrazce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-278">It creates a SqlBuilder of the shape</span></span>

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

<span data-ttu-id="9d34e-279">Kde \<leftSqlSelectStatement > a \<rightSqlSelectStatement > jsou SqlSelectStatements získány návštěvou každého ze vstupů a \<setOp > je odpovídající operace (například UNION ALL).</span><span class="sxs-lookup"><span data-stu-id="9d34e-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>

### <a name="dbscanexpression"></a><span data-ttu-id="9d34e-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-280">DbScanExpression</span></span>

<span data-ttu-id="9d34e-281">Pokud jste navštívili v kontextu spojení (jako vstup do příkazu JOIN, který je levou podřízenou položkou jiného spojení), vrátí DbScanExpression SqlBuilder s cílovým SQL pro odpovídající cíl, což je buď definiční dotaz, tabulka nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="9d34e-282">V opačném případě se vytvoří nový SqlSelectStatement s nastavením pole od, které odpovídá příslušnému cíli.</span><span class="sxs-lookup"><span data-stu-id="9d34e-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>

### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="9d34e-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-283">DbVariableReferenceExpression</span></span>

<span data-ttu-id="9d34e-284">Návštěva DbVariableReferenceExpression vrátí symbol odpovídající tomuto výrazu odkazu na proměnnou na základě hledání v tabulce symbolů.</span><span class="sxs-lookup"><span data-stu-id="9d34e-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="9d34e-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-285">DbPropertyExpression</span></span>

<span data-ttu-id="9d34e-286">Při návštěvě DbPropertyExpression se identifikuje a zpracuje sloučení aliasů připojení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>

<span data-ttu-id="9d34e-287">Nejprve se navštíví vlastnost instance a výsledkem je symbol, JoinSymbol nebo SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="9d34e-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="9d34e-288">Tady je způsob, jakým se zpracovávají tyto tři případy:</span><span class="sxs-lookup"><span data-stu-id="9d34e-288">Here is how these three cases are handled:</span></span>

- <span data-ttu-id="9d34e-289">Pokud se vrátí JoinSymbol, než jeho vlastnost NameToExtent obsahuje symbol pro potřebnou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9d34e-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="9d34e-290">Pokud symbol spojení představuje vnořené spojení, vrátí se pomocí symbolu JOIN nový pár symbolů, který bude sledovat symbol, který se použije jako alias instance, a symbol představující skutečnou vlastnost pro další řešení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>

- <span data-ttu-id="9d34e-291">Pokud se vrátí SymbolPair a část sloupce je symbolem spojení, vrátí se znovu symbol spojení, ale teď se aktualizuje vlastnost sloupce tak, aby odkazovala na vlastnost reprezentovanou aktuálním výrazem vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9d34e-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="9d34e-292">V opačném případě se SqlBuilder vrátí se zdrojem SymbolPair jako s aliasem a symbolem pro aktuální vlastnost jako sloupec.</span><span class="sxs-lookup"><span data-stu-id="9d34e-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>

- <span data-ttu-id="9d34e-293">Pokud je vrácen symbol, metoda návštěvy vrátí metodu SqlBuilder s touto instancí jako alias a název vlastnosti jako název sloupce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>

### <a name="dbnewinstanceexpression"></a><span data-ttu-id="9d34e-294">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-294">DbNewInstanceExpression</span></span>

<span data-ttu-id="9d34e-295">Když se použije jako vlastnost projekce DbProjectExpression, vytvoří DbNewInstanceExpression čárkami oddělený seznam argumentů, které reprezentují předpokládané sloupce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>

<span data-ttu-id="9d34e-296">Pokud má DbNewInstanceExpression návratový typ kolekce a definuje novou kolekci výrazů poskytovaných jako argumenty, zpracují se následující tři případy samostatně:</span><span class="sxs-lookup"><span data-stu-id="9d34e-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>

- <span data-ttu-id="9d34e-297">Pokud DbNewInstanceExpression má DbElementExpression jako jediný argument, je přeložen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9d34e-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>

```sql
NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
```

<span data-ttu-id="9d34e-298">Pokud DbNewInstanceExpression nemá žádné argumenty (představuje prázdnou tabulku), DbNewInstanceExpression se převede na:</span><span class="sxs-lookup"><span data-stu-id="9d34e-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

<span data-ttu-id="9d34e-299">V opačném případě DbNewInstanceExpression sestaví každý žebřík argumentu Union:</span><span class="sxs-lookup"><span data-stu-id="9d34e-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a><span data-ttu-id="9d34e-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-300">DbFunctionExpression</span></span>

<span data-ttu-id="9d34e-301">Kanonické a integrované funkce jsou zpracovávány stejným způsobem: Pokud potřebují speciální zpracování (například TRIM (String) pro LTRIM (například RTRIM (String)), je vyvolána příslušná obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="9d34e-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="9d34e-302">V opačném případě jsou přeloženy do funkce Function (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="9d34e-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>

<span data-ttu-id="9d34e-303">Slovníky slouží k udržení přehledu o tom, které funkce vyžadují speciální zpracování a jejich vhodné obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="9d34e-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>

<span data-ttu-id="9d34e-304">Uživatelsky definované funkce jsou přeloženy na obor názvů Namespace. Function (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="9d34e-304">User-defined functions are translated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>

### <a name="dbelementexpression"></a><span data-ttu-id="9d34e-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-305">DbElementExpression</span></span>

<span data-ttu-id="9d34e-306">Metoda, která navštíví DbElementExpression, je vyvolána pouze pro návštěvy DbElementExpression, pokud se používá k reprezentaci skalárního poddotazu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="9d34e-307">Proto se DbElementExpression převede na úplný SqlSelectStatement a přidá se kolem něj hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="9d34e-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>

### <a name="dbquantifierexpression"></a><span data-ttu-id="9d34e-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-308">DbQuantifierExpression</span></span>

<span data-ttu-id="9d34e-309">V závislosti na typu výrazu (any nebo All) je DbQuantifierExpression přeložen jako:</span><span class="sxs-lookup"><span data-stu-id="9d34e-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated as:</span></span>

```sql
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a><span data-ttu-id="9d34e-310">Třída DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-310">DbNotExpression</span></span>

<span data-ttu-id="9d34e-311">V některých případech je možné sbalit překlad třída DbNotExpression se vstupním výrazem.</span><span class="sxs-lookup"><span data-stu-id="9d34e-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="9d34e-312">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9d34e-312">For example:</span></span>

```sql
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

<span data-ttu-id="9d34e-313">Důvod, proč je provedeno druhé sbalení, je, že poskytovatel při překladu DbQuantifierExpression typu All zavedl neefektivní efektivity.</span><span class="sxs-lookup"><span data-stu-id="9d34e-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="9d34e-314">Proto Entity Framework nemohl provést zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="9d34e-314">Thus the Entity Framework could not have done the simplification.</span></span>

### <a name="dbisemptyexpression"></a><span data-ttu-id="9d34e-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="9d34e-315">DbIsEmptyExpression</span></span>

<span data-ttu-id="9d34e-316">DbIsEmptyExpression je přeložen jako:</span><span class="sxs-lookup"><span data-stu-id="9d34e-316">DbIsEmptyExpression is translated as:</span></span>

```sql
IsEmpty(input) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="9d34e-317">Druhá fáze generování SQL: vygenerování řetězcového příkazu</span><span class="sxs-lookup"><span data-stu-id="9d34e-317">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="9d34e-318">Při generování příkazu String SQL SqlSelectStatement vytvoří vlastní aliasy pro symboly, které řeší problém s názvem sloupce a přejmenováním aliasu rozsahu.</span><span class="sxs-lookup"><span data-stu-id="9d34e-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>

<span data-ttu-id="9d34e-319">K přejmenování aliasu rozsahu dojde při zápisu objektu SqlSelectStatement do řetězce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="9d34e-320">Nejprve vytvořte seznam všech aliasů používaných vnějšími rozsahy.</span><span class="sxs-lookup"><span data-stu-id="9d34e-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="9d34e-321">Každý symbol v FromExtents (nebo AllJoinExtents Pokud není null) se přejmenuje, pokud koliduje s libovolným vnějším rozsahem.</span><span class="sxs-lookup"><span data-stu-id="9d34e-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="9d34e-322">Pokud je potřeba přejmenování, nebude v konfliktu s žádným rozsahem shromážděným v AllExtentNames.</span><span class="sxs-lookup"><span data-stu-id="9d34e-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>

<span data-ttu-id="9d34e-323">Při zápisu objektu symbolu do řetězce dojde k přejmenování sloupce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="9d34e-324">AddDefaultColumns v první fázi určuje, zda je nutné přejmenovat určitý symbol sloupce.</span><span class="sxs-lookup"><span data-stu-id="9d34e-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="9d34e-325">V druhé fázi se pouze přejmenování provádí se zachováním, že vytvořený název není v konfliktu s žádným názvem používaným v AllColumnNames.</span><span class="sxs-lookup"><span data-stu-id="9d34e-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>

<span data-ttu-id="9d34e-326">Pro vytváření jedinečných názvů pro aliasy rozsahu i pro sloupce použijte \<existing_name > _n, kde n je nejmenší alias, který se ještě nepoužil.</span><span class="sxs-lookup"><span data-stu-id="9d34e-326">To produce unique names both for extent aliases and for columns, use \<existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="9d34e-327">Globální seznam všech aliasů zvyšuje nutnost kaskádového přejmenování.</span><span class="sxs-lookup"><span data-stu-id="9d34e-327">The global list of all aliases increases the need for cascading renames.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d34e-328">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d34e-328">See also</span></span>

- [<span data-ttu-id="9d34e-329">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="9d34e-329">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
