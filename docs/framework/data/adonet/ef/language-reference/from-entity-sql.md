---
title: Z (entita SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: de2ad24e5c6399ed1ca91e3907da4a66c056e337
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="from-entity-sql"></a>Z (entita SQL)
Určuje kolekci použít v [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který poskytuje kolekci, použít jako zdroj v `SELECT` příkaz.  
  
## <a name="remarks"></a>Poznámky  
 A `FROM` klauzule je textový soubor s oddělovači seznam jedné nebo více `FROM` klauzule položky. `FROM` Klauzuli lze použít k zadání jednoho nebo více zdrojů pro `SELECT` příkaz. Nejjednodušší forma `FROM` klauzule je výraz jeden dotaz, který identifikuje kolekce a použít jako zdroj v alias `SELECT` příkaz, jak je znázorněno v následujícím příkladu:  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a>Z klauzule položek  
 Každý `FROM` položka klauzule odkazuje na kolekci zdrojové v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje následující třídy `FROM` položky klauzule: jednoduchý `FROM` položky klauzule `JOIN FROM` klauzule položky a `APPLY FROM` klauzule položky. Každá z těchto `FROM` klauzule položky je podrobně popsaná v další v následujících částech.  
  
### <a name="simple-from-clause-item"></a>Jednoduché z klauzule položky  
 Nejjednodušším `FROM` položka klauzule je jeden výraz, který identifikuje do kolekce a alias. Výraz může být jednoduše sadu entit nebo poddotazu nebo jiných výraz, který je typu kolekce. Následuje příklad:  
  
```  
LOB.Customers as c  
```  
  
 Alias specifikace je volitelná. Alternativní specifikaci výše z klauzule položky může být následující:  
  
```  
LOB.Customers  
```  
  
 Pokud není zadaný žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí generovat alias na základě kolekce výrazu.  
  
### <a name="join-from-clause-item"></a>PŘIPOJENÍ z položka klauzule  
 A `JOIN FROM` položka klauzule představuje spojení mezi dvěma `FROM` klauzule položky. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje křížové spojení, vnitřní spojení, levé a pravé vnější spojení a úplné vnější spojení. Všechny tyto spojení jsou podporované podobně jako způsob, jakým jsou podporovány v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], dva `FROM` součástí klauzule položky `JOIN` musí být nezávislé. To znamená že nelze korelaci. A `CROSS APPLY` nebo `OUTER APPLY` lze použít pro tyto případy.  
  
#### <a name="cross-joins"></a>Křížové spojení  
 A `CROSS JOIN` dotazu výraz vytváří kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a>Vnitřní spojení  
 `INNER JOIN` Vytváří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 Předchozí výrazu dotazu zpracovává kombinaci každý element kolekce na levé straně spárovat proti každý element v kolekci podle pravé, kde `ON` je splněna podmínka. Pokud žádné `ON` je zadaná podmínka, `INNER JOIN` degeneruje k `CROSS JOIN`.  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a>Levé vnější spojení a levé vnější spojení  
 `OUTER JOIN` Dotazu výraz vytvoří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 Předchozí výrazu dotazu zpracovává kombinaci každý element kolekce na levé straně spárovat proti každý element v kolekci podle pravé, kde `ON` je splněna podmínka. Pokud `ON` podmínka vyhodnocena jako false, výraz stále zpracovává jednu instanci elementu na levé straně spárovat proti element na pravé straně, se hodnota null.  
  
 A `RIGHT OUTER JOIN` podobným způsobem je možné vyjádřit.  
  
#### <a name="full-outer-joins"></a>Úplné vnější spojení  
 Explicitního `FULL OUTER JOIN` vytváří omezené kartézský součin dvou kolekce, jak je znázorněno v následujícím příkladu:  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 Předchozí výrazu dotazu zpracovává kombinaci každý element kolekce na levé straně spárovat proti každý element v kolekci podle pravé, kde `ON` je splněna podmínka. Pokud `ON` podmínka vyhodnocena jako false, výraz stále zpracovává jednu instanci elementu na levé straně spárovat proti element na pravé straně, se hodnota null. Zpracuje také jednu instanci prvku na pravé straně spárovat proti elementu na levé straně, se hodnota null.  
  
> [!NOTE]
>  Zachování kompatibility s SQL-92 v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] – klíčové slovo vnější je volitelný. Proto `LEFT JOIN`, `RIGHT JOIN`, a `FULL JOIN` jsou synonyma pro `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, a `FULL OUTER JOIN`.  
  
### <a name="apply-clause-item"></a>POUŽÍT položka klauzule  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dva typy z `APPLY`: `CROSS APPLY` a `OUTER APPLY`.  
  
 A `CROSS APPLY` vytváří jedinečný párování každého prvku kolekce na levé straně s elementem kolekce vyprodukované vyhodnocení výrazu na pravé straně. S `CROSS APPLY`, výraz na pravé straně je funkčně závislé na elementu na levé straně, jak je znázorněno v následujícím příkladu přiřazené kolekce:  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 Chování `CROSS APPLY` je podobná seznamu spojení. Pokud je výsledkem výrazu na pravé straně prázdnou kolekci, `CROSS APPLY` neprodukuje žádný dvojic u dané instance elementu vlevo.  
  
 `OUTER APPLY` Vypadá takto: `CROSS APPLY`, s výjimkou párování se stále vytvářejí i v případě, že na pravé straně vyhodnocen jako prázdnou kolekci. Tady je příklad `OUTER APPLY`:  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  Na rozdíl od v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], není nutné explicitní příkazu unnest krok v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
> [!NOTE]
>  `CROSS` a `OUTER APPLY` operátory byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)]. V některých případech může být kanálu dotazu jazyka Transact-SQL, který obsahuje `CROSS APPLY` nebo `OUTER APPLY` operátory. Protože někteří poskytovatelé back-end, včetně verze systému SQL Server starších než [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nepodporují tyto operátory, takové dotazy se nedá spustit na tyto zprostředkovatele back-end.  
>   
>  Některé typické scénáře, které mohou vést k přítomnost `CROSS APPLY` nebo `OUTER APPLY` operátory v dotazu výstupní jsou následující: korelační poddotaz s stránkování; AnyElement přes korelační poddotazu nebo přes kolekci vyprodukované navigační; LINQ dotazy, které používají seskupování metody, které přijímají selektorem elementu; dotaz, ve kterém `CROSS APPLY` nebo `OUTER APPLY` jsou explicitně určena; dotaz, který má `DEREF` vytvořit přes `REF` vytvořit.  
  
## <a name="multiple-collections-in-the-from-clause"></a>Více kolekcí v od – klauzule  
 `FROM` Klauzule může obsahovat více než jednu kolekci oddělených čárkami. V těchto případech kolekce se předpokládá, že se propojeny. Vezměte v úvahu tyto jako n způsob křížové spojení.  
  
 V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`.  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 V předchozím příkladu je logicky ekvivalentní v následujícím příkladu:  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a>Levá korelace  
 Položky v `FROM` klauzule mohou odkazovat na položky zadaná v dřívější klauzule. V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`:  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 To je logicky ekvivalentní:  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a>Sémantika  
 Logicky, kolekcí v `FROM` klauzule jsou považovány za součást `n`-způsobem křížové spojení (s výjimkou v případě 1způsob křížové spojení). Aliasy v `FROM` klauzule jsou zpracovávány zleva doprava a jsou přidány do aktuálního oboru pro pozdější použití. `FROM` Klauzule se předpokládá, že k vytvoření multimnožina řádků. Bude jedno pole pro každou položku v `FROM` klauzuli, která představuje jeden element z této kolekce položky.  
  
 `FROM` Vytvoří logicky klauzule multimnožina řádků typu řádku (c, d, e), kde pole c, d a e považují za element typu `C`, `D`, a `c.Names`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] představuje alias pro každý jednoduchý `FROM` položka klauzule v oboru. Například v následujícím z klauzule fragment, jsou do oboru názvů c, d a e.  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (na rozdíl od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` klauzule pouze zavádí zástupci do oboru. Všechny odkazy na sloupce (Vlastnosti) těchto kolekcí musí být kvalifikovaný pomocí alias.  
  
## <a name="pulling-up-keys-from-nested-queries"></a>Stahování se klíče z vnořené dotazy  
 Některé typy dotazů, které vyžadují stahování až klíče ze vnořeném dotazu nejsou podporovány. Například následující dotaz je neplatný:  
  
```  
select c.Orders from Customers as c   
```  
  
 Následující dotaz však není platný, protože vnořený dotaz nemá žádné klíče:  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
