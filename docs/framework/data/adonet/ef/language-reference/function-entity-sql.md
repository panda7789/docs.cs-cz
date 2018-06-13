---
title: FUNKCE (entita SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: c101032aed3e94e6bbf1d16319a616131fa6b60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760671"
---
# <a name="function-entity-sql"></a><span data-ttu-id="1db03-102">FUNKCE (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="1db03-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="1db03-103">Definuje funkci v oboru příkaz dotazu Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="1db03-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db03-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="1db03-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1db03-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="1db03-106">Název funkce.</span><span class="sxs-lookup"><span data-stu-id="1db03-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="1db03-107">Název parametru ve funkci.</span><span class="sxs-lookup"><span data-stu-id="1db03-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="1db03-108">Platný výraz Entity SQL, který je funkce.</span><span class="sxs-lookup"><span data-stu-id="1db03-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="1db03-109">Příkaz ve funkci může fungovat na `parameter_name` funkci byl předán parametry.</span><span class="sxs-lookup"><span data-stu-id="1db03-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="1db03-110">Název podporovaného typu.</span><span class="sxs-lookup"><span data-stu-id="1db03-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="1db03-111">KOLEKCE (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="1db03-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="1db03-112">Výraz, který vrátí kolekce podporované typy, řádky nebo odkazy.</span><span class="sxs-lookup"><span data-stu-id="1db03-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="1db03-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="1db03-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="1db03-114">Výraz, který vrátí odkaz na typ entity.</span><span class="sxs-lookup"><span data-stu-id="1db03-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="1db03-115">ŘÁDEK **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="1db03-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="1db03-116">Výraz, který vrátí anonymní, strukturálně zadali záznamů z jednoho nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="1db03-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="1db03-117">Další informace najdete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1db03-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1db03-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1db03-118">Remarks</span></span>  
 <span data-ttu-id="1db03-119">Víc funkcí se stejným názvem lze deklarovat vložením, tak dlouho, dokud se liší funkce podpisů.</span><span class="sxs-lookup"><span data-stu-id="1db03-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="1db03-120">Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1db03-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="1db03-121">Vložená funkce jde volat v Entity SQL příkazu až poté, co byla definována v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="1db03-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="1db03-122">Vložená funkce lze však volat uvnitř jiné vložená funkce před i po definování volaná funkce.</span><span class="sxs-lookup"><span data-stu-id="1db03-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="1db03-123">V následujícím příkladu funkce A volání funkce B předtím, než je definována funkce B:</span><span class="sxs-lookup"><span data-stu-id="1db03-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="1db03-124">Další informace najdete v tématu [postupy: volání funkce definované uživatelem](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span><span class="sxs-lookup"><span data-stu-id="1db03-124">For more information, see [How to: Call a User-Defined Function](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span></span>  
  
 <span data-ttu-id="1db03-125">Funkce lze deklarovat také v přímo pro model.</span><span class="sxs-lookup"><span data-stu-id="1db03-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="1db03-126">Funkce, které jsou deklarované v modelu se stejným způsobem provést, protože funkce deklarované vložené v příkazu.</span><span class="sxs-lookup"><span data-stu-id="1db03-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="1db03-127">Další informace najdete v tématu [funkce definované uživatelem](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1db03-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db03-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="1db03-128">Example</span></span>  
 <span data-ttu-id="1db03-129">Následující příkaz Entity SQL definuje funkci `Products` celočíselnou hodnotu pro filtrování vrácených produktů, která má.</span><span class="sxs-lookup"><span data-stu-id="1db03-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="1db03-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="1db03-130">Example</span></span>  
 <span data-ttu-id="1db03-131">Následující příkaz Entity SQL definuje funkci `StringReturnsCollection` , která má kolekci řetězců pro filtrování vrácených kontaktů.</span><span class="sxs-lookup"><span data-stu-id="1db03-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="1db03-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="1db03-132">See Also</span></span>  
 [<span data-ttu-id="1db03-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1db03-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="1db03-134">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1db03-134">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
