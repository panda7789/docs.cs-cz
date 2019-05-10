---
title: Strukturované typy s možnou hodnotou Null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6e1669bdc62de379051df60d6650fddb0c808da4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641834"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="647e2-102">Strukturované typy s možnou hodnotou Null (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="647e2-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="647e2-103">A `null` instance strukturovaný typ je instanci, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="647e2-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="647e2-104">Tím se liší od existující instanci, ve kterém mají všechny vlastnosti `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="647e2-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="647e2-105">Toto téma popisuje strukturované typy s možnou hodnotou Null, včetně typů, které jsou s možnou hodnotou Null a vzor, který kód produktu `null` výskyty strukturované typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="647e2-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="647e2-106">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="647e2-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="647e2-107">Existují tři druhy typů s povolenou hodnotou Null struktury:</span><span class="sxs-lookup"><span data-stu-id="647e2-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="647e2-108">Typy řádků.</span><span class="sxs-lookup"><span data-stu-id="647e2-108">Row types.</span></span>  
  
- <span data-ttu-id="647e2-109">Komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="647e2-109">Complex types.</span></span>  
  
- <span data-ttu-id="647e2-110">Typy entit.</span><span class="sxs-lookup"><span data-stu-id="647e2-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="647e2-111">Vzory v kódu, které vyvolávají Null instancemi strukturované typy</span><span class="sxs-lookup"><span data-stu-id="647e2-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="647e2-112">Následující scénáře vytvoření `null` instancí:</span><span class="sxs-lookup"><span data-stu-id="647e2-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="647e2-113">Strukturování `null` jako strukturovaný typ.:</span><span class="sxs-lookup"><span data-stu-id="647e2-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="647e2-114">Upcasting základního typu odvozeného typu:</span><span class="sxs-lookup"><span data-stu-id="647e2-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="647e2-115">Vnější spojení na false podmínku:</span><span class="sxs-lookup"><span data-stu-id="647e2-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="647e2-116">--nebo</span><span class="sxs-lookup"><span data-stu-id="647e2-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="647e2-117">--nebo</span><span class="sxs-lookup"><span data-stu-id="647e2-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="647e2-118">Přesměrování `null` odkaz:</span><span class="sxs-lookup"><span data-stu-id="647e2-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="647e2-119">Získání ANYELEMENT z prázdné kolekce:</span><span class="sxs-lookup"><span data-stu-id="647e2-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="647e2-120">Kontrola `null` instance strukturovaných typů:</span><span class="sxs-lookup"><span data-stu-id="647e2-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="647e2-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="647e2-121">See also</span></span>

- [<span data-ttu-id="647e2-122">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="647e2-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
