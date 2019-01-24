---
title: Generování SQL ze stromů příkazů – osvědčené postupy
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 476a2b9d6d3a8efb6094afce0143abed765bdb48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659092"
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Generování SQL ze stromů příkazů – osvědčené postupy
Stromy příkazů výstup dotazu věrně modelovala dotazů v SQL anyAttribute. Existují však některé běžné problémy pro zprostředkovatele modulů pro zápis při generování SQL ze strom výstup příkazu. Toto téma popisuje tyto problémy. V dalším tématu se zprostředkovateli ukázek ukazuje, jak tyto problémy.  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Seskupování uzlů DbExpression v příkazu SQL SELECT  
 Typické příkaz jazyka SQL má vnořené struktury následujícím tvaru:  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 Jednu či více klauzulí může být prázdný.  Vnořený příkaz SELECT může dojít v žádném z řádků.  
  
 Je to možné překlad dotazu stromu příkazů do příkazu SQL SELECT byste mohli vytvořit jeden poddotaz pro každý relační operátor. Nicméně, které by mohlo dojít k zbytečné vnořené poddotazy, které by bylo obtížné číst.  Na některá úložiště dat může provést dotaz špatně.  
  
 Jako příklad zvažte následující stromu příkazů dotazů  
  
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
  
 Všimněte si, že každý uzel relační výraz stane nový příkaz SQL SELECT.  
  
 Proto je potřeba agregovat tolik uzly výrazu nejdříve do jednoho příkazu SQL SELECT při zachování správnosti.  
  
 Výsledkem těchto agregace pro příklad uvedený výše by byl:  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a>Sloučit spojení v příkazu SQL SELECT  
 Jeden případ agregaci více uzlů do jednoho příkazu SQL SELECT je agregovat více spojení výrazů do jednoho příkazu SQL SELECT. DbJoinExpression představuje jeden spojení mezi dvěma vstupy. Ale v rámci jednoho příkazu SQL SELECT, je možné zadat více než jedno spojení. V takovém případě spojení jsou prováděny v uvedeném pořadí.  
  
 Spine spojení LEFT, můžete snadněji sloučí (spojení, které se zobrazují jako levého potomka jiného spojení) do jednoho příkazu SQL SELECT. Představte si třeba následující příkaz stromu dotazu:  
  
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
  
 To může být správně přeloženy do:  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 Však-levé straně spine spojení nelze snadno sloučí a by se neměl pokoušet linearizace. Například příkaz spojení do ní následující dotaz stromu:  
  
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
  
 By byl přeložen na příkazu SQL SELECT s poddotazu.  
  
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
 Abychom vysvětlili, přesměrování vstupní alias, vezměte v úvahu struktura relační výrazy, jako je například DbFilterExpression DbProjectExpression, objekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, Dbgroupaggregate, objektu DbApplyExpression, a DbSkipExpression.  
  
 Každý z těchto typů má jednu nebo více vlastností vstup, které popisují vstupní kolekce a odpovídající pro každý vstupní vazby proměnné se používá k reprezentaci všech prvků objektu vstup během procházení kolekce. Proměnné vazby se používá k odkazování na element input, například v predikátu vlastnost DbFilterExpression nebo vlastnost projekce DbProjectExpression.  
  
 Když může agregaci více uzlů relační výraz do jednoho příkazu SQL SELECT a vyhodnocení výrazu, který je součástí výrazu relační (například část vlastnosti projekce DbProjectExpression) proměnné vazby, kterou používá nesmí být stejný jako alias vstupu, jak víc vazeb výrazu musel být přesměrováno do jedné míry.  Tento problém se nazývá přejmenování alias.  
  
 Podívejte se na první příklad v tomto tématu. Pokud se tím překlad naivní a překladu a.x projekce (DbPropertyExpression (a, x)), je správné a přeloží ji do `a.x` máme alias vstupu jako "a" tak, aby odpovídaly vazby proměnné.  Ale při agregování obou uzlů v jediném příkazu SQL SELECT, budete muset překládat stejnou DbPropertyExpression do `b.x`, jako vstup byl vytvořen alias s "b".  
  
## <a name="join-alias-flattening"></a>Připojte se k vyrovnání Alias  
 Na rozdíl od libovolný jiný relační výraz ve výstupu příkazu stromu DbJoinExpression Vypíše typ výsledku, který je řádek skládající se z dva sloupce, z nichž každý představuje jednu ze vstupů. Při vytváření DbPropertyExpresssion pro přístup k skalární vlastnost pocházející z spojení, je prostřednictvím jiného DbPropertyExpresssion.  
  
 Mezi příklady patří "a.b.y" v příkladu 2 a "b.c.y" v příkladu 3. Ale v odpovídajících příkazů SQL tyto jsou označovány jako "b.y". Re aliasy se nazývá spojení sloučení alias.  
  
## <a name="column-name-and-extent-alias-renaming"></a>Název sloupce a míry Alias přejmenování  
 Pokud je dotaz SQL SELECT, který obsahuje spojení dokončit projekce, při vytváření výčtu všech zúčastněných sloupců ze vstupů, kolize názvů může dojít, jako více než jeden vstup může mít stejný název sloupce. Použijte jiný název sloupce, aby se zabránilo kolize.  
  
 Navíc při sloučení spojení, tabulky (nebo poddotazy) může mít kolize aliasy ve které malá a velká tyto nutné přejmenovat.  
  
## <a name="avoid-select-"></a>Vyhněte se vybrat *  
 Nepoužívejte `SELECT *` k výběru ze základních tabulek. V modelu úložiště [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace může obsahovat pouze podmnožinu sloupců, které jsou v tabulce databáze. V takovém případě `SELECT *` může způsobit nesprávný výsledek. Místo toho měli byste určit všechny zúčastněné sloupce s použitím názvy sloupců z typ výsledku zúčastněných výrazů.  
  
## <a name="reuse-of-expressions"></a>Opakované použití výrazů  
 Výrazy mohou být znovu použity ve stromu příkazů dotazů předávány [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Nepředpokládejte, že každý výraz se vyskytuje jenom jednou v dotazu strom příkazů.  
  
## <a name="mapping-primitive-types"></a>Mapování primitivní typy  
 Při mapování typů koncepční (EDM) na poskytovatele typů, byste měli namapovat na nejširší typ (Int32) tak, aby se vešly všechny možné hodnoty. Navíc neměla být mapování pro typy, které nelze použít pro mnoho operací, jako jsou typy objektů BLOB (například `ntext` v systému SQL Server).  
  
## <a name="see-also"></a>Viz také:
- [Generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
