---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 676080a6cc4208ea1a4d72b85a4a55e01fafe638
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641451"
---
# <a name="row-entity-sql"></a>ROW (Entity SQL)
Sestaví anonymní, strukturálně typy záznamů z jedné nebo více hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrací hodnotu k sestavení kompletních v typu řádku.  
  
 `alias`  
 Určuje alias pro hodnotu zadanou v typu řádku. Pokud není k dispozici jako alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat alias na základě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pravidel pro vytvoření aliasu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Typ řádku.  
  
## <a name="remarks"></a>Poznámky  
 Použití konstruktorů řádek v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k sestavení kompletních anonymní, strukturálně typy záznamů z jedné nebo více hodnot. Výsledný typ konstruktoru řádku je typ řádku, jejichž pole typy odpovídají typům hodnot, které byly použity k vytvoření řádku. Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Pokud nezadáte alias pro výraz v konstruktoru row, Entity Framework se pokusí vygenerovat. Další informace najdete v tématu "Pravidla pro aliasy" část [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tématu.  
  
 Výraz aliasing v konstruktoru row platí následující pravidla:  
  
- Výrazy v konstruktoru row nelze odkazovat na jiné aliasy v konstruktoru stejné.  
  
- Dvou výrazů ve stejné konstruktor row nemůže mít stejný alias.  
  
 Další informace o konstruktorech dotazu naleznete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor řádek k vytvoření anonymní, strukturálně typy záznamů. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Definice typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
