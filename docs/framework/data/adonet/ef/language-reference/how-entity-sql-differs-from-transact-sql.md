---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 54d7a3fa8ce6e8a0aba6194bfc034eb4d47dbf60
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489929"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Jak se Entity SQL liší od Transact-SQL
Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a příkazů jazyka Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Dědičnost a vztahy podpory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pracuje přímo s konceptuálními schématy entity a podporuje funkce konceptuální model, jako je dědičnost a vztahy.  
  
 Při práci s dědičnosti, je často užitečné vybrat instance podtypu z kolekce instancí nadtyp. [Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operátor v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobně jako `oftype` v C# pořadí) tuto možnost nabízí.  
  
## <a name="support-for-collections"></a>Podpora pro kolekce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekce se považuje za první třídy entit. Příklad:  
  
- Výrazy kolekce jsou platné v `from` klauzuli.  
  
- `in` a `exists` poddotazy mají byl zobecněn umožňující žádných kolekcí.  
  
     Poddotaz je jeden typ kolekce. `e1 in e2` a `exists(e)` jsou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukty, které tyto operace provést.  
  
- Množinové operace, jako například `union`, `intersect`, a `except`, nyní pracují s kolekcí.  
  
- Spojení pracovat s kolekcí.  
  
## <a name="support-for-expressions"></a>Podpora pro výrazy  
 Příkaz Transact-SQL má poddotazy (tabulky) a výrazy (řádků a sloupců).  
  
 Pro podporu kolekce a vnořené kolekce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] všechno, co je výraz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je složení více než příkazů jazyka Transact-SQL – každý výraz lze použít kdekoli. Dotaz výrazy vždy způsobit kolekcí předpokládané typů a mohou být použity kdekoli je povolen výraz kolekce. Informace o výrazech jazyka Transact-SQL, nejsou podporované v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], naleznete v tématu [nepodporované výrazy](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
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
 Zadaný jeho důraz na tabulky, příkazů jazyka Transact-SQL provede kontextové výklad poddotazy. Například poddotaz v `from` klauzule se považuje za multiset (tabulka). Ale stejné poddotaz používané `select` klauzule je považována za skalární poddotaz. Obdobně poddotaz použit na levé straně `in` – operátor se považuje za skalární poddotazu, zatímco pravé straně se očekává multiset – poddotaz.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Eliminuje tyto rozdíly. Výraz má jednotné interpretace, které nejsou závislé na kontextu, ve kterém se používá. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bere v úvahu všech poddotazech bude multiset – poddotazy. Pokud je poddotazu, skalární hodnota [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje `anyelement` operátor, který funguje na kolekce (v tomto případě poddotazu) a extrahuje hodnotu singleton z kolekce.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Jak se vyhnout implicitní převody pro poddotazy  
 Související vedlejším účinkem jednotné zacházení s poddotazy je implicitní převod poddotazů na skalární hodnoty. Konkrétně v příkazů jazyka Transact-SQL, použita třída multiset řádků (s jedním polem) implicitně převeden do skalární hodnoty, jejichž datový typ je, že pole.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Toto implicitní převod není podporován. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje operátora ANYELEMENT extrahovat hodnotu singleton z kolekce a `select value` klauzule vyhnout se vytváření Obálka řádků během výrazu dotazu.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Vyberte hodnotu: Jak se vyhnout obálky implicitní řádek  
 Klauzule select v poddotazu příkazů jazyka Transact-SQL implicitně vytvoří obálku kolem položky řádku v klauzuli. Z toho vyplývá, že nemůžeme vytvořit kolekce skaláry nebo objekty. Příkaz Transact-SQL umožňuje implicitní převod mezi rowtype s jedním polem a hodnotu singleton stejného datového typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje `select value` klauzule vynechat konstrukce implicitní řádek. Možné zadat pouze jednu položku `select value` klauzuli. Při použití těchto klauzulí žádný řádek obálky je postavena na položky v `select` klauzule a kolekce na požadovaný tvar může vytvářet, například: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také poskytuje konstruktoru řádku k vytvoření libovolné řádky. `select` použije jeden nebo více prvků v projekci a výsledky datového záznamu vložením polí, následujícím způsobem:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Levá korelace a aliasy  
 V jazyce Transact-SQL, výrazy v daném oboru (jako jedna klauzule `select` nebo `from`) nemůže odkazovat na výrazy, které jsou definované výše ve stejném oboru. Některé dialekty SQL (včetně příkazů jazyka Transact-SQL) podporují omezené formuláře z nich najdete v `from` klauzuli.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zobecňuje levé korelace v `from` klauzule a rovnoměrně je zpracovává. Výrazy v `from` klauzule můžete odkazovat starší definice (definice na levé straně) v klauzuli stejné bez nutnosti další syntaxi.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také ukládá další omezení pro dotazy zahrnující `group by` klauzule. Výrazy v `select` klauzule a `having` klauzule takové dotazy mohou odkazovat pouze na `group by` klíče účtů prostřednictvím jejich aliasy. Je platný v příkazů jazyka Transact-SQL, ale ne v jsou následující konstrukce [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Chcete-li to provést v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>(Vlastnosti) odkazujících sloupců z tabulky (kolekce)  
 Všechny odkazy na sloupce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být kvalifikovaný pomocí aliasu tabulky. Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T`) je platná v příkazů jazyka Transact-SQL, ale ne v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Je formulář  
  
```  
select t.a as A from T as t  
```  
  
 Jsou nepovinné v aliasu tabulky `from` klauzuli. Název tabulky se používá jako implicitní alias. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje následující tvar:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Navigace prostřednictvím objektů  
 Pomocí jazyka Transact-SQL "." zápis pro odkazujících sloupců (řádek) tabulky. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozšiřuje tento zápis (si z programovacích jazyků) pro podporu navigace prostřednictvím vlastností objektu.  
  
 Například pokud `p` je výraz, zadejte osobu, následuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe pro odkazování na město adresa této osoby.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Žádná podpora pro *  
 Podporuje příkaz Transact-SQL neúplný * syntaxe jako alias pro celý řádek a úplný \* syntaxe (t.\*) jako zástupce pro pole tabulky. Kromě toho umožňuje speciální počet příkazů jazyka Transact-SQL (\*) agregace, který obsahuje hodnoty Null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje * konstrukce. Dotazy Transact-SQL ve tvaru `select * from T` a `select T1.* from T1, T2...` může být vyjádřena v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`v uvedeném pořadí. Kromě toho tato konstrukce zpracování dědičnosti (hodnota dodávek), zatímco `select *` varianty jsou omezeny na nejvyšší úrovni vlastnosti deklarovaného typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje `count(*)` agregace. Místo nich se používá `count(0)`.  
  
## <a name="changes-to-group-by"></a>Změny Seskupit podle  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje aliasing z `group by` klíče. Výrazy v `select` klauzule a `having` klauzule musí odkazovat `group by` klíče účtů prostřednictvím tyto aliasy. Například to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxi:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... je ekvivalentem následujícího příkazů jazyka Transact-SQL:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Na základě kolekce agregace  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dva typy agregací.  
  
 Na základě kolekce agregace pracovat s kolekcí a vytvářet agregovaný výsledek. Toto může vyskytovat kdekoli v dotazu a nevyžadují, aby `group by` klauzuli. Příklad:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také podporuje agregaci SQL-style. Příklad:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY – klauzule využití  
 Příkaz Transact-SQL umožňuje klauzule ORDER BY zadán pouze v vrchní POLOŽKU... Z... Pokud blok. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený výraz klauzule ORDER BY a může být umístěna kdekoli v dotazu, ale není zachováváno pořadí v vnořeného dotazu.  
  
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
 V jazyce Transact-SQL porovnání identifikátoru podle řazení aktuální databázi. V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifikátory jsou vždy malá a velká písmena a rozlišovat diakritiku (to znamená, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozlišuje mezi znaky s diakritikou a výslovnost příslušných hlásek bez; například "a" se nerovná "ấ"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zpracovává verzích zpravodaje, které se zobrazí stejná, ale jsou z různých znakových stránek jako jiné znaky. Další informace najdete v tématu [vstupní znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkce jazyka Transact-SQL není k dispozici v Entity SQL  
 Následující funkce jazyka Transact-SQL není k dispozici v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aktuálně nepodporuje příkazy DML (vložení, aktualizace nebo odstranění).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje DDL v aktuální verzi.  
  
 imperativní programování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje imperativní programování, na rozdíl od příkazů jazyka Transact-SQL. Místo toho použijte programovací jazyk.  
  
 Funkce seskupování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ještě neposkytuje podporu pro seskupení funkce (například CUBE, ROLLUP a GROUPING_SET).  
  
 Analytické funkce  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ne (ještě) poskytuje podporu pro analytických funkcí.  
  
 Integrovaných funkcí, operátorů  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje podmnožinu příkazů jazyka Transact-SQL předdefinované funkce a operátory. Tyto operátory a funkce můžou být podporovanou poskytovateli hlavní úložiště. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele. Kromě toho [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umožňuje deklarovat integrované a funkce, uživatelem definované existující úložiště pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používat.  
  
 Pomocné parametry  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] neposkytuje mechanismy pro pomocné parametry dotazu.  
  
 Dávkové zpracování výsledků dotazu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dávkování výsledků dotazu není podporována. Následující je příklad, platný Transact-SQL (odeslání v dávce):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Ale ekvivalentní [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se nepodporuje:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje pouze jeden příkaz dotazu výsledek ze kterého vznikne jeden příkaz.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Nepodporované výrazy](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
