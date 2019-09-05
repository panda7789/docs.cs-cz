---
title: Strukturované typy s možnou hodnotou null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b078ae458aba73e82957f84408b1000b216aef9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249805"
---
# <a name="nullable-structured-types-entity-sql"></a>Strukturované typy s možnou hodnotou null (Entity SQL)
`null` Instance strukturovaného typu je instance, která neexistuje. To se liší od existující instance, ve které všechny vlastnosti mají `null` hodnoty.  
  
 Toto téma popisuje strukturované typy s možnou hodnotou null, včetně typů s možnou hodnotou null `null` a které vzory kódu vytváří instance strukturovaných typů s možnou hodnotou null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Druhy strukturovaných typů s možnou hodnotou null  
 Existují tři typy struktury s možnou hodnotou null:  
  
- Typy řádků.  
  
- Komplexní typy.  
  
- Typy entit.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Vzory kódu, které vytváří instance s hodnotou Null strukturovaných typů  
 Následující scénáře poskytují `null` instance:  
  
- Tvarování `null` jako strukturovaného typu:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Přetypování základního typu na odvozený typ:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Vnější spojení při nepravdivém stavu:  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --nebo  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --nebo  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- Přesměrování `null` odkazu:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
- Získávání ANYELEMENT z prázdné kolekce:  
  
    ```  
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
