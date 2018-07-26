---
title: new – – operátor (Referenční dokumentace jazyka C#)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243944"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="d90c8-102">new – – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d90c8-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="d90c8-103">Použít k vytvoření objektů a vyvolávání konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="d90c8-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="d90c8-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d90c8-104">For example:</span></span>  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="d90c8-105">Používá se také k vytváření instancí anonymních typů:</span><span class="sxs-lookup"><span data-stu-id="d90c8-105">It is also used to create instances of anonymous types:</span></span>  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 <span data-ttu-id="d90c8-106">`new` Operátor slouží také k vyvolání výchozího konstruktoru pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="d90c8-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="d90c8-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d90c8-107">For example:</span></span>  
  
```csharp
int i = new int();  
```  
  
 <span data-ttu-id="d90c8-108">V předchozím příkazu `i` je inicializován na `0`, což je výchozí hodnota pro typ `int`.</span><span class="sxs-lookup"><span data-stu-id="d90c8-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="d90c8-109">Příkaz má stejný účinek jako následující:</span><span class="sxs-lookup"><span data-stu-id="d90c8-109">The statement has the same effect as the following:</span></span>  
  
```csharp
int i = 0;  
```  
  
 <span data-ttu-id="d90c8-110">Úplný seznam výchozích hodnot, naleznete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="d90c8-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="d90c8-111">Mějte na paměti, že se jedná o chybu deklarovat výchozí konstruktor [struktura](../../../csharp/language-reference/keywords/struct.md) vzhledem k tomu, že každý typ hodnoty implicitně nemá veřejný výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d90c8-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="d90c8-112">Je možné deklarovat konstruktor s parametry u typu Struktura nastavit jeho počáteční hodnoty, ale to je potřeba, pouze pokud jsou požadované hodnoty jiné než výchozí.</span><span class="sxs-lookup"><span data-stu-id="d90c8-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="d90c8-113">Objekty typu hodnoty, jako jsou struktury a objekty typu odkazu, jako jsou třídy, jsou zničeny automaticky, ale objekty typu hodnoty je zničen při zničení jejich obsahující kontext, zatímco objekty typu odkazu jsou zničeny podle uvolňování paměti kolekce neurčené době po odebrání poslední odkazy na ně.</span><span class="sxs-lookup"><span data-stu-id="d90c8-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="d90c8-114">Pro typy, které obsahují prostředky, jako jsou popisovače souborů nebo připojení k síti je třeba využívat deterministické vyčištění zajistit, že se prostředky, které obsahují vydávají co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="d90c8-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="d90c8-115">Další informace najdete v tématu [příkaz using](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d90c8-115">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="d90c8-116">`new` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="d90c8-116">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="d90c8-117">Pokud `new` operátor selže přidělování paměti, vyvolá výjimku, <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="d90c8-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d90c8-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d90c8-118">Example</span></span>  
 <span data-ttu-id="d90c8-119">V následujícím příkladu `struct` jsou vytvořeny a inicializovány pomocí objektů a objekt třídy `new` operátor a potom přiřadit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d90c8-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="d90c8-120">Zobrazí se výchozí nastavení a přiřazené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d90c8-120">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="d90c8-121">Všimněte si, že v příkladu, který je výchozí hodnota řetězce `null`.</span><span class="sxs-lookup"><span data-stu-id="d90c8-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="d90c8-122">Proto se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="d90c8-122">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d90c8-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d90c8-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d90c8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d90c8-124">See Also</span></span>  
 [<span data-ttu-id="d90c8-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d90c8-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d90c8-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d90c8-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d90c8-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d90c8-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d90c8-128">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="d90c8-128">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="d90c8-129">new</span><span class="sxs-lookup"><span data-stu-id="d90c8-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="d90c8-130">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="d90c8-130">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
