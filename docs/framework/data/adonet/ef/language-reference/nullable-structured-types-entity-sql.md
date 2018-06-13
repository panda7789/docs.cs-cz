---
title: Strukturované typy s možnou hodnotou Null (entita SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b949cebfa1b16f8e6fb5a133c61c5668d90b3bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762384"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="01aa1-102">Strukturované typy s možnou hodnotou Null (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="01aa1-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="01aa1-103">A `null` instance strukturovaného typu je instanci, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="01aa1-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="01aa1-104">Tento proces se liší z existující instance, ve kterém mají všechny vlastnosti `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01aa1-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="01aa1-105">Toto téma popisuje typy s možnou hodnotou Null strukturovaných, včetně typů, které jsou s možnou hodnotou Null a který kód vzory produktu `null` instancí strukturovaných typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="01aa1-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="01aa1-106">Typy s možnou hodnotou Null strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="01aa1-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="01aa1-107">Existují tři druhy typy s možnou hodnotou Null strukturu:</span><span class="sxs-lookup"><span data-stu-id="01aa1-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="01aa1-108">Typy řádků.</span><span class="sxs-lookup"><span data-stu-id="01aa1-108">Row types.</span></span>  
  
-   <span data-ttu-id="01aa1-109">Komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="01aa1-109">Complex types.</span></span>  
  
-   <span data-ttu-id="01aa1-110">Typy entit.</span><span class="sxs-lookup"><span data-stu-id="01aa1-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="01aa1-111">Kód vzorů, které vytvářejí Null instancí strukturovaných typů</span><span class="sxs-lookup"><span data-stu-id="01aa1-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="01aa1-112">Následující scénáře vytvořit `null` instancí:</span><span class="sxs-lookup"><span data-stu-id="01aa1-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="01aa1-113">Shaping `null` jako strukturovaný typ.:</span><span class="sxs-lookup"><span data-stu-id="01aa1-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="01aa1-114">Přetypování nahoru základní typ pro odvozený typ:</span><span class="sxs-lookup"><span data-stu-id="01aa1-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="01aa1-115">Vnější spojení na false podmínku:</span><span class="sxs-lookup"><span data-stu-id="01aa1-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="01aa1-116">--nebo</span><span class="sxs-lookup"><span data-stu-id="01aa1-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="01aa1-117">--nebo</span><span class="sxs-lookup"><span data-stu-id="01aa1-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="01aa1-118">Vyhodnocení `null` odkaz:</span><span class="sxs-lookup"><span data-stu-id="01aa1-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="01aa1-119">Získání ANYELEMENT z prázdnou kolekci:</span><span class="sxs-lookup"><span data-stu-id="01aa1-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="01aa1-120">Kontrola `null` instancí strukturovaných typů:</span><span class="sxs-lookup"><span data-stu-id="01aa1-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01aa1-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="01aa1-121">See Also</span></span>  
 [<span data-ttu-id="01aa1-122">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="01aa1-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
