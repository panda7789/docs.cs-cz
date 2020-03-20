---
title: FUNKCE (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: fd7f484733e7135d2d6c8094b6527d672a988088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150295"
---
# <a name="function-entity-sql"></a>FUNKCE (Entita SQL)
Definuje funkci v oboru příkazu dotazu SQL entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
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
  
## <a name="arguments"></a>Argumenty  
 `function-name`  
 Název funkce.  
  
 `parameter-name`  
 Název parametru ve funkci.  
  
 `function_expression`  
 Platný výraz SQL entity, který je funkcí. Příkaz ve funkci může `parameter_name` pracovat na parametry předané funkci.  
  
 `data_type`  
 Název podporovaného typu.  
  
 KOLEKCE (`>` <type_definition )  
 Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.  
  
 REF **(**`data_type`**)**  
 Výraz, který vrací odkaz na typ entity.  
  
 ŘÁDEK **(**`row_expression`**)**  
 Výraz, který vrací anonymní, strukturálně zadaný záznamy z jedné nebo více hodnot. Další informace naleznete v tématu [ROW](row-entity-sql.md).  
  
## <a name="remarks"></a>Poznámky  
 Více funkcí se stejným názvem lze deklarovat vřádku, pokud se podpisy funkcí liší. Další informace naleznete v [tématu Function Overload Resolution](function-overload-resolution-entity-sql.md).  
  
 Vřaditelovou funkci lze volat v příkazu SQL entity až poté, co byla definována v tomto příkazu. Válčivá funkce však může být volána uvnitř jiné vřadné funkce před nebo po definované volané funkce. V následujícím příkladu funkce A volá funkci B před definovanou funkcí B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Další informace naleznete v [tématu How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 Funkce mohou být také deklarovány v samotném modelu. Funkce deklarované v modelu jsou spouštěny stejným způsobem jako funkce deklarované v příkazu. Další informace naleznete v [tématu User-Defined Functions](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz SQL entity definuje `Products` funkci, která k filtrování vrácených produktů přebírá hodnotu celéčíslo.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>Příklad  
 Následující příkaz SQL entity definuje `StringReturnsCollection` funkci, která přebírá kolekci řetězců k filtrování vrácených kontaktů.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
- [Jazyk Entity SQL](entity-sql-language.md)
