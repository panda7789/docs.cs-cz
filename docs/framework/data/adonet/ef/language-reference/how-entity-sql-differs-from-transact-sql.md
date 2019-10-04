---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833713"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Jak se Entity SQL liší od Transact-SQL
Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Podpora dědičnosti a vztahů  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funguje přímo s koncepčními schématy entit a podporuje koncepční modelové funkce, jako je například dědičnost a vztahy.  
  
 Při práci s děděním je často vhodné vybrat instance podtypu z kolekce instancí typu nadtyp. Tato funkce poskytuje operátor [OfType](oftype-entity-sql.md) v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobně jako @no__t- C# 2 v sekvencích).  
  
## <a name="support-for-collections"></a>Podpora pro kolekce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zpracovává kolekce jako entity první třídy. Příklad:  
  
- Výrazy kolekce jsou platné v klauzuli `from`.  
  
- poddotazy `in` a `exists` byly zobecněny, aby umožňovaly všechny kolekce.  
  
     Poddotaz je jeden druh kolekce. `e1 in e2` a `exists(e)` jsou konstrukce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provedení těchto operací.  
  
- Nastavení operací, například `union`, `intersect` a `except`, nyní fungují na kolekcích.  
  
- Spojení se spouštějí na kolekcích.  
  
## <a name="support-for-expressions"></a>Podpora pro výrazy  
 V jazyce Transact-SQL jsou poddotazy (tabulky) a výrazy (řádky a sloupce).  
  
 Aby bylo možné podporovat kolekce a vnořené kolekce, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provede všechny výrazy. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je mnohem sestavitelný než Transact-SQL – každý výraz lze použít kdekoli. Výrazy dotazů mají vždycky za následek kolekce projektových typů a dají se použít kdekoli je povolený výraz kolekce. Informace o výrazech jazyka Transact-SQL, které nejsou podporovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], naleznete v tématu [nepodporované výrazy](unsupported-expressions-entity-sql.md).  
  
 Níže jsou uvedené všechny platné dotazy [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednotné zpracování poddotazů  
 V jazyce Transact-SQL, který má vzhledem k tabulkám zdůraznění, provádí kontextovou interpretaci poddotazů. Například poddotaz v klauzuli `from` se považuje za multiset (tabulka). Ale stejný poddotaz použitý v klauzuli `select` je považován za skalární poddotaz. Podobně by byl poddotaz použitý na levé straně operátoru `in` považován za skalární poddotaz, zatímco na pravé straně se očekává poddotaz multiset.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] eliminuje tyto rozdíly. Výraz má jednotný výklad, který není závislý na kontextu, ve kterém je použit. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] předpokládá, že všechny poddotazy budou multiset poddotazy. Pokud je v poddotazu požadováno skalární hodnota, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje operátor `anyelement`, který pracuje na kolekci (v tomto případě poddotaz), a extrahuje hodnotu singleton z kolekce.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Zamezení implicitních vynucení pro poddotazy  
 Související vedlejší účinky jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty. Konkrétně v jazyce Transact-SQL je multiset řádků (s jedním polem) implicitně převeden na skalární hodnotu, jejíž datový typ je to pole.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje tuto implicitní vynucení. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje operátor ANYELEMENT k extrakci hodnoty singleton z kolekce a klauzule `select value`, aby nedošlo k vytvoření řádku-obálky během výrazu dotazu.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Vyberte hodnotu: vyloučí se obálku implicitního řádku.  
 Klauzule SELECT v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položek v klauzuli. To znamená, že nemůžeme vytvořit kolekce skalárních objektů nebo objektů. Transact-SQL umožňuje implicitní vynucení mezi RowType a jedním polem a hodnotou singleton stejného datového typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje klauzuli `select value` pro přeskočení vytváření implicitních řádků. V klauzuli `select value` lze zadat pouze jednu položku. Je-li použita taková klauzule, není vytvořena obálka řádku kolem položek v klauzuli `select` a může být vytvořena kolekce požadovaného tvaru, například: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje také konstruktor Row pro vytvoření libovolných řádků. `select` přebírá jeden nebo více prvků v projekci a vede datový záznam s poli, a to takto:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Levá korelace a aliasy  
 V jazyce Transact-SQL výrazy v daném oboru (jediná klauzule, jako je například `select` nebo `from`), nemohou odkazovat na výrazy definované dříve ve stejném oboru. Některé dialekty jazyka SQL (včetně jazyka Transact-SQL) podporují omezené formy těchto hodnot v klauzuli `from`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] generalizuje levá korelace v klauzuli `from` a považuje je jednotně. Výrazy v klauzuli `from` mohou odkazovat na předchozí definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také zavádí další omezení dotazů týkajících se klauzulí `group by`. Výrazy v klauzuli `select` a klauzule `having` takových dotazů mohou odkazovat pouze na klíče `group by` prostřednictvím jejich aliasů. Následující konstrukce je platná v jazyce Transact-SQL, ale není v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 K tomu je potřeba [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odkazy na sloupce (vlastnosti) tabulek (kolekcí)  
 Všechny odkazy na sloupce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být kvalifikovány pomocí aliasu tabulky. Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T`) je platný v jazyce Transact-SQL, ale ne v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```sql  
SELECT a FROM T
```  
  
 Formulář [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Aliasy tabulky jsou v klauzuli `from` volitelné. Název tabulky se používá jako implicitní alias. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje také následující formulář:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Navigace prostřednictvím objektů  
 Transact-SQL používá notaci "." pro odkazující sloupce (řádek) tabulky. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozšiřuje tento zápis (vypůjčil z programovacích jazyků), aby podporoval navigaci prostřednictvím vlastností objektu.  
  
 Například pokud je `p` výraz typu person, následuje následující syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pro odkazování města adresy této osoby.  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Žádná podpora pro *  
 Transact-SQL podporuje nekvalifikované * syntaxi jako alias pro celý řádek a kvalifikovanou syntaxi \* (t. \*) jako zástupce pro pole této tabulky. Kromě toho Transact-SQL umožňuje pro agregaci se speciálním počtem (\*), který zahrnuje hodnoty null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje konstrukci *. Dotazy Transact-SQL formuláře `select * from T` a `select T1.* from T1, T2...` lze vyjádřit v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...` v uvedeném pořadí. Kromě toho tyto konstrukce zpracovávají dědičnost (nahraditelnosti hodnoty), zatímco varianty `select *` jsou omezeny na vlastnosti nejvyšší úrovně deklarovaného typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje agregaci `count(*)`. Místo nich se používá `count(0)`.  
  
## <a name="changes-to-group-by"></a>Změny pro seskupení podle  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje aliasy klíčů `group by`. Výrazy v klauzuli `select` a klauzule `having` musí odkazovat na klíče `group by` prostřednictvím těchto aliasů. Například tato syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... je ekvivalentní následujícímu jazyku Transact-SQL:  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Agregace založené na kolekcích  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dva druhy agregací.  
  
 Agregace založené na kolekcích pracují s kolekcemi a vytváří agregovaný výsledek. Ty se můžou objevit kdekoli v dotazu a nevyžadují klauzuli `group by`. Příklad:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také podporuje agregace ve stylu SQL. Příklad:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Použití klauzule ORDER BY  
Transact-SQL povoluje zadání `ORDER BY` klauzulí pouze v horním bloku `SELECT .. FROM .. WHERE`. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený výraz `ORDER BY` a může být umístěn kdekoli v dotazu, ale řazení vnořeného dotazu není zachováno.  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Identifikátory  
 V jazyce Transact-SQL je porovnání identifikátorů založeno na kolaci aktuální databáze. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mají identifikátory vždycky nerozlišovat velikost písmen a musí rozlišovat diakritiku (tj. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozlišuje mezi znaky s diakritikou a neakcenty, například ' a ' se nerovná ' ấ '). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zpracovává verze písmen, které vypadají stejně, ale z různých znakových stránek jako jiné znaky. Další informace najdete v tématu [vstupní znaková sada](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.  
 Následující funkce jazyka Transact-SQL nejsou k dispozici v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 OPERACÍ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v současné době neposkytuje podporu pro příkazy DML (INSERT, Update, DELETE).  
  
 SKRIPT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] neposkytuje podporu pro DDL v aktuální verzi.  
  
 imperativní programování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] neposkytuje podporu pro imperativní programování, na rozdíl od jazyka Transact-SQL. Místo toho použijte programovací jazyk.  
  
 Seskupení funkcí  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zatím neposkytuje podporu pro seskupování funkcí (například KRYCHLe, souhrn a GROUPING_SET).  
  
 Analytické funkce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (zatím) neposkytuje podporu pro analytické funkce.  
  
 Předdefinované funkce, operátory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje podmnožinu vestavěných funkcí a operátorů jazyka Transact-SQL. Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli úložiště. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele. Kromě toho Entity Framework umožňuje deklarovat předdefinované a uživatelsky definované funkce úložiště, pro které [!INCLUDE[esql](../../../../../../includes/esql-md.md)] použít.  
  
 Pomocné parametry  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] neposkytuje mechanismy pro pomocný parametr dotazu.  
  
 Dávkování výsledků dotazu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje dávkování výsledků dotazu. Například následuje platný příkaz Transact-SQL (odeslání jako dávky):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] však není podporován:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje pouze jeden příkaz dotazu produkující výsledek na příkaz.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
- [Nepodporované výrazy](unsupported-expressions-entity-sql.md)
