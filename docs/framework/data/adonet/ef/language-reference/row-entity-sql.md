---
title: ŘÁDEK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 4fb16fe0072066580bff36ac0879ff38217f1e34
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319378"
---
# <a name="row-entity-sql"></a>ŘÁDEK (Entity SQL)
Vytvoří anonymní, strukturální záznamy typu z jedné nebo více hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací hodnotu pro sestavení typu řádku.  
  
 `alias`  
 Určuje alias pro hodnotu zadanou v typu řádku. Pokud alias není k dispozici, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí vygenerovat alias na základě pravidel generování aliasů [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="return-value"></a>Návratová hodnota  
 Typ řádku.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktory řádků v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] slouží k vytváření anonymních strukturně typových záznamů z jedné nebo více hodnot. Typ výsledku konstruktoru řádku je typ řádku, jehož typy polí odpovídají typům hodnot, které byly použity k vytvoření řádku. Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`.  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Pokud neposkytnete alias pro výraz v konstruktoru řádku, Entity Framework se pokusí jednu vygenerovat. Další informace najdete v části pravidla aliasing v tématu [identifikátory](identifiers-entity-sql.md) .  
  
 Následující pravidla platí pro aliasy výrazů v konstruktoru řádku:  
  
- Výrazy v konstruktoru řádku nemůžou odkazovat na jiné aliasy ve stejném konstruktoru.  
  
- Dva výrazy v konstruktoru stejného řádku nemohou mít stejný alias.  
  
 Další informace o konstruktorech dotazů naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor řádku k vytvoření anonymních strukturovaných záznamů typu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](constructing-types-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [Definice typů](type-definitions-entity-sql.md)
