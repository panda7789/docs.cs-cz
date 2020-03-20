---
title: FUNKCE (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: fd7f484733e7135d2d6c8094b6527d672a988088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150295"
---
# <a name="function-entity-sql"></a><span data-ttu-id="f7d31-102">FUNKCE (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="f7d31-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="f7d31-103">Definuje funkci v oboru příkazu dotazu SQL entity.</span><span class="sxs-lookup"><span data-stu-id="f7d31-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7d31-104">Syntax</span></span>  
  
```sql  
FUNCTION function-name  
( [ { parameter_name <type_definition>
        [ ,...n ]  
  ]  
) AS ( function_expression )
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )
                | REF ( data_type )
                | ROW ( row_expression )
        }
```  
  
## <a name="arguments"></a><span data-ttu-id="f7d31-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f7d31-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="f7d31-106">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="f7d31-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="f7d31-107">Název parametru ve funkci.</span><span class="sxs-lookup"><span data-stu-id="f7d31-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="f7d31-108">Platný výraz SQL entity, který je funkcí.</span><span class="sxs-lookup"><span data-stu-id="f7d31-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="f7d31-109">Příkaz ve funkci může `parameter_name` pracovat na parametry předané funkci.</span><span class="sxs-lookup"><span data-stu-id="f7d31-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="f7d31-110">Název podporovaného typu.</span><span class="sxs-lookup"><span data-stu-id="f7d31-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="f7d31-111">KOLEKCE (`>` <type_definition )</span><span class="sxs-lookup"><span data-stu-id="f7d31-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="f7d31-112">Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.</span><span class="sxs-lookup"><span data-stu-id="f7d31-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="f7d31-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="f7d31-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="f7d31-114">Výraz, který vrací odkaz na typ entity.</span><span class="sxs-lookup"><span data-stu-id="f7d31-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="f7d31-115">ŘÁDEK **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="f7d31-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="f7d31-116">Výraz, který vrací anonymní, strukturálně zadaný záznamy z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="f7d31-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="f7d31-117">Další informace naleznete v tématu [ROW](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f7d31-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7d31-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7d31-118">Remarks</span></span>  
 <span data-ttu-id="f7d31-119">Více funkcí se stejným názvem lze deklarovat vřádku, pokud se podpisy funkcí liší.</span><span class="sxs-lookup"><span data-stu-id="f7d31-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="f7d31-120">Další informace naleznete v [tématu Function Overload Resolution](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f7d31-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="f7d31-121">Vřaditelovou funkci lze volat v příkazu SQL entity až poté, co byla definována v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="f7d31-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="f7d31-122">Válčivá funkce však může být volána uvnitř jiné vřadné funkce před nebo po definované volané funkce.</span><span class="sxs-lookup"><span data-stu-id="f7d31-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="f7d31-123">V následujícím příkladu funkce A volá funkci B před definovanou funkcí B:</span><span class="sxs-lookup"><span data-stu-id="f7d31-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="f7d31-124">Další informace naleznete v [tématu How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f7d31-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="f7d31-125">Funkce mohou být také deklarovány v samotném modelu.</span><span class="sxs-lookup"><span data-stu-id="f7d31-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="f7d31-126">Funkce deklarované v modelu jsou spouštěny stejným způsobem jako funkce deklarované v příkazu.</span><span class="sxs-lookup"><span data-stu-id="f7d31-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="f7d31-127">Další informace naleznete v [tématu User-Defined Functions](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f7d31-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7d31-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7d31-128">Example</span></span>  
 <span data-ttu-id="f7d31-129">Následující příkaz SQL entity definuje `Products` funkci, která k filtrování vrácených produktů přebírá hodnotu celéčíslo.</span><span class="sxs-lookup"><span data-stu-id="f7d31-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a><span data-ttu-id="f7d31-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7d31-130">Example</span></span>  
 <span data-ttu-id="f7d31-131">Následující příkaz SQL entity definuje `StringReturnsCollection` funkci, která přebírá kolekci řetězců k filtrování vrácených kontaktů.</span><span class="sxs-lookup"><span data-stu-id="f7d31-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="f7d31-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7d31-132">See also</span></span>

- [<span data-ttu-id="f7d31-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f7d31-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f7d31-134">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f7d31-134">Entity SQL Language</span></span>](entity-sql-language.md)
