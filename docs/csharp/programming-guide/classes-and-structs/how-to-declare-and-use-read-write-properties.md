---
title: Postup deklarace a použití vlastností čtení a zápisu – Průvodce programováním v C#
description: Naučte se používat vlastnosti pro čtení a zápis v jazyce C#. Tato ukázka obsahuje dvě vlastnosti, z nichž každý má přístupové objekty get a set, takže vlastnosti jsou pro čtení i zápis.
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 08bdaa9446491d473cfb16e3b82bac41d7af5b79
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864446"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="3f798-104">Postup deklarace a použití vlastností čtení a zápisu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3f798-104">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="3f798-105">Vlastnosti poskytují pohodlí pro veřejné datové členy, aniž by došlo k rizikům, která jsou součástí nechráněného, nekontrolovaného a neověřeného přístupu k datům objektu.</span><span class="sxs-lookup"><span data-stu-id="3f798-105">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="3f798-106">To se provádí prostřednictvím *přístupových objektů*: speciální metody, které přiřazují a načítají hodnoty z podkladového datového člena.</span><span class="sxs-lookup"><span data-stu-id="3f798-106">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="3f798-107">Přistupující objekt [set](../../language-reference/keywords/set.md) umožňuje přiřadit datové členy a přistupující objekt [Get](../../language-reference/keywords/get.md) načte hodnoty datových členů.</span><span class="sxs-lookup"><span data-stu-id="3f798-107">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="3f798-108">Tato ukázka ukazuje `Person` třídu, která má dvě vlastnosti: `Name` (String) a `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="3f798-108">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="3f798-109">Obě vlastnosti poskytují `get` a `set` přistupující objekty, takže se považují za vlastnosti pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="3f798-109">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f798-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f798-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3f798-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="3f798-111">Robust Programming</span></span>  
 <span data-ttu-id="3f798-112">V předchozím příkladu `Name` `Age` jsou vlastnosti a [veřejné](../../language-reference/keywords/public.md) a zahrnují i `get` `set` přistupující objekt a.</span><span class="sxs-lookup"><span data-stu-id="3f798-112">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="3f798-113">To umožňuje všem objektům číst a zapisovat tyto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3f798-113">This allows any object to read and write these properties.</span></span> <span data-ttu-id="3f798-114">Někdy je však žádoucí, aby jeden z přístupových objektů vyloučil.</span><span class="sxs-lookup"><span data-stu-id="3f798-114">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="3f798-115">Vynechání `set` přístupového objektu například nastaví vlastnost jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="3f798-115">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="3f798-116">Alternativně můžete zveřejnit jeden přistupující objekt veřejně, ale nastavit ho jako privátní nebo chráněný.</span><span class="sxs-lookup"><span data-stu-id="3f798-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="3f798-117">Další informace najdete v tématu [přístupnost asymetrického přístupového objektu](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="3f798-117">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="3f798-118">Jakmile jsou vlastnosti deklarovány, mohou být použity, jako kdyby byly polem třídy.</span><span class="sxs-lookup"><span data-stu-id="3f798-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="3f798-119">To umožňuje velmi přirozenou syntaxi při získávání a nastavování hodnoty vlastnosti, jako v následujících příkazech:</span><span class="sxs-lookup"><span data-stu-id="3f798-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="3f798-120">Všimněte si, že v `set` metodě vlastnosti `value` je k dispozici speciální proměnná.</span><span class="sxs-lookup"><span data-stu-id="3f798-120">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="3f798-121">Tato proměnná obsahuje hodnotu zadanou uživatelem, například:</span><span class="sxs-lookup"><span data-stu-id="3f798-121">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="3f798-122">Všimněte si čisté syntaxe pro zvýšení hodnoty `Age` vlastnosti `Person` objektu:</span><span class="sxs-lookup"><span data-stu-id="3f798-122">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="3f798-123">Pokud se `set` `get` pro vlastnosti modelu použily samostatné metody a, může podobný kód vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="3f798-123">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="3f798-124">`ToString`Metoda je přepsána v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="3f798-124">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="3f798-125">Všimněte si, že `ToString` se v programu explicitně nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="3f798-125">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="3f798-126">Je vyvolána ve výchozím nastavení `WriteLine` voláními.</span><span class="sxs-lookup"><span data-stu-id="3f798-126">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f798-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f798-127">See also</span></span>

- [<span data-ttu-id="3f798-128">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="3f798-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3f798-129">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3f798-129">Properties</span></span>](./properties.md)
- [<span data-ttu-id="3f798-130">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="3f798-130">Classes and Structs</span></span>](./index.md)
