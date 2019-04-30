---
title: – FUNKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: efab5f1abbc5e0c22e404c37dc80dd5aafa09ce1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879603"
---
# <a name="function-entity-sql"></a><span data-ttu-id="3fe45-102">– FUNKCE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3fe45-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="3fe45-103">Definuje funkci v rozsahu příkazu dotazu Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="3fe45-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fe45-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="3fe45-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3fe45-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="3fe45-106">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="3fe45-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="3fe45-107">Název parametru ve funkci.</span><span class="sxs-lookup"><span data-stu-id="3fe45-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="3fe45-108">Platný výraz Entity SQL, který je funkce.</span><span class="sxs-lookup"><span data-stu-id="3fe45-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="3fe45-109">Příkaz ve funkci dají dále rozvíjet `parameter_name` parametry předané do funkce.</span><span class="sxs-lookup"><span data-stu-id="3fe45-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="3fe45-110">Název podporovaného typu.</span><span class="sxs-lookup"><span data-stu-id="3fe45-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="3fe45-111">KOLEKCE (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="3fe45-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="3fe45-112">Výraz, který vrátí kolekci podporovaných typů, řádky nebo odkazy.</span><span class="sxs-lookup"><span data-stu-id="3fe45-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="3fe45-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="3fe45-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="3fe45-114">Výraz, který vrátí odkaz na typ entity.</span><span class="sxs-lookup"><span data-stu-id="3fe45-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="3fe45-115">ROW **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="3fe45-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="3fe45-116">Výraz, který vrátí anonymní, typované strukturálně záznamů z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="3fe45-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="3fe45-117">Další informace najdete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3fe45-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fe45-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fe45-118">Remarks</span></span>  
 <span data-ttu-id="3fe45-119">Více funkcí se stejným názvem, mohou být deklarovány jako vložené, jako signatur funkce se liší.</span><span class="sxs-lookup"><span data-stu-id="3fe45-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="3fe45-120">Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3fe45-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="3fe45-121">Vložená funkce lze volat v příkazu k Entity SQL až po je definována v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="3fe45-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="3fe45-122">Ale vložená funkce lze volat jiné vložené funkce před nebo po definování volané funkce.</span><span class="sxs-lookup"><span data-stu-id="3fe45-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="3fe45-123">V následujícím příkladu volání funkcí A funkci B předtím, než je definována funkce B:</span><span class="sxs-lookup"><span data-stu-id="3fe45-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="3fe45-124">Další informace najdete v tématu [jak: Volání uživatelem definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3fe45-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="3fe45-125">Funkce mohou být deklarovány také v modelu, samotného.</span><span class="sxs-lookup"><span data-stu-id="3fe45-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="3fe45-126">Funkce deklarované v modelu jsou provedeny stejným způsobem jako funkce deklarovaná vložené v příkazu.</span><span class="sxs-lookup"><span data-stu-id="3fe45-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="3fe45-127">Další informace najdete v tématu [uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3fe45-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fe45-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fe45-128">Example</span></span>  
 <span data-ttu-id="3fe45-129">Pomocí následujícího příkazu Entity SQL definuje funkci `Products` , který přebírá hodnotu celého čísla pro filtrování vrácených produktů.</span><span class="sxs-lookup"><span data-stu-id="3fe45-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="3fe45-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fe45-130">Example</span></span>  
 <span data-ttu-id="3fe45-131">Pomocí následujícího příkazu Entity SQL definuje funkci `StringReturnsCollection` , který vezme kolekci řetězce vráceného kontaktů filtr.</span><span class="sxs-lookup"><span data-stu-id="3fe45-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="3fe45-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fe45-132">See also</span></span>

- [<span data-ttu-id="3fe45-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3fe45-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3fe45-134">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3fe45-134">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
