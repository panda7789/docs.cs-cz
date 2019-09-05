---
title: ŘÁDEK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: dfd0031f49cbdf41797cecf21c149fafde4d7a8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249251"
---
# <a name="row-entity-sql"></a>ŘÁDEK (Entity SQL)
Vytvoří anonymní, strukturální záznamy typu z jedné nebo více hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací hodnotu pro sestavení typu řádku.  
  
 `alias`  
 Určuje alias pro hodnotu zadanou v typu řádku. Pokud alias není k dispozici, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroj se pokusí vygenerovat alias na základě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pravidel generování aliasů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Typ řádku.  
  
## <a name="remarks"></a>Poznámky  
 Použijete konstruktory řádků v rozhraní [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k sestavení anonymních strukturovaných typů záznamů z jedné nebo více hodnot. Typ výsledku konstruktoru řádku je typ řádku, jehož typy polí odpovídají typům hodnot, které byly použity k vytvoření řádku. Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Pokud neposkytnete alias pro výraz v konstruktoru řádku, Entity Framework se pokusí jednu vygenerovat. Další informace najdete v části pravidla aliasing v tématu [identifikátory](identifiers-entity-sql.md) .  
  
 Následující pravidla platí pro aliasy výrazů v konstruktoru řádku:  
  
- Výrazy v konstruktoru řádku nemůžou odkazovat na jiné aliasy ve stejném konstruktoru.  
  
- Dva výrazy v konstruktoru stejného řádku nemohou mít stejný alias.  
  
 Další informace o konstruktorech dotazů naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor řádku k vytvoření anonymních strukturovaných záznamů typu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](constructing-types-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [Definice typů](type-definitions-entity-sql.md)
