---
title: Struktury – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 35b39da0b15c41b7b2c7a6567bea5dca3fb430e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970322"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="57399-102">Struktury (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="57399-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="57399-103">Struktury jsou definované pomocí klíčového slova [struct](../../language-reference/keywords/struct.md) , například:</span><span class="sxs-lookup"><span data-stu-id="57399-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="57399-104">Struktury sdílejí většinu stejné syntaxe jako třídy.</span><span class="sxs-lookup"><span data-stu-id="57399-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="57399-105">Název struktury musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="57399-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="57399-106">Struktury jsou více omezené než třídy následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="57399-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="57399-107">V rámci deklarace struktury nelze pole inicializovat, pokud nejsou deklarována jako const nebo static.</span><span class="sxs-lookup"><span data-stu-id="57399-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="57399-108">Struktura nemůže deklarovat konstruktor bez parametrů (konstruktor bez parametrů) nebo finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="57399-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="57399-109">Struktury se zkopírují při přiřazení.</span><span class="sxs-lookup"><span data-stu-id="57399-109">Structs are copied on assignment.</span></span> <span data-ttu-id="57399-110">Když je struktura přiřazena nové proměnné, zkopírují se všechna data a jakákoli změna nové kopie nemění data původní kopie.</span><span class="sxs-lookup"><span data-stu-id="57399-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="57399-111">To je důležité pamatovat při práci s kolekcemi typů hodnot, jako je `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="57399-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="57399-112">Struktury jsou typy hodnot, na rozdíl od tříd, které jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="57399-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="57399-113">Na rozdíl od tříd lze vytvořit instanci struktur bez použití operátoru `new`.</span><span class="sxs-lookup"><span data-stu-id="57399-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="57399-114">Struktury mohou deklarovat konstruktory, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="57399-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="57399-115">Struktura nemůže dědit z jiné struktury nebo třídy a nemůže být základem třídy.</span><span class="sxs-lookup"><span data-stu-id="57399-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="57399-116">Všechny struktury dědí přímo z <xref:System.ValueType>, které dědí z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="57399-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="57399-117">Struktura může implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="57399-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="57399-118">Strukturu nelze `null`a proměnnou struktury nelze přiřadit `null`, pokud je proměnná deklarována jako typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="57399-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable value type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="57399-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57399-119">See also</span></span>

- [<span data-ttu-id="57399-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="57399-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="57399-121">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="57399-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="57399-122">Třídy</span><span class="sxs-lookup"><span data-stu-id="57399-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="57399-123">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="57399-123">Nullable value types</span></span>](../../language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="57399-124">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="57399-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="57399-125">Použití struktur</span><span class="sxs-lookup"><span data-stu-id="57399-125">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="57399-126">Jak zjistit rozdíl mezi předáním struktury a předáním odkazu na třídu metodě</span><span class="sxs-lookup"><span data-stu-id="57399-126">How to know the difference between passing a struct and passing a class reference to a method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
