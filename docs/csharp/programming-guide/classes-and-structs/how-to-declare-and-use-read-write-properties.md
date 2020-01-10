---
title: Jak deklarovat a používat vlastnosti pro čtení a zápis C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 5b880cfc3ace197a3bad2f707cf55543dbe7b78e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714921"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="7cf80-102">Postup deklarace a použití vlastností čtení a zápisu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="7cf80-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="7cf80-103">Vlastnosti poskytují pohodlí pro veřejné datové členy, aniž by došlo k rizikům, která jsou součástí nechráněného, nekontrolovaného a neověřeného přístupu k datům objektu.</span><span class="sxs-lookup"><span data-stu-id="7cf80-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="7cf80-104">To se provádí prostřednictvím *přístupových objektů*: speciální metody, které přiřazují a načítají hodnoty z podkladového datového člena.</span><span class="sxs-lookup"><span data-stu-id="7cf80-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="7cf80-105">Přistupující objekt [set](../../language-reference/keywords/set.md) umožňuje přiřadit datové členy a přistupující objekt [Get](../../language-reference/keywords/get.md) načte hodnoty datových členů.</span><span class="sxs-lookup"><span data-stu-id="7cf80-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="7cf80-106">Tato ukázka ukazuje třídu `Person`, která má dvě vlastnosti: `Name` (String) a `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="7cf80-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="7cf80-107">Obě vlastnosti poskytují přístupové objekty `get` a `set`, takže se považují za vlastnosti pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="7cf80-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cf80-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cf80-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7cf80-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7cf80-109">Robust Programming</span></span>  
 <span data-ttu-id="7cf80-110">V předchozím příkladu jsou vlastnosti `Name` a `Age` [veřejné](../../language-reference/keywords/public.md) a zahrnují `get` i přistupující objekt `set`.</span><span class="sxs-lookup"><span data-stu-id="7cf80-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="7cf80-111">To umožňuje všem objektům číst a zapisovat tyto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cf80-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="7cf80-112">Někdy je však žádoucí, aby jeden z přístupových objektů vyloučil.</span><span class="sxs-lookup"><span data-stu-id="7cf80-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="7cf80-113">Vynechání přístupového objektu `set` například nastaví vlastnost jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="7cf80-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="7cf80-114">Alternativně můžete zveřejnit jeden přistupující objekt veřejně, ale nastavit ho jako privátní nebo chráněný.</span><span class="sxs-lookup"><span data-stu-id="7cf80-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="7cf80-115">Další informace najdete v tématu [přístupnost asymetrického přístupového objektu](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="7cf80-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="7cf80-116">Jakmile jsou vlastnosti deklarovány, mohou být použity, jako kdyby byly polem třídy.</span><span class="sxs-lookup"><span data-stu-id="7cf80-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="7cf80-117">To umožňuje velmi přirozenou syntaxi při získávání a nastavování hodnoty vlastnosti, jako v následujících příkazech:</span><span class="sxs-lookup"><span data-stu-id="7cf80-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="7cf80-118">Všimněte si, že ve vlastnosti `set` metoda je k dispozici speciální `value` proměnná.</span><span class="sxs-lookup"><span data-stu-id="7cf80-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="7cf80-119">Tato proměnná obsahuje hodnotu zadanou uživatelem, například:</span><span class="sxs-lookup"><span data-stu-id="7cf80-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="7cf80-120">Všimněte si čisté syntaxe pro zvýšení `Age` vlastnosti u objektu `Person`:</span><span class="sxs-lookup"><span data-stu-id="7cf80-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="7cf80-121">Pokud byly pro vlastnosti modelu použity samostatné metody `set` a `get`, podobný kód by mohl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7cf80-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="7cf80-122">Metoda `ToString` je v tomto příkladu přepsána:</span><span class="sxs-lookup"><span data-stu-id="7cf80-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="7cf80-123">Všimněte si, že `ToString` není explicitně použit v programu.</span><span class="sxs-lookup"><span data-stu-id="7cf80-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="7cf80-124">Je vyvolána ve výchozím nastavení voláním `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="7cf80-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf80-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cf80-125">See also</span></span>

- [<span data-ttu-id="7cf80-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7cf80-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7cf80-127">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7cf80-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="7cf80-128">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="7cf80-128">Classes and Structs</span></span>](./index.md)
