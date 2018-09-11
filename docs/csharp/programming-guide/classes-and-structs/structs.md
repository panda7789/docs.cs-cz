---
title: Struktury (Průvodce programováním v C#)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 27d4b0d7edf1b5e89e84ac1df5783d68ebb4efe0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259481"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="4d8b7-102">Struktury (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4d8b7-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="4d8b7-103">Struktury jsou definované pomocí [struktura](../../language-reference/keywords/struct.md) – klíčové slovo, například:</span><span class="sxs-lookup"><span data-stu-id="4d8b7-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="4d8b7-104">Struktury sdílet většina podle stejné syntaxe jako třídy.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="4d8b7-105">Název struktury musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="4d8b7-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="4d8b7-106">Struktury jsou omezeny více než třídy následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="4d8b7-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="4d8b7-107">V deklaraci struktury pole nelze inicializovat, jestliže nejsou deklarovány jako const nebo statické.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="4d8b7-108">Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="4d8b7-109">Struktury se zkopírují na přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-109">Structs are copied on assignment.</span></span> <span data-ttu-id="4d8b7-110">Když je struktura přiřazena nové proměnné, se data kopírují a jakékoli změny nová kopie nezmění data pro původní kopírování.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="4d8b7-111">To je důležité pamatovat při práci s kolekcemi hodnoty typy, jako `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="4d8b7-112">Struktury jsou typy hodnot, na rozdíl od tříd, které jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="4d8b7-113">Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="4d8b7-114">Struktury můžete deklarovat konstruktory, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="4d8b7-115">Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="4d8b7-116">Všechny struktury dědí přímo z <xref:System.ValueType>, který dědí z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="4d8b7-117">Struktury můžou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-117">A struct can implement interfaces.</span></span>  
- <span data-ttu-id="4d8b7-118">Struktura může sloužit jako typ připouštějící hodnotu Null a je možné přiřadit hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4d8b7-118">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4d8b7-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4d8b7-119">Related sections</span></span>  

<span data-ttu-id="4d8b7-120">Další informace:</span><span class="sxs-lookup"><span data-stu-id="4d8b7-120">For more information:</span></span>  
  
- [<span data-ttu-id="4d8b7-121">Použití struktur</span><span class="sxs-lookup"><span data-stu-id="4d8b7-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="4d8b7-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="4d8b7-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="4d8b7-123">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="4d8b7-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="4d8b7-124">Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na třídu metodě</span><span class="sxs-lookup"><span data-stu-id="4d8b7-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="4d8b7-125">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="4d8b7-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="4d8b7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d8b7-126">See also</span></span>

- [<span data-ttu-id="4d8b7-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4d8b7-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4d8b7-128">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="4d8b7-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="4d8b7-129">Třídy</span><span class="sxs-lookup"><span data-stu-id="4d8b7-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="4d8b7-130">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="4d8b7-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
