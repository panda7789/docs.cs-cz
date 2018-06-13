---
title: Seskupit podle (entita SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 3b5edee08afef8418f19df433223818218ae909d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763183"
---
# <a name="group-by-entity-sql"></a>Seskupit podle (entita SQL)
Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasedExpression`  
 Jakýkoli platný dotaz výraz, ve kterém se provádí seskupení. `expression` může být vlastnost nebo není agregační výraz, který odkazuje vlastnost vrácený klauzule FROM. Každý výraz v klauzuli GROUP BY musí být typ, který může být porovnána shoda. Tyto typy jsou obecně skalární primitiv například čísla, řetězce a data. Nelze seskupit podle kolekce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud agregační funkce, které jsou zahrnuty v klauzuli SELECT \<seznamu výběru >, GROUP BY vypočítá souhrnnou hodnotu pro každou skupinu. Při zadání GROUP BY je každý název vlastnosti v jakékoli jiné než agregované výraz v seznamu select by měl být součástí seznamu GROUP BY nebo výraz GROUP BY musí přesně odpovídat výrazu seznamu výběru.  
  
> [!NOTE]
>  Pokud není zadán v klauzuli ORDER BY, nejsou skupiny vrácené v klauzuli GROUP BY v libovolném pořadí. Pokud chcete zadat konkrétní řazení dat, doporučujeme vždy použít klauzuli ORDER by.  
  
 Při zadání klauzule GROUP BY je buď explicitně nebo implicitně (například klauzule HAVING v dotazu), aktuální obor je skrytá a zavádí nový obor.  
  
 Klauzule SELECT, klauzuli HAVING a klauzuli ORDER by už nebudou k odkazování na element názvy zadané v klauzuli FROM. Mohou odkazovat pouze na výrazy seskupení sami. K tomuto účelu můžete přiřadit nové názvy (aliasy) pro každý výraz seskupení. Pokud není zadán žádný alias pro výraz seskupení [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí jej vygenerovat pomocí pravidel pro vytvoření aliasu, jak je znázorněno v následujícím příkladu.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 Výrazy v klauzuli GROUP BY nelze odkazovat na názvy definované výše v stejné klauzule GROUP BY.  
  
 Kromě názvy seskupení můžete také zadat agregace v klauzuli SELECT, klauzuli HAVING a klauzuli ORDER by. Agregace obsahuje výraz, který se vyhodnotí pro každý prvek skupiny. Agregační operátor snižuje hodnoty těchto výrazů (obvykle, ale ne vždy do jedinou hodnotu). Agregační výraz můžete nastavit odkazy na původní element názvy viditelné v nadřazeném oboru nebo na některé nové názvy zavedených v klauzuli GROUP BY, sám sebe. I když agregace se zobrazí v klauzuli SELECT, klauzuli HAVING a ORDER BY – klauzule, jsou ve skutečnosti vyhodnocovány v rámci stejného oboru jako seskupení výrazy, jak je znázorněno v následujícím příkladu.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 Tento dotaz používá v klauzuli GROUP BY k vytvoření sestavy náklady na všechny produkty, řazení, rozděleno podle produktu. Nabízí název `name` produktu jako součást výrazu seskupení a pak odkazy, které se název v seznamu SELECT. Určuje také agregace `sum` v seznamu SELECT, který interně odkazuje na ceny a množství na řádku pořadí.  
  
 Každý výraz GROUP By klíče musí mít aspoň jednu referenci k vstupnímu rozsahu:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 Příklad použití GROUP BY, naleznete v části [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor GROUP BY určit skupiny, do kterých jsou objekty vrácených dotazem. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
