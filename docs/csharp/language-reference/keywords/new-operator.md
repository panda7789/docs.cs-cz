---
title: "new – – operátor (Referenční dokumentace jazyka C#)"
ms.date: 03/15/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab582cd14bc649ca8d1678a583a8f95e78c6bf7e
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2018
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="35456-102">new – – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="35456-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="35456-103">Slouží k vytvoření objektů a vyvolání konstruktory.</span><span class="sxs-lookup"><span data-stu-id="35456-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="35456-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="35456-104">For example:</span></span>  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="35456-105">Také se používá k vytvoření instance anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="35456-105">It is also used to create instances of anonymous types:</span></span>  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 <span data-ttu-id="35456-106">`new` Operátor slouží také k vyvolání pro typy hodnot výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="35456-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="35456-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="35456-107">For example:</span></span>  
  
```csharp
int i = new int();  
```  
  
 <span data-ttu-id="35456-108">V předchozím příkazu `i` je inicializováno `0`, což je výchozí hodnota pro typ `int`.</span><span class="sxs-lookup"><span data-stu-id="35456-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="35456-109">Příkaz má stejný účinek jako následující:</span><span class="sxs-lookup"><span data-stu-id="35456-109">The statement has the same effect as the following:</span></span>  
  
```csharp
int i = 0;  
```  
  
 <span data-ttu-id="35456-110">Úplný seznam výchozích hodnot, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="35456-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="35456-111">Mějte na paměti, že se jedná o chybu deklarovat pro výchozí konstruktor [struktura](../../../csharp/language-reference/keywords/struct.md) vzhledem k tomu, že každý typ hodnoty implicitně má výchozí veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="35456-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="35456-112">Je možné deklarovat parametrizované konstruktory typu Struktura k nastavení jeho počáteční hodnoty, ale to je potřeba, pouze pokud jiné než výchozí hodnoty jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="35456-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="35456-113">Typ hodnoty objekty, jako je například struktury a odkaz na typ objektů, jako jsou třídy zničen automaticky, ale typ hodnoty objekty budou ztraceny při jejich obsahující kontext zničení, zatímco paměti jsou zničena objekty typu odkazu kolekce neurčené během po odebrání odkazu na poslední k nim.</span><span class="sxs-lookup"><span data-stu-id="35456-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="35456-114">Pro typy, které obsahují prostředky, jako jsou popisovače souborů nebo připojení k síti je třeba použít deterministický čištění zajistit, aby co nejdříve uvolnění prostředků, které obsahují.</span><span class="sxs-lookup"><span data-stu-id="35456-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="35456-115">Další informace najdete v tématu [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="35456-115">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="35456-116">`new` Operátor nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="35456-116">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="35456-117">Pokud `new` operátor se nepodařilo přidělit paměť, vyvolá výjimku, <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="35456-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35456-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="35456-118">Example</span></span>  
 <span data-ttu-id="35456-119">V následujícím příkladu `struct` objekt a objekt třídy jsou vytvořeny a inicializovány pomocí `new` operátor a potom přiřadit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="35456-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="35456-120">Zobrazí se výchozí hodnota a přiřazené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="35456-120">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="35456-121">Všimněte si v příkladu, který je výchozí hodnota řetězce `null`.</span><span class="sxs-lookup"><span data-stu-id="35456-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="35456-122">Proto se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="35456-122">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="35456-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35456-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35456-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="35456-124">See Also</span></span>  
 [<span data-ttu-id="35456-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35456-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="35456-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="35456-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="35456-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35456-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="35456-128">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="35456-128">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="35456-129">new</span><span class="sxs-lookup"><span data-stu-id="35456-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="35456-130">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="35456-130">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
