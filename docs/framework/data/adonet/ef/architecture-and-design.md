---
title: Architektura a návrh
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 8f58fb521aa0d9f389dab8c061f40e41b779c743
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690249"
---
# <a name="architecture-and-design"></a>Architektura a návrh

Modul generování SQL v [zprostředkovateli ukázek](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) je implementovaný jako návštěvníky na strom výrazu, který představuje strom příkazů. Generování se provádí v jednom průchodu přes strom výrazu.

Uzly stromu jsou zpracovávány zdola nahoru. Nejprve je vytvořen zprostředkující struktury: SqlSelectStatement nebo SqlBuilder, obě implementující ISqlFragment. V dalším kroku řetězec příkazu SQL je vytvořený z této struktury. Existují dva důvody pro zprostředkující strukturu:

- Příkaz SELECT se vyplní logicky, mimo pořadí. Uzly, které jsou součástí v klauzuli FROM jsou zobrazeny před uzly, které jsou součástí WHERE, GROUP BY a ORDER BY – klauzule.

- Přejmenování aliasy, je nutné určit všech použitých aliasy pro zabránění kolizím při přejmenování. Přejmenování možnosti v SqlBuilder odložit, představují sloupce, které jsou kandidáty pro přejmenování pomocí symbolu objektů.

![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")

V první fázi při návštěvě stromu výrazů výrazy jsou seskupené do SqlSelectStatements, spojení se sloučí a aliasy spojení se sloučí. V této fázi Symbol objekty představují sloupce nebo vstupní aliasy, které mohou být přejmenován.

V druhé fáze, při vytváření aktuální řetězcovou jsou přejmenované aliasy.

## <a name="data-structures"></a>Datové struktury

Tato část popisuje typy používané [zprostředkovateli ukázek](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , který používáte k vytvoření příkazu SQL.

### <a name="isqlfragment"></a>ISqlFragment

Tato část popisuje třídy, které implementují rozhraní ISqlFragment, které má dva účely:

- Běžné návratový typ pro všechny metody návštěvníka.

- Poskytuje metodu pro zápis konečný řetězec SQL.

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a>SqlBuilder

SqlBuilder je shromažďování zařízení pro konečný řetězec SQL, který je podobný StringBuilder. Skládá se z řetězců, které tvoří konečné SQL spolu s ISqlFragments, které mohou být převedeny na řetězce.

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a>SqlSelectStatement

SqlSelectStatement představuje canonical příkazu SQL SELECT tvaru vyberte..." Z... KDE... SESKUPIT PODLE... ŘADIT PODLE".

Každá klauzule SQL je reprezentován StringBuilder. Kromě toho sleduje, zda byl zadán Distinct a zda je příkaz nejvyšší. Pokud není příkaz nejvyšší, klauzule ORDER by je vynechána, pokud příkaz obsahuje taky klauzuli TOP.

FromExtents obsahuje seznam vstupů pro příkaz SELECT. V tomto obvykle není právě jeden element. Příkazy SELECT pro spojení dočasně může mít více než jeden element.

Pokud příkaz SELECT vytvoří připojení k uzlu, SqlSelectStatement udržuje seznam všechny rozsahy, které se sloučí ve spojení v AllJoinExtents. OuterExtents představuje vnější odkazy SqlSelectStatement a používá se pro přejmenování vstupní alias.

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

TopClause představuje výraz TOP v SqlSelectStatement. Vlastnost TopCount označuje počet prvních řádků by měla být zaškrtnutá.  Při splnění WithTies TopClause byla vytvořena z DbLimitExpression.

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a>Symboly

Třídy související s symbolů a tabulky symbolů provádějí přejmenování vstupní alias, spojení sloučení alias a přejmenování alias sloupce.

Třída Symbol představuje rozsah, vnořeného příkazu SELECT nebo sloupec. Používá se místo skutečných alias umožňující přejmenování poté, co bylo použito a taky mají další informace pro artefakt, který představuje (jako je typ).

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

Ukládá název původní alias pro zastoupené v rozsahu, vnořeného příkazu SELECT nebo sloupec.

NewName ukládá alias, který se použije v příkazu SELECT. Je původně nastavena na název a přejmenovat pouze v případě potřeby při generování konečný řetězec dotazu.

Typ je platný pouze pro symboly představující rozsahy a vnořených příkazů SELECT.

#### <a name="symbolpair"></a>SymbolPair

Třída SymbolPair řeší záznam sloučení.

Vezměte v úvahu výraz pro vlastnost D (v, "j3.j2.j1.a.x"), kde je v VarRef, j1, j2, j3 jsou spojení, je v rozsahu a x je sloupce.

Tato akce nemá nakonec převést na {j'}. {x'}. Zdrojové pole představuje nejkrajnější Příkaz_sql představující výrazu join (třeba j2); Toto je vždy symbol spojení. Pole sloupce přesune z jeden symbol spojení na další končí na symbol nikoli na spojení. To je vrácena při návštěvě DbPropertyExpression, ale nikdy je přidán SqlBuilder.

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a>JoinSymbol

Symbol spojení je Symbol, který představuje vnořeného příkazu SELECT s spojení nebo spojení vstup.

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

Seznam sloupců představuje seznam sloupců v klauzuli SELECT, pokud tento symbol představuje příkaz SQL SELECT. ExtentList je seznam rozsahů v klauzuli SELECT. Má-li spojení více rozsahů sloučí na nejvyšší úrovni, sleduje FlattenedExtentList rozsahy k zajištění tohoto rozsahu, v jakém jsou správně přejmenovat aliasy.

NameToExtent má všechny rozsahy v ExtentList jako slovník. IsNestedJoin slouží k určení, zda je JoinSymbol symbol běžné spojení nebo, pokud má odpovídající SqlSelectStatement.

Všechny seznamy jsou nastavit přesně jednou a pak použít pro vyhledávání nebo výčet.

#### <a name="symboltable"></a>SymbolTable

SymbolTable se používá k překladu názvů proměnných na symboly. SymbolTable je implementovaný jako zásobníku se nový záznam pro každý obor. Vyhledávání hledat v horní části zásobníku do dolní části dokud nebude nalezen záznam.

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

Pouze jeden SymbolTable na jednu instanci modulu generování Sql není k dispozici. Obory jsou zadané a byla ukončena, pro každý uzel relační. Všechny symboly v dřívější obory jsou viditelné pro pozdější obory Pokud skrytý za jiných symbolů se stejným názvem.

### <a name="global-state-for-the-visitor"></a>Globální stav pro návštěvníka

Při přejmenování aliasy a sloupců, Udržovat seznam všech názvů sloupců (AllColumnNames) a aliasy rozsahu (AllExtentNames), které se používají v prvním připojovat přes stromu dotazu.  Tabulky symbolů přeloží názvy proměnných na symboly. IsVarRefSingle slouží pouze pro účely ověření není nezbytně nutné.

Dvě zásobníky použít prostřednictvím CurrentSelectStatement a IsParentAJoin se používají pro předávání "parametrů" z nadřazeného podřízené uzly, protože model návštěvníka neumožňuje pro předání parametrů.

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

## <a name="common-scenarios"></a>Obvyklé scénáře

Tato část popisuje běžné scénáře zprostředkovatele.

### <a name="grouping-expression-nodes-into-sql-statements"></a>Seskupování uzlů výraz na příkazy SQL

SqlSelectStatement se vytvoří při prvním uzlu relační dochází (obvykle DbScanExpression rozsahu) při návštěvě stromové struktuře zdola nahoru. Vytvořit příkaz SQL SELECT s jako málo vnořené nejvíce agregační tolik svých nadřazených uzlů je možné tuto SqlSelectStatement dotazy.

Rozhodnutí, jestli daný uzel (relační) mohou být přidány do aktuálního SqlSelectStatement (ten vrátí při návštěvě vstupu) nebo jestli je potřeba spustit nové prohlášení je vypočítán metodou IsCompatible a závisí na to, co je již v SqlSelectStatement závisí na uzly byly níže daný uzel.

Obvykle Pokud klauzule příkaz SQL se vyhodnocují po klauzulích, kde nejsou prázdné uzly se nebude zvažovat sloučení, uzel nelze přidat k aktuálnímu příkazu. Například pokud další uzel je filtr, takový uzel může být zahrnut do aktuální SqlSelectStatement pouze v případě, že platí následující:

- Vyberte seznam je prázdný. Pokud seznam SELECT není prázdný, seznamu příkazu select se vytvořil parametrem uzlu předchází filtr a predikát mohou odkazovat na sloupce produkované tohoto seznamu výběru.

- GROUPBY je prázdný. Pokud funkce GROUPBY není prázdná, přidání filtru by znamenal filtrování před seskupení, který není správný.

- Klauzule TOP je prázdný. Pokud klauzule TOP není prázdná, přidání filtru by znamenal filtrování než přistoupíte k horní části, který není správný.

To se nevztahují na nerelačních uzlů jako DbConstantExpression nebo aritmetických výrazů, protože jsou vždy součástí existující SqlSelectStatement.

Při zjištění kořen stromu join (připojení k uzlu, který nemá připojení k nadřazené), je spuštěn nový SqlSelectStatement. Všechny jeho podřízené objekty levém hřbetu spojení se agregují do této SqlSelectStatement.

Pokaždé, když je spuštěn nový SqlSelectStatement a tu se přidá do vstupní, může aktuální SqlSelectStatement musíte provést přidáním sloupce projekce (klauzule SELECT), pokud ještě neexistuje. To se provádí pomocí metody AddDefaultColumns, která prohledá FromExtents SqlSelectStatement a přidá všechny sloupce, které seznamu rozsahů reprezentována FromExtents přináší v rozsahu do seznamu předpokládané sloupců. Je to, protože v tomto okamžiku Neznámý sloupce, které odkazují jiných uzlech. To lze optimalizovat do projektu pouze sloupce, které mohou být později použity.

### <a name="join-flattening"></a>Připojte se k vyrovnání

Vlastnost IsParentAJoin pomáhá určit, zda lze plochý dané připojení. Konkrétně se vrátí IsParentAJoin `true` pouze pro vstupní levé podřízené spojení a pro každý DbScanExpression, který je ihned k připojení k, v takovém případě tento podřízený uzel opakovaně používá stejnou SqlSelectStatement nadřazené by tu používat. Další informace najdete v tématu "Join Expressions".

### <a name="input-alias-redirecting"></a>Vstupní Alias přesměrování

Přesměrování vstupní alias se provádí s tabulkou symbolů.

Abychom vysvětlili, přesměrování vstupní alias, najdete v prvním příkladu v [generování SQL ze stromů příkazů – osvědčené postupy](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).  Existuje "a" potřeba přesměrovat na "b" v projekci.

Když je vytvořen objekt SqlSelectStatement, rozsah, který je vstupem uzlu je umístěn ve vlastnosti From SqlSelectStatement. Symbol (\<symbol_b >) je vytvořen na základě názvu vstupní vazby ("b") pro reprezentaci této míře a "AS" + \<symbol_b > se připojí k klauzule From.  Symbol je taky přidaný ke FromExtents vlastnost.

Symbol je taky přidaný do tabulky symbolů pro odkaz na něj název vstupní vazby ("b", \<symbol_b >).

Pokud následné uzel opětovně používá tento SqlSelectStatement, přidá položku do tabulky symbolů pro propojení názvu Vstupní vazba na tento symbol. V našem příkladu by opakovaně používat SqlSelectStatement a přidejte DbProjectExpression vstupní vazby názvem "a" ("a", \< symbol_b >) do tabulky.

Když výrazy odkazovat na název vstupní vazby uzlu, který je použití SqlSelectStatement, odkaz je přeložit pomocí tabulky symbolů správné přesměrovaného symbol. Až se "a" z "a.x" vyřeší při návštěvě DbVariableReferenceExpression představující "a" it se přeloží na Symbol \<symbol_b >.

### <a name="join-alias-flattening"></a>Připojte se k vyrovnání Alias

Připojení k vyrovnání alias se dosáhne, když návštěv DbPropertyExpression, jak je popsáno v části s názvem DbPropertyExpression.

### <a name="column-name-and-extent-alias-renaming"></a>Název sloupce a míry Alias přejmenování

Problém název sloupce a míry přejmenování alias je určeno pomocí symbolů, které pouze získat nahrazeny s aliasy ve druhé fázi generování je popsáno v části s názvem druhou fázi generování SQL: Generování příkazu řetězec.

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>První fáze generování SQL: Navštívit stromu výrazů

Tato část popisuje první fázi generování SQL, když je vytvořen představující výraz, který navštívil dotaz a zprostředkujících strukturu, buď SqlSelectStatement nebo SqlBuilder.

Tato část popisuje zásady hostujícími kategorie uzlu jiný výraz a podrobnosti hostujících typy konkrétní výrazů.

### <a name="relational-non-join-nodes"></a>Relační uzly (nikoli na spojení)

Následující typy výrazů podporují – připojení k uzlům:

- DbDistinctExpression

- DbFilterExpression

- DbGroupByExpression

- DbLimitExpression

- DbProjectExpression

- DbSkipExpression

- DbSortExpression

Navštívit tyto uzly následuje následujícímu vzoru:

1. Navštivte relační vstupní a získat výsledný SqlSelectStatement. Vstup do relační uzlu může být jeden z následujících akcí:

    - Relační uzlu, včetně rozsahu (DbScanExpression, například). Navštívit takový uzel vrátí SqlSelectStatement.

    - Operace výraz sady (UNION ALL, například). Výsledek musí být zabalené v hranatých závorkách a put v klauzuli FROM nové SqlSelectStatement.

2. Zkontrolujte, zda aktuální uzel, mohou být přidány do SqlSelectStatement vytvářených vstupu. V části s názvem výrazy seskupování na příkazy SQL popisuje to. Pokud ne,

    - Aktuální objekt SqlSelectStatement POP.

    - Vytvořit nový objekt SqlSelectStatement a přidejte popped SqlSelectStatement jako z nového objektu SqlSelectStatement.

    - Vložte nový objekt vrcholu zásobníku.

3. Přesměrování vazby vstupní výraz na správném symbolu ze vstupu. Tyto informace se udržuje v SqlSelectStatement objektu.

4. Přidáte nový obor SymbolTable.

5. Získáte součást bez zadání výrazu (například projekce a predikát).

6. Vyvolat přes POP všechny objekty přidávané do globální zásobníků.

 DbSkipExpression nemají přímý ekvivalent v SQL. Logicky je přeložen do:

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a>Připojte se k výrazy

Následující považují spojení výrazů a jejich zpracování v běžným způsobem metodou VisitJoinExpression:

- DbApplyExpression

- DbJoinExpression

- DbCrossJoinExpression

Tady jsou kroky najdete:

Nejprve před podřízené objekty, je vyvolána IsParentAJoin ke kontrole, jestli je spojení uzel potomka spojení podél levém hřbetu. Pokud vrátí hodnotu false, je spuštěn nový SqlSelectStatement. V tomto smyslu spojení navštívené jinak zbývající uzly, jako nadřazený (připojení k uzlu) vytvoří SqlSelectStatement pro děti pravděpodobně používat.

Za druhé zpracovávat vstupy jeden najednou. Pro každý vstupní:

1. Navštivte vstupu.

2. Proces příspěvek výsledek hostujících vstup vyvoláním ProcessJoinInputResult, která zodpovídá za údržbu tabulky symbolů po navštívit podřízený výrazu spojení a pravděpodobně dokončení SqlSelectStatement vytvářených podřízené. Dítěte výsledkem může být jeden z následujících akcí:

    - SqlSelectStatement jinak než ke které se přidají nadřazené. V takovém případě bude pravděpodobně nutné dokončit tak, že přidáte výchozí sloupce. Pokud tento vstup byl spojení, musíte vytvořit nový symbol spojení. V opačném případě vytvořte symbol normální.

    - Rozsah (DbScanExpression, například), ve kterém v takovém případě se jednoduše přidá na seznam vstupů nadřazené SqlSelectStatement.

    - Není SqlSelectStatement, ve kterém složené závorky případu, které je zabalena.

    - Stejné SqlSelectStatement, ke kterému se přidá nadřazené. V takovém případě potřebujete symboly v seznamu FromExtents nahradit jednu novou JoinSymbol představující všechny.

    - Pro první tři případy se nazývá AddFromSymbol přidejte klauzuli AS a aktualizovat tabulky symbolů.

Třetí je zobrazeny jako podmínku připojení (pokud existuje).

### <a name="set-operations"></a>Množinové operace

Množinové operace DbUnionAllExpression DbExceptExpression a DbIntersectExpression jsou zpracovány metoda VisitSetOpExpression. Vytvoří SqlBuilder tvaru

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

Kde \<leftSqlSelectStatement > a \<rightSqlSelectStatement > jsou SqlSelectStatements získali na jednotlivých vstupních hodnot, a \<setOp > je odpovídající operace (UNION ALL příkladu).

### <a name="dbscanexpression"></a>DbScanExpression

Je-li zobrazeny v kontextu spojení (jako vstup do spojení, která je levého potomka jiné připojení), vrátí DbScanExpression SqlBuilder s cílem SQL pro odpovídající cíl, který definuje dotaz, tabulka nebo zobrazení. V opačném případě nová SqlSelectStatement se vytvoří s pole FROM nastavit tak, aby odpovídaly odpovídající cíle.

### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

Navštivte DbVariableReferenceExpression vrátí Symbol odpovídající tento výraz odkazu na proměnnou podle pohled nahoru v tabulce symbolů.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Spojení sloučení alias je identifikovat a zpracovány při návštěvě DbPropertyExpression.

Vlastnost Instance je nejprve nenavštívil a výsledkem je Symbol, JoinSymbol nebo SymbolPair. Tady je způsob zpracování těchto třech případech:

- Pokud se vrátí JoinSymbol, než jeho NameToExtent vlastnost obsahuje symbol pro vlastnost potřebné. Pokud spojení symbol představuje vnořené spojení, vrátí se nový pár Symbol symbolem spojení ke sledování symbol, který se použije jako instance alias a symbol představující skutečný vlastnost pro další řešení.

- Pokud se vrátí SymbolPair a části sloupce je symbol, spojení, znovu vrátí symbol spojení, ale nyní je vlastnost sloupec aktualizovat tak, aby odkazoval na vlastnost reprezentována výrazem aktuální vlastnost. Jinak se vrátí SqlBuilder zdrojem SymbolPair jako alias a symbolů pro aktuální vlastnost jako sloupec.

- Pokud je Symbol, navštivte metoda vrátí SqlBuilder metodou instance jako alias a název jako název sloupce.

### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

Při použití jako vlastnost DbProjectExpression projekce DbNewInstanceExpression vytváří čárkou oddělený seznam argumentů pro reprezentaci předpokládané sloupce.

Pokud DbNewInstanceExpression má návratový typ kolekce a definuje novou kolekci výrazů ve formě argumentů, následující tři případy se řeší samostatně:

- Pokud DbNewInstanceExpression DbElementExpression jako jediný argument, je přeložen následujícím způsobem:

    ```
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
    ```

Pokud DbNewInstanceExpression nemá žádné argumenty (představuje prázdné tabulky), DbNewInstanceExpression je přeložit na:

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

V opačném případě DbNewInstanceExpression sestavení žebříku sjednocení všech argumentů:

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a>DbFunctionExpression

Canonical a integrované funkce jsou zpracovány stejně: Pokud se vyžadují speciální zacházení (TRIM(string) k LTRIM(RTRIM(string), například), je vyvolána odpovídající obslužná rutina. V opačném případě jsou přeloženy na FunctionName (arg1, arg2,..., argn).

Slovníky se používají k udržovat přehled o funkcích, které potřebují zvláštní zacházení a jejich odpovídající obslužné rutiny.

Uživatelem definované funkce jsou přeloženy na NamespaceName.FunctionName (arg1, arg2,..., argn).

### <a name="dbelementexpression"></a>DbElementExpression

Metoda, která se navštíví DbElementExpression se vyvolá pouze navštívili DbElementExpression, když se používá k reprezentování skalární poddotaz. Proto DbElementExpression překládá do dokončení SqlSelectStatement a přidá závorky kolem něj.

### <a name="dbquantifierexpression"></a>DbQuantifierExpression

V závislosti na typu výrazu (některé nebo všechny), je přeložen DbQuantifierExpression jako:

```
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a>DbNotExpression

V některých případech je možné sbalit překladu třída DbNotExpression s jeho vstupní výraz. Příklad:

```
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

Z důvodů, proč se provádí druhý sbalit totiž nedostatečnou zavedených zprostředkovatelem překladu DbQuantifierExpression z type All. Entity Framework proto nelze provést zjednodušení.

### <a name="dbisemptyexpression"></a>DbIsEmptyExpression

DbIsEmptyExpression je přeložen jako:

```
IsEmpty(inut) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druhá fáze generování SQL: Generování příkazu řetězec

Při generování řetězec příkazu SQL, SqlSelectStatement vytvoří skutečné aliasy pro symboly, které řeší problém název sloupce a míry přejmenování alias.

Přejmenování alias rozsahu vyvolá se při zápisu objektu SqlSelectStatement do řetězce. Nejprve vytvořte seznam všechny aliasy, které používá vnější rozsah. Pokud koliduje s žádným z rozsahů vnější, získá každý symbol FromExtents (nebo AllJoinExtents, pokud je jiná než null), přejmenovat. V případě potřeby přejmenování to nebude v konfliktu s žádným z rozsahů shromážděných v AllExtentNames.

Přejmenování sloupců, nastane při zápisu Symbol – objekt na řetězec. AddDefaultColumns v první fázi určil, pokud symbol určité sloupce musí být přejmenována. Ve druhé fázi dochází pouze přejmenovat a ujistěte se, že název vytvořeného není v konfliktu s používán AllColumnNames

Chcete-li vytvořit jedinečné názvy pro aliasy rozsahu a sloupců, použijte \<existing_name > _n, kde n je nejmenší alias, který nebyl dosud použit. Globální seznam všechny aliasy zvyšuje potřebu kaskádové přejmenuje.

## <a name="see-also"></a>Viz také:

- [Generování SQL ve zprostředkovateli ukázek](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
