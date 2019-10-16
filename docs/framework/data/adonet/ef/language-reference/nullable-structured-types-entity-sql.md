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
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="916f1-102">Strukturované typy s možnou hodnotou null (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="916f1-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="916f1-103">Instance `null` strukturovaného typu je instance, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="916f1-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="916f1-104">To se liší od existující instance, ve které všechny vlastnosti mají hodnoty `null`.</span><span class="sxs-lookup"><span data-stu-id="916f1-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="916f1-105">Toto téma popisuje strukturované typy s možnou hodnotou null, včetně typů s možnou hodnotou null a které vytváří vzory kódu `null` instancí strukturovaných typů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="916f1-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="916f1-106">Druhy strukturovaných typů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="916f1-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="916f1-107">Existují tři typy struktury s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="916f1-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="916f1-108">Typy řádků.</span><span class="sxs-lookup"><span data-stu-id="916f1-108">Row types.</span></span>  
  
- <span data-ttu-id="916f1-109">Komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="916f1-109">Complex types.</span></span>  
  
- <span data-ttu-id="916f1-110">Typy entit.</span><span class="sxs-lookup"><span data-stu-id="916f1-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="916f1-111">Vzory kódu, které vytváří instance s hodnotou Null strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="916f1-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="916f1-112">Následující scénáře vytváří instance `null`:</span><span class="sxs-lookup"><span data-stu-id="916f1-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="916f1-113">Tvarování `null` jako strukturovaného typu:</span><span class="sxs-lookup"><span data-stu-id="916f1-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="916f1-114">Přetypování základního typu na odvozený typ:</span><span class="sxs-lookup"><span data-stu-id="916f1-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="916f1-115">Vnější spojení při nepravdivém stavu:</span><span class="sxs-lookup"><span data-stu-id="916f1-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="916f1-116">--nebo</span><span class="sxs-lookup"><span data-stu-id="916f1-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="916f1-117">--nebo</span><span class="sxs-lookup"><span data-stu-id="916f1-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="916f1-118">Přesměrování odkazu `null`:</span><span class="sxs-lookup"><span data-stu-id="916f1-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="916f1-119">Získávání ANYELEMENT z prázdné kolekce:</span><span class="sxs-lookup"><span data-stu-id="916f1-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="916f1-120">Probíhá kontrola `null` instancí strukturovaných typů:</span><span class="sxs-lookup"><span data-stu-id="916f1-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="916f1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="916f1-121">See also</span></span>

- [<span data-ttu-id="916f1-122">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="916f1-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
