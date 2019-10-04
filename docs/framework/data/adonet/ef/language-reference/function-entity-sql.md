---
title: FUNKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: bacc773351812a5db60f493f3025c8e4b07dbaa2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833790"
---
# <a name="function-entity-sql"></a><span data-ttu-id="4d230-102">FUNKCE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4d230-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="4d230-103">Definuje funkci v oboru příkazu Entity SQL dotazu.</span><span class="sxs-lookup"><span data-stu-id="4d230-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d230-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d230-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="4d230-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4d230-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="4d230-106">Název funkce</span><span class="sxs-lookup"><span data-stu-id="4d230-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="4d230-107">Název parametru ve funkci.</span><span class="sxs-lookup"><span data-stu-id="4d230-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="4d230-108">Platný výraz Entity SQL, který je funkcí.</span><span class="sxs-lookup"><span data-stu-id="4d230-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="4d230-109">Příkaz ve funkci může působit na parametry `parameter_name` předané do funkce.</span><span class="sxs-lookup"><span data-stu-id="4d230-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="4d230-110">Název podporovaného typu.</span><span class="sxs-lookup"><span data-stu-id="4d230-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="4d230-111">KOLEKCE (< type_definition @ no__t-0)</span><span class="sxs-lookup"><span data-stu-id="4d230-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="4d230-112">Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.</span><span class="sxs-lookup"><span data-stu-id="4d230-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="4d230-113">REF **(** `data_type` **)**</span><span class="sxs-lookup"><span data-stu-id="4d230-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="4d230-114">Výraz, který vrací odkaz na typ entity.</span><span class="sxs-lookup"><span data-stu-id="4d230-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="4d230-115">ŘÁDEK **(** `row_expression` **)**</span><span class="sxs-lookup"><span data-stu-id="4d230-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="4d230-116">Výraz, který vrací anonymní, strukturální záznamy typu z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="4d230-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="4d230-117">Další informace najdete v části [řádek](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4d230-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d230-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d230-118">Remarks</span></span>  
 <span data-ttu-id="4d230-119">Je možné deklarovat vložené více funkcí se stejným názvem, pokud se signatury funkce liší.</span><span class="sxs-lookup"><span data-stu-id="4d230-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="4d230-120">Další informace najdete v tématu [řešení přetížení funkce](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4d230-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="4d230-121">Vloženou funkci lze volat v příkazu Entity SQL pouze poté, co byla definována v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="4d230-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="4d230-122">Vložená funkce může být však volána uvnitř jiné vložené funkce buď před, nebo po definování volané funkce.</span><span class="sxs-lookup"><span data-stu-id="4d230-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="4d230-123">V následujícím příkladu funkce Function A funkce B před definováním funkce B:</span><span class="sxs-lookup"><span data-stu-id="4d230-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="4d230-124">Další informace naleznete v tématu [How to: Calling a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4d230-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="4d230-125">Funkce lze také deklarovat v samotném modelu.</span><span class="sxs-lookup"><span data-stu-id="4d230-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="4d230-126">Funkce deklarované v modelu jsou spouštěny stejným způsobem jako funkce deklarované jako vložené v příkazu.</span><span class="sxs-lookup"><span data-stu-id="4d230-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="4d230-127">Další informace najdete v tématu [uživatelsky definované funkce](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4d230-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d230-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d230-128">Example</span></span>  
 <span data-ttu-id="4d230-129">Následující Entity SQL příkaz definuje funkci `Products`, která přebírá celočíselnou hodnotu pro filtrování vrácených produktů.</span><span class="sxs-lookup"><span data-stu-id="4d230-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a><span data-ttu-id="4d230-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d230-130">Example</span></span>  
 <span data-ttu-id="4d230-131">Následující Entity SQL příkaz definuje funkci `StringReturnsCollection`, která přebírá kolekce řetězců k filtrování vrácených kontaktů.</span><span class="sxs-lookup"><span data-stu-id="4d230-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="4d230-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d230-132">See also</span></span>

- [<span data-ttu-id="4d230-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4d230-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="4d230-134">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4d230-134">Entity SQL Language</span></span>](entity-sql-language.md)
