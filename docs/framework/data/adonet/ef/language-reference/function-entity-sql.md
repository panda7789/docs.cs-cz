---
title: FUNKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: ae8da3985f11a2e9f52852876a21f50a412e3b27
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250941"
---
# <a name="function-entity-sql"></a><span data-ttu-id="c0722-102">FUNKCE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c0722-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="c0722-103">Definuje funkci v oboru příkazu Entity SQL dotazu.</span><span class="sxs-lookup"><span data-stu-id="c0722-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0722-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0722-104">Syntax</span></span>  
  
```  
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
  
## <a name="arguments"></a><span data-ttu-id="c0722-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c0722-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="c0722-106">Název funkce</span><span class="sxs-lookup"><span data-stu-id="c0722-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="c0722-107">Název parametru ve funkci.</span><span class="sxs-lookup"><span data-stu-id="c0722-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="c0722-108">Platný výraz Entity SQL, který je funkcí.</span><span class="sxs-lookup"><span data-stu-id="c0722-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="c0722-109">Příkaz ve funkci může působit na `parameter_name` parametry předané do funkce.</span><span class="sxs-lookup"><span data-stu-id="c0722-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="c0722-110">Název podporovaného typu.</span><span class="sxs-lookup"><span data-stu-id="c0722-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="c0722-111">KOLEKCE (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="c0722-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="c0722-112">Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.</span><span class="sxs-lookup"><span data-stu-id="c0722-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="c0722-113">REF **(** `data_type` **)**</span><span class="sxs-lookup"><span data-stu-id="c0722-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="c0722-114">Výraz, který vrací odkaz na typ entity.</span><span class="sxs-lookup"><span data-stu-id="c0722-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="c0722-115">ROW **(** `row_expression` **)**</span><span class="sxs-lookup"><span data-stu-id="c0722-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="c0722-116">Výraz, který vrací anonymní, strukturální záznamy typu z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="c0722-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="c0722-117">Další informace najdete v části [řádek](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c0722-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0722-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0722-118">Remarks</span></span>  
 <span data-ttu-id="c0722-119">Je možné deklarovat vložené více funkcí se stejným názvem, pokud se signatury funkce liší.</span><span class="sxs-lookup"><span data-stu-id="c0722-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="c0722-120">Další informace najdete v tématu [řešení přetížení funkce](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c0722-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c0722-121">Vloženou funkci lze volat v příkazu Entity SQL pouze poté, co byla definována v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="c0722-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="c0722-122">Vložená funkce může být však volána uvnitř jiné vložené funkce buď před, nebo po definování volané funkce.</span><span class="sxs-lookup"><span data-stu-id="c0722-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="c0722-123">V následujícím příkladu funkce Function A funkce B před definováním funkce B:</span><span class="sxs-lookup"><span data-stu-id="c0722-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="c0722-124">Další informace najdete v tématu [jak: Volání uživatelsky definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c0722-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="c0722-125">Funkce lze také deklarovat v samotném modelu.</span><span class="sxs-lookup"><span data-stu-id="c0722-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="c0722-126">Funkce deklarované v modelu jsou spouštěny stejným způsobem jako funkce deklarované jako vložené v příkazu.</span><span class="sxs-lookup"><span data-stu-id="c0722-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="c0722-127">Další informace najdete v tématu [uživatelsky definované funkce](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c0722-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0722-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0722-128">Example</span></span>  
 <span data-ttu-id="c0722-129">Následující Entity SQL příkaz definuje funkci `Products` , která přebírá celočíselnou hodnotu pro filtrování vrácených produktů.</span><span class="sxs-lookup"><span data-stu-id="c0722-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="c0722-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0722-130">Example</span></span>  
 <span data-ttu-id="c0722-131">Následující Entity SQL příkaz definuje funkci `StringReturnsCollection` , která přebírá kolekci řetězců k filtrování vrácených kontaktů.</span><span class="sxs-lookup"><span data-stu-id="c0722-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="c0722-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0722-132">See also</span></span>

- [<span data-ttu-id="c0722-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c0722-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c0722-134">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c0722-134">Entity SQL Language</span></span>](entity-sql-language.md)
