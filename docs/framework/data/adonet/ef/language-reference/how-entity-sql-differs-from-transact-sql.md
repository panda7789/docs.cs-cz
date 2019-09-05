---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 1a4bf8267ee5f036effc5f7bc91c28d1485b7612
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250861"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Jak se Entity SQL liší od Transact-SQL
Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Podpora dědičnosti a vztahů  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]pracuje přímo s koncepčními schématy entit a podporuje koncepční modelové funkce, jako je například dědičnost a vztahy.  
  
 Při práci s děděním je často vhodné vybrat instance podtypu z kolekce instancí typu nadtyp. Tato [](oftype-entity-sql.md) funkce poskytuje operátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] OfType v ( `oftype` podobně C# jako v sekvencích).  
  
## <a name="support-for-collections"></a>Podpora pro kolekce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zpracovává kolekce jako entity první třídy. Příklad:  
  
- Výrazy kolekce jsou platné v `from` klauzuli.  
  
- `in`a `exists` poddotazy byly zobecněny, aby umožňovaly všechny kolekce.  
  
     Poddotaz je jeden druh kolekce. `e1 in e2``exists(e)` a[!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou konstrukcemi k provedení těchto operací.  
  
- Nastavení operací, `union`jako jsou, `intersect`a `except`, teď fungují na kolekcích.  
  
- Spojení se spouštějí na kolekcích.  
  
## <a name="support-for-expressions"></a>Podpora pro výrazy  
 V jazyce Transact-SQL jsou poddotazy (tabulky) a výrazy (řádky a sloupce).  
  
 Aby bylo možné podporovat kolekce a vnořené [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekce, provede vše výraz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]je více sestavitelný než Transact-SQL – každý výraz lze použít kdekoli. Výrazy dotazů mají vždycky za následek kolekce projektových typů a dají se použít kdekoli je povolený výraz kolekce. Informace o výrazech jazyka Transact-SQL, které nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji podporovány, naleznete v tématu [nepodporované výrazy](unsupported-expressions-entity-sql.md).  
  
 Níže jsou uvedené všechny platné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednotné zpracování poddotazů  
 V jazyce Transact-SQL, který má vzhledem k tabulkám zdůraznění, provádí kontextovou interpretaci poddotazů. Například poddotaz v `from` klauzuli se považuje za multiset (Table). Ale stejný poddotaz použitý v `select` klauzuli je považován za skalární poddotaz. Podobně, poddotaz použitý na levé straně `in` operátoru se považuje za skalární poddotaz, zatímco na pravé straně se očekává poddotaz multiset.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]eliminuje tyto rozdíly. Výraz má jednotný výklad, který není závislý na kontextu, ve kterém je použit. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]posuzuje všechny poddotazy, které mají být multiset poddotazy. Pokud je v poddotazu požadováno skalární hodnota, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `anyelement` poskytuje operátor, který pracuje na kolekci (v tomto případě poddotaz), a extrahuje hodnotu singleton z kolekce.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Zamezení implicitních vynucení pro poddotazy  
 Související vedlejší účinky jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty. Konkrétně v jazyce Transact-SQL je multiset řádků (s jedním polem) implicitně převeden na skalární hodnotu, jejíž datový typ je to pole.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nepodporuje tuto implicitní převod. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje operátor AnyElement k extrakci hodnoty singleton z kolekce a `select value` klauzule, která vyloučí řádkovou obálku během výrazu dotazu.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Vyberte hodnotu: Zamezení obálky implicitního řádku  
 Klauzule SELECT v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položek v klauzuli. To znamená, že nemůžeme vytvořit kolekce skalárních objektů nebo objektů. Transact-SQL umožňuje implicitní vynucení mezi RowType a jedním polem a hodnotou singleton stejného datového typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]`select value` poskytuje klauzuli pro přeskočení vytváření implicitních řádků. V `select value` klauzuli lze zadat pouze jednu položku. Je-li použita taková klauzule, není kolem položek v `select` klauzuli vytvořena obálka řádku a může být vytvořena kolekce požadovaného tvaru, například:. `select value a`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]také poskytuje konstruktor Row pro vytvoření libovolných řádků. `select`přebírá jeden nebo více prvků v projekci a vede datový záznam s poli, jak je znázorněno níže:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Levá korelace a aliasy  
 V jazyce Transact-SQL výrazy v daném oboru (jedna klauzule jako `select` nebo `from`) nemohou odkazovat na výrazy definované dříve ve stejném oboru. Některé dialekty jazyka SQL (včetně jazyka Transact-SQL) podporují omezené formy těchto v `from` klauzuli.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]generalizuje levé korelační `from` klauzule v klauzuli a považuje je jednotně. Výrazy v `from` klauzuli mohou odkazovat na dřívější definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]také zavádí další omezení dotazů týkajících `group by` se klauzulí. Výrazy v `select` klauzuli a `having` klauzuli těchto dotazů `group by` mohou odkazovat pouze na klíče přes jejich aliasy. Následující konstrukce je platná v jazyce Transact-SQL, ale není v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Postup:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odkazy na sloupce (vlastnosti) tabulek (kolekcí)  
 Všechny odkazy na sloupce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v nástroji musí být kvalifikovány pomocí aliasu tabulky. Následující konstrukce (za předpokladu `a` , že je platný sloupec tabulky `T`) je platná v jazyce Transact-SQL, ale [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ne v.  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formulář je  
  
```  
select t.a as A from T as t  
```  
  
 Aliasy tabulky jsou v `from` klauzuli volitelné. Název tabulky se používá jako implicitní alias. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]umožňuje také následující formulář:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Navigace prostřednictvím objektů  
 Transact-SQL používá notaci "." pro odkazující sloupce (řádek) tabulky. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]rozšiřuje tento zápis (vypůjčil z programovacích jazyků), aby podporoval navigaci prostřednictvím vlastností objektu.  
  
 Například pokud `p` je výraz typu person, následuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe pro odkazování města adresy této osoby.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Žádná podpora pro *  
 Transact-SQL podporuje nekvalifikované * syntaxi jako alias pro celý řádek a kvalifikovanou \* syntaxi (t.\*) jako zástupce pro pole této tabulky. Kromě toho jazyk Transact-SQL umožňuje použití speciální agregace Count (\*), která zahrnuje hodnoty null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nepodporuje konstrukci *. Dotazy Transact-SQL formuláře `select * from T` a `select T1.* from T1, T2...` lze je vyjádřit v podobě jako [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`v uvedeném pořadí. Kromě toho tyto konstrukce zpracovávají dědičnost (hodnotu nahraditelnosti), zatímco `select *` varianty jsou omezeny na vlastnosti nejvyšší úrovně deklarovaného typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]`count(*)` nepodporuje agregaci. Místo nich se používá `count(0)`.  
  
## <a name="changes-to-group-by"></a>Změny pro seskupení podle  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje aliasy `group by` klíčů. Výrazy v `select` klauzuli a `having` klauzule musí odkazovat na klíčepřestytoaliasy.`group by` Například tato [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... je ekvivalentní následujícímu jazyku Transact-SQL:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Agregace založené na kolekcích  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje dva druhy agregací.  
  
 Agregace založené na kolekcích pracují s kolekcemi a vytváří agregovaný výsledek. Ty se můžou objevit kdekoli v dotazu a nevyžadují `group by` klauzuli. Příklad:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje také agregace ve stylu SQL. Příklad:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>Použití klauzule ORDER BY  
 Příkaz Transact-SQL umožňuje zadat klauzule ORDER BY pouze v horním výběru. Z.. Blok WHERE. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený výraz ORDER by a může být umístěn kdekoli v dotazu, ale řazení vnořeného dotazu není zachováno.  
  
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
 V jazyce Transact-SQL je porovnání identifikátorů založeno na kolaci aktuální databáze. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jsou identifikátory vždy bez rozlišení velkých a malých písmen a s diakritikou ( [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to znamená rozlišení mezi znaky s diakritikou a neakcenty, například ' a ' se nerovná ' ấ '). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zpracovává verze písmen, které vypadají stejně, ale z různých znakových stránek jako jiné znaky. Další informace najdete v tématu [vstupní znaková sada](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.  
 Následující funkce jazyka Transact-SQL nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji k dispozici.  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]v současné době není k dispozici žádná podpora pro příkazy DML (vložení, aktualizace, odstranění).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]v aktuální verzi neposkytuje žádnou podporu pro DDL.  
  
 imperativní programování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]neposkytuje žádnou podporu pro imperativní programování, na rozdíl od jazyka Transact-SQL. Místo toho použijte programovací jazyk.  
  
 Seskupení funkcí  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ještě neposkytuje podporu pro seskupování funkcí (například KRYCHLe, souhrn a GROUPING_SET).  
  
 Analytické funkce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ještě neposkytuje podporu pro analytické funkce.  
  
 Předdefinované funkce, operátory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje podmnožinu vestavěných funkcí a operátorů jazyka Transact-SQL. Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli úložiště. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele. Kromě toho [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umožňuje deklarovat předdefinované a uživatelem definované funkce úložiště [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , které se mají použít.  
  
 Pomocné parametry  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]neposkytuje mechanismy pro pomocný parametr dotazu.  
  
 Dávkování výsledků dotazu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nepodporuje dávkování výsledků dotazu. Například následuje platný příkaz Transact-SQL (odeslání jako dávky):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] však není podporován:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]pro každý příkaz podporuje pouze jeden příkaz dotazu vytvářející výsledek.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
- [Nepodporované výrazy](unsupported-expressions-entity-sql.md)
