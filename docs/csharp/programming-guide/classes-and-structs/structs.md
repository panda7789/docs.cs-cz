---
title: Struktury (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322985"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="ef862-102">Struktury (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ef862-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="ef862-103">Struktury jsou definované pomocí [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo, například:</span><span class="sxs-lookup"><span data-stu-id="ef862-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="ef862-104">Struktury sdílet většina stejnou syntaxi jako třídy, i když jsou omezenější než třídy struktury:</span><span class="sxs-lookup"><span data-stu-id="ef862-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="ef862-105">V deklaraci struktura nelze inicializovat pole Pokud jsou deklarovány jako const nebo statické.</span><span class="sxs-lookup"><span data-stu-id="ef862-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="ef862-106">Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="ef862-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="ef862-107">Struktury se zkopírují na přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ef862-107">Structs are copied on assignment.</span></span> <span data-ttu-id="ef862-108">Když struktury je přiřazen k nové proměnné, ale data se zkopírují a všechny změny nové kopie nezmění data pro původní kopii.</span><span class="sxs-lookup"><span data-stu-id="ef862-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="ef862-109">To je důležité si pamatovat při práci s kolekcí typů hodnot, jako je například slovník\<string, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="ef862-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="ef862-110">Struktury jsou hodnotové typy a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="ef862-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="ef862-111">Na rozdíl od třídy, struktury se dá vytvořit instance bez použití `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="ef862-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="ef862-112">Struktury můžou deklarovat konstruktory, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="ef862-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="ef862-113">Struktury nemůže Zdědit z jiné třídy nebo struktury a nesmí být základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ef862-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="ef862-114">Všechny struktury dědí přímo z `System.ValueType`, který dědí z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="ef862-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="ef862-115">Struktury můžete implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ef862-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="ef862-116">Struktura slouží jako typ s možnou hodnotou Null a lze přiřadit hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ef862-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ef862-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ef862-117">Related Sections</span></span>  
 <span data-ttu-id="ef862-118">Další informace:</span><span class="sxs-lookup"><span data-stu-id="ef862-118">For more information:</span></span>  
  
-   [<span data-ttu-id="ef862-119">Použití struktur</span><span class="sxs-lookup"><span data-stu-id="ef862-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="ef862-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ef862-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="ef862-121">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="ef862-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="ef862-122">Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na třídu metodě</span><span class="sxs-lookup"><span data-stu-id="ef862-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="ef862-123">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="ef862-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef862-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef862-124">See Also</span></span>  
 [<span data-ttu-id="ef862-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ef862-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ef862-126">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="ef862-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="ef862-127">Třídy</span><span class="sxs-lookup"><span data-stu-id="ef862-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
