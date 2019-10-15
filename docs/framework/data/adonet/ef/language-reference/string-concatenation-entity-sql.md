---
title: + (Zřetězení řetězců) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 9c078e193eeecd4d331c5e3c04c66dee2c4a1daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319317"
---
# <a name="-string-concatenation-entity-sql"></a>+ (Zřetězení řetězců) (Entity SQL)
Zřetězí dva řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz modelu EDM. Řetězcové datové typy. Oba výrazy musí být stejného datového typu nebo jeden výraz musí být možné implicitně převést na datový typ druhého výrazu.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem propagace implicitního typu obou argumentů. Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor + k zřetězení dvou řetězců. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Typy konceptuálních modelů (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
