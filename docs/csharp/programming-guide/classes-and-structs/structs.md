---
title: Struktury (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: abe39b336aa8e9aa7a8a8ee96ed6848804644ddd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518700"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="67138-102">Struktury (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="67138-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="67138-103">Struktury jsou definované pomocí [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo, například:</span><span class="sxs-lookup"><span data-stu-id="67138-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="67138-104">Většinu podle stejné syntaxe jako třídy, struktury sdílet, ačkoli struktury jsou omezeny více než třídy:</span><span class="sxs-lookup"><span data-stu-id="67138-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="67138-105">V deklaraci struktury pole nelze inicializovat, jestliže nejsou deklarovány jako const nebo statické.</span><span class="sxs-lookup"><span data-stu-id="67138-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="67138-106">Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="67138-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="67138-107">Struktury se zkopírují na přiřazení.</span><span class="sxs-lookup"><span data-stu-id="67138-107">Structs are copied on assignment.</span></span> <span data-ttu-id="67138-108">Když je struktura přiřazena nové proměnné, se data kopírují a jakékoli změny nová kopie nezmění data pro původní kopírování.</span><span class="sxs-lookup"><span data-stu-id="67138-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="67138-109">To je důležité pamatovat při práci s kolekcemi typů hodnot, jako je například slovníku\<řetězec, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="67138-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="67138-110">Struktury jsou typy hodnot a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="67138-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="67138-111">Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="67138-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="67138-112">Struktury můžete deklarovat konstruktory, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="67138-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="67138-113">Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy.</span><span class="sxs-lookup"><span data-stu-id="67138-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="67138-114">Všechny struktury dědí přímo z `System.ValueType`, který dědí z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="67138-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="67138-115">Struktury můžou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67138-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="67138-116">Struktura může sloužit jako typ připouštějící hodnotu Null a je možné přiřadit hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="67138-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="67138-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="67138-117">Related Sections</span></span>  
 <span data-ttu-id="67138-118">Další informace:</span><span class="sxs-lookup"><span data-stu-id="67138-118">For more information:</span></span>  
  
-   [<span data-ttu-id="67138-119">Použití struktur</span><span class="sxs-lookup"><span data-stu-id="67138-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="67138-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="67138-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="67138-121">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="67138-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="67138-122">Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na třídu metodě</span><span class="sxs-lookup"><span data-stu-id="67138-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="67138-123">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="67138-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="67138-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="67138-124">See Also</span></span>

- [<span data-ttu-id="67138-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="67138-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="67138-126">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="67138-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="67138-127">Třídy</span><span class="sxs-lookup"><span data-stu-id="67138-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
