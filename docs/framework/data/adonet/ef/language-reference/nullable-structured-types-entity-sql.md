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
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="41d2f-102">Strukturované typy s možnou hodnotou Null (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="41d2f-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="41d2f-103">A `null` instance strukturovaného typu je instanci, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="41d2f-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="41d2f-104">Tento proces se liší z existující instance, ve kterém mají všechny vlastnosti `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="41d2f-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="41d2f-105">Toto téma popisuje typy s možnou hodnotou Null strukturovaných, včetně typů, které jsou s možnou hodnotou Null a který kód vzory produktu `null` instancí strukturovaných typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="41d2f-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="41d2f-106">Typy s možnou hodnotou Null strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="41d2f-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="41d2f-107">Existují tři druhy typy s možnou hodnotou Null strukturu:</span><span class="sxs-lookup"><span data-stu-id="41d2f-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="41d2f-108">Typy řádků.</span><span class="sxs-lookup"><span data-stu-id="41d2f-108">Row types.</span></span>  
  
-   <span data-ttu-id="41d2f-109">Komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="41d2f-109">Complex types.</span></span>  
  
-   <span data-ttu-id="41d2f-110">Typy entit.</span><span class="sxs-lookup"><span data-stu-id="41d2f-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="41d2f-111">Kód vzorů, které vytvářejí Null instancí strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="41d2f-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="41d2f-112">Následující scénáře vytvořit `null` instancí:</span><span class="sxs-lookup"><span data-stu-id="41d2f-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="41d2f-113">Shaping `null` jako strukturovaný typ.:</span><span class="sxs-lookup"><span data-stu-id="41d2f-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="41d2f-114">Přetypování nahoru základní typ pro odvozený typ:</span><span class="sxs-lookup"><span data-stu-id="41d2f-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="41d2f-115">Vnější spojení na false podmínku:</span><span class="sxs-lookup"><span data-stu-id="41d2f-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="41d2f-116">--nebo</span><span class="sxs-lookup"><span data-stu-id="41d2f-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="41d2f-117">--nebo</span><span class="sxs-lookup"><span data-stu-id="41d2f-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="41d2f-118">Vyhodnocení `null` odkaz:</span><span class="sxs-lookup"><span data-stu-id="41d2f-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="41d2f-119">Získání ANYELEMENT z prázdnou kolekci:</span><span class="sxs-lookup"><span data-stu-id="41d2f-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="41d2f-120">Kontrola `null` instancí strukturovaných typů:</span><span class="sxs-lookup"><span data-stu-id="41d2f-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41d2f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="41d2f-121">See Also</span></span>  
 [<span data-ttu-id="41d2f-122">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="41d2f-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
