---
title: Main() a argumenty příkazového řádku - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: f1cbbc6081c0e2f3e29d49f413e00c7346ea7e60
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968995"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="87ead-102">Main() a argumenty příkazového řádku (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="87ead-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="87ead-103">`Main` Metoda je vstupní bod aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="87ead-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="87ead-104">(Knihoven a služeb nevyžadují `Main` metoda jako vstupní bod.) Při spuštění aplikace `Main` metody je první metoda, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="87ead-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="87ead-105">Může existovat pouze jeden vstupní bod v programu v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="87ead-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="87ead-106">Pokud máte více než jednu třídu, která má `Main` metodu, musí zkompilujete program se **/main** – možnost kompilátoru k určení `Main` metody pro použití jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="87ead-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="87ead-107">Další informace najdete v tématu [/Main (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="87ead-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="87ead-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="87ead-108">Overview</span></span>

- <span data-ttu-id="87ead-109">`Main` Metoda je vstupním bodem spustitelný program; je ve kterém ovládací prvek programu začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="87ead-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="87ead-110">`Main` je deklarované uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="87ead-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="87ead-111">`Main` musí být [statické](../../../csharp/language-reference/keywords/static.md) a nemusí být [veřejné](../../../csharp/language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="87ead-111">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="87ead-112">(V předchozím příkladu přijme výchozí přístup [privátní](../../../csharp/language-reference/keywords/private.md).) Nadřazené třídy nebo struktury se musí být statické.</span><span class="sxs-lookup"><span data-stu-id="87ead-112">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="87ead-113">`Main` mohou mít buď `void`, `int`, nebo od verze C# 7.1, `Task`, nebo `Task<int>` návratového typu.</span><span class="sxs-lookup"><span data-stu-id="87ead-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="87ead-114">Pouze v případě `Main` vrátí `Task` nebo `Task<int>`, deklarace `Main` mohou zahrnovat [ `async` ](../../language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="87ead-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="87ead-115">Všimněte si, že to vylučuje `async void Main` metody.</span><span class="sxs-lookup"><span data-stu-id="87ead-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="87ead-116">`Main` Metody mohou být deklarovány s nebo bez něj `string[]` parametr, který obsahuje argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="87ead-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="87ead-117">Při používání sady Visual Studio k vytváření aplikací pro Windows, které můžete ručně přidejte parametr jinak použít <xref:System.Environment> třídy získat argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="87ead-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="87ead-118">Parametry se načtou jako argumenty příkazového řádku nulový index.</span><span class="sxs-lookup"><span data-stu-id="87ead-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="87ead-119">Na rozdíl od jazyka C a C++ název aplikace není považován za první argument příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="87ead-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="87ead-120">Přidání `async` a `Task`, `Task<int>` vrátí typy zjednodušuje kód programu při konzolové aplikace, musí spustit a `await` asynchronních operací v `Main`.</span><span class="sxs-lookup"><span data-stu-id="87ead-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="87ead-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="87ead-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="87ead-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87ead-122">See also</span></span>

- [<span data-ttu-id="87ead-123">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="87ead-123">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="87ead-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="87ead-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="87ead-125">Metody</span><span class="sxs-lookup"><span data-stu-id="87ead-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="87ead-126">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="87ead-126">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)
