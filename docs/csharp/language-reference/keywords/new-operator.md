---
title: operátor new - C# odkaz
ms.custom: seodec18
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 1c14d50e31b89f4c77c94e5899e8207766a3540f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977168"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="5a3b3-102">New – operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5a3b3-102">new operator (C# Reference)</span></span>

<span data-ttu-id="5a3b3-103">Použít k vytvoření objektů a vyvolávání konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="5a3b3-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5a3b3-104">For example:</span></span>

```csharp
Class1 obj  = new Class1();
```

<span data-ttu-id="5a3b3-105">Používá se také k vytváření instancí anonymních typů:</span><span class="sxs-lookup"><span data-stu-id="5a3b3-105">It is also used to create instances of anonymous types:</span></span>

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

<span data-ttu-id="5a3b3-106">`new` Operátor se používá také k vyvolání konstruktoru bez parametrů pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-106">The `new` operator is also used to invoke the parameterless constructor for value types.</span></span> <span data-ttu-id="5a3b3-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5a3b3-107">For example:</span></span>

```csharp
int i = new int();
```

<span data-ttu-id="5a3b3-108">V předchozím příkazu `i` je inicializován na `0`, což je výchozí hodnota pro typ `int`.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="5a3b3-109">Příkaz má stejný účinek jako následující:</span><span class="sxs-lookup"><span data-stu-id="5a3b3-109">The statement has the same effect as the following:</span></span>

```csharp
int i = 0;
```

<span data-ttu-id="5a3b3-110">Úplný seznam výchozích hodnot, naleznete v tématu [tabulka výchozích hodnot](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="5a3b3-110">For a complete list of default values, see [Default Values Table](default-values-table.md).</span></span>

<span data-ttu-id="5a3b3-111">Mějte na paměti, že se jedná o chybu deklarovat konstruktor bez parametrů pro [struktura](struct.md) vzhledem k tomu, že každý typ hodnoty má implicitně veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-111">Remember that it is an error to declare a parameterless constructor for a [struct](struct.md) because every value type implicitly has a public parameterless constructor.</span></span> <span data-ttu-id="5a3b3-112">Je možné deklarovat konstruktor s parametry u typu Struktura nastavit jeho počáteční hodnoty, ale to je potřeba, pouze pokud jsou požadované hodnoty jiné než výchozí.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>

<span data-ttu-id="5a3b3-113">Objekty typu hodnoty, jako jsou struktury a objekty typu odkazu, jako jsou třídy, jsou zničeny automaticky, ale objekty typu hodnoty je zničen při zničení jejich obsahující kontext, zatímco objekty typu odkazu jsou zničeny podle uvolňování paměti kolekce neurčené době po odebrání poslední odkazy na ně.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="5a3b3-114">Pro typy, které obsahují prostředky, jako jsou popisovače souborů nebo připojení k síti je třeba využívat deterministické vyčištění zajistit, že se prostředky, které obsahují vydávají co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="5a3b3-115">Další informace najdete v tématu [příkaz using](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5a3b3-115">For more information, see [using Statement](using-statement.md).</span></span>

<span data-ttu-id="5a3b3-116">`new` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-116">The `new` operator cannot be overloaded.</span></span>

<span data-ttu-id="5a3b3-117">Pokud `new` operátor selže přidělování paměti, vyvolá výjimku, <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="5a3b3-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a3b3-118">Example</span></span>

<span data-ttu-id="5a3b3-119">V následujícím příkladu `struct` jsou vytvořeny a inicializovány pomocí objektů a objekt třídy `new` operátor a potom přiřadit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="5a3b3-120">Zobrazí se výchozí nastavení a přiřazené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-120">The default and the assigned values are displayed.</span></span>

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

<span data-ttu-id="5a3b3-121">Všimněte si, že v příkladu, který je výchozí hodnota řetězce `null`.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="5a3b3-122">Proto se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="5a3b3-122">Therefore, it is not displayed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5a3b3-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a3b3-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5a3b3-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a3b3-124">See also</span></span>

- [<span data-ttu-id="5a3b3-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a3b3-125">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="5a3b3-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5a3b3-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5a3b3-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a3b3-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5a3b3-128">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="5a3b3-128">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="5a3b3-129">new</span><span class="sxs-lookup"><span data-stu-id="5a3b3-129">new</span></span>](new.md)
- [<span data-ttu-id="5a3b3-130">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="5a3b3-130">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)