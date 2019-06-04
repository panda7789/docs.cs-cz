---
title: Z (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 36e3059869ed048bd7c5294c4f5f5407288610b2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489938"
---
# <a name="from-entity-sql"></a>Z (Entity SQL)
Určuje kolekci používané [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, jehož výsledkem jsou použít jako zdroj v kolekci `SELECT` příkazu.  
  
## <a name="remarks"></a>Poznámky  
 A `FROM` klauzule je čárkou oddělený seznam jednoho nebo víc `FROM` klauzule položky. `FROM` Klauzuli lze použít k určení pro jeden nebo více zdrojů `SELECT` příkazu. Nejjednodušší forma `FROM` je klauzule výrazu jednoho dotazu, která identifikuje kolekci a použít jako zdroj v aliasu `SELECT` příkaz, jak je znázorněno v následujícím příkladu:  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a>Z položky – klauzule  
 Každý `FROM` klauzule položka odkazuje na kolekci zdrojové v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje následující třídy `FROM` klauzule položky: jednoduché `FROM` klauzule položky `JOIN FROM` klauzule položky a `APPLY FROM` klauzule položky. Každá z těchto `FROM` klauzule položky je popsána podrobněji v následujících částech.  
  
### <a name="simple-from-clause-item"></a>Jednoduché položka klauzule FROM  
 Nejjednodušší `FROM` položka klauzule je jediný výraz, který identifikuje kolekci a alias. Výraz může být jednoduše sadu entit, nebo poddotaz nebo jiný výraz, který se o typ kolekce. Následuje příklad:  
  
```  
LOB.Customers as c  
```  
  
 Specifikace alias je volitelné. Alternativní specifikace z výše uvedených položka klauzule from může být následující:  
  
```  
LOB.Customers  
```  
  
 Pokud není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat alias založené na výrazu kolekce.  
  
### <a name="join-from-clause-item"></a>Připojte se k položka klauzule FROM  
 A `JOIN FROM` položka klauzule představuje spojení mezi dvěma `FROM` klauzule položky. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje různé spojení, vnitřní spojení, levé a pravé vnější spojení a plné vnější spojení. Všechny tyto spojení jsou podporovány podobným způsobem, že jsou podporovány v příkazů jazyka Transact-SQL. Stejně jako v příkazů jazyka Transact-SQL, dva `FROM` součástí klauzule položky `JOIN` musí být nezávislé. To znamená že nelze korelaci. A `CROSS APPLY` nebo `OUTER APPLY` lze použít pro tyto případy.  
  
#### <a name="cross-joins"></a>Křížové spojení  
 A `CROSS JOIN` dotazu výraz vytvoří kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a>Vnitřní spojení  
 `INNER JOIN` Vytváří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 Předchozí výrazu dotazu zpracovává kombinaci každý prvek kolekce na levé straně spáruje každý prvek v kolekci podle pravé, kde `ON` je podmínka pravdivá. Pokud ne `ON` je zadána podmínka, `INNER JOIN` degeneruje k `CROSS JOIN`.  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a>Levé vnější spojení a levé vnější spojení  
 `OUTER JOIN` Dotazu výraz vytvoří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 Předchozí výrazu dotazu zpracovává kombinaci každý prvek kolekce na levé straně spáruje každý prvek v kolekci podle pravé, kde `ON` je podmínka pravdivá. Pokud `ON` podmínka není splněna, výraz stále zpracovává jednu instanci elementu na levé straně spáruje elementu na pravé straně s hodnotou null.  
  
 A `RIGHT OUTER JOIN` podobným způsobem je možné vyjádřit.  
  
#### <a name="full-outer-joins"></a>Úplné vnější spojení  
 Explicitní `FULL OUTER JOIN` vytváří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 Předchozí výrazu dotazu zpracovává kombinaci každý prvek kolekce na levé straně spáruje každý prvek v kolekci podle pravé, kde `ON` je podmínka pravdivá. Pokud `ON` podmínka není splněna, výraz stále zpracovává jeden výskyt elementu na levé straně spáruje elementu na pravé straně s hodnotou null. Zpracovává také jednu instanci elementu na pravé straně spáruje elementu na levé straně, s hodnotou null.  
  
> [!NOTE]
>  Chcete-li zachovat kompatibilitu s SQL-92 v příkazů jazyka Transact-SQL – klíčové slovo vnější je volitelný. Proto `LEFT JOIN`, `RIGHT JOIN`, a `FULL JOIN` jsou synonyma pro `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, a `FULL OUTER JOIN`.  
  
### <a name="apply-clause-item"></a>POUŽITÍ klauzule položky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dva typy z `APPLY`: `CROSS APPLY` a `OUTER APPLY`.  
  
 A `CROSS APPLY` vytvoří jedinečný párování jednotlivých elementů kolekce na levé straně s elementem kolekci vytvořenou testovaným vyhodnocení výrazu na pravé straně. S `CROSS APPLY`, výraz na pravé straně je funkčně závislé na element na levé straně, jak je znázorněno v následujícím příkladu přiřazené kolekce:  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 Chování `CROSS APPLY` se podobá seznamu spojení. Pokud výraz na pravé straně je vyhodnocen jako prázdnou kolekci, `CROSS APPLY` vytváří žádné párování pro tuto instanci elementu na levé straně.  
  
 `OUTER APPLY` Vypadá podobně jako `CROSS APPLY`, s výjimkou párování se stále vytváří, i v případě, že výraz na pravé straně je vyhodnocen jako prázdnou kolekci. Následující je příkladem `OUTER APPLY`:  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  Na rozdíl od není nutné pro explicitní unnest krok v příkazů jazyka Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
> [!NOTE]
>  `CROSS` a `OUTER APPLY` operátory byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)]. V některých případech může být kanálu dotazu jazyka Transact-SQL, který obsahuje `CROSS APPLY` a/nebo `OUTER APPLY` operátory. Protože někteří poskytovatelé back-end, včetně verze SQL serveru starší než [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nepodporují tyto operátory, tyto dotazy se nedá spustit na těchto zprostředkovatelů back-endu.  
>   
>  Některé typické scénáře, které by mohly vést k výskytu `CROSS APPLY` a/nebo `OUTER APPLY` operátory v dotazu výstupu jsou následující: korelační poddotaz s stránkování; AnyElement přes korelační poddotaz nebo kolekci vytvořenou testovaným navigace; LINQ dotazy, které používají metody, které přijímají elementu selektoru; seskupení dotaz, ve kterém `CROSS APPLY` nebo `OUTER APPLY` jsou explicitně zadány; dotaz, který má `DEREF` vytvořit přes `REF` vytvořit.  
  
## <a name="multiple-collections-in-the-from-clause"></a>Více kolekcí v FROM – klauzule  
 `FROM` Klauzule může obsahovat více než jednu kolekci, oddělené čárkami. V těchto případech kolekce se předpokládá, že spojit dohromady. Si můžete představte jako křížové spojení n způsobem.  
  
 V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`.  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 V předchozím příkladu je logicky ekvivalentní v následujícím příkladu:  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a>Levá korelace  
 Položky v `FROM` klauzule mohou odkazovat na položky uvedené v předchozích klauzule. V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`:  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 To je logicky ekvivalentní:  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a>Sémantika  
 Logicky, kolekce v `FROM` klauzule jsou považovány za součást `n`-způsobem křížové spojení (s výjimkou v případě 1způsob cross join). Aliasy v `FROM` klauzule jsou zpracovávány zleva doprava a jsou přidány do aktuálního oboru pro pozdější použití. `FROM` Klauzule předpokládá, že je vytvořit multiset řádků. Bude mít jedno pole pro každou položku v `FROM` klauzuli, která představuje jeden element z této položky kolekce.  
  
 `FROM` Vytvoří logicky klauzule multiset řádků typu řádku (c, d, e), kde pole jazyka c, d a e se předpokládá se, že element typu `C`, `D`, a `c.Names`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] představuje alias pro každý jednoduchý `FROM` položka klauzule v oboru. V následujícím z klauzule fragment, například názvy zavedené v oboru jsou c, d a e.  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (na rozdíl od příkazů jazyka Transact-SQL), `FROM` klauzule pouze zavádí aliasy do oboru. Všechny odkazy na sloupce (Vlastnosti) těchto kolekcí musí být kvalifikován s aliasem.  
  
## <a name="pulling-up-keys-from-nested-queries"></a>Stahují se klíče z vnořené dotazy  
 Některé typy dotazů, které vyžadují stahují do klíče z vnořeného dotazu nejsou podporovány. Například následující dotaz je neplatný:  
  
```  
select c.Orders from Customers as c   
```  
  
 Následující dotaz, ale není platný, protože vnořený dotaz nemá žádné klíče:  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
