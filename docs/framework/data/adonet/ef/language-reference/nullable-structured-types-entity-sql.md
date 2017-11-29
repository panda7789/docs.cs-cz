---
title: "Strukturované typy s možnou hodnotou Null (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ac7405aea459d51154ac25171bc76d637a94bf81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="nullable-structured-types-entity-sql"></a>Strukturované typy s možnou hodnotou Null (entita SQL)
A `null` instance strukturovaného typu je instanci, která neexistuje. Tento proces se liší z existující instance, ve kterém mají všechny vlastnosti `null` hodnoty.  
  
 Toto téma popisuje typy s možnou hodnotou Null strukturovaných, včetně typů, které jsou s možnou hodnotou Null a který kód vzory produktu `null` instancí strukturovaných typy s možnou hodnotou Null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Typy s možnou hodnotou Null strukturovaných typů  
 Existují tři druhy typy s možnou hodnotou Null strukturu:  
  
-   Typy řádků.  
  
-   Komplexní typy.  
  
-   Typy entit.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Kód vzorů, které vytvářejí Null instancí strukturovaných typů  
 Následující scénáře vytvořit `null` instancí:  
  
-   Shaping `null` jako strukturovaný typ.:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Přetypování nahoru základní typ pro odvozený typ:  
  
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
  
-   Vyhodnocení `null` odkaz:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   Získání ANYELEMENT z prázdnou kolekci:  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   Kontrola `null` instancí strukturovaných typů:  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přehled SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
