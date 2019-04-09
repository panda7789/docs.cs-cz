---
title: Strukturované typy s možnou hodnotou Null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 632b092e1d0d99a2a40cc3cd4b323e234de6232b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127852"
---
# <a name="nullable-structured-types-entity-sql"></a>Strukturované typy s možnou hodnotou Null (Entity SQL)
A `null` instance strukturovaný typ je instanci, která neexistuje. Tím se liší od existující instanci, ve kterém mají všechny vlastnosti `null` hodnoty.  
  
 Toto téma popisuje strukturované typy s možnou hodnotou Null, včetně typů, které jsou s možnou hodnotou Null a vzor, který kód produktu `null` výskyty strukturované typy s možnou hodnotou Null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Strukturované typy s možnou hodnotou Null  
 Existují tři druhy typů s povolenou hodnotou Null struktury:  
  
-   Typy řádků.  
  
-   Komplexní typy.  
  
-   Typy entit.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Vzory v kódu, které vyvolávají Null instancemi strukturované typy  
 Následující scénáře vytvoření `null` instancí:  
  
-   Strukturování `null` jako strukturovaný typ.:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Upcasting základního typu odvozeného typu:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   Vnější spojení na false podmínku:  
  
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
  
-   Přesměrování `null` odkaz:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   Získání ANYELEMENT z prázdné kolekce:  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   Kontrola `null` instance strukturovaných typů:  
  
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

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
