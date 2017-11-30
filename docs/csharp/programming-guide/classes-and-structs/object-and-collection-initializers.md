---
title: "Inicializátory objektu a kolekce (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7445a2919baaa477b4611c4c5ee5a0031539ca30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="f11ad-102">Inicializátory objektu a kolekce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f11ad-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="f11ad-103">Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="f11ad-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="f11ad-104">Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.</span><span class="sxs-lookup"><span data-stu-id="f11ad-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="f11ad-105">Následující příklad ukazuje, jak pomocí inicializátoru objektů s typem s názvem `Cat` a postup vyvolání výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f11ad-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="f11ad-106">Všimněte si, automaticky implementované vlastnosti v `Cat` třídy.</span><span class="sxs-lookup"><span data-stu-id="f11ad-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="f11ad-107">Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f11ad-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="f11ad-108">Syntaxe inicializátory objektu umožňuje vytvoření instance, a poté přiřadí nově vytvořený objekt s její přiřazenou vlastnosti k proměnné v přiřazení.</span><span class="sxs-lookup"><span data-stu-id="f11ad-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="f11ad-109">Inicializátory objektů s anonymními typy</span><span class="sxs-lookup"><span data-stu-id="f11ad-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="f11ad-110">Inicializátory objektů lze v libovolném kontextu, ale jsou užitečné zejména v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu výrazy.</span><span class="sxs-lookup"><span data-stu-id="f11ad-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="f11ad-111">Výrazy dotazů využívají často [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), který lze inicializovat pouze pomocí inicializátoru objektů, jak je znázorněno v následující prohlášení.</span><span class="sxs-lookup"><span data-stu-id="f11ad-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="f11ad-112">Povolit anonymní typy `select` klauzuli v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výraz, který se do objektů, jehož hodnota a tvar může lišit od původního transformace objektů původní pořadí.</span><span class="sxs-lookup"><span data-stu-id="f11ad-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="f11ad-113">Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f11ad-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="f11ad-114">V následujícím příkladu předpokládáme, že objekt produktu (`p`) obsahuje mnoho pole a metody, a že vás zajímá pouze při vytváření pořadí objektů, které obsahují název produktu a jednotkové ceny.</span><span class="sxs-lookup"><span data-stu-id="f11ad-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="f11ad-115">Po provedení tohoto dotazu `productInfos` proměnná bude obsahovat objekty, které jsou přístupné z `foreach` příkaz, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f11ad-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="f11ad-116">Jednotlivé objekty v novém anonymním typu mají dvě veřejné vlastnosti, kterým budou přiděleny stejné názvy, jako mají vlastnosti nebo pole v původním objektu.</span><span class="sxs-lookup"><span data-stu-id="f11ad-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="f11ad-117">Můžete také přejmenovat pole při vytváření anonymní typ; v následujícím příkladu se přejmenuje `UnitPrice` do `Price`.</span><span class="sxs-lookup"><span data-stu-id="f11ad-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="f11ad-118">Inicializátory objektů s typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="f11ad-118">Object initializers with nullable types</span></span>  
 <span data-ttu-id="f11ad-119">Pokud použijete inicializátor objektu se strukturou null, dojde k chybě v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f11ad-119">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="f11ad-120">Inicializátory kolekce</span><span class="sxs-lookup"><span data-stu-id="f11ad-120">Collection initializers</span></span>  
 <span data-ttu-id="f11ad-121">Inicializátory kolekcí umožňují zadat jeden nebo více inicializátory elementů polí, když inicializuje kolekci zadejte této implementuje <xref:System.Collections.IEnumerable> a má `Add` s odpovídajícím podpisem jako metodu instance nebo metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f11ad-121">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="f11ad-122">Inicializátory prvku mohou být tvořeny jednoduchou hodnotou, výrazem nebo inicializátorem objektu.</span><span class="sxs-lookup"><span data-stu-id="f11ad-122">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="f11ad-123">Pomocí inicializátoru kolekce nemáte zadejte několik volání `Add` metoda třídy ve zdrojovém kódu; kompilátor přidá volání.</span><span class="sxs-lookup"><span data-stu-id="f11ad-123">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="f11ad-124">Následující příklady znázorňují dva jednoduché inicializátory kolekce:</span><span class="sxs-lookup"><span data-stu-id="f11ad-124">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="f11ad-125">Následující kolekce inicializátoru používá inicializátory objektů se inicializovat objekty `Cat` třídy definované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f11ad-125">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="f11ad-126">Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="f11ad-126">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="f11ad-127">Můžete zadat [null](../../../csharp/language-reference/keywords/null.md) jako element v inicializátoru kolekce Pokud kolekce `Add` metoda umožňuje.</span><span class="sxs-lookup"><span data-stu-id="f11ad-127">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="f11ad-128">Můžete zadat indexované prvky, pokud kolekce podporuje indexování.</span><span class="sxs-lookup"><span data-stu-id="f11ad-128">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="example"></a><span data-ttu-id="f11ad-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="f11ad-129">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f11ad-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f11ad-130">See Also</span></span>  
 [<span data-ttu-id="f11ad-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f11ad-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f11ad-132">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="f11ad-132">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="f11ad-133">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f11ad-133">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
