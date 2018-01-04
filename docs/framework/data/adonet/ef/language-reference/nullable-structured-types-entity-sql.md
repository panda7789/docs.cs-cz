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
ms.workload: dotnet
ms.openlocfilehash: 3f294088e92951e964c3daa2a105b767bca1d288
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="bb808-102">Strukturované typy s možnou hodnotou Null (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="bb808-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="bb808-103">A `null` instance strukturovaného typu je instanci, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="bb808-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="bb808-104">Tento proces se liší z existující instance, ve kterém mají všechny vlastnosti `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bb808-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="bb808-105">Toto téma popisuje typy s možnou hodnotou Null strukturovaných, včetně typů, které jsou s možnou hodnotou Null a který kód vzory produktu `null` instancí strukturovaných typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="bb808-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="bb808-106">Typy s možnou hodnotou Null strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="bb808-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="bb808-107">Existují tři druhy typy s možnou hodnotou Null strukturu:</span><span class="sxs-lookup"><span data-stu-id="bb808-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="bb808-108">Typy řádků.</span><span class="sxs-lookup"><span data-stu-id="bb808-108">Row types.</span></span>  
  
-   <span data-ttu-id="bb808-109">Komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="bb808-109">Complex types.</span></span>  
  
-   <span data-ttu-id="bb808-110">Typy entit.</span><span class="sxs-lookup"><span data-stu-id="bb808-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="bb808-111">Kód vzorů, které vytvářejí Null instancí strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="bb808-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="bb808-112">Následující scénáře vytvořit `null` instancí:</span><span class="sxs-lookup"><span data-stu-id="bb808-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="bb808-113">Shaping `null` jako strukturovaný typ.:</span><span class="sxs-lookup"><span data-stu-id="bb808-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="bb808-114">Přetypování nahoru základní typ pro odvozený typ:</span><span class="sxs-lookup"><span data-stu-id="bb808-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="bb808-115">Vnější spojení na false podmínku:</span><span class="sxs-lookup"><span data-stu-id="bb808-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="bb808-116">--nebo</span><span class="sxs-lookup"><span data-stu-id="bb808-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="bb808-117">--nebo</span><span class="sxs-lookup"><span data-stu-id="bb808-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="bb808-118">Vyhodnocení `null` odkaz:</span><span class="sxs-lookup"><span data-stu-id="bb808-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="bb808-119">Získání ANYELEMENT z prázdnou kolekci:</span><span class="sxs-lookup"><span data-stu-id="bb808-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="bb808-120">Kontrola `null` instancí strukturovaných typů:</span><span class="sxs-lookup"><span data-stu-id="bb808-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb808-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb808-121">See Also</span></span>  
 [<span data-ttu-id="bb808-122">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bb808-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
