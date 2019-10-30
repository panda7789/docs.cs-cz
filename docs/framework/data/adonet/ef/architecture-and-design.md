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
# <a name="architecture-and-design"></a>Architektura a návrh

Modul pro generování SQL ve [vzorovém poskytovateli](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) je implementován jako návštěvník ve stromu výrazů, který představuje strom příkazů. Generování se provádí v rámci jednoho průchodu ve stromu výrazu.

Uzly stromu jsou zpracovávány zdola nahoru. Nejprve je vytvořena zprostředkující struktura: SqlSelectStatement nebo SqlBuilder, jak implementace ISqlFragment. Dále je příkaz String jazyka SQL vytvořen z této struktury. Existují dva důvody pro mezilehlé struktury:

- Logicky se vyplní příkaz SQL SELECT mimo pořadí. Uzly, které jsou součástí klauzule FROM, jsou navštíveny před uzly, které jsou součástí klauzule WHERE, GROUP BY a ORDER BY.

- Chcete-li přejmenovat aliasy, je nutné identifikovat všechny použité aliasy, abyste se vyhnuli kolizím při přejmenování. Chcete-li odložit možnosti přejmenování v SqlBuilder, použijte objekty symbolů pro reprezentaci sloupců, které jsou kandidáty k přejmenování.

