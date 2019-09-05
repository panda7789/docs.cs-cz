---
title: FUNKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: ae8da3985f11a2e9f52852876a21f50a412e3b27
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250941"
---
# <a name="function-entity-sql"></a>FUNKCE (Entity SQL)
Definuje funkci v oboru příkazu Entity SQL dotazu.  
  
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
 Název funkce  
  
 `parameter-name`  
 Název parametru ve funkci.  
  
 `function_expression`  
 Platný výraz Entity SQL, který je funkcí. Příkaz ve funkci může působit na `parameter_name` parametry předané do funkce.  
  
 `data_type`  
 Název podporovaného typu.  
  
 KOLEKCE (< type_definition`>` )  
 Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.  
  
 REF **(** `data_type` **)**  
 Výraz, který vrací odkaz na typ entity.  
  
 ROW **(** `row_expression` **)**  
 Výraz, který vrací anonymní, strukturální záznamy typu z jedné nebo více hodnot. Další informace najdete v části [řádek](row-entity-sql.md).  
  
## <a name="remarks"></a>Poznámky  
 Je možné deklarovat vložené více funkcí se stejným názvem, pokud se signatury funkce liší. Další informace najdete v tématu [řešení přetížení funkce](function-overload-resolution-entity-sql.md).  
  
 Vloženou funkci lze volat v příkazu Entity SQL pouze poté, co byla definována v tomto příkazu. Vložená funkce může být však volána uvnitř jiné vložené funkce buď před, nebo po definování volané funkce. V následujícím příkladu funkce Function A funkce B před definováním funkce B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Další informace najdete v tématu [jak: Volání uživatelsky definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 Funkce lze také deklarovat v samotném modelu. Funkce deklarované v modelu jsou spouštěny stejným způsobem jako funkce deklarované jako vložené v příkazu. Další informace najdete v tématu [uživatelsky definované funkce](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL příkaz definuje funkci `Products` , která přebírá celočíselnou hodnotu pro filtrování vrácených produktů.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL příkaz definuje funkci `StringReturnsCollection` , která přebírá kolekci řetězců k filtrování vrácených kontaktů.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Jazyk Entity SQL](entity-sql-language.md)
