---
title: Seskupit podle (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 574d952e0183eb65c88864f2788eb7d698c9f2ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302943"
---
# <a name="group-by-entity-sql"></a>Seskupit podle (Entity SQL)
Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasedExpression`  
 Libovolný výraz platný dotaz, na kterém se provádí seskupení. `expression` může být vlastnost ani není agregační výraz, který odkazuje na vlastnost vrácené v klauzuli FROM. Každý výraz v klauzuli GROUP BY musí vyhodnotit na typ, který může být porovnána shoda. Tyto typy jsou obecně skalární primitivních elementů, jako jsou čísla, řetězce a data. Nelze seskupit podle kolekce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud agregační funkce jsou zahrnuty v klauzuli SELECT \<seznamu příkazu select >, GROUP BY vypočítá souhrnnou hodnotu pro každou skupinu. Je-li seskupit podle zadána, název každé vlastnosti v jakékoli jiné než agregované výraz v seznamu select, měly by být součástí seznamu GROUP BY nebo výraz GROUP BY musí přesně odpovídat výrazu seznamu příkazu select.  
  
> [!NOTE]
>  Pokud není zadána klauzule ORDER BY, nejsou skupiny vrácené v klauzuli GROUP BY v libovolném pořadí. Chcete-li určit konkrétní pořadí dat, doporučujeme vždy používat klauzuli ORDER by.  
  
 Pokud klauzule GROUP BY je zadán, buď explicitně nebo implicitně (například pomocí klauzule HAVING v dotazu), je skrytý v aktuálním oboru a zavedl nový obor.  
  
 Klauzule SELECT, klauzuli HAVING a ORDER BY – klauzule již nebude moci odkazovat na názvy elementů zadaný v klauzuli FROM. Mohou odkazovat pouze na výrazy seskupování sami. K tomuto účelu můžete přiřadit nové názvy (aliasy) pro každý výraz seskupení. Pokud není zadán žádný alias pro výraz grouping [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat pomocí pravidel pro vytvoření aliasu, jak je znázorněno v následujícím příkladu.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 Výrazy v klauzuli GROUP BY nemůže odkazovat na názvy definované výše v stejné klauzule GROUP BY.  
  
 Kromě seskupení názvy můžete také určit agregace v klauzuli SELECT, klauzuli HAVING a ORDER BY – klauzule. Agregace obsahuje výraz, který se vyhodnocuje pro každý prvek skupiny. Agregační operátor snižuje hodnoty těchto výrazů (obvykle, ale ne vždy do jediné hodnoty). Agregační výraz můžete vytvořit odkazy na původní názvy prvků viditelné v nadřazeném oboru nebo na nové názvy zavedené v klauzuli GROUP BY, samotného. I když se v klauzuli SELECT, klauzuli HAVING a ORDER BY – klauzule zobrazí agregací, ve skutečnosti vyhodnocují se v rámci stejného oboru jako výrazy seskupování, jak je znázorněno v následujícím příkladu.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 Tento dotaz používá k vytvoření sestavy nákladů na všechny produkty, které jsou uspořádány v klauzuli GROUP BY rozděleno podle produktu. Poskytuje název `name` produktu jako součást výrazu seskupení a pak odkazy, které název v seznamu SELECT. Určuje také agregace `sum` v seznamu SELECT, který interně odkazuje cena a množství objednávky.  
  
 Každý výraz GROUP By klíče musí mít alespoň jeden odkaz na vstupní obor:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 Příklad použití GROUP BY, naleznete v tématu [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor GROUP BY k určení skupin, do kterých jsou objekty vrácených dotazem. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
