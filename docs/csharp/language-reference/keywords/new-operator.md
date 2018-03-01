---
title: "new – – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
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
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="9bbc6-102">new – – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9bbc6-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="9bbc6-103">Slouží k vytvoření objektů a vyvolání konstruktory.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="9bbc6-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9bbc6-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="9bbc6-105">Také se používá k vytvoření instance anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="9bbc6-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="9bbc6-106">`new` Operátor slouží také k vyvolání pro typy hodnot výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="9bbc6-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9bbc6-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="9bbc6-108">V předchozím příkazu `i` je inicializováno `0`, což je výchozí hodnota pro typ `int`.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="9bbc6-109">Příkaz má stejný účinek jako následující:</span><span class="sxs-lookup"><span data-stu-id="9bbc6-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="9bbc6-110">Úplný seznam výchozích hodnot, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc6-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="9bbc6-111">Mějte na paměti, že se jedná o chybu deklarovat pro výchozí konstruktor [struktura](../../../csharp/language-reference/keywords/struct.md) vzhledem k tomu, že každý typ hodnoty implicitně má výchozí veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="9bbc6-112">Je možné deklarovat parametrizované konstruktory typu Struktura k nastavení jeho počáteční hodnoty, ale to je potřeba, pouze pokud jiné než výchozí hodnoty jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="9bbc6-113">Typ hodnoty objekty například struktury jsou vytvořené v zásobníku, zatímco odkazový typ objektů, jako jsou třídy vytvořené v haldě.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="9bbc6-114">Oba typy objektů jsou zničen automaticky, ale objekty na základě typů hodnotu jsou zničený, když se dostala mimo rozsah, zatímco na základě objektů odkazové typy jsou zničen neurčené během po odebrání odkazu na poslední k nim.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="9bbc6-115">Pro odkazové typy, které využívají pevné prostředky, jako je například velké množství paměti, obslužné rutiny souborů nebo připojení k síti je někdy žádoucí využívat deterministické dokončení zajistit, že objekt co nejdříve zničena.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="9bbc6-116">Další informace najdete v tématu [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc6-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="9bbc6-117">`new` Operátor nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="9bbc6-118">Pokud `new` operátor se nepodařilo přidělit paměť, vyvolá výjimku, <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbc6-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bbc6-119">Example</span></span>  
 <span data-ttu-id="9bbc6-120">V následujícím příkladu `struct` objekt a objekt třídy jsou vytvořeny a inicializovány pomocí `new` operátor a potom přiřadit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="9bbc6-121">Zobrazí se výchozí hodnota a přiřazené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-121">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="9bbc6-122">Všimněte si v příkladu, který je výchozí hodnota řetězce `null`.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-122">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="9bbc6-123">Proto se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-123">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9bbc6-124">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9bbc6-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9bbc6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bbc6-125">See Also</span></span>  
 [<span data-ttu-id="9bbc6-126">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9bbc6-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9bbc6-127">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9bbc6-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9bbc6-128">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9bbc6-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9bbc6-129">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="9bbc6-129">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="9bbc6-130">Nový</span><span class="sxs-lookup"><span data-stu-id="9bbc6-130">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="9bbc6-131">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="9bbc6-131">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
