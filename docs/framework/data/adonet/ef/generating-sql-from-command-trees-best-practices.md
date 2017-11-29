---
title: "Generování příkazu SQL ze stromy příkazů – doporučené postupy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 06d2711d9dac203645c127fa86581a9888db3cb1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Generování příkazu SQL ze stromy příkazů – doporučené postupy
Stromy příkazů dotazu výstup úzce model dotazů v SQL vyjádřit kombinací. Existují však určité běžné problémy pro zprostředkovatele zapisovače při generování SQL ze stromu příkazů výstupu. Toto téma popisuje tyto problémy. V dalším tématu ukázkového zprostředkovatele ukazuje, jak vyřešit tyto problémy.  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Uzly od objektu DbExpression skupiny v příkazu SQL SELECT  
 Typické příkazu jazyka SQL má vnořené struktura následující tvar:  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 Jeden nebo více klauzulích může být prázdná.  Vnořené příkazu SELECT mohlo dojít v některém z řádků.  
  
 Možné překlad dotazu stromu příkazů do příkazu SQL SELECT vytvoří pro každou relační operátor jeden poddotazu. Ale povede k nepotřebné vnořené poddotazy, které by bylo obtížné číst.  V některých úložišť dat dotazu může být špatná.  
  
 Jako příklad zvažte následující strom příkazů dotazu  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 Neefektivní překlad byste mohli vytvořit:  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 Všimněte si, že každý uzel relační výraz se nové příkazu SQL SELECT.  
  
 Proto je důležité k agregaci tolik uzly výrazu nejdříve do jednoho příkazu SQL SELECT při zachování správnosti.  
  
 Výsledek takové agregace pro tento příklad popsané výše by byl:  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a>Vyrovnání spojení v příkazu SQL SELECT  
 Jeden malá agregování více uzlů do jednoho příkazu SQL SELECT je agregování více výrazů spojení do jednoho příkazu SQL SELECT. DbJoinExpression představuje jeden spojení mezi dvěma vstupy. Ale v rámci jednoho příkazu SQL SELECT, je možné zadat více než jedno připojení. V takovém případě spojení v uvedeném pořadí.  
  
 Levé spojení spine, můžete snadno průmětu (spojení, které se zobrazují jako levé podřízenou jiné připojení) do jednoho příkazu SQL SELECT. Zvažte například následující příkaz stromu dotazu:  
  
```  
InnerJoin(  
   a = LeftOuterJoin(  
   b = Extent("TableA")  
   c = Extent("TableB")  
   ON b.y = c.x ),  
   d = Extent("TableC")   
   ON a.b.y = d.z  
)  
```  
  
 To může být správně přeložit na:  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 Ale spine levé straně spojení nelze snadno vyrovnány a by se neměl pokoušet vyrovnání je. Například spojení v následujícím dotazu příkaz stromové struktury:  
  
```  
InnerJoin(  
   a = Extent("TableA")   
   b = LeftOuterJoin(  
   c = Extent("TableB")  
   d = Extent("TableC")  
   ON c.y = d.x),  
   ON a.z = b.c.y  
)  
```  
  
 By byl přeložen do příkazu SQL SELECT s poddotazu.  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a>Vstupní Alias přesměrování  
 Chcete-li popisují vstupní alias přesměrování, zvažte strukturu relační výrazy, například DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, a DbSkipExpression.  
  
 Každý z těchto typů má jednu nebo více vlastností vstup, které popisují vstupní kolekce a odpovídající každé vstupní proměnné vazby se používá k reprezentování každý prvek tento vstup při průchodu kolekce. Tato proměnná vazbu se použije k odkazování na elementu vstupu, například v predikátu vlastnost DbFilterExpression nebo vlastnost projekce DbProjectExpression.  
  
 Když může agregování další uzly relační výrazu do jednoho příkazu SQL SELECT a vyhodnocení vazby proměnné, která používá výraz, který je součástí relační výraz (například součást vlastnost projekce DbProjectExpression) není být stejný jako alias vstupu, jako by bylo víc vazeb výraz přesměrováni do jedné míry.  Tento problém se nazývá přejmenování alias.  
  
 Zvažte v prvním příkladu v tomto tématu. Pokud to překlad naïve a překladu projekce a.x (DbPropertyExpression (a, x)), je správné přeloží ji do `a.x` protože máme alias vstupu jako "a" tak, aby odpovídaly vazba proměnné.  Ale při agregování oba uzly do jednoho příkazu SQL SELECT, budete muset překládat stejnou DbPropertyExpression do `b.x`, jako vstup byl alias s "b".  
  
## <a name="join-alias-flattening"></a>Připojení k vyrovnání Alias  
 Na rozdíl od libovolný jiný relační výraz ve stromu příkazů výstupu DbJoinExpression výstupy typem výsledku, který je řádek skládající se z dva sloupce, z nichž každý představuje jednu ze vstupních údajů. Když DbPropertyExpresssion je sestavena pro přístup k skalární vlastnost pocházející z spojení, je nad jiné DbPropertyExpresssion.  
  
 Mezi příklady patří "a.b.y" v příkladu 2 a "b.c.y" v příkladu 3. Ale v odpovídajících příkazů SQL tyto se označují jako "b.y". Opětovná aliasy se nazývá vyrovnání alias spojení.  
  
## <a name="column-name-and-extent-alias-renaming"></a>Název sloupce a míry Alias přejmenování  
 Pokud dotaz SQL SELECT, který má spojení má provést s projekci, při vytváření výčtu všech zúčastněných sloupců ze vstupních hodnot, může dojít, kolize názvů, jako více než jeden vstup může mít stejný název sloupce. Použijte jiný název pro sloupec, aby se zabránilo kolizí.  
  
 Kromě toho po vyrovnání spojení, zúčastněných tabulky (nebo poddotazy) může být kolize aliasy ve kterém případ tyto potřeba přejmenovat.  
  
## <a name="avoid-select-"></a>Vyhněte se vyberte *  
 Nepoužívejte `SELECT *` k výběru ze základních tabulek. V modelu úložiště [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace může obsahovat pouze podmnožinu sloupců, které jsou v tabulce databáze. V takovém případě `SELECT *` mohou poskytnout nesprávný výsledek. Místo toho musíte zadat všechny sloupce zúčastněných s využitím názvy sloupců z výsledný typ zúčastněných výrazy.  
  
## <a name="reuse-of-expressions"></a>Opakované použití výrazů  
 Výrazy mohou být znovu použity ve stromu příkaz dotazu předaná [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Nepředpokládejte, že každý výraz zobrazí pouze jednou v dotazu strom příkazů.  
  
## <a name="mapping-primitive-types"></a>Mapování primitivní typy  
 Při mapování typů koncepční (EDM) na typy zprostředkovatele, by měl namapujte nejširší typ (Int32) tak, aby vyhovovaly všech možných hodnot. Vyhněte se také, mapování na typy, které nelze použít u mnoha operací, jako jsou typy objektů BLOB (například `ntext` v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]).  
  
## <a name="see-also"></a>Viz také  
 [Generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