![Znázorňuje](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")

V první fázi při návštěvě stromu výrazů jsou výrazy seskupeny do SqlSelectStatements, spojení jsou shrnuty a jsou shrnuty aliasy. Během tohoto průchodu objekty symbolů reprezentují sloupce nebo vstupní aliasy, které mohou být přejmenovány.

Ve druhé fázi se při vytváření skutečného řetězce přejmenují aliasy.

## <a name="data-structures"></a>Datové struktury

Tato část popisuje typy používané v [ukázkovém poskytovateli](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , který používáte k vytvoření příkazu SQL.

### <a name="isqlfragment"></a>ISqlFragment

Tato část se zabývá třídami, které implementují rozhraní ISqlFragment, které slouží ke dvěma účelům:

- Společný návratový typ pro všechny metody návštěvníka.

- Poskytuje metodu pro zápis konečného řetězce SQL.

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a>SqlBuilder

SqlBuilder je shromáždění zařízení pro finální řetězec SQL, podobně jako StringBuilder. Skládá se z řetězců, které tvoří finální SQL, spolu s ISqlFragments, které je možné převést do řetězců.

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a>SqlSelectStatement

SqlSelectStatement představuje kanonický příkaz SQL SELECT obrazce "vybrat... Z.. KDE... SESKUPIT PODLE... ORDER BY.

Jednotlivé klauzule jazyka SQL jsou reprezentovány pomocí StringBuilder. Kromě toho sleduje, zda je zadána odlišná a zda je příkaz zcela na nejvyšší úrovni. Pokud příkaz není zcela na nejvyšší úrovni, klauzule ORDER BY je vynechána, pokud příkaz nemá také klauzuli TOP.

FromExtents obsahuje seznam vstupů pro příkaz SELECT. V tomto případě je obvykle pouze jeden prvek. Příkazy SELECT pro spojení mohou dočasně mít více než jeden prvek.

Pokud je příkaz SELECT vytvořen pomocí uzlu JOIN, SqlSelectStatement udržuje seznam všech rozsahů, které byly shrnuty v JOIN v AllJoinExtents. OuterExtents představuje vnější odkazy na SqlSelectStatement a používá se pro přejmenování vstupního aliasu.

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

#### <a name="topclause"></a>TopClause

TopClause představuje výraz TOP v SqlSelectStatement. Vlastnost TopCount určuje, kolik HORNÍch řádků by mělo být vybráno.  Pokud má WithTies hodnotu true, TopClause byl sestaven z DbLimitExpression.

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a>Symboly

Třídy související s symboly a tabulka symbolů provádějí přejmenování vstupního aliasu, sloučení aliasů a přejmenování aliasu sloupce.

Třída symbol reprezentuje rozsah, vnořený výběrový příkaz nebo sloupec. Používá se místo skutečného aliasu pro povolení přejmenování po jeho použití a také další informace pro artefakt, který představuje (například typ).

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

Název ukládá původní alias pro zastoupený rozsah, vnořený příkaz SELECT nebo sloupec.

NewName ukládá alias, který se použije v příkazu SQL SELECT. Je původně nastavené na název a v případě potřeby je přejmenovaná, pokud se generuje finální dotaz řetězce.

Typ je vhodný pouze pro symboly představující rozsahy a vnořené příkazy SELECT.

#### <a name="symbolpair"></a>SymbolPair

Třída SymbolPair řeší sloučení záznamů.

Vezměte v úvahu výraz vlastnosti D (v, "J3. J2. J1. a. x"), kde v je VarRef, J1, J2, J3, je rozsah a x je sloupce.

To je třeba přeložit do {j}. {x}. Zdrojové pole představuje nejvzdálenější SqlStatement, představující výraz Join (řekněme J2); Toto je vždy symbol spojení. Sloupcové pole se přesune z jednoho symbolu spojení na další, dokud se nezastaví na symbolu bez spojení. Tato zpráva se vrátí při návštěvě DbPropertyExpression, ale nikdy se nepřidá do SqlBuilder.

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a>JoinSymbol

Symbol spojení je symbol, který představuje vnořený příkaz SELECT s připojením nebo vstupem spojení.

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

ColumnList představuje seznam sloupců v klauzuli SELECT, pokud tento symbol představuje příkaz SQL SELECT. ExtentList je seznam rozsahů v klauzuli SELECT. Pokud je spojení více rozsahů shrnuto na nejvyšší úrovni, FlattenedExtentList sleduje rozsahy, aby bylo zajištěno, že se aliasy rozsahu přejmenují správně.

NameToExtent má všechny rozsahy v ExtentList jako slovník. IsNestedJoin se používá k určení, zda je JoinSymbol běžným spojovacím symbolem nebo s odpovídajícím SqlSelectStatement.

Všechny seznamy jsou nastavené přesně jednou a pak se použijí pro vyhledávání nebo výčet.

#### <a name="symboltable"></a>Symbolová

Symbolová proměnná se používá k překladu názvů proměnných na symboly. Symbolová sada je implementována jako zásobník s novou položkou pro každý obor. Vyhledávání vyhledá v horní části zásobníku do dolní části, dokud se nenajde položka.

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

Pro jednu instanci modulu SQL Generation existuje pouze jedna pole typu symbol. Obory se zadávají a ukončí pro každý relační uzel. Všechny symboly v dřívějších oborech jsou viditelné pro pozdější obory, pokud nejsou skryté jinými symboly se stejným názvem.

### <a name="global-state-for-the-visitor"></a>Globální stav návštěvníka

Chcete-li pomoct při přejmenování aliasů a sloupců, udržujte seznam všech názvů sloupců (AllColumnNames) a aliasy rozsahu (AllExtentNames), které byly použity v prvním průchodu ve stromu dotazu.  Tabulka symbolů překládá názvy proměnných na symboly. IsVarRefSingle se používá jenom pro účely ověření, není to bezpodmínečně nutné.

Dvě zásobníky používané přes CurrentSelectStatement a IsParentAJoin se používají k předání "parametrů" z nadřazených uzlů do podřízených uzlů, protože vzor návštěvníka nám neumožňuje předat parametry.

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

## <a name="common-scenarios"></a>Běžné scénáře

Tato část se zabývá běžnými scénáři poskytovatele.

### <a name="grouping-expression-nodes-into-sql-statements"></a>Seskupení uzlů výrazů do příkazů SQL

SqlSelectStatement se vytvoří při zjištění prvního relačního uzlu (obvykle DbScanExpression) při návštěvě stromu od dolní části. Chcete-li vytvořit příkaz SQL SELECT s co nejmenším počtem vnořených dotazů, můžete agregovat tolik svých nadřazených uzlů, kolik je možné v tomto SqlSelectStatement.

Rozhodnutí o tom, zda daný (relační) uzel lze přidat do aktuálního SqlSelectStatement (který byl vrácen při návštěvě vstupu), nebo pokud je nutné spustit nový příkaz, je vypočítán metodou kompatibilní a závisí na tom, co je již v SqlSelectStatement, která závisí na tom, jaké uzly byly pod daným uzlem.

V případě, že jsou klauzule příkazů SQL vyhodnocovány po klauzulích, kde jsou uzly zvažovány pro sloučení prázdné, uzel nelze do aktuálního příkazu přidat. Pokud je například dalším uzlem filtr, tento uzel lze do aktuálního SqlSelectStatement začlenit pouze v případě, že platí následující:

- Seznam pro výběr je prázdný. Pokud seznam SELECT není prázdný, seznam Select byl vytvořen uzlem před filtrem a predikát může odkazovat na sloupce vytvářené tímto seznamem SELECT.

- GROUPBY je prázdný. Pokud GROUPBY není prázdné, přidání filtru by znamenalo filtrování před seskupením, což není správné.

- Klauzule TOP je prázdná. Pokud klauzule TOP není prázdná, přidání filtru by znamenalo filtrování před provedením HORNÍch, což není správné.

To se nevztahuje na nerelační uzly, jako je DbConstantExpression nebo aritmetické výrazy, protože jsou vždycky zahrnuté jako součást existující SqlSelectStatement.

Také při zjištění kořene stromu spojení (spojovací uzel, který nemá nadřazený objekt JOIN) je spuštěn nový SqlSelectStatement. Všechna jeho levá hřbet – děti jsou shrnuty do tohoto SqlSelectStatement.

Když se spustí nový SqlSelectStatement a do vstupu se přidá aktuální SqlSelectStatement, může se stát, že aktuální se musí dokončit přidáním sloupců projekce (klauzule SELECT), pokud neexistuje. To se provádí s metodou AddDefaultColumns, která se zabývá FromExtentsem SqlSelectStatement a přidává všechny sloupce, které seznam rozsahů reprezentovaných FromExtents přináší v oboru do seznamu projektových sloupců. To je provedeno, protože v tomto okamžiku není známo, na které sloupce odkazují jiné uzly. To může být optimalizováno pouze na projekt, který lze později použít.

### <a name="join-flattening"></a>Spojit sloučení

Vlastnost IsParentAJoin pomáhá určit, zda lze dané spojení Sloučit. Konkrétně IsParentAJoin vrací `true` pouze pro levý podřízený objekt JOIN a pro každý DbScanExpression, který je okamžitým vstupem ke spojení. v takovém případě bude podřízený uzel znovu používat stejný SqlSelectStatement, který by měl nadřazený objekt později použít. Další informace najdete v tématu výrazy JOIN.

### <a name="input-alias-redirecting"></a>Přesměrování vstupního aliasu

Přesměrování vstupního aliasu je provedeno s tabulkou symbolů.

Chcete-li vysvětlit přesměrování vstupního aliasu, podívejte se na první příklad v tématu [generování SQL z příkazových stromů – osvědčené postupy](generating-sql-from-command-trees-best-practices.md).  V projekci je potřeba přesměrovat "a" na "b".

Když je vytvořen objekt SqlSelectStatement, rozsah, který je vstupem do uzlu, je umístěn do vlastnosti from třídy SqlSelectStatement. Symbol (\<symbol_b >) se vytvoří na základě názvu vstupní vazby ("b"), který bude představovat tento rozsah, a > se k klauzuli FROM připojí \<symbol_b.  Symbol je také přidán do vlastnosti FromExtents.

Symbol je také přidán do tabulky symbolů, aby propojí název vstupní vazby s ním ("b", \<symbol_b >).

Pokud následující uzel znovu použije tuto SqlSelectStatement, přidá položku do tabulky symbolů, aby propojí svůj název vstupní vazby s tímto symbolem. V našem příkladu DbProjectExpression s názvem vstupní vazby "a" by znovu použil SqlSelectStatement a přidat ("a", \< symbol_b >) do tabulky.

Když výrazy odkazují na název vstupní vazby uzlu, který znovu používá SqlSelectStatement, tento odkaz se vyřeší pomocí tabulky symbolů do správného přesměrovaného symbolu. Při řešení "a" z "a. x" při návštěvě DbVariableReferenceExpression představujícího "a" se přeloží na symbol \<symbol_b >.

### <a name="join-alias-flattening"></a>Spojit sloučení aliasů

Sloučení aliasu JOIN se dosáhne při návštěvě DbPropertyExpression, jak je popsáno v části s názvem DbPropertyExpression.

### <a name="column-name-and-extent-alias-renaming"></a>Název sloupce a přejmenování aliasu rozsahu

Problémy s názvem sloupce a přejmenováním aliasu rozsahu jsou adresovány pomocí symbolů, které nahradí pouze aliasy ve druhé fázi generování popsané v části s názvem druhá fáze generování kódu SQL: vygenerování příkazu řetězce.

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>První fáze generování SQL: návštěvy stromu výrazů

Tato část popisuje první fázi generování kódu SQL, pokud je výraz reprezentující dotaz navštíven a je vytvořena zprostředkující struktura, buď SqlSelectStatement nebo SqlBuilder.

Tato část popisuje principy navštívení různých kategorií uzlů výrazů a podrobnosti o návštěvě specifických typů výrazů.

### <a name="relational-non-join-nodes"></a>Relační uzly (bez spojení)

Následující typy výrazů podporují uzly bez připojení:

- DbDistinctExpression

- DbFilterExpression

- DbGroupAggregate

- DbLimitExpression

- DbProjectExpression

- DbSkipExpression

- DbSortExpression

Návštěvy těchto uzlů se řídí následujícím vzorem:

1. Přejděte na relační vstup a získejte výsledný SqlSelectStatement. Vstup do relačního uzlu může být jeden z následujících:

    - Relační uzel, včetně rozsahu (například DbScanExpression). Návštěvy takového uzlu vrátí SqlSelectStatement.

    - Výraz operace set (například UNION ALL). Výsledek musí být zabalen do závorek a musí být vložen do klauzule FROM nového SqlSelectStatement.

2. Ověřte, zda je možné přidat aktuální uzel do SqlSelectStatement vyprodukovaného vstupem. Popisuje oddíl s názvem výrazy seskupení do příkazů SQL. Pokud ne,

    - Byl automaticky zobrazen aktuální objekt SqlSelectStatement.

    - Vytvořte nový objekt SqlSelectStatement a přidejte jako z nového objektu SqlSelectStatement SqlSelectStatementy se systémem.

    - Vložte nový objekt nad zásobník.

3. Přesměruje vazbu vstupního výrazu na správný symbol ze vstupu. Tyto informace jsou uchovávány v objektu SqlSelectStatement.

4. Přidejte nový obor typu.

5. Navštivte nevstupní část výrazu (například projekce a predikát).

6. Všechny objekty přidané do globálních zásobníků.

 DbSkipExpression nemá přímý ekvivalent v SQL. Logicky je přeložena do:

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a>Výrazy JOIN

Následující jsou považovány za výrazy JOIN a jsou zpracovávány běžným způsobem pomocí metody VisitJoinExpression:

- Argumenty DbApplyExpression pro

- DbJoinExpression

- DbCrossJoinExpression

Postup najdete v následujících krocích:

Nejdřív se před návštěvou podřízených objektů vyvolá IsParentAJoin, aby se zkontrolovalo, jestli je uzel spojení podřízeným objektem JOIN podél levé hřbety. Pokud vrátí hodnotu false, spustí se nový SqlSelectStatement. V takovém smyslu jsou spojení navštívena odlišně ze zbývajících uzlů, protože nadřazený objekt (spojovací uzel) vytvoří SqlSelectStatement pro podřízené objekty, které mohou být použity.

Za druhé zpracujte vstupy v jednom okamžiku. Pro každý vstup:

1. Přejděte na vstup.

2. Post Process výsledek návštěvy vstupu vyvoláním ProcessJoinInputResult, který zodpovídá za údržbu tabulky symbolů po navštívení podřízeného výrazu JOIN a případně dokončí SqlSelectStatement vyprodukovaný podřízenou položkou. Výsledkem podřízeného objektu může být jedna z následujících:

    - SqlSelectStatement se liší od, ke kterému bude přidán nadřazený objekt. V takovém případě může být nutné provést Přidání výchozích sloupců. Pokud byl vstup připojen, je nutné vytvořit nový symbol spojení. V opačném případě vytvořte normální symbol.

    - Rozsah (například DbScanExpression), kdy se v takovém případě jednoduše přidá do seznamu vstupů nadřazeného objektu SqlSelectStatement.

    - Nejedná se o SqlSelectStatement. v takovém případě je zabalený pomocí závorek.

    - Stejný SqlSelectStatement, ke kterému je přidán nadřazený prvek. V takovém případě je třeba symboly v seznamu FromExtents nahradit jediným novým JoinSymbol, které jim představují všechny.

    - Pro první tři případy je volána metoda AddFromSymbol, aby přidala klauzuli AS a aktualizovala tabulku symbolů.

Třetí, podmínka spojení (pokud existuje) se navštíví.

### <a name="set-operations"></a>Množinové operace

Množina operací DbUnionAllExpression, DbExceptExpression a DbIntersectExpression se zpracovává metodou VisitSetOpExpression. Vytvoří SqlBuilder obrazce.

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

Kde \<leftSqlSelectStatement > a \<rightSqlSelectStatement > jsou SqlSelectStatements získány návštěvou každého ze vstupů a \<setOp > je odpovídající operace (například UNION ALL).

### <a name="dbscanexpression"></a>DbScanExpression

Pokud jste navštívili v kontextu spojení (jako vstup do příkazu JOIN, který je levou podřízenou položkou jiného spojení), vrátí DbScanExpression SqlBuilder s cílovým SQL pro odpovídající cíl, což je buď definiční dotaz, tabulka nebo zobrazení. V opačném případě se vytvoří nový SqlSelectStatement s nastavením pole od, které odpovídá příslušnému cíli.

### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

Návštěva DbVariableReferenceExpression vrátí symbol odpovídající tomuto výrazu odkazu na proměnnou na základě hledání v tabulce symbolů.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Při návštěvě DbPropertyExpression se identifikuje a zpracuje sloučení aliasů připojení.

Nejprve se navštíví vlastnost instance a výsledkem je symbol, JoinSymbol nebo SymbolPair. Tady je způsob, jakým se zpracovávají tyto tři případy:

- Pokud se vrátí JoinSymbol, než jeho vlastnost NameToExtent obsahuje symbol pro potřebnou vlastnost. Pokud symbol spojení představuje vnořené spojení, vrátí se pomocí symbolu JOIN nový pár symbolů, který bude sledovat symbol, který se použije jako alias instance, a symbol představující skutečnou vlastnost pro další řešení.

- Pokud se vrátí SymbolPair a část sloupce je symbolem spojení, vrátí se znovu symbol spojení, ale teď se aktualizuje vlastnost sloupce tak, aby odkazovala na vlastnost reprezentovanou aktuálním výrazem vlastnosti. V opačném případě se SqlBuilder vrátí se zdrojem SymbolPair jako s aliasem a symbolem pro aktuální vlastnost jako sloupec.

- Pokud je vrácen symbol, metoda návštěvy vrátí metodu SqlBuilder s touto instancí jako alias a název vlastnosti jako název sloupce.

### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

Když se použije jako vlastnost projekce DbProjectExpression, vytvoří DbNewInstanceExpression čárkami oddělený seznam argumentů, které reprezentují předpokládané sloupce.

Pokud má DbNewInstanceExpression návratový typ kolekce a definuje novou kolekci výrazů poskytovaných jako argumenty, zpracují se následující tři případy samostatně:

- Pokud DbNewInstanceExpression má DbElementExpression jako jediný argument, je přeložen následujícím způsobem:

```sql
NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
```

Pokud DbNewInstanceExpression nemá žádné argumenty (představuje prázdnou tabulku), DbNewInstanceExpression se převede na:

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

V opačném případě DbNewInstanceExpression sestaví každý žebřík argumentu Union:

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a>DbFunctionExpression

Kanonické a integrované funkce jsou zpracovávány stejným způsobem: Pokud potřebují speciální zpracování (například TRIM (String) pro LTRIM (například RTRIM (String)), je vyvolána příslušná obslužná rutina. V opačném případě jsou přeloženy do funkce Function (arg1, arg2,..., argn).

Slovníky slouží k udržení přehledu o tom, které funkce vyžadují speciální zpracování a jejich vhodné obslužné rutiny.

Uživatelsky definované funkce jsou přeloženy na obor názvů Namespace. Function (arg1, arg2,..., argn).

### <a name="dbelementexpression"></a>DbElementExpression

Metoda, která navštíví DbElementExpression, je vyvolána pouze pro návštěvy DbElementExpression, pokud se používá k reprezentaci skalárního poddotazu. Proto se DbElementExpression převede na úplný SqlSelectStatement a přidá se kolem něj hranaté závorky.

### <a name="dbquantifierexpression"></a>DbQuantifierExpression

V závislosti na typu výrazu (any nebo All) je DbQuantifierExpression přeložen jako:

```sql
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a>Třída DbNotExpression

V některých případech je možné sbalit překlad třída DbNotExpression se vstupním výrazem. Příklad:

```sql
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

Důvod, proč je provedeno druhé sbalení, je, že poskytovatel při překladu DbQuantifierExpression typu All zavedl neefektivní efektivity. Proto Entity Framework nemohl provést zjednodušení.

### <a name="dbisemptyexpression"></a>DbIsEmptyExpression

DbIsEmptyExpression je přeložen jako:

```sql
IsEmpty(input) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druhá fáze generování SQL: vygenerování řetězcového příkazu

Při generování příkazu String SQL SqlSelectStatement vytvoří vlastní aliasy pro symboly, které řeší problém s názvem sloupce a přejmenováním aliasu rozsahu.

K přejmenování aliasu rozsahu dojde při zápisu objektu SqlSelectStatement do řetězce. Nejprve vytvořte seznam všech aliasů používaných vnějšími rozsahy. Každý symbol v FromExtents (nebo AllJoinExtents Pokud není null) se přejmenuje, pokud koliduje s libovolným vnějším rozsahem. Pokud je potřeba přejmenování, nebude v konfliktu s žádným rozsahem shromážděným v AllExtentNames.

Při zápisu objektu symbolu do řetězce dojde k přejmenování sloupce. AddDefaultColumns v první fázi určuje, zda je nutné přejmenovat určitý symbol sloupce. V druhé fázi se pouze přejmenování provádí se zachováním, že vytvořený název není v konfliktu s žádným názvem používaným v AllColumnNames.

Pro vytváření jedinečných názvů pro aliasy rozsahu i pro sloupce použijte \<existing_name > _n, kde n je nejmenší alias, který se ještě nepoužil. Globální seznam všech aliasů zvyšuje nutnost kaskádového přejmenování.

## <a name="see-also"></a>Viz také:

- [Generování SQL ve zprostředkovateli ukázek](sql-generation-in-the-sample-provider.md)
