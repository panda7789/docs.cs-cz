---
title: 'Postupy: deklarování a použití vlastností čtení/zápisu (C# Programming Guide)'
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 77db2841d6ef9af21d38736f39e6041699ca13d5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129391"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="3cdde-102">Postupy: deklarování a použití vlastností čtení/zápisu (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="3cdde-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="3cdde-103">Vlastnosti poskytují pohodlí veřejné datové členy bez rizika, které jsou součástí nechráněné, nekontrolovaného a neověřený přístup k datům objektu.</span><span class="sxs-lookup"><span data-stu-id="3cdde-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="3cdde-104">To lze provést prostřednictvím *přistupující objekty*: speciální metody, které přiřadíte a načítat hodnoty ze základní datový člen.</span><span class="sxs-lookup"><span data-stu-id="3cdde-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="3cdde-105">[Nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt umožňuje datové členy mají být přiřazeny a [získat](../../../csharp/language-reference/keywords/get.md) přistupující objekt načte hodnoty datových členů.</span><span class="sxs-lookup"><span data-stu-id="3cdde-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="3cdde-106">Tento příklad ukazuje `Person` třídu, která má dvě vlastnosti: `Name` (řetězec) a `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="3cdde-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="3cdde-107">Obě vlastnosti poskytují `get` a `set` přístupových objektů, takže jsou považovány za čtení a zápisu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3cdde-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cdde-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cdde-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3cdde-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="3cdde-109">Robust Programming</span></span>  
 <span data-ttu-id="3cdde-110">V předchozím příkladu `Name` a `Age` vlastnosti jsou [veřejné](../../../csharp/language-reference/keywords/public.md) a oba `get` a `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="3cdde-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="3cdde-111">To umožňuje libovolný objekt pro čtení a zápis těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="3cdde-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="3cdde-112">Ale je v některých případech žádoucí, vyloučit jeden přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="3cdde-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="3cdde-113">Vynechání `set` přístupový objekt, například je vlastnost jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="3cdde-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 <span data-ttu-id="3cdde-114">Alternativně můžete veřejně zpřístupnit jeden přistupující objekt, ale jiné soukromé nebo chráněné.</span><span class="sxs-lookup"><span data-stu-id="3cdde-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="3cdde-115">Další informace najdete v tématu [asymetrického přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="3cdde-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="3cdde-116">Jakmile vlastnosti jsou deklarovány, můžete jako by byly pole třídy používá.</span><span class="sxs-lookup"><span data-stu-id="3cdde-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="3cdde-117">To umožňuje velmi přirozené syntaxe při získávání i nastavování hodnoty vlastnosti, jako v následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="3cdde-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 <span data-ttu-id="3cdde-118">Všimněte si, že ve vlastnosti `set` metoda a speciální `value` proměnná je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3cdde-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="3cdde-119">Tato proměnná obsahuje hodnotu, kterou uživatel specifikoval, například:</span><span class="sxs-lookup"><span data-stu-id="3cdde-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 <span data-ttu-id="3cdde-120">Všimněte si, že čisté syntaxe se zvyšuje `Age` vlastnosti `Person` objektu:</span><span class="sxs-lookup"><span data-stu-id="3cdde-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 <span data-ttu-id="3cdde-121">Pokud samostatný `set` a `get` metodách, které byly použity k modelování vlastnosti, ekvivalentní kód může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="3cdde-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="3cdde-122">`ToString` Je přepsána metoda v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="3cdde-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 <span data-ttu-id="3cdde-123">Všimněte si, že `ToString` není použito explicitně v programu.</span><span class="sxs-lookup"><span data-stu-id="3cdde-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="3cdde-124">Vyvolá se ve výchozím nastavení `WriteLine` volání.</span><span class="sxs-lookup"><span data-stu-id="3cdde-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cdde-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cdde-125">See Also</span></span>

- [<span data-ttu-id="3cdde-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3cdde-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3cdde-127">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3cdde-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="3cdde-128">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="3cdde-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
