---
title: join – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: a868c52cf753b1e4285586ec41c1993f519299d7
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243719"
---
# <a name="join-clause-c-reference"></a>join – klauzule (Referenční dokumentace jazyka C#)
`join` Klauzule je užitečné pro přidružení prvky z jiné zdrojové sekvence, které nemají žádný vztah s přímým přístupem v objektovém modelu. Jediným požadavkem je, že prvky v jednotlivých zdrojů sdílet některá z hodnot, který může být porovnána shoda. Distributora potravin může mít třeba seznam dodavatelů určité produktu a seznamu odběratelů. A `join` klauzuli lze použít například k vytvoření seznamu dodavatelů a zadaný kupci tohoto produktu, kteří jsou ve stejné oblasti.  
  
 A `join` klauzule dvou zdrojových posloupností přijímá jako vstup. Prvky v každé sekvence musí být buď nebo obsahovat vlastnost, která je možné porovnat s odpovídající vlastnost v jiné sekvence. `join` Klauzule porovná rovnost zadaného klíče pomocí speciální `equals` – klíčové slovo. Všechny spojení prováděné `join` klauzule jsou equijoins. Tvar výstup `join` klauzule závisí na konkrétní typ spojení provádíte. Tady jsou tři nejběžnější typy spojení:  
  
-   Vnitřní spojení  
  
-   Spojení skupiny  
  
-   Levé vnější spojení  
  
## <a name="inner-join"></a>Vnitřní spojení  
 Následující příklad ukazuje jednoduchý vnitřní porovnávání. Tento dotaz vytvoří plochý sekvence "název produktu nebo kategorie" dvojice. Stejné kategorie řetězec se zobrazí ve více prvků. Pokud element z `categories` nemá odpovídající `products`, dané kategorie se nezobrazí ve výsledcích.  
  
 [!code-csharp[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 Další informace najdete v tématu [postupy: provádění vnitřních spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## <a name="group-join"></a>Group Join  
 A `join` klauzule `into` výraz se nazývá skupina spojení.  
  
 [!code-csharp[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 Spojení skupiny vytvoří hierarchické sekvenci, která přidruží jeden nebo více prvků odpovídající pravé straně zdrojové sekvence prvků v levém zdrojové sekvence. Spojení skupiny nemá žádný ekvivalent v relační podmínky; je v podstatě posloupnost pole objektů.  
  
 Pokud se nenajdou žádné elementy ze správné zdrojové sekvence tak, aby odpovídaly prvek ve zdroji vlevo `join` klauzule vytvoří prázdné pole pro danou položku. Proto spojení skupiny je stále v podstatě vnitřní porovnávání s tím rozdílem, že je výsledek pořadí uspořádaných do skupin.  
  
 Pokud vyberete jenom výsledky spojení skupiny, můžete přístup k položkám, ale nemůže identifikovat klíč, který budou odpovídat na. Proto je obecně vzato užitečnější vyberte výsledky spojení skupiny na nový typ, který také obsahuje název klíče, jak je znázorněno v předchozím příkladu.  
  
 Samozřejmě můžete také výsledek spojení skupiny jako generátor jiného poddotaz:  
  
 [!code-csharp[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 Další informace najdete v tématu [postupy: provádění seskupených spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## <a name="left-outer-join"></a>Levé vnější spojení  
 V levé vnější spojení jsou vráceny všechny prvky v levém zdrojové sekvence, i když žádné vyhovující prvky jsou ve správné pořadí. K provedení levé vnější spojení v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], použijte `DefaultIfEmpty` metoda v kombinaci s spojení skupiny k určení výchozí element na pravé straně vytvoří, pokud levé prvek nemá žádné odpovídající položky. Můžete použít `null` jako výchozí hodnotu pro každý odkaz typu nebo můžete zadat typ definovaný uživatelem výchozí. V následujícím příkladu se zobrazí výchozí uživatelský typ:  
  
 [!code-csharp[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 Další informace najdete v tématu [postupy: provádění vnější spojení levé straně](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## <a name="the-equals-operator"></a>Operátor je rovno  
 A `join` klauzule provede porovnávání. Jinými slovy můžete pouze základní odpovídajících položek na rovnost dvou klíčů. Jiné typy porovnání, jako jsou "větší než" nebo "není rovno" nejsou podporované. Aby se vyjasnilo, že jsou všechna spojení equijoins, `join` používá klauzuli `equals` – klíčové slovo místo `==` operátor. `equals` – Klíčové slovo lze použít pouze v `join` klauzule a to se liší od `==` operátor důležité jedním způsobem. S `equals`klávesa Šipka vlevo využívá vnější zdrojové sekvence a využívá klávesa Šipka vpravo vnitřních zdrojů. Vnější zdroj je jenom v oboru levé strany operátoru `equals` a vnitřní zdrojové sekvence je jenom v oboru pravé strany.  
  
## <a name="non-equijoins"></a>Bez Equijoins  
 Bez equijoins, křížového spojení a dalších vlastních operací spojování provést pomocí několika `from` klauzule zavedení nového pořadí nezávisle na sobě do dotazu. Další informace najdete v tématu [postup: provedení vlastní připojení Operations](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="joins-on-object-collections-vs-relational-tables"></a>Spojení u objektů kolekcí vs. relačními tabulkami  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výraz dotazu, spojení, operace se provádějí s kolekcí objektů. Objekt kolekce nemůže být "připojené" přesně stejným způsobem jako relační tabulkami. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], explicitní `join` klauzule jsou jenom dvou zdrojových posloupností nejsou vázány podle jakékoli relaci je vyžadována. Při práci s [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], cizího klíče tabulky jsou reprezentovány v objektovém modelu ve formě vlastnosti primární tabulce. Tabulky Zákazník má v databázi Northwind vztah cizího klíče v tabulce objednávky. Při mapování tabulky k objektovému modelu třídy zákazníka má vlastnost objednávek, který obsahuje kolekci objednávek, které jsou přidružené k tohoto zákazníka. Ve skutečnosti spojení už proběhla za vás.  
  
 Další informace o dotazování napříč souvisejících tabulkách v kontextu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], naleznete v tématu [postupy: mapování databázových relace](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
## <a name="composite-keys"></a>Složené klíče  
 Můžete otestovat rovnost více hodnot s použitím složený klíč. Další informace najdete v tématu [postupy: spojení pomocí složených klíčů pomocí](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md). Složené klíče můžete také použít v `group` klauzuli.  
  
## <a name="example"></a>Příklad  
 Následující příklad porovnává výsledky vnitřního spojení, skupiny spojení a levé vnější spojení na stejné zdroje dat s použitím stejného odpovídající klíče. Některé další kód se přidá do těchto příkladech upřesnit výsledky do zobrazení konzoly.  
  
 [!code-csharp[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## <a name="remarks"></a>Poznámky  
 A `join` klauzuli, která nenásleduje `into` převedena <xref:System.Linq.Enumerable.Join%2A> volání metody. A `join` klauzuli, která následuje `into` se přeloží na <xref:System.Linq.Enumerable.GroupJoin%2A> volání metody.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Operace sjednocení](../../programming-guide/concepts/linq/join-operations.md)  
 [group – klauzule](../../../csharp/language-reference/keywords/group-clause.md)  
 [Postupy: provedení levých vnějších spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Postupy: provádění vnitřních spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Postupy: provádění seskupených spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Postupy: řazení výsledků Klauzule Join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Postupy: spojení pomocí složených klíčů](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Postupy: Instalace ukázkových databází](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
