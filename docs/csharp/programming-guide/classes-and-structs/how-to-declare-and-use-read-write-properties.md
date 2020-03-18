---
title: Jak deklarovat a používat vlastnosti zápisu pro čtení - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170283"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="ea1bb-102">Jak deklarovat a používat vlastnosti zápisu pro čtení (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ea1bb-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="ea1bb-103">Vlastnosti poskytují pohodlí veřejných datových členů bez rizik, která přicházejí s nechráněným, nekontrolovaným a neověřeným přístupem k datům objektu.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="ea1bb-104">Toho lze dosáhnout prostřednictvím *přístupových objektů*: speciální metody, které přiřazují a načítají hodnoty z podkladového datového člena.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="ea1bb-105">Přistupující [přístupový odkaz set](../../language-reference/keywords/set.md) umožňuje přiřazení datových členů a [get](../../language-reference/keywords/get.md) accessor načte hodnoty datových členů.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="ea1bb-106">Tato ukázka `Person` ukazuje třídu, `Name` která má `Age` dvě vlastnosti: (řetězec) a (int).</span><span class="sxs-lookup"><span data-stu-id="ea1bb-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="ea1bb-107">Obě vlastnosti poskytují `get` a `set` přistupující objekty, takže jsou považovány za vlastnosti čtení a zápisu.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea1bb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea1bb-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ea1bb-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ea1bb-109">Robust Programming</span></span>  
 <span data-ttu-id="ea1bb-110">V předchozím příkladu `Name` `Age` a vlastnosti jsou `get` [veřejné](../../language-reference/keywords/public.md) a zahrnují jak a a přistupující objekt. `set`</span><span class="sxs-lookup"><span data-stu-id="ea1bb-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="ea1bb-111">To umožňuje libovolný objekt číst a zapisovat tyto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="ea1bb-112">Někdy je však žádoucí vyloučit jeden z přistupujících.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="ea1bb-113">Vynechání matného objektu `set` například způsobí, že vlastnost je jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="ea1bb-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="ea1bb-114">Alternativně můžete vystavit jeden přístupový odkaz veřejně, ale jiné soukromé nebo chráněné.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="ea1bb-115">Další informace naleznete [v tématu Asymetrické přístupové připojení přístupkovou informací](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="ea1bb-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="ea1bb-116">Jakmile jsou vlastnosti deklarovány, mohou být použity, jako by byly pole třídy.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="ea1bb-117">To umožňuje velmi přirozenou syntaxi při získávání a nastavování hodnoty vlastnosti, jako v následujících příkazech:</span><span class="sxs-lookup"><span data-stu-id="ea1bb-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="ea1bb-118">Všimněte si, `set` že `value` v metodě vlastnosti je k dispozici speciální proměnná.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="ea1bb-119">Tato proměnná obsahuje hodnotu, kterou uživatel zadal, například:</span><span class="sxs-lookup"><span data-stu-id="ea1bb-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="ea1bb-120">Všimněte si čisté syntaxe `Age` pro zvýšení `Person` vlastnosti na objekt:</span><span class="sxs-lookup"><span data-stu-id="ea1bb-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="ea1bb-121">Pokud `set` samostatné `get` a metody byly použity k modelování vlastností, ekvivalentní kód může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="ea1bb-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="ea1bb-122">Metoda `ToString` je přepsána v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="ea1bb-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="ea1bb-123">Všimněte `ToString` si, že není explicitně použit v programu.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="ea1bb-124">Je vyvolána ve výchozím `WriteLine` nastavení volání.</span><span class="sxs-lookup"><span data-stu-id="ea1bb-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1bb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea1bb-125">See also</span></span>

- [<span data-ttu-id="ea1bb-126">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ea1bb-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ea1bb-127">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ea1bb-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="ea1bb-128">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="ea1bb-128">Classes and Structs</span></span>](./index.md)
