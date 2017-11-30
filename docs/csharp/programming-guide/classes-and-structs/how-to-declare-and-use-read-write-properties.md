---
title: "Postupy: deklarování a použití vlastností čtení zápisu (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17bdd05196f834b491c69f648bec0b7cb6e3cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="ff358-102">Postupy: deklarování a použití vlastností čtení zápisu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ff358-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="ff358-103">Vlastnosti zajistí pohodlí veřejná data členů bez rizika, které jsou součástí nechráněné, neřízené a neověřených přístup k datům objektu.</span><span class="sxs-lookup"><span data-stu-id="ff358-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="ff358-104">To se provádí prostřednictvím *přístupové objekty*: speciální metody, které přiřadit a načítání hodnot z základní datový člen.</span><span class="sxs-lookup"><span data-stu-id="ff358-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="ff358-105">[Nastavit](../../../csharp/language-reference/keywords/set.md) přistupujícího objektu umožňuje členům data přiřazen a [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu načte data hodnoty členů.</span><span class="sxs-lookup"><span data-stu-id="ff358-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="ff358-106">Tento příklad ukazuje `Person` třídu, která má dvě vlastnosti: `Name` (string) a `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="ff358-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="ff358-107">Obě vlastnosti poskytují `get` a `set` přístupových objektů, takže je považována za čtení/zápisu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ff358-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff358-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff358-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ff358-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ff358-109">Robust Programming</span></span>  
 <span data-ttu-id="ff358-110">V předchozím příkladu `Name` a `Age` vlastnosti jsou [veřejné](../../../csharp/language-reference/keywords/public.md) a současně obsahovat `get` a `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="ff358-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="ff358-111">To umožňuje číst a zapisovat tyto vlastnosti libovolného objektu.</span><span class="sxs-lookup"><span data-stu-id="ff358-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="ff358-112">Ale je někdy žádoucí, jeden přístupové objekty vyloučit.</span><span class="sxs-lookup"><span data-stu-id="ff358-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="ff358-113">Vynechání `set` přistupujícího objektu, například umožňuje vlastnost jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="ff358-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 <span data-ttu-id="ff358-114">Alternativně můžete vystavit jednoho přístupového objektu veřejně, ale zkontrolujte další privátní nebo chráněný.</span><span class="sxs-lookup"><span data-stu-id="ff358-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="ff358-115">Další informace najdete v tématu [asymetrické přístupnosti přistupujícího objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="ff358-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="ff358-116">Jakmile jsou deklarované vlastnosti, můžete jako kdyby byly pole třídy použít.</span><span class="sxs-lookup"><span data-stu-id="ff358-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="ff358-117">To umožňuje velmi přirozené syntaxe při získání a nastavení hodnoty vlastnosti, jako v následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="ff358-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 <span data-ttu-id="ff358-118">Všimněte si, že se ve vlastnosti `set` metoda a zvláštní `value` proměnná je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ff358-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="ff358-119">Tato proměnná obsahuje hodnotu, která uživatel zadal, například:</span><span class="sxs-lookup"><span data-stu-id="ff358-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 <span data-ttu-id="ff358-120">Všimněte si čistou syntaxe zvyšování `Age` vlastnost `Person` objektu:</span><span class="sxs-lookup"><span data-stu-id="ff358-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 <span data-ttu-id="ff358-121">Pokud samostatné `set` a `get` metody použité k jejich vlastnosti modelu, kód ekvivalentní může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="ff358-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="ff358-122">`ToString` Je metoda potlačena v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="ff358-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 <span data-ttu-id="ff358-123">Všimněte si, že `ToString` nepoužívá explicitně v programu.</span><span class="sxs-lookup"><span data-stu-id="ff358-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="ff358-124">Vyvolá se ve výchozím nastavení `WriteLine` volání.</span><span class="sxs-lookup"><span data-stu-id="ff358-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff358-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff358-125">See Also</span></span>  
 [<span data-ttu-id="ff358-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ff358-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ff358-127">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ff358-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="ff358-128">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="ff358-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
