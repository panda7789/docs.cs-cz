---
title: Generování SQL ze stromů příkazů – osvědčené postupy
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 869722b91550855a184a74e706271c3e2d417b84
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040001"
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Generování SQL ze stromů příkazů – osvědčené postupy

Ve stromových strukturách příkazů pro výstup dotazu jsou dotazy vyhodnotit v SQL. Existují však některé běžné výzvy pro zapisovače poskytovatele při generování SQL z výstupního stromu příkazů. Toto téma popisuje tyto výzvy. V dalším tématu poskytovatel ukázkových řešení ukazuje, jak tyto výzvy vyřešit.

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Seskupení uzlů DbExpression v příkazu SQL SELECT

Typický příkaz SQL má vnořenou strukturu následujícího tvaru:

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

Jedna nebo více klauzulí může být prázdné.  Vnořený příkaz SELECT může nastat v některém z řádků.

Možný převod stromu příkazů dotazu na příkaz SQL SELECT by vytvořil jeden poddotaz pro každý relační operátor. To by ale vedlo k zbytečným vnořeným poddotazům, které by bylo obtížné přečíst.  V některých úložištích dat může dotaz fungovat špatně.

Podívejte se například na následující strom příkazů dotazu.

```csharp
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

Neefektivní překlad by vytvořil:

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

Všimněte si, že každý uzel relačních výrazů se stal novým příkazem SQL SELECT.

Proto je důležité agregovat co nejvíce uzlů výrazů do jednoho příkazu SELECT jazyka SQL a přitom zachovat správnost.

Výsledek takové agregace pro příklad uvedený výše by byl:

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a>Sloučit spojení v příkazu SQL SELECT

Jeden případ agregace více uzlů do jednoho příkazu SELECT SQL sestaví více výrazů JOIN do jednoho příkazu SELECT jazyka SQL. DbJoinExpression představuje jedno spojení mezi dvěma vstupy. V rámci jednoho příkazu SELECT jazyka SQL je však možné zadat více než jedno spojení. V takovém případě se spojení provádějí v zadaném pořadí.

Spojení s levou hřbetou, (spojení, která se zobrazují jako levý podřízený objekt jiného spojení), lze snadněji sloučit do jednoho příkazu SELECT jazyka SQL. Zvažte například následující strom příkazů dotazu:

```csharp
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

To se dá správně přeložit na:

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

Spojení páteře bez levého hřbetu ale nejdou snadno sloučit a neměli byste je slučovat. Například spojení v následujícím stromu příkazů dotazu:

```csharp
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

By byl přeložen na příkaz jazyka SQL SELECT s poddotazem.

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a>Přesměrování vstupního aliasu

Chcete-li vysvětlovat přesměrování vstupu aliasu, zvažte strukturu relačních výrazů, například DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupAggregate, argumenty DbApplyExpression pro a DbSkipExpression.

Každý z těchto typů má jednu nebo více vstupních vlastností popisujících vstupní kolekci a proměnná vazby odpovídající jednotlivým vstupům slouží k reprezentaci každého prvku daného vstupu během průchodu kolekcí. Proměnná vazby se používá při odkazování na element input, například ve vlastnosti predikátu DbFilterExpression nebo vlastnosti projekce třídy DbProjectExpression.

Při agregaci dalších uzlů relačních výrazů do jednoho příkazu SELECT jazyka SQL a vyhodnocení výrazu, který je součástí relačního výrazu (například část vlastnosti projekce DbProjectExpression), kterou proměnnou vazby může používat. nesmí být stejný jako alias vstupu, protože vícenásobné vazby výrazů by musely být přesměrovány do jednoho rozsahu.  Tento problém se nazývá přejmenování aliasu.

Vezměte v úvahu první příklad v tomto tématu. Pokud se provádí překlad Naive a překlad projekce a. x (DbPropertyExpression (a, x)), je správné ho přeložit do `a.x`, protože máme alias zadaný jako "a", aby se shodoval s proměnnou vazby.  Při agregaci uzlů do jednoho příkazu SELECT SQL je však nutné přeložit stejný DbPropertyExpression do `b.x`, protože vstup byl alias "b".

## <a name="join-alias-flattening"></a>Spojit sloučení aliasů

Na rozdíl od jakéhokoli jiného relačního výrazu ve stromové struktuře příkazu OUTPUT DbJoinExpression vypíše výsledný typ, který je řádek sestávající ze dvou sloupců, z nichž každý odpovídá jednomu ze vstupů. Když je DbPropertyExpression sestaven pro přístup k skalární vlastnosti pocházející z JOIN, je nad jinou DbPropertyExpression.

Mezi příklady patří "a. b. y" v příkladu 2 a "b. c. y" v příkladu 3. V odpovídajících příkazech SQL se však říká "b. y". Tento opakovaný alias se nazývá sloučení aliasů spojování.

## <a name="column-name-and-extent-alias-renaming"></a>Název sloupce a přejmenování aliasu rozsahu

Pokud je dotaz SELECT SQL, který má spojení, dokončen s projekcí, při vytváření výčtu všech zúčastněných sloupců ze vstupů může dojít ke kolizi názvů, protože více než jeden vstup může mít stejný název sloupce. Chcete-li se vyhnout kolizi, použijte jiný název sloupce.

Také při sloučení spojení mohou mít zúčastněné tabulky (nebo poddotazy) kolizi s aliasy, v takovém případě je třeba je přejmenovat.

## <a name="avoid-select-"></a>Vyhněte se výběru *

Nepoužívejte `SELECT *` k výběru ze základních tabulek. Model úložiště v aplikaci Entity Framework může obsahovat jenom podmnožinu sloupců, které se nacházejí v tabulce databáze. V takovém případě `SELECT *` může vést k nesprávnému výsledku. Místo toho byste měli zadat všechny účastnící se sloupce pomocí názvů sloupců z výsledného typu výrazů, které se účastní.

## <a name="reuse-of-expressions"></a>Opakované použití výrazů

Výrazy se můžou znovu použít ve stromu příkazů dotazu, který předává Entity Framework. Nepředpokládáme, že se každý výraz ve stromu příkazů dotazu vyskytuje jenom jednou.

## <a name="mapping-primitive-types"></a>Mapování primitivních typů

Při mapování koncepčních typů (EDM) na typy poskytovatelů byste měli mapovat na nejširší typ (Int32) tak, aby se všechny možné hodnoty vešly. Nepoužívejte také mapování na typy, které nelze použít pro mnoho operací, jako jsou typy objektů BLOB (například `ntext` v SQL Server).

## <a name="see-also"></a>Viz také:

- [Generování SQL](sql-generation.md)
