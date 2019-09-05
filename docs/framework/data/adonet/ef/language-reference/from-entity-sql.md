---
title: Z (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 993e71e6fee2e18806da789bdb10a488337d030f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250954"
---
# <a name="from-entity-sql"></a>Z (Entity SQL)
Určuje kolekci používanou v příkazech [Select](select-entity-sql.md) .

## <a name="syntax"></a>Syntaxe

```
FROM expression [ ,...n ] as C
```

## <a name="arguments"></a>Arguments

`expression` \
Libovolný platný výraz dotazu, který vydává kolekci, která se má použít jako `SELECT` zdroj v příkazu

## <a name="remarks"></a>Poznámky

Klauzule je čárkami oddělený seznam jedné nebo více `FROM` položek klauzule. `FROM` Klauzuli lze použít k zadání jednoho nebo více zdrojů `SELECT` pro příkaz. `FROM` Nejjednodušší forma `FROM` klauzule je jeden výraz dotazu, který identifikuje kolekci a alias použitý jako zdroj `SELECT` v příkazu, jak je znázorněno v následujícím příkladu:

`FROM C as c`

## <a name="from-clause-items"></a>Položky klauzule FROM

Každá `FROM` položka klauzule odkazuje na zdrojovou kolekci [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v dotazu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje následující třídy `FROM` položek klauzule: jednoduché `FROM` položky klauzule, `JOIN FROM` položky klauzule a `APPLY FROM` položky klauzule. Každá z těchto `FROM` položek klauzule je podrobněji popsána v následujících částech.

### <a name="simple-from-clause-item"></a>Jednoduchá položka klauzule FROM

Nejjednodušší `FROM` položka klauzule je jeden výraz, který identifikuje kolekci a alias. Výraz může být jednoduše sada entit nebo poddotaz nebo jakýkoli jiný výraz, který je typem kolekce. Následuje příklad:

```sql
LOB.Customers as c
```

Specifikace aliasu je volitelná. Alternativní specifikace předchozí položky klauzule FROM by mohla být následující:

```sql
LOB.Customers
```

Pokud není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aplikace se pokusí vygenerovat alias na základě výrazu kolekce.

### <a name="join-from-clause-item"></a>PROPOJIT položku klauzule FROM

Položka klauzule představuje spojení mezi dvěma `FROM` položkami klauzule. `JOIN FROM` [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje vzájemné spojení, vnitřní spojení, levé a pravé vnější spojení a úplné vnější spojení. Všechna tato spojení jsou podporovaná podobným způsobem, jakým jsou podporované v jazyce Transact-SQL. Stejně jako v jazyce Transact-SQL `FROM` `JOIN` musí být položky obou klauzulí, které jsou součástí, nezávislé. To znamená, že nelze provést korelaci. V `CROSS APPLY` těchto `OUTER APPLY` případech lze použít nebo.

#### <a name="cross-joins"></a>Vzájemné spojení

Výraz `CROSS JOIN` dotazu vytvoří produkt kartézském ze dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>Vnitřní spojení

`INNER JOIN` Vytvoří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c [INNER] JOIN D AS d ON e`

Předchozí výraz dotazu zpracuje kombinaci každého prvku kolekce na levé straně párování s každým prvkem kolekce na pravé straně, kde `ON` je podmínka pravdivá. Pokud není `ON` zadána žádná podmínka, výjimku `INNER JOIN` vygeneruje `CROSS JOIN`.

#### <a name="left-outer-joins-and-right-outer-joins"></a>Levé vnější spojení a pravé vnější spojení

Výraz `OUTER JOIN` dotazu vytváří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

Předchozí výraz dotazu zpracuje kombinaci každého prvku kolekce na levé straně párování s každým prvkem kolekce na pravé straně, kde `ON` je podmínka pravdivá. Pokud je `ON` podmínka NEPRAVDA, výraz stále zpracovává jednu instanci elementu vlevo spárovaného proti elementu na pravé straně s hodnotou null.

`RIGHT OUTER JOIN` Může být vyjádřen podobným způsobem.

#### <a name="full-outer-joins"></a>Úplné vnější spojení

Explicitní `FULL OUTER JOIN` vytvoří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c FULL OUTER JOIN D AS d ON e`

Předchozí výraz dotazu zpracuje kombinaci každého prvku kolekce na levé straně párování s každým prvkem kolekce na pravé straně, kde `ON` je podmínka pravdivá. Pokud je `ON` podmínka NEPRAVDA, výraz stále zpracovává jednu instanci elementu vlevo spárovaného proti elementu na pravé straně s hodnotou null. Také zpracovává jednu instanci prvku na pravé straně spárovánou s elementem vlevo s hodnotou null.

> [!NOTE]
> Aby se zachovala kompatibilita s SQL-92, je klíčové slovo OUTER v jazyce Transact-SQL volitelné. `LEFT JOIN` `FULL JOIN` `RIGHT OUTER JOIN`Proto,, a jsou synonyma pro `LEFT OUTER JOIN`, a. `FULL OUTER JOIN` `RIGHT JOIN`

### <a name="apply-clause-item"></a>Položka klauzule APPLy

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje dva druhy `APPLY`: `CROSS APPLY` a `OUTER APPLY`.

Vytvoří `CROSS APPLY` jedinečné párování každého prvku kolekce na levé straně s prvkem kolekce vytvořeným vyhodnocením výrazu na pravé straně. `CROSS APPLY`V případě, je výraz na pravé straně funkčně závislý na elementu na levé straně, jak je znázorněno v následujícím příkladu přidružené kolekce:

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

Chování `CROSS APPLY` je podobné jako v seznamu spojení. Pokud je výraz na pravé straně vyhodnocen jako prázdná kolekce, `CROSS APPLY` nevytvoří žádné párování pro tuto instanci elementu vlevo.

Se podobá `CROSS APPLY`, s tím rozdílem, že párování je stále vytvořeno i v případě, že je výraz na pravé straně vyhodnocen jako prázdná kolekce. `OUTER APPLY` Následuje příklad `OUTER APPLY`:

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> Na rozdíl od jazyka Transact-SQL není nutné explicitní krok unvnořování v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

> [!NOTE]
> `CROSS`operátory `OUTER APPLY` a byly představeny v SQL Server 2005. V některých případech může kanál dotazů vydávat Transact-SQL, který obsahuje `CROSS APPLY` operátory and/ `OUTER APPLY` or. Vzhledem k tomu, že někteří poskytovatelé back-end, včetně verzí SQL Server starších než SQL Server 2005, tyto operátory nepodporují, takové dotazy nelze na těchto back-end poskytovateli spustit.
>
> Některé typické scénáře, které by mohly vést k přítomnosti `CROSS APPLY` operátorů a `OUTER APPLY` /nebo ve výstupním dotazu, jsou následující: korelační poddotaz se stránkováním; AnyElement přes korelační poddotaz nebo přes kolekci vytvořenou navigací; Dotazy LINQ používající seskupovací metody, které přijímají selektor elementu; `CROSS APPLY` dotaz, ve kterém `OUTER APPLY` je explicitně zadáno, a dotaz, který `REF` má `DEREF` konstruktor nad konstrukcí.

## <a name="multiple-collections-in-the-from-clause"></a>Více kolekcí v klauzuli FROM

`FROM` Klauzule může obsahovat více než jednu kolekci oddělenou čárkami. V těchto případech se předpokládá, že se kolekce spojí dohromady. Ty si můžete představit jako n-Way KŘÍŽové spojení.

V `C` následujícím příkladu `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`.

```sql
FROM C AS c, D AS d, c.Names AS e
```

Předchozí příklad je logicky shodný s následujícím příkladem:

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Levá korelace
 Položky v `FROM` klauzuli mohou odkazovat na položky zadané v předchozích klauzulích. V `C` následujícím příkladu `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`:

```sql
from C as c, D as d, c.Names as e
```

To je logicky ekvivalentní:

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>Sémantiku

Logicky, kolekce v `FROM` klauzuli se považují za součást `n`vzájemného křížového spojení (kromě případu, kdy se jedná o jednosměrné křížové spojení). Aliasy v `FROM` klauzuli jsou zpracovávány zleva doprava a jsou přidány do aktuálního oboru pro pozdější použití referenčních informací. `FROM` Klauzule se předpokládá, že se vytvoří multiset řádků. Pro každou položku v `FROM` klauzuli, která představuje jeden prvek z této položky kolekce, bude k dispozici jedno pole.

Klauzule logicky vytvoří multiset řádků typu řádek (c, d, e), kde se předpokládá, že pole c, d a e jsou `C`typu prvku, `D`a `c.Names`. `FROM`

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zavádí alias pro každou položku jednoduché `FROM` klauzule v oboru. Například v následujícím fragmentu klauzule FROM, názvy zavedené do rozsahu jsou c, d a e.

```sql
from (C as c join D as d) cross apply c.Names as e
```

V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (na rozdíl od jazyka Transact-SQL) `FROM` klauzule zavádí pouze aliasy do oboru. Všechny odkazy na sloupce (vlastnosti) těchto kolekcí musí být kvalifikovány s aliasem.

## <a name="pulling-up-keys-from-nested-queries"></a>Přijímání klíčů z vnořených dotazů

Některé typy dotazů, které vyžadují přijetí klíčů z vnořeného dotazu, nejsou podporovány. Například následující dotaz je platný:

```sql
select c.Orders from Customers as c
```

Následující dotaz však není platný, protože vnořený dotaz nemá žádné klíče:

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Výrazy dotazu](query-expressions-entity-sql.md)
- [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)
