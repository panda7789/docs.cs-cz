---
title: FUNKCE (entita SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: c101032aed3e94e6bbf1d16319a616131fa6b60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="function-entity-sql"></a>FUNKCE (entita SQL)
Definuje funkci v oboru příkaz dotazu Entity SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Arguments  
 `function-name`  
 Název funkce.  
  
 `parameter-name`  
 Název parametru ve funkci.  
  
 `function_expression`  
 Platný výraz Entity SQL, který je funkce. Příkaz ve funkci může fungovat na `parameter_name` funkci byl předán parametry.  
  
 `data_type`  
 Název podporovaného typu.  
  
 KOLEKCE (< type_definition`>` )  
 Výraz, který vrátí kolekce podporované typy, řádky nebo odkazy.  
  
 REF **(**`data_type`**)**  
 Výraz, který vrátí odkaz na typ entity.  
  
 ŘÁDEK **(**`row_expression`**)**  
 Výraz, který vrátí anonymní, strukturálně zadali záznamů z jednoho nebo více hodnot. Další informace najdete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Poznámky  
 Víc funkcí se stejným názvem lze deklarovat vložením, tak dlouho, dokud se liší funkce podpisů. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Vložená funkce jde volat v Entity SQL příkazu až poté, co byla definována v tomto příkazu. Vložená funkce lze však volat uvnitř jiné vložená funkce před i po definování volaná funkce. V následujícím příkladu funkce A volání funkce B předtím, než je definována funkce B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Další informace najdete v tématu [postupy: volání funkce definované uživatelem](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).  
  
 Funkce lze deklarovat také v přímo pro model. Funkce, které jsou deklarované v modelu se stejným způsobem provést, protože funkce deklarované vložené v příkazu. Další informace najdete v tématu [funkce definované uživatelem](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz Entity SQL definuje funkci `Products` celočíselnou hodnotu pro filtrování vrácených produktů, která má.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Příklad  
 Následující příkaz Entity SQL definuje funkci `StringReturnsCollection` , která má kolekci řetězců pro filtrování vrácených kontaktů.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Jazyk Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
