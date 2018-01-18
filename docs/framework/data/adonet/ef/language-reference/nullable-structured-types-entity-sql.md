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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29b0aa7f6f155de2c55f88b4c796ecc482d1cb84
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="e6f68-102">Strukturované typy s možnou hodnotou Null (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="e6f68-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="e6f68-103">A `null` instance strukturovaného typu je instanci, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e6f68-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="e6f68-104">Tento proces se liší z existující instance, ve kterém mají všechny vlastnosti `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e6f68-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="e6f68-105">Toto téma popisuje typy s možnou hodnotou Null strukturovaných, včetně typů, které jsou s možnou hodnotou Null a který kód vzory produktu `null` instancí strukturovaných typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="e6f68-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="e6f68-106">Typy s možnou hodnotou Null strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="e6f68-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="e6f68-107">Existují tři druhy typy s možnou hodnotou Null strukturu:</span><span class="sxs-lookup"><span data-stu-id="e6f68-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="e6f68-108">Typy řádků.</span><span class="sxs-lookup"><span data-stu-id="e6f68-108">Row types.</span></span>  
  
-   <span data-ttu-id="e6f68-109">Komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="e6f68-109">Complex types.</span></span>  
  
-   <span data-ttu-id="e6f68-110">Typy entit.</span><span class="sxs-lookup"><span data-stu-id="e6f68-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="e6f68-111">Kód vzorů, které vytvářejí Null instancí strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="e6f68-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="e6f68-112">Následující scénáře vytvořit `null` instancí:</span><span class="sxs-lookup"><span data-stu-id="e6f68-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="e6f68-113">Shaping `null` jako strukturovaný typ.:</span><span class="sxs-lookup"><span data-stu-id="e6f68-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="e6f68-114">Přetypování nahoru základní typ pro odvozený typ:</span><span class="sxs-lookup"><span data-stu-id="e6f68-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="e6f68-115">Vnější spojení na false podmínku:</span><span class="sxs-lookup"><span data-stu-id="e6f68-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="e6f68-116">--nebo</span><span class="sxs-lookup"><span data-stu-id="e6f68-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="e6f68-117">--nebo</span><span class="sxs-lookup"><span data-stu-id="e6f68-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="e6f68-118">Vyhodnocení `null` odkaz:</span><span class="sxs-lookup"><span data-stu-id="e6f68-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="e6f68-119">Získání ANYELEMENT z prázdnou kolekci:</span><span class="sxs-lookup"><span data-stu-id="e6f68-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="e6f68-120">Kontrola `null` instancí strukturovaných typů:</span><span class="sxs-lookup"><span data-stu-id="e6f68-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6f68-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6f68-121">See Also</span></span>  
 [<span data-ttu-id="e6f68-122">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e6f68-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
