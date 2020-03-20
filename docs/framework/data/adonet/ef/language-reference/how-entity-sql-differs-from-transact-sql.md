---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150228"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Jak se Entity SQL liší od Transact-SQL
Toto téma popisuje rozdíly [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mezi a Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Podpora dědičnosti a vztahů  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]pracuje přímo se schématy koncepčních entit a podporuje funkce konceptuálního modelu, jako je dědičnost a vztahy.  
  
 Při práci s dědičností je často užitečné vybrat instance podtypu z kolekce instancí nadtypu. [Oftype](oftype-entity-sql.md) operátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v (podobně jako `oftype` v C# Sekvence) poskytuje tuto možnost.  
  
## <a name="support-for-collections"></a>Podpora kolekcí  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zachází s kolekcemi jako s entitami první třídy. Například:  
  
- Kolekce výrazy jsou `from` platné v klauzuli.  
  
- `in`a `exists` poddotazy byly zobecněny tak, aby umožňovaly všechny kolekce.  
  
     Poddotaz je jeden druh kolekce. `e1 in e2`a `exists(e)` jsou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukce k provedení těchto operací.  
  
- Nastavte operace, `union`například `intersect` `except`, a , nyní pracují na kolekcích.  
  
- Spojení pracovat na kolekce.  
  
## <a name="support-for-expressions"></a>Podpora výrazů  
 Transact-SQL má poddotazy (tabulky) a výrazy (řádky a sloupce).  
  
 Pro podporu kolekcí a vnořených kolekcí, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dělá vše výraz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]je kompozitnější než Transact-SQL – každý výraz lze použít kdekoli. Výrazy dotazu vždy za následek kolekce promítnuté typy a lze použít kdekoli výraz kolekce je povoleno. Informace o výrazech Transact-SQL, které [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nejsou podporovány v aplikaci , naleznete v [tématu Nepodporované výrazy](unsupported-expressions-entity-sql.md).  
  
 Níže jsou všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] platné dotazy:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednotné zacházení s poddotazy  
 Vzhledem k jeho důraz na tabulky, Transact-SQL provádí kontextovou interpretaci poddotazů. Například poddotaz v `from` klauzuli je považován za multiset (tabulka). Ale stejný poddotaz použitý `select` v klauzuli je považován za skalární poddotaz. Podobně poddotaz použitý na levé straně `in` operátoru je považován za skalární poddotaz, zatímco pravá strana se očekává, že vícemnožinový poddotaz.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tyto rozdíly eliminuje. Výraz má jednotný výklad, který nezávisí na kontextu, ve kterém se používá. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]považuje všechny poddotazy za vícemnožinové poddotazy. Pokud skalární hodnota je žádoucí z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poddotazu, poskytuje `anyelement` operátor, který pracuje na kolekci (v tomto případě poddotaz) a extrahuje hodnotu singleton z kolekce.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Jak se vyhnout implicitním nátlakům pro poddotazy  
 Související vedlejší účinek jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty. Konkrétně v Transact-SQL je vícenásobná sada řádků (s jedním polem) implicitně převedena na skalární hodnotu, jejíž datový typ je datový masív pole.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nepodporuje toto implicitní nátlak. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje operátor ANYELEMENT extrahovat hodnotu singleton `select value` z kolekce a klauzule, aby se zabránilo vytvoření obálky řádku během výrazu dotazu.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Vybrat hodnotu: Vyhnout se implicitnímu obálkovi řádku  
 Select klauzule v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položky v klauzuli. To znamená, že nemůžeme vytvářet kolekce skalárů nebo objektů. Transact-SQL umožňuje implicitní nátlaku mezi typem řádku s jedním polem a singletonovým hodnotou stejného datového typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje `select value` klauzuli přeskočit implicitní konstrukce řádku. V klauzuli může být `select value` zadána pouze jedna položka. Při použití takové klauzule, žádné obálky řádku je `select` vytvořen kolem položky v klauzuli a kolekce `select value a`požadovaný tvar může být vytvořena, například: .  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]také poskytuje konstruktor řádku pro vytvoření libovolných řádků. `select`trvá jeden nebo více prvků v projekci a výsledkem je datový záznam s poli takto:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Levá korelace a aliasing  
 V Transact-SQL výrazy v daném oboru (jedna klauzule jako `select` nebo `from`) nemůže odkazovat na výrazy definované dříve ve stejném oboru. Některé dialekty SQL (včetně Transact-SQL) podporují omezené formy `from` těchto v klauzuli.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zobecňuje levé `from` korelace v klauzuli a zachází s nimi jednotně. Výrazy v `from` klauzuli můžete odkazovat na dřívější definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]rovněž ukládá další omezení na `group by` dotazy týkající se doložek. Výrazy v `select` klauzuli a `having` klauzule těchto dotazů může odkazovat pouze na `group by` klíče prostřednictvím svých aliasů. Následující konstrukce je platná v Transact-SQL, ale nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Chcete-li [!INCLUDE[esql](../../../../../../includes/esql-md.md)]to provést v :  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odkazování na sloupce (vlastnosti) tabulek (kolekce)  
 Všechny odkazy na [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sloupce v písmenu musí být kvalifikovány aliasem tabulky. Následující konstrukce (za `a` předpokladu, že `T`je platný sloupec tabulky ) [!INCLUDE[esql](../../../../../../includes/esql-md.md)]je platný v Transact-SQL, ale není v .  
  
```sql  
SELECT a FROM T
```  
  
 Formulář [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Aliasy tabulky jsou volitelné `from` v klauzuli. Název tabulky se používá jako implicitní alias. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]umožňuje také následující formu:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Navigace přes objekty  
 Transact-SQL používá notaci "." pro odkazování na sloupce (řádek) tabulky. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]rozšiřuje tento zápis (vypůjčený z programovacích jazyků) pro podporu navigace přes vlastnosti objektu.  
  
 Například pokud `p` je výraz typu Osoba, následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je syntaxe pro odkazování na město adresy této osoby.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Žádná podpora pro *  
 Transact-SQL podporuje nekvalifikovanou * syntaxi jako alias pro \* celý řádek\*a kvalifikovanou syntaxi (t. ) jako zástupce pro pole této tabulky. Kromě toho Transact-SQL umožňuje speciální\*počet( ) agregace, která obsahuje nulls.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nepodporuje * konstrukci. Transact-SQL dotazy `select * from T` formuláře a `select T1.* from T1, T2...` mohou být [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vyjádřeny v jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`, v uvedeném pořadí. Kromě toho tyto konstrukce zpracovávat dědičnost (hodnota substitutability), zatímco `select *` varianty jsou omezeny na nejvyšší úrovni vlastnosti deklarovaného typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nepodporuje agregát. `count(*)` Místo toho použijte `count(0)`.  
  
## <a name="changes-to-group-by"></a>Změny v seskupení podle  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje aliasing `group by` klíčů. Výrazy v `select` klauzuli a `having` klauzuli musí odkazovat na `group by` klíče prostřednictvím těchto aliasů. Například tato [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... je ekvivalentní následujícímu Transact-SQL:  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Agregáty založené na kolekci  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje dva druhy agregátů.  
  
 Agregace založené na kolekcích pracují na kolekcích a vytvářejí agregovaný výsledek. Ty se mohou objevit kdekoli v dotazu a nevyžadují klauzuli. `group by` Například:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje také agregace ve stylu SQL. Například:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>POUŽITÍ KLAUZULE OBJEDNÁNÍ Podle  
Transact-SQL `ORDER BY` umožňuje klauzule, které mají `SELECT .. FROM .. WHERE` být zadány pouze v nejvyšším bloku. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený `ORDER BY` výraz a může být umístěn kdekoli v dotazu, ale řazení v vnořený dotaz není zachována.  
  
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
 V Transact-SQL porovnání identifikátorů je založena na řazení aktuální databáze. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)]znaku jsou identifikátory vždy rozlišovány [!INCLUDE[esql](../../../../../../includes/esql-md.md)] malá a velká písmena (to znamená rozlišování mezi znaky s diakritikou a znaky bez diakritiky; například "a" se nerovná znaku "a"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zachází s verzemi písmen, která vypadají stejně, ale jsou z různých znakových stránek jako různé znaky. Další informace naleznete [v tématu Input Character Set](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkce Transact-SQL nejsou v entitě SQL k dispozici  
 Následující funkce Transact-SQL není k [!INCLUDE[esql](../../../../../../includes/esql-md.md)]dispozici v aplikaci .  
  
 Dml  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]v současné době neposkytuje žádnou podporu pro příkazy DML (vložit, aktualizovat, odstranit).  
  
 Ddl  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]neposkytuje žádnou podporu pro DDL v aktuální verzi.  
  
 imperativní programování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]neposkytuje žádnou podporu pro imperativní programování, na rozdíl od Transact-SQL. Místo toho použijte programovací jazyk.  
  
 Seskupování funkcí  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]dosud neposkytuje podporu pro seskupování funkcí (například CUBE, ROLLUP a GROUPING_SET).  
  
 Analytické funkce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)](zatím) neposkytuje podporu analytických funkcí.  
  
 Vestavěné funkce, operátoři  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje podmnožinu vestavěných funkcí a operátorů Transact-SQL. Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli obchodů. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele. Kromě toho entity framework umožňuje deklarovat integrované a uživatelem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] definované existující funkce úložiště pro použití.  
  
 Tipy  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]neposkytuje mechanismy pro rady při psaní dotazu.  
  
 Dávkování výsledků dotazu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nepodporuje dávkování výsledků dotazu. Například následující je platný Transact-SQL (odesílání jako dávka):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] však není podporován:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje pouze jeden příkaz dotazu vytvářející výsledky na příkaz.  
  
## <a name="see-also"></a>Viz také

- [Přehled Entity SQL](entity-sql-overview.md)
- [Nepodporované výrazy](unsupported-expressions-entity-sql.md)
