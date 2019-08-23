---
title: Seskupit podle (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: d9074b1c2ea4f8f9206c8de1e658c1aac762a74f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936095"
---
# <a name="group-by-entity-sql"></a>Seskupit podle (Entity SQL)
Určuje skupiny, do kterých se mají umístit objekty vrácené výrazem dotazu ([Select](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasedExpression`  
 Libovolný platný výraz dotazu, na kterém je prováděno seskupování. `expression`může se jednat o vlastnost nebo neagregovaný výraz, který odkazuje na vlastnost vrácenou klauzulí FROM. Každý výraz v klauzuli GROUP BY musí být vyhodnocen jako typ, který lze porovnat s rovností. Tyto typy jsou všeobecně skalární primitivní prvky, jako jsou čísla, řetězce a data. Nelze seskupit podle kolekce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud jsou agregační funkce zahrnuté v klauzuli \<SELECT, vyberte seznam >, Group by vypočítá souhrnnou hodnotu pro každou skupinu. Pokud je zadána možnost GROUP BY, každý název vlastnosti v jakémkoli neagregačním výrazu v seznamu SELECT by měl být zahrnut do seznamu GROUP by, nebo výraz GROUP BY musí přesně odpovídat výrazu SELECT list.  
  
> [!NOTE]
> Pokud není zadána klauzule ORDER BY, skupiny vrácené klauzulí GROUP BY nejsou v žádném konkrétním pořadí. K určení konkrétního pořadí dat doporučujeme vždy použít klauzuli ORDER BY.  
  
 Pokud je zadána klauzule GROUP BY, ať už explicitně nebo implicitně (například v klauzuli HAVING v dotazu), je aktuální obor skrytý a zavedený nový obor.  
  
 Klauzule SELECT, klauzule HAVING a klauzule ORDER BY již nebudou moci odkazovat na názvy prvků zadané v klauzuli FROM. Můžete odkazovat pouze na samotné výrazy seskupení. Chcete-li to provést, můžete každému výrazu seskupení přiřadit nové názvy (aliasy). Pokud pro seskupovací výraz není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroj se pokusí vygenerovat jeden pomocí pravidel generování aliasů, jak je znázorněno v následujícím příkladu.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 Výrazy v klauzuli GROUP BY nemůžou odkazovat na názvy definované dříve v klauzuli GROUP BY.  
  
 Kromě seskupení názvů můžete také zadat agregace v klauzuli SELECT, klauzuli HAVING a klauzuli ORDER BY. Agregace obsahuje výraz, který je vyhodnocen pro každý prvek skupiny. Agregační operátor omezuje hodnoty všech těchto výrazů (obvykle ale ne vždy na jednu hodnotu). Agregační výraz může vytvořit odkazy na původní názvy elementů, které jsou viditelné v nadřazeném oboru, nebo na kterýkoli z nových názvů zavedených klauzulí GROUP BY. I když se agregace zobrazují v klauzuli SELECT, klauzule HAVING a klauzule ORDER by, jsou ve skutečnosti vyhodnoceny v rámci stejného oboru jako výrazy seskupení, jak je znázorněno v následujícím příkladu.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 Tento dotaz pomocí klauzule GROUP BY vytvoří sestavu nákladů na všechny seřazené produkty, které jsou rozdělené podle produktu. Poskytuje název `name` produktu jako součást seskupovacího výrazu a pak odkazuje na tento název v seznamu SELECT. Určuje také agregaci `sum` v seznamu SELECT, který interně odkazuje na cenu a množství řádku objednávky.  
  
 Každý výraz GROUP by musí obsahovat alespoň jeden odkaz na vstupní rozsah:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 Příklad použití klauzule GROUP BY naleznete v tématu [having](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor GROUP BY k určení skupin, do kterých jsou objekty vraceny dotazem. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
