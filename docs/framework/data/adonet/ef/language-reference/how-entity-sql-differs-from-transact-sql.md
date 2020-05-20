---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 96e2283074b6c69e51bb7fee4d4f257cdb58d615
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615628"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Způsob, jakým se Entity SQL liší od jazyka Transact-SQL

Tento článek popisuje rozdíly mezi Entity SQL a Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Podpora dědičnosti a vztahů  
 Entity SQL pracuje přímo s koncepčními schématy entit a podporuje koncepční modelové funkce, jako je například dědičnost a vztahy.  
  
 Při práci s děděním je často vhodné vybrat instance podtypu z kolekce instancí typu nadtyp. Tato funkce poskytuje operátor [OfType](oftype-entity-sql.md) v Entity SQL (podobně jako `oftype` v sekvencích C#).  
  
## <a name="support-for-collections"></a>Podpora pro kolekce  
 Entity SQL považuje kolekce za entity první třídy. Například:  
  
- Výrazy kolekce jsou platné v `from` klauzuli.  
  
- `in`a `exists` poddotazy byly zobecněny, aby umožňovaly všechny kolekce.  
  
     Poddotaz je jeden druh kolekce. `e1 in e2`a `exists(e)` jsou Entity SQL konstrukce pro provedení těchto operací.  
  
- Nastavení operací, jako jsou `union` , `intersect` a `except` , teď fungují na kolekcích.  
  
- Spojení se spouštějí na kolekcích.  
  
## <a name="support-for-expressions"></a>Podpora pro výrazy  
 V jazyce Transact-SQL jsou poddotazy (tabulky) a výrazy (řádky a sloupce).  
  
 Aby bylo možné podporovat kolekce a vnořené kolekce, Entity SQL provede všechny výrazy. Entity SQL je lépe sestavitelný než Transact-SQL – každý výraz lze použít kdekoli. Výrazy dotazů mají vždycky za následek kolekce projektových typů a dají se použít kdekoli je povolený výraz kolekce. Informace o výrazech jazyka Transact-SQL, které nejsou v Entity SQL podporovány, naleznete v tématu [nepodporované výrazy](unsupported-expressions-entity-sql.md).  
  
 Níže jsou uvedené všechny platné dotazy Entity SQL:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednotné zpracování poddotazů  
 V jazyce Transact-SQL, který má vzhledem k tabulkám zdůraznění, provádí kontextovou interpretaci poddotazů. Například poddotaz v `from` klauzuli se považuje za multiset (Table). Ale stejný poddotaz použitý v `select` klauzuli je považován za skalární poddotaz. Podobně, poddotaz použitý na levé straně `in` operátoru se považuje za skalární poddotaz, zatímco na pravé straně se očekává poddotaz multiset.  
  
 Entity SQL eliminují tyto rozdíly. Výraz má jednotný výklad, který není závislý na kontextu, ve kterém je použit. Entity SQL předpokládá, že všechny poddotazy budou multiset poddotazy. Pokud je v poddotazu požadováno skalární hodnota, Entity SQL poskytuje `anyelement` operátor, který pracuje na kolekci (v tomto případě poddotaz), a extrahuje hodnotu singleton z kolekce.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Zamezení implicitních vynucení pro poddotazy  
 Související vedlejší účinky jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty. Konkrétně v jazyce Transact-SQL je multiset řádků (s jedním polem) implicitně převeden na skalární hodnotu, jejíž datový typ je to pole.  
  
 Entity SQL nepodporuje tuto implicitní vynucení. Entity SQL poskytuje `ANYELEMENT` operátor pro extrakci hodnoty typu Singleton z kolekce a `select value` klauzule, která vyloučí řádkovou obálku během výrazu dotazu.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Vyberte hodnotu: vyloučí se obálku implicitního řádku.  
 Klauzule SELECT v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položek v klauzuli. To znamená, že nemůžeme vytvořit kolekce skalárních objektů nebo objektů. Transact-SQL umožňuje implicitní vynucení mezi `rowtype` s jedním polem a hodnotou singleton stejného datového typu.  
  
 Entity SQL poskytuje `select value` klauzuli pro přeskočení vytváření implicitních řádků. V klauzuli lze zadat pouze jednu položku `select value` . Je-li použita taková klauzule, není kolem položek v klauzuli vytvořena obálka řádku `select` a může být vytvořena kolekce požadovaného tvaru, například `select value a` .  
  
 Entity SQL také poskytuje konstruktor Row pro sestavování libovolných řádků. `select`přebírá jeden nebo více prvků v projekci a vede datový záznam s poli:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Levá korelace a aliasy  
 V jazyce Transact-SQL výrazy v daném oboru (jedna klauzule jako `select` nebo `from` ) nemohou odkazovat na výrazy definované dříve ve stejném oboru. Některé dialekty jazyka SQL (včetně jazyka Transact-SQL) podporují omezené formy těchto v `from` klauzuli.  
  
 Entity SQL generalizuje levá korelace v `from` klauzuli a považuje je jednotně. Výrazy v `from` klauzuli mohou odkazovat na dřívější definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.  
  
 Entity SQL také zavádí dodatečná omezení pro dotazy zahrnující `group by` klauzule. Výrazy v `select` klauzuli a `having` klauzuli těchto dotazů mohou odkazovat pouze na `group by` klíče přes jejich aliasy. Následující konstrukce je platná v jazyce Transact-SQL, ale není v Entity SQL:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Postup v Entity SQL:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odkazy na sloupce (vlastnosti) tabulek (kolekcí)  
 Všechny odkazy na sloupce v Entity SQL musí být kvalifikovány pomocí aliasu tabulky. Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T` ) je platná v jazyce Transact-SQL, ale ne v Entity SQL.  
  
```sql  
SELECT a FROM T
```  
  
 Formulář Entity SQL je  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Aliasy tabulky jsou v klauzuli volitelné `from` . Název tabulky se používá jako implicitní alias. Entity SQL umožňuje také následující formulář:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Navigace prostřednictvím objektů  
 Transact-SQL používá notaci "." pro odkazující sloupce (řádek) tabulky. Entity SQL rozšiřuje tento zápis (vypůjčil z programovacích jazyků), aby podporoval navigaci prostřednictvím vlastností objektu.  
  
 Například pokud `p` je výraz typu person, následuje následující syntaxe Entity SQL pro odkazování města adresy této osoby.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Žádná podpora pro\*  
 Transact-SQL podporuje nekvalifikovanou \* syntaxi jako alias pro celý řádek a kvalifikovanou \* syntaxi (t. \* ) jako zástupce pro pole této tabulky. Kromě toho jazyk Transact-SQL umožňuje použití speciální agregace Count ( \* ), která zahrnuje hodnoty null.  
  
 Entity SQL nepodporuje konstrukci *. Dotazy Transact-SQL formuláře `select * from T` a `select T1.* from T1, T2...` lze je vyjádřit v Entity SQL jako a v `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` uvedeném pořadí. Kromě toho tyto konstrukce zpracovávají dědičnost (hodnotu nahraditelnosti), zatímco `select *` varianty jsou omezeny na vlastnosti nejvyšší úrovně deklarovaného typu.  
  
 Entity SQL nepodporuje `count(*)` agregaci. Místo toho použijte `count(0)`.  
  
## <a name="changes-to-group-by"></a>Změny pro seskupení podle  
 Entity SQL podporuje aliasy `group by` klíčů. Výrazy v `select` klauzuli a `having` klauzule musí odkazovat na `group by` klíče přes tyto aliasy. Například tato syntaxe Entity SQL:  
  
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
 Entity SQL podporuje dva druhy agregací.  
  
 Agregace založené na kolekcích pracují s kolekcemi a vytváří agregovaný výsledek. Ty se můžou objevit kdekoli v dotazu a nevyžadují `group by` klauzuli. Například:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 Entity SQL podporuje také agregace ve stylu SQL. Například:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Použití klauzule ORDER BY  
Klauzule Transact-SQL umožňují `ORDER BY` zadat pouze v horním `SELECT .. FROM .. WHERE` bloku. V Entity SQL můžete použít vnořený `ORDER BY` výraz a může být umístěn kdekoli v dotazu, ale řazení vnořeného dotazu není zachováno.  
  
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
 V jazyce Transact-SQL je porovnání identifikátorů založeno na kolaci aktuální databáze. V Entity SQL identifikátory jsou vždy bez rozlišení velkých a malých písmen a s diakritikou (to znamená Entity SQL rozlišovat znaky s diakritikou a nezvýrazněnými znaky; například ' a ' se nerovná ' ấ '). Entity SQL zachází s verzemi písmen, které vypadají stejně, ale z různých znakových stránek jako jiné znaky. Další informace najdete v tématu [vstupní znaková sada](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.  
 Následující funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.  
  
 OPERACÍ  
 Entity SQL v současné době neposkytuje podporu pro příkazy DML (INSERT, Update, DELETE).  
  
 SKRIPT  
 Entity SQL neposkytuje žádnou podporu pro DDL v aktuální verzi.  
  
 imperativní programování  
 Entity SQL neposkytuje žádnou podporu pro imperativní programování, na rozdíl od jazyka Transact-SQL. Místo toho použijte programovací jazyk.  
  
 Seskupení funkcí  
 Entity SQL ještě neposkytuje podporu seskupování funkcí (například datová krychle, souhrn a GROUPING_SET).  
  
 Analytické funkce  
 Entity SQL ještě neposkytuje podporu pro analytické funkce.  
  
 Předdefinované funkce, operátory  
 Entity SQL podporuje podmnožinu vestavěných funkcí a operátorů jazyka Transact-SQL. Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli úložiště. Entity SQL používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele. Kromě toho Entity Framework umožňuje deklarovat předdefinované a uživatelsky definované funkce úložiště, které Entity SQL použít.  
  
 Pomocné parametry  
 Entity SQL neposkytuje mechanismy pro pomocný parametr dotazu.  
  
 Dávkování výsledků dotazu  
 Entity SQL nepodporuje dávkování výsledků dotazu. Například následuje platný příkaz Transact-SQL (odeslání jako dávky):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Ekvivalentní Entity SQL však není podporován:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 Entity SQL podporuje pouze jeden příkaz dotazu vytvářejícího výsledek na příkaz.  
  
## <a name="see-also"></a>Viz také

- [Přehled Entity SQL](entity-sql-overview.md)
- [Nepodporované výrazy](unsupported-expressions-entity-sql.md)
