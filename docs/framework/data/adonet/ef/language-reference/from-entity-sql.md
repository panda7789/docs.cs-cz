---
title: Z (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 2334a30009d6bef9544d2ca1e0ab923a7441d6f2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833822"
---
# <a name="from-entity-sql"></a>Z (Entity SQL)
Určuje kolekci používanou v příkazech [Select](select-entity-sql.md) .

## <a name="syntax"></a>Syntaxe

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a>Argumenty

`expression` \
Libovolný platný výraz dotazu, který vydává kolekci, která se má použít jako zdroj v příkazu `SELECT`.

## <a name="remarks"></a>Poznámky

Klauzule `FROM` je čárkami oddělený seznam jedné nebo více položek klauzule `FROM`. Klauzuli `FROM` lze použít k zadání jednoho nebo více zdrojů pro příkaz `SELECT`. Nejjednodušší forma klauzule `FROM` je jeden výraz dotazu, který identifikuje kolekci a alias použitý jako zdroj v příkazu `SELECT`, jak je znázorněno v následujícím příkladu:

`FROM C as c`

## <a name="from-clause-items"></a>Položky klauzule FROM

Každá položka klauzule `FROM` odkazuje na zdrojovou kolekci v dotazu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje následující třídy položek klauzule `FROM`: jednoduché položky klauzule `FROM`, položky klauzule `JOIN FROM` a položky `APPLY FROM` klauzule. Každá z těchto položek klauzule `FROM` je podrobněji popsána v následujících oddílech.

### <a name="simple-from-clause-item"></a>Jednoduchá položka klauzule FROM

Nejjednodušší položka klauzule `FROM` je jeden výraz, který identifikuje kolekci a alias. Výraz může být jednoduše sada entit nebo poddotaz nebo jakýkoli jiný výraz, který je typem kolekce. Následuje příklad:

```sql
LOB.Customers as c
```

Specifikace aliasu je volitelná. Alternativní specifikace předchozí položky klauzule FROM by mohla být následující:

```sql
LOB.Customers
```

Pokud není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí vygenerovat alias na základě výrazu kolekce.

### <a name="join-from-clause-item"></a>PROPOJIT položku klauzule FROM

Položka klauzule `JOIN FROM` představuje spojení mezi dvěma položkami klauzule `FROM`. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje vzájemné spojení, vnitřní spojení, levé a pravé vnější spojení a úplné vnější spojení. Všechna tato spojení jsou podporovaná podobným způsobem, jakým jsou podporované v jazyce Transact-SQL. Stejně jako v jazyce Transact-SQL musí být položky obou `FROM` zahrnuté v `JOIN` nezávislé. To znamená, že nelze provést korelaci. V těchto případech lze použít `CROSS APPLY` nebo `OUTER APPLY`.

#### <a name="cross-joins"></a>Vzájemné spojení

`CROSS JOIN` výraz dotazu vytvoří produkt kartézském ze dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>Vnitřní spojení

`INNER JOIN` vytváří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c [INNER] JOIN D AS d ON e`

Předchozí výraz dotazu zpracuje kombinaci každého prvku kolekce na levé straně párování s každým prvkem kolekce na pravé straně, kde je podmínka `ON` pravdivá. Pokud není zadána žádná podmínka `ON`, `INNER JOIN` je vygenerována `CROSS JOIN`.

#### <a name="left-outer-joins-and-right-outer-joins"></a>Levé vnější spojení a pravé vnější spojení

Výraz `OUTER JOIN` dotazu vytvoří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

Předchozí výraz dotazu zpracuje kombinaci každého prvku kolekce na levé straně párování s každým prvkem kolekce na pravé straně, kde je podmínka `ON` pravdivá. Pokud je `ON` podmínka NEPRAVDA, výraz stále zpracovává jednu instanci elementu vlevo spárovaného proti elementu na pravé straně s hodnotou null.

Podobným způsobem je možné vyjádřit `RIGHT OUTER JOIN`.

#### <a name="full-outer-joins"></a>Úplné vnější spojení

Explicitní `FULL OUTER JOIN` vytváří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:

`FROM C AS c FULL OUTER JOIN D AS d ON e`

Předchozí výraz dotazu zpracuje kombinaci každého prvku kolekce na levé straně párování s každým prvkem kolekce na pravé straně, kde je podmínka `ON` pravdivá. Pokud je `ON` podmínka NEPRAVDA, výraz stále zpracovává jednu instanci elementu vlevo spárovaného proti elementu na pravé straně s hodnotou null. Také zpracovává jednu instanci prvku na pravé straně spárovánou s elementem vlevo s hodnotou null.

> [!NOTE]
> Aby se zachovala kompatibilita s SQL-92, je klíčové slovo OUTER v jazyce Transact-SQL volitelné. Proto `LEFT JOIN`, `RIGHT JOIN`a `FULL JOIN` jsou synonyma pro `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`a `FULL OUTER JOIN`.

### <a name="apply-clause-item"></a>Položka klauzule APPLy

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dva druhy `APPLY`: `CROSS APPLY` a `OUTER APPLY`.

`CROSS APPLY` vytvoří jedinečné párování každého prvku kolekce na levé straně s prvkem kolekce vytvořeným vyhodnocením výrazu na pravé straně. U `CROSS APPLY`je výraz na pravé straně funkčně závislý na elementu na levé straně, jak je znázorněno v následujícím příkladu přidružené kolekce:

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

Chování `CROSS APPLY` je podobné jako seznam spojení. Pokud je výraz na pravé straně vyhodnocen jako prázdná kolekce, `CROSS APPLY` nevytvoří žádné párování pro tuto instanci elementu na levé straně.

`OUTER APPLY` se podobá `CROSS APPLY`, s výjimkou, že párování je stále vytvořeno i v případě, že je výraz na pravé straně vyhodnocen jako prázdná kolekce. Následuje příklad `OUTER APPLY`:

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> Na rozdíl od jazyka Transact-SQL není nutné explicitní krok unvnořování v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

> [!NOTE]
> v SQL Server 2005 byly představeny operátory `CROSS` a `OUTER APPLY`. V některých případech může kanál dotazů vydávat jazyk Transact-SQL, který obsahuje operátory `CROSS APPLY` a/nebo `OUTER APPLY`. Vzhledem k tomu, že někteří poskytovatelé back-end, včetně verzí SQL Server starších než SQL Server 2005, tyto operátory nepodporují, takové dotazy nelze na těchto back-end poskytovateli spustit.
>
> Některé typické scénáře, které by mohly vést k přítomnosti `CROSS APPLY` a/nebo operátorů `OUTER APPLY` ve výstupním dotazu, jsou následující: korelační poddotaz se stránkováním; AnyElement přes korelační poddotaz nebo přes kolekci vytvořenou navigací; Dotazy LINQ používající seskupovací metody, které přijímají selektor elementu; dotaz, ve kterém jsou explicitně zadány `CROSS APPLY` nebo `OUTER APPLY`; dotaz, který má `DEREF` konstrukce přes `REF` konstrukce.

## <a name="multiple-collections-in-the-from-clause"></a>Více kolekcí v klauzuli FROM

Klauzule `FROM` může obsahovat více než jednu kolekci oddělenou čárkami. V těchto případech se předpokládá, že se kolekce spojí dohromady. Ty si můžete představit jako n-Way KŘÍŽové spojení.

V následujícím příkladu jsou `C` a `D` nezávislé kolekce, ale `c.Names` je závislá na `C`.

```sql
FROM C AS c, D AS d, c.Names AS e
```

Předchozí příklad je logicky shodný s následujícím příkladem:

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Levá korelace
 Položky v klauzuli `FROM` mohou odkazovat na položky zadané v předchozích klauzulích. V následujícím příkladu jsou `C` a `D` nezávislé kolekce, ale `c.Names` je závislá na `C`:

```sql
from C as c, D as d, c.Names as e
```

To je logicky ekvivalentní:

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>Sémantiku

Logicky, kolekce v klauzuli `FROM` se považují za součást křížového spojení mezi `n`(kromě případu, kdy se jedná o jednosměrné křížové spojení). Aliasy v klauzuli `FROM` jsou zpracovávány zleva doprava a přidány do aktuálního oboru pro pozdější referenci. Klauzule `FROM` se předpokládá, že vytvoří multiset řádků. Pro každou položku v klauzuli `FROM`, která představuje jeden prvek z této položky kolekce, bude k dispozici jedno pole.

Klauzule `FROM` logicky vytvoří multiset řádků typu řádek (c, d, e), kde se předpokládá, že pole c, d a e jsou typu prvku `C`, `D`a `c.Names`.

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zavádí alias pro každou jednoduchou `FROM` položku klauzule v oboru. Například v následujícím fragmentu klauzule FROM, názvy zavedené do rozsahu jsou c, d a e.

```sql
from (C as c join D as d) cross apply c.Names as e
```

V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (na rozdíl od jazyka Transact-SQL) klauzule `FROM` zavádí pouze aliasy do oboru. Všechny odkazy na sloupce (vlastnosti) těchto kolekcí musí být kvalifikovány s aliasem.

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
