---
title: "Architektura a návrh"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 48b80856242730a5412cd9d5d8dd2c7f857304ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="architecture-and-design"></a>Architektura a návrh
Modul generování SQL v [ukázka zprostředkovatele](http://go.microsoft.com/fwlink/?LinkId=180616) je implementovaný jako návštěvníka na strom výrazu, který představuje strom příkazů. Generování probíhá v jednom průchodu přes strom výrazu.  
  
 Uzly stromu jsou zpracovávány zdola nahoru. Nejprve se vytvářejí zprostředkující struktura: SqlSelectStatement nebo SqlBuilder, obě implementuje ISqlFragment. V dalším kroku řetězec příkazu jazyka SQL se vytvářejí z této struktury. Existují dva důvody pro zprostředkující strukturu:  
  
-   Příkaz SELECT se naplní logicky, mimo pořadí. Uzly, které jsou součástí klauzule FROM navštívené před uzly, které jsou součástí WHERE, GROUP BY a klauzuli ORDER by.  
  
-   Pokud chcete přejmenovat aliasy, musí identifikovat všechny používané aliasy pro zabrání se tím kolizím při přejmenování. Symbol objekty odložení přejmenování volbám v SqlBuilder, lze použijte k reprezentaci sloupce, které jsou kandidáty pro přejmenování.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")  
  
 V první fázi, při návštěvě strom výrazu výrazy jsou seskupené do SqlSelectStatements, se sloučí spojení a aliasy spojení se sloučí. V tomto průchodu Symbol objekty představují vstupní aliasy, které může být přejmenován nebo sloupce.  
  
 Ve druhé fázi se při vytváření konkrétní řetězec jsou přejmenovány aliasy.  
  
## <a name="data-structures"></a>Datové struktury  
 Tato část popisuje typy používané v [ukázka zprostředkovatele](http://go.microsoft.com/fwlink/?LinkId=180616) používané k vytvoření příkazu SQL.  
  
### <a name="isqlfragment"></a>ISqlFragment  
 Tato část obsahuje třídy, které implementují rozhraní ISqlFragment, která má dva účely:  
  
-   Běžné návratový typ pro všechny metody návštěvníka.  
  
-   Poskytuje metodu pro zápis konečné řetězec SQL.  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a>SqlBuilder  
 SqlBuilder je shromažďování zařízení pro konečné řetězec SQL, podobně jako StringBuilder. Skládá se z řetězců, které tvoří konečné SQL, společně s ISqlFragments, kterou můžete převést do řetězce.  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a>SqlSelectStatement  
 SqlSelectStatement představuje kanonický příkazu SQL SELECT tvaru vyberte..." Z... KDE... SESKUPIT PODLE... ŘADIT PODLE".  
  
 Každý z klauzule SQL je reprezentována StringBuilder. Kromě toho sleduje, zda byla zadána klauzule Distinct, a jestli je nejhornější příkaz. Pokud příkaz není nejhornější, klauzule ORDER by je vynechán, pokud příkaz také obsahuje klauzuli TOP.  
  
 FromExtents obsahuje seznam vstupy pro příkaz SELECT. V tomto obvykle není právě jeden element. Příkazy SELECT pro spojení dočasně může mít více než jeden element.  
  
 Pokud příkaz SELECT se vytvoří pomocí připojení k uzlu, SqlSelectStatement udržuje seznam všechny rozsahy, které byly průmětu ve spojení v AllJoinExtents. OuterExtents představuje vnější odkazů SqlSelectStatement a používá se pro přejmenování vstupní alias.  
  
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
  
#### <a name="topclause"></a>TopClause  
 TopClause představuje výraz TOP v SqlSelectStatement. Vlastnost TopCount Určuje, kolik HORNÍCH řádků měla by být vybrána.  Pokud WithTies hodnotu true, TopClause byl sestaven z DbLimitExpession.  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a>Symboly  
 Třídy související s Symbol a tabulky symbolů provádění přejmenování vstupní alias, vyrovnání alias spojení a přejmenování alias sloupce.  
  
 Třída Symbol představuje rozsah, vnořené příkazu SELECT nebo sloupec. Místo skutečného alias se používá k povolení pro přejmenování po byla použita a spojeno také další informace o artefaktu, který představuje (např. typu).  
  
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
  
 Ukládá název aliasu původní pro reprezentována rozsah, vnořené příkazu SELECT nebo sloupec.  
  
 NewName ukládá alias, který se použije v příkazu SQL SELECT. Je původně nastavena na název a přejmenovat pouze v případě potřeby při generování v posledním řetězci dotazu.  
  
 Typ je platný pouze pro symboly představující rozsahy a vnořených příkazů SELECT.  
  
#### <a name="symbolpair"></a>SymbolPair  
 Třída SymbolPair řeší záznamů sloučení.  
  
 Vezměte v úvahu výraz vlastnost D (v, "j3.j2.j1.a.x"), kde je v VarRef, j1, j2, j3 jsou spojení, je rozsah a x sloupců.  
  
 Tento postup je nakonec přeložit na  }. {x'}.Pole zdroje představuje nejkrajnější SqlStatement, představující výraz spojení (například j2); Toto je vždy symbol spojení. Pole sloupec přesune z jednoho připojení k symbol na další končí na symbol – připojení k. To je vrácena, pokud návštěvou DbPropertyExpression, ale nikdy je přidán do SqlBuilder.  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a>JoinSymbol  
 Symbol spojení je Symbol, který představuje vnořený příkaz SELECT s spojení nebo spojení vstup.  
  
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
  
 Seznam sloupců představuje seznam sloupců v klauzuli SELECT, pokud tento symbol představuje příkazu SQL SELECT. ExtentList je seznam rozsahů v klauzuli SELECT. Pokud připojení k více rozsahů průmětu na nejvyšší úrovni, sleduje FlattenedExtentList rozsahy zajistit této míře, které aliasy jsou přejmenovány správně.  
  
 NameToExtent má všechny rozsahy v ExtentList jako slovník. IsNestedJoin slouží k určení, zda je JoinSymbol symbol obyčejnou spojení nebo ten, který má odpovídající SqlSelectStatement.  
  
 Všechny seznamy jsou nastavit přesně jednou a pak se použije pro hledání nebo výčet.  
  
#### <a name="symboltable"></a>SymbolTable  
 SymbolTable se používá k překladu názvů proměnných na symboly. SymbolTable je implementovaný jako zásobníku se nový záznam pro každý obor. Hledání vyhledávání z horní části zásobníku k dolnímu dokud nebude nalezen položku.  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 Není k dispozici pouze jeden SymbolTable na jednu instanci modulu generování Sql. Zadaný a byl ukončen pro každý uzel relační oborů. Všechny symboly v dřívější obory jsou viditelné pro novější obory, pokud není skrytý na základě jiných symbolů se stejným názvem.  
  
### <a name="global-state-for-the-visitor"></a>Globální stav pro návštěvníka  
 Jako pomoc při přejmenování aliasy a sloupce, spravovat seznam všechny názvy sloupců (AllColumnNames) a aliasy rozsah (AllExtentNames), které byly použity v první předání přes stromu dotazu.  Tabulky symbolů přeloží názvy proměnných na symboly. IsVarRefSingle se používá pouze pro účely ověření není nezbytně nutné.  
  
 Dva zásobníky používá prostřednictvím CurrentSelectStatement a IsParentAJoin jsou sloužící k předávání "parametry" z nadřazené do podřízené uzly, vzhledem k tomu, že nám předat parametry neumožňuje vzoru návštěvníka.  
  
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
  
## <a name="common-scenarios"></a>Běžné scénáře  
 Tato část popisuje běžné scénáře zprostředkovatele.  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a>Seskupování uzlů výraz do SQL příkazy  
 SqlSelectStatement se vytvoří při prvním relační uzlu je došlo (obvykle rozsah DbScanExpression) při návštěvě stromu zdola nahoru. K vytvoření příkazu SQL SELECT s jako několika vnořené dotazy nejdříve agregační jako řadu svých nadřazených uzlů co možná v tomto SqlSelectStatement.  
  
 Rozhodnutí, zda daný uzel (relační) mohou být přidány do aktuální SqlSelectStatement (jeden, vrácena při návštěvě vstup) nebo pokud je třeba spustit nové prohlášení je počítaný metodou IsCompatible a závisí na co se již SqlSelectStatement, což závisí na uzly byly dole daný uzel.  
  
 Obvykle Pokud klauzule příkazu SQL, jsou vyhodnoceny po klauzule kde uzly za ke sloučení nejsou prázdné, uzel nelze přidat do aktuální příkaz. Například pokud další uzel je filtr, aby uzel lze začlenit do aktuální SqlSelectStatement pouze v případě, že platí následující:  
  
-   Vyberte seznam je prázdný. Pokud seznamu příkazu SELECT není prázdná, seznamu příkazu select bylo vytvořeno uzel předcházející filtr a predikát může odkazovat na sloupce vyprodukované tohoto seznamu, vyberte možnost.  
  
-   GROUPBY je prázdný. Pokud GROUPBY není prázdná, přidání filtru znamená filtrování před seskupení, která není správný.  
  
-   Klauzule TOP je prázdný. Když klauzule TOP není prázdná, přidání filtru by totiž filtrování před provedením NAHOŘE, který není správný.  
  
 To neplatí pro nerelační uzly jako DbConstantExpression nebo aritmetických výrazech, protože se jedná vždy součástí existující SqlSelectStatement.  
  
 Při zjištění kořenu stromu spojení (připojení k uzlu, který nemá připojení k nadřazené), je spuštěn nový SqlSelectStatement. Všechny podřízené spojení levé spine se agregován do tohoto SqlSelectStatement.  
  
 Vždy, když se spustí novou SqlSelectStatement a stávající se přidá do vstupní, aktuální SqlSelectStatement může třeba provést přidáním sloupce projekce (klauzuli SELECT), pokud neexistuje. To se provádí pomocí metody AddDefaultColumns, který zjistí FromExtents SqlSelectStatement a přidá všechny sloupce, které přináší seznam rozsahů reprezentována FromExtents v oboru do seznamu předpokládané sloupců. Důvodem je, protože v tomto okamžiku Neznámý sloupce, které odkazují na jiných uzlech. To může být optimalizovaná tak, aby pouze projektu sloupce, které můžete později použít.  
  
### <a name="join-flattening"></a>Připojení k vyrovnání  
 Vlastnost IsParentAJoin pomáhá určit, zda lze vyrovnány dané připojení. Konkrétně IsParentAJoin vrátí `true` pouze pro podřízený objekt levé spojení a pro každou DbScanExpression, který je okamžitý vstupní spojení, v takovém případě tento podřízený uzel opětovně používá stejné SqlSelectStatement, nadřazený byste použili později. Další informace najdete v tématu "Výrazy připojení".  
  
### <a name="input-alias-redirecting"></a>Vstupní Alias přesměrování  
 Přesměrování vstupní alias je provedeno pomocí tabulky symbolů.  
  
 Vysvětlení, přesměrování vstupní alias, naleznete v prvním příkladu v [generování SQL z stromy příkazů – doporučené postupy](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).  Existuje "a" potřeba přesměrovat na "b" v projekci.  
  
 Když je vytvořen objekt SqlSelectStatement, rozsah, který je vstup uzlu uveden vlastnost From SqlSelectStatement. Symbol (< symbol_b >) se vytvoří na základě název vstupní vazby ("b") představují tento rozsah a "AS" + < symbol_b > je připojeno k klauzule From.  Symbol je taky přidaný ke FromExtents vlastnost.  
  
 Symbol je taky přidaná do tabulky symbolů propojení název vstupní vazby k němu ("b", < symbol_b >).  
  
 Pokud následné uzlu opětovně používá tento SqlSelectStatement, přidá položku do tabulky symbolů propojení její název Vstupní vazba na tento symbol. V našem příkladu by opakovaně použít SqlSelectStatement a přidejte DbProjectExpression s názvem Vstupní vazba "a" ("a", \< symbol_b >) do tabulky.  
  
 Když výrazy odkazovat na název vstupní vazby uzlu, který je použití SqlSelectStatement, že je odkaz přeložit pomocí tabulky symbolů na správný přesměrovaného symbol. Při "a" z "a.x" vyřešení při návštěvě představující DbVariableReferenceExpression "a" it přeloží na symbol < symbol_b >.  
  
### <a name="join-alias-flattening"></a>Připojení k vyrovnání Alias  
 Připojení k vyrovnání alias se dosáhne, když návštěvou DbPropertyExpression, jak je popsáno v části s názvem DbPropertyExpression.  
  
### <a name="column-name-and-extent-alias-renaming"></a>Název sloupce a míry Alias přejmenování  
 Problém název sloupce a míry alias přejmenování je řešit pomocí znaky, které pouze získat nahrazena s aliasy ve druhé fázi generování popsané v části s názvem druhé fáze generování SQL: generování příkaz String.  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>První fáze generování SQL: návštěvou strom výrazu  
 Tato část popisuje první fáze generování SQL, když je vytvořil výraz představující, které je navštívené dotaz a zprostředkující struktura, buď SqlSelectStatement nebo SqlBuilder.  
  
 Tato část popisuje zásad hostujícími jiný výraz uzlu kategorií a podrobnosti hostujících typy konkrétní výrazů.  
  
### <a name="relational-non-join-nodes"></a>Relační uzlů (bez připojení k)  
 Následující typy výrazů podporují – připojení k uzly:  
  
-   DbDistinctExpression  
  
-   DbFilterExpression  
  
-   DbGroupByExpression  
  
-   DbLimitExpession  
  
-   DbProjectExpression  
  
-   DbSkipExpression  
  
-   DbSortExpression  
  
 Kteří navštěvují tyto uzly se následující následující:  
  
1.  Navštivte relační vstupní a získat výsledné SqlSelectStatement. Vstup relační uzel může být jeden z následujících akcí:  
  
    -   Relační uzlu, včetně rozsah (DbScanExpression, např.). Návštěvou takový uzel vrátí SqlSelectStatement.  
  
    -   Operace výraz sady (UNION ALL, např.). Výsledek musí být uzavřen do závorek a put v klauzuli FROM nové SqlSelectStatement.  
  
2.  Zkontrolujte, zda aktuální uzel mohou být přidány do SqlSelectStatement vyprodukované vstupu. V části s názvem výrazy seskupení do příkazů SQL popisuje to. Pokud ne,  
  
    -   Aktuální objekt SqlSelectStatement POP.  
  
    -   Vytvořit nový objekt SqlSelectStatement a přidejte popped SqlSelectStatement jako od nového objektu SqlSelectStatement.  
  
    -   Uveďte nový objekt nad zásobníku.  
  
3.  Přesměrování vazby vstupní výraz na správný symbol ze vstupu. Tyto informace se udržuje v SqlSelectStatement objektu.  
  
4.  Přidáte nový obor SymbolTable.  
  
5.  Navštivte pro jiný vstup část výrazu (například projekce a predikát).  
  
6.  POP – všechny objekty přidané do globální zásobníky.  
  
 DbSkipExpression nemá přímé ekvivalent v systému SQL. Logicky je převeden do:  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a>Připojení k výrazy  
 Následující jsou zvažovány spojení výrazy a běžné způsobem, jsou zpracovávány metodou VisitJoinExpression:  
  
-   DbApplyExpression  
  
-   DbJoinExpression  
  
-   Objekt DbCrossJoinExpression  
  
 Tady jsou kroky najdete:  
  
 Před návštěvou podřízené objekty, je nejprve IsParentAJoin a zkontrolujte, zda připojení k uzlu podřízenou spojení podél levého spine volána. Pokud vrátí hodnotu false, nové SqlSelectStatement je spuštěn. V tomto smysl spojení navštívené odlišně od zbytku uzly, jako nadřazené (připojení k uzlu) vytvoří SqlSelectStatement pro děti pravděpodobně používat.  
  
 Za druhé zpracovat vstupy jeden najednou. Pro každý vstupní:  
  
1.  Navštivte vstupu.  
  
2.  Proces POST výsledek hostujících vstup vyvoláním ProcessJoinInputResult, který zodpovídá za údržbu tabulky symbolů po návštěvou podřízenou výraz spojení a pravděpodobně dokončení SqlSelectStatement vyprodukované podřízený objekt. Výsledek dítěte může být jeden z následujících akcí:  
  
    -   SqlSelectStatement liší od ten, do které budou přidány nadřazený. V takovém případě je třeba provést přidáním sloupce výchozí. Pokud tento vstup byl spojení, budete muset vytvořit nový symbol spojení. Jinak vytvořte symbol normální.  
  
    -   Rozsah (DbScanExpression, např.), ve kterém je případ, který je jednoduše přidat do seznamu vstupy nadřazené SqlSelectStatement.  
  
    -   Není SqlSelectStatement, ve kterém případu, který je uzavřen do závorky.  
  
    -   Stejné SqlSelectStatement, ke kterému je nadřazená přidána. V takovém případě je nutné symboly v seznamu FromExtents nahradit pomocí jednoho nové JoinSymbol představující je všechny.  
  
    -   První tři v případech se nazývá AddFromSymbol přidat klauzuli a aktualizovat tabulky symbolů.  
  
 Třetí je navštívené podmínku připojení (pokud existuje).  
  
### <a name="set-operations"></a>Množinové operace  
 Množinové operace DbUnionAllExpression, DbExceptExpression a DbIntersectExpression zpracovává metodu VisitSetOpExpression. Vytvoří SqlBuilder tvaru  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 Kde \<leftSqlSelectStatement > a \<rightSqlSelectStatement > se získala při každé vstupních hodnot, kteří navštěvují SqlSelectStatements a \<setOp > je odpovídající operace (UNION ALL např.).  
  
### <a name="dbscanexpression"></a>DbScanExpression  
 Pokud navštívené v kontextu připojení (jako vstup pro připojení k, které je levé podřízená jiné připojení), vrátí DbScanExpression SqlBuilder s cílem SQL pro odpovídající cíl, který je definující dotazu, tabulka nebo zobrazení. Jinak se vytvoří nový SqlSelectStatement s pole od nastavit tak, aby odpovídaly odpovídající cíl.  
  
### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 Návštěvu DbVariableReferenceExpression vrátí Symbol odpovídající tento výraz odkazu na proměnnou podle vyhledávání v tabulce symbolu.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Vyrovnání alias spojení je identifikovat a zpracování při návštěvě DbPropertyExpression.  
  
 Vlastnost Instance první návštěvě a výsledkem je Symbol, JoinSymbol nebo SymbolPair. Tady je způsob zpracování těchto třech případech:  
  
-   Pokud je vrácen JoinSymbol, než jeho NameToExtent vlastnost obsahuje symbol pro vlastnost potřebné. Pokud je symbol spojení představuje vnořené spojení, se vrátí nový pár Symbol s symbol připojení ke sledování symbol, který se použije jako instance alias a symbol reprezentující skutečné vlastnost pro další řešení.  
  
-   Pokud je vrácen SymbolPair a část sloupec je symbol spojení, znovu vrátí symbol spojení, ale nyní je vlastnost column aktualizovat tak, aby odkazoval na vlastnost vyjádřený výrazem aktuální vlastnost. Jinak se vrátí SqlBuilder s zdroji SymbolPair jako alias a symbol pro aktuální vlastnost jako sloupec.  
  
-   Pokud Symbol je vrácena, vrátí metoda návštěvu SqlBuilder metodu s dané instance jako alias a název vlastnosti jako název sloupce.  
  
### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 Když se použije jako vlastnost projekce DbProjectExpression, DbNewInstanceExpression vytvoří textový soubor s oddělovači seznam argumentů představují předpokládané sloupce.  
  
 Když DbNewInstanceExpression má návratový typ kolekce a definuje novou kolekci výrazů zadané jako argumenty, jsou zpracovávány samostatně následujících třech případech:  
  
-   Pokud DbNewInstanceExpression DbElementExpression jako argument pouze, je přeložit takto:  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 Pokud má DbNewInstanceExpression bez argumentů (prázdná tabulka představuje), DbNewInstanceExpression je přeložit na:  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 V opačném případě DbNewInstanceExpression sestavení union all žebříku argumentů:  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Kanonické a integrované funkce jsou zpracovávány stejným způsobem jako: Pokud potřebují zvláštní zpracování (TRIM(string) k LTRIM(RTRIM(string), např.), je vyvolána příslušnou obslužnou rutinu. Jinak jsou převedeny na %{FunctionName/ (arg1, arg2,..., argn).  
  
 Slovník slouží k udržování přehledu o funkcích, které potřebují zvláštní zpracování a jejich odpovídající obslužné rutiny.  
  
 Uživatelem definované funkce jsou tanslated k NamespaceName.FunctionName (arg1, arg2,..., argn).  
  
### <a name="dbelementexpression"></a>DbElementExpression  
 Metoda, která navštíví DbElementExpression je volána, pouze pro návštěvou DbElementExpression, když se používá k reprezentování skalární poddotazu. Proto DbElementExpression překládá do dokončení SqlSelectStatement a přidá hranaté závorky.  
  
### <a name="dbquantifierexpression"></a>DbQuantifierExpression  
 V závislosti na typ výrazu (některé nebo všechny), DbQuantifierExpression přeložit jej jako:  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a>Třída DbNotExpression  
 V některých případech je možné sbalit překlad DbNotExpression s jeho vstupní výraz. Příklad:  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 Z důvodu, který provádí druhý sbalit totiž nedostatky, které byly zavedeny zprostředkovatelem při překladu DbQuantifierExpression z zadejte všechny. Rozhraní Entity Framework proto nelze provést zjednodušení.  
  
### <a name="dbisemptyexpression"></a>DbIsEmptyExpression  
 DbIsEmptyExpression je přeložená jako:  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druhé fáze generování SQL: generování příkaz String  
 Při generování řetězec příkazu SQL, SqlSelectStatement vytvoří skutečné aliasy pro symboly, které řeší problém název sloupce a míry přejmenování alias.  
  
 Přejmenování alias rozsah dojde při zápisu objektu SqlSelectStatement do řetězce. Nejprve vytvořte seznam všechny aliasy používá vnější rozsahy. Každý symbol v FromExtents (nebo AllJoinExtents, pokud je jinou hodnotu než null), získá přejmenovat, pokud ji koliduje s žádným z rozsahů vnější. V případě potřeby přejmenování ho nebude v konfliktu s žádným z rozsahů shromážděny v AllExtentNames.  
  
 Přejmenování sloupce dojde při zápisu Symbol objekt na řetězec. AddDefaultColumns v první fázi určil, pokud symbol některé sloupce musí být přejmenována. V druhé fázi dojde pouze přejmenování, a ujistěte se, že název vytvořeného nejsou v konfliktu s libovolným názvem použít v AllColumnNames  
  
 K vytvoření jedinečné názvy pro rozsah aliasy i pro sloupce, použijte _n < existing_name >, kde n je nejmenší alias, který nebyl dosud použit. Globální seznam všechny aliasy zvyšuje potřebu kaskádových přejmenuje.  
  
## <a name="see-also"></a>Viz také  
 [Generování SQL ve zprostředkovateli ukázek](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
