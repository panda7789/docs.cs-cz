---
title: Jak se liší od Transact-SQL Entity SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: d34c6933e0f19c73b954446fdf18cea7243eae0d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Jak se liší od Transact-SQL Entity SQL
Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
## <a name="inheritance-and-relationships-support"></a>Dědičnost a vztahy podpory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pracuje přímo s koncepční entity schémata a podporuje konceptuálního modelu funkce jako je například dědičnosti a vztahy.  
  
 Při práci s použitím dědičnosti, je často užitečné k výběru instancí podtypu z kolekce instancí nadtyp. [Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operátor v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobně jako `oftype` v C# pořadí) umožňuje používat tuto funkci.  
  
## <a name="support-for-collections"></a>Podpora pro kolekce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekce se považuje za první třídy entity. Příklad:  
  
-   Jsou platné v kolekci výrazy `from` klauzule.  
  
-   `in` a `exists` poddotazy jste zobecnili umožňující žádných kolekcí.  
  
     Poddotaz je jeden typ kolekce. `e1 in e2` a `exists(e)` jsou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukce k provádění těchto operací.  
  
-   Nastavte operace, jako je třeba `union`, `intersect`, a `except`, nyní fungovat na kolekce.  
  
-   Spojení pracovat kolekce.  
  
## <a name="support-for-expressions"></a>Podpora pro výrazy  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] má poddotazy (tabulky) a výrazy (řádků a sloupců).  
  
 Pro podporu kolekcí a vnořené kolekcí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] všechno, co je výraz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] složení více než [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]– každých výraz lze použít kdekoli. Dotaz výrazy vždy mít za následek kolekcí předpokládané typů a mohou být použity kdekoli je povolen výraz kolekce. Informace o [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazy, které nejsou podporované v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], najdete v části [nepodporované výrazy](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
 Následující položky jsou všechny platné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednotné zacházení s poddotazy  
 Zadané jeho důraz na tabulky, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] provede kontextové výklad poddotazy. Například poddotazu v `from` klauzule se považuje za multimnožina (tabulky). Ale stejné poddotazu používán `select` se považuje za skalární poddotazu klauzule. Podobně poddotaz použit na levé straně `in` operátor se považuje za skalární poddotazu, zatímco pravé straně se očekává multiset poddotazu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Eliminuje tyto rozdíly. Výraz obsahuje jednotný výklad, která není závislá na kontext, ve kterém se používá. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zvažuje všech poddotazech být multiset poddotazy. Pokud se požaduje skalární hodnotu poddotazu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje `anyelement` operátor, který funguje na kolekci (v tomto případě je poddotaz) a extrahuje hodnotu singleton z kolekce.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Zamezení implicitní Coercions pro poddotazy  
 Související vedlejším účinkem jednotné zacházení s poddotazy je implicitní převod poddotazy skalárních hodnot. Konkrétně v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], multimnožina řádků (s jedním polem) je implicitně převést na skalární hodnotu s datovým typem je, že pole.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje tento implicitní převod. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje operátor ANYELEMENT extrahovat hodnotu singleton z kolekce a `select value` klauzule Vyhněte se vytváření obálce řádek během výrazu dotazu.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Vyberte hodnotu: Zamezení implicitní řádek obálky  
 V klauzuli select [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] poddotazu implicitně vytvoří řádek obálku kolem položky v klauzuli. To znamená, že nemůžeme vytvořit kolekcí skalárních hodnot nebo objekty. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umožňuje implicitní vynucení mezi rowtype s jedno pole a hodnotu singleton stejného datového typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje `select value` klauzule tak, aby přeskočil konstrukce implicitní řádek. Možné zadat jen jednu položku `select value` klauzule. Pokud se používá tato klauzule, žádný řádek obálky je postavena na položky v `select` klauzule a kolekce požadovaný tvar může být vytvořil, například: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také poskytuje konstruktor row můžete vytvořit libovolný řádků. `select` přijímá jeden či více elementů v projekci a má za následek záznam dat s poli, následujícím způsobem:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Levá korelace a aliasy  
 V [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], výrazy v daném oboru (jako jedna klauzule `select` nebo `from`) nemůže odkazovat na výrazy definovaného dříve ve stejném oboru. Některé dialekty SQL (včetně [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) podporují omezené formy v `from` klauzule.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Umožňuje zobecnit v levém korelací `from` klauzuli a pracuje s nimi jednotně. Výrazy v `from` klauzule odkazovat v klauzuli stejné bez nutnosti další syntaxe starší definice (definice doleva).  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také ukládá další omezení na dotazy zahrnující `group by` klauzule. Výrazy v `select` klauzule a `having` klauzule takové dotazy mohou odkazovat pouze na `group by` klíče prostřednictvím jejich aliasy. Platí následující konstrukce v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 To uděláte v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>(Vlastnosti) odkazujících sloupců tabulky (kolekce)  
 Všechny odkazy na sloupce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být kvalifikovaný pomocí tabulky alias. Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T`) je platný v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale ne v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formulář  
  
```  
select t.a as A from T as t  
```  
  
 Aliasy tabulky jsou v volitelný `from` klauzule. Název tabulky se používá jako implicitní alias. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Umožňuje také následující tvar:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Navigace prostřednictvím objektů  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] používá "." zápis pro sloupce (řádek) odkazující na tabulku. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozšiřuje tento zápis (vždy pouze vypůjčí na programovací jazyky) pro podporu navigační prostřednictvím vlastnosti objektu.  
  
 Například pokud `p` je výraz, který typ osoba, následuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe pro odkazování na město adresy této osoby.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Žádná podpora pro *  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] podporuje nekvalifikované * syntaxe jako alias pro celý řádek a kvalifikovaný \* syntaxe (t.\*) jako zástupce pro pole této tabulky. Kromě toho [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umožňuje speciální Count (\*) agregace, který obsahuje hodnoty Null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje * konstrukce. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] dotazy, formuláře `select * from T` a `select T1.* from T1, T2...` může být vyjádřený v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`, v uvedeném pořadí. Kromě toho tyto konstrukce zpracování dědičnosti (hodnota dodávek), zatímco `select *` variant jsou omezeny na deklarovaný typ vlastnosti nejvyšší úrovně.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje `count(*)` agregační. Místo nich se používá `count(0)`.  
  
## <a name="changes-to-group-by"></a>Změny Seskupit podle  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje aliasy z `group by` klíče. Výrazy v `select` klauzule a `having` klauzule musí odkazovat `group by` klíče přes tyto aliasy. Například to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 .. je ekvivalentní pro následující [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Na základě kolekce agregace  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dva druhy agregace.  
  
 Na základě kolekce agregace pracovat kolekce a vytvoření agregované výsledku. To může vyskytovat kdekoli v dotazu a nevyžadují `group by` klauzule. Příklad:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje také agreguje stylu SQL. Příklad:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY – klauzule využití  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] Umožňuje klauzule ORDER BY zadat pouze v nejhornější SELECT... Z... KDE blok. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít výraz vnořené klauzule ORDER BY a mohou být umístěny kdekoli v dotazu, ale řazení v vnořený dotaz není zachován.  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Identifikátory  
 V [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], porovnání identifikátoru je založena na kolaci aktuální databáze. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifikátory jsou vždy aktivní a malých písmen a rozlišovat znaky s diakritikou (tedy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozlišuje mezi znaky s diakritikou a příslušných; například "a" není rovno "ấ"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zpracovává verzích písmena, která zobrazí stejné, ale jsou z jiné znakové stránky jako jiné znaky. Další informace najdete v tématu [vstup znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Příkaz Transact-SQL funkce není k dispozici v entitě SQL  
 Následující [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] funkce není k dispozici v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aktuálně poskytuje žádná podpora pro příkazy DML (vložení, aktualizaci, odstranění).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje žádná podpora pro DDL v aktuální verzi.  
  
 Imperativní programování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje žádná podpora pro imperativní programování, na rozdíl od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Místo toho použijte programovací jazyk.  
  
 Funkce seskupování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ještě neposkytuje podporu pro seskupování funkce (například CUBE, ROLLUP a GROUPING_SET).  
  
 Analytické funkce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ne (ještě) poskytuje podporu pro analytické funkce.  
  
 Integrované funkce, operátory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje podmnožinu [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]je součástí funkce a operátory. Tyto operátory a funkce budou pravděpodobně podporovat poskytovatelé hlavní úložiště. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele. Kromě toho [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umožňuje deklarovat předdefinované a vlastní existující uloží funkce, pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používat.  
  
 Pomocné parametry  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] neposkytuje mechanismy pro pomocné parametry dotazu.  
  
 Dávkování výsledky dotazu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje dávkování výsledky dotazu. Například následující platí [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (odesílajícím jako dávku):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Ale ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není podporována:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje pouze jeden příkaz dotazu generovala výsledek za příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Nepodporované výrazy](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
