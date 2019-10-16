---
title: Strukturované typy s možnou hodnotou null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: b155c672d8c0bef8b01fb26fb49908f094add25a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319476"
---
# <a name="nullable-structured-types-entity-sql"></a>Strukturované typy s možnou hodnotou null (Entity SQL)
Instance `null` strukturovaného typu je instance, která neexistuje. To se liší od existující instance, ve které všechny vlastnosti mají hodnoty `null`.  
  
 Toto téma popisuje strukturované typy s možnou hodnotou null, včetně typů s možnou hodnotou null a které vytváří vzory kódu `null` instancí strukturovaných typů s možnou hodnotou null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Druhy strukturovaných typů s možnou hodnotou null  
 Existují tři typy struktury s možnou hodnotou null:  
  
- Typy řádků.  
  
- Komplexní typy.  
  
- Typy entit.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Vzory kódu, které vytváří instance s hodnotou Null strukturovaných typů  
 Následující scénáře vytváří instance `null`:  
  
- Tvarování `null` jako strukturovaného typu:  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Přetypování základního typu na odvozený typ:  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Vnější spojení při nepravdivém stavu:  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --nebo  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --nebo  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- Přesměrování odkazu `null`:  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- Získávání ANYELEMENT z prázdné kolekce:  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- Probíhá kontrola `null` instancí strukturovaných typů:  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
