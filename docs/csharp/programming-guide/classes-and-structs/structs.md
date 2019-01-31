---
title: Struktury – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 609169d4624802f679f9661b7aa0596403cc48e7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261617"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="034da-102">Struktury (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="034da-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="034da-103">Struktury jsou definované pomocí [struktura](../../language-reference/keywords/struct.md) – klíčové slovo, například:</span><span class="sxs-lookup"><span data-stu-id="034da-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="034da-104">Struktury sdílet většina podle stejné syntaxe jako třídy.</span><span class="sxs-lookup"><span data-stu-id="034da-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="034da-105">Název struktury musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="034da-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="034da-106">Struktury jsou omezeny více než třídy následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="034da-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="034da-107">V deklaraci struktury pole nelze inicializovat, jestliže nejsou deklarovány jako const nebo statické.</span><span class="sxs-lookup"><span data-stu-id="034da-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="034da-108">Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="034da-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="034da-109">Struktury se zkopírují na přiřazení.</span><span class="sxs-lookup"><span data-stu-id="034da-109">Structs are copied on assignment.</span></span> <span data-ttu-id="034da-110">Když je struktura přiřazena nové proměnné, se data kopírují a jakékoli změny nová kopie nezmění data pro původní kopírování.</span><span class="sxs-lookup"><span data-stu-id="034da-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="034da-111">To je důležité pamatovat při práci s kolekcemi hodnoty typy, jako `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="034da-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="034da-112">Struktury jsou typy hodnot, na rozdíl od tříd, které jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="034da-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="034da-113">Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="034da-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="034da-114">Struktury můžete deklarovat konstruktory, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="034da-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="034da-115">Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy.</span><span class="sxs-lookup"><span data-stu-id="034da-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="034da-116">Všechny struktury dědí přímo z <xref:System.ValueType>, který dědí z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="034da-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="034da-117">Struktury můžou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="034da-117">A struct can implement interfaces.</span></span> 
- <span data-ttu-id="034da-118">Struktura nemůže být `null`, a proměnnou struktury nelze přiřadit `null` Pokud je proměnná deklarována jako typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="034da-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="034da-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="034da-119">Related sections</span></span>  

<span data-ttu-id="034da-120">Další informace:</span><span class="sxs-lookup"><span data-stu-id="034da-120">For more information:</span></span>  
  
- [<span data-ttu-id="034da-121">Použití struktur</span><span class="sxs-lookup"><span data-stu-id="034da-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="034da-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="034da-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="034da-123">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="034da-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="034da-124">Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na metodu třídu</span><span class="sxs-lookup"><span data-stu-id="034da-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="034da-125">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="034da-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="034da-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="034da-126">See also</span></span>

- [<span data-ttu-id="034da-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="034da-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="034da-128">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="034da-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="034da-129">Třídy</span><span class="sxs-lookup"><span data-stu-id="034da-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="034da-130">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="034da-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
