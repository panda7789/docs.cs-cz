---
title: – FUNKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: efab5f1abbc5e0c22e404c37dc80dd5aafa09ce1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106363"
---
# <a name="function-entity-sql"></a>– FUNKCE (Entity SQL)
Definuje funkci v rozsahu příkazu dotazu Entity SQL.  
  
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
 Platný výraz Entity SQL, který je funkce. Příkaz ve funkci dají dále rozvíjet `parameter_name` parametry předané do funkce.  
  
 `data_type`  
 Název podporovaného typu.  
  
 KOLEKCE (< type_definition`>` )  
 Výraz, který vrátí kolekci podporovaných typů, řádky nebo odkazy.  
  
 REF **(**`data_type`**)**  
 Výraz, který vrátí odkaz na typ entity.  
  
 ROW **(**`row_expression`**)**  
 Výraz, který vrátí anonymní, typované strukturálně záznamů z jedné nebo více hodnot. Další informace najdete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Poznámky  
 Více funkcí se stejným názvem, mohou být deklarovány jako vložené, jako signatur funkce se liší. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Vložená funkce lze volat v příkazu k Entity SQL až po je definována v tomto příkazu. Ale vložená funkce lze volat jiné vložené funkce před nebo po definování volané funkce. V následujícím příkladu volání funkcí A funkci B předtím, než je definována funkce B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Další informace najdete v tématu [jak: Volání uživatelem definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 Funkce mohou být deklarovány také v modelu, samotného. Funkce deklarované v modelu jsou provedeny stejným způsobem jako funkce deklarovaná vložené v příkazu. Další informace najdete v tématu [uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Pomocí následujícího příkazu Entity SQL definuje funkci `Products` , který přebírá hodnotu celého čísla pro filtrování vrácených produktů.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Příklad  
 Pomocí následujícího příkazu Entity SQL definuje funkci `StringReturnsCollection` , který vezme kolekci řetězce vráceného kontaktů filtr.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Jazyk Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
