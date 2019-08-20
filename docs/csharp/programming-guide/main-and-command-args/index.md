---
title: Main () a argumenty příkazového řádku – C# Průvodce programováním
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
ms.openlocfilehash: db4464cdd3d98103bbc61b824081b59cb1e01cb9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588914"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="00476-102">Argumenty Main () a příkazového řádku (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="00476-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="00476-103">Metoda je vstupním bodem C# aplikace. `Main`</span><span class="sxs-lookup"><span data-stu-id="00476-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="00476-104">(Knihovny a služby nevyžadují `Main` metodu jako vstupní bod.) Po spuštění `Main` aplikace je metoda první vyvolanou metodou.</span><span class="sxs-lookup"><span data-stu-id="00476-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="00476-105">V C# programu může být pouze jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="00476-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="00476-106">Pokud máte více než jednu třídu, která má `Main` metodu, je nutné zkompilovat program pomocí možnosti kompilátoru **/Main** a určit, kterou `Main` metodu použít jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="00476-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="00476-107">Další informace naleznete v tématu [/Main (C# možnosti kompilátoru)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="00476-107">For more information, see [/main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="00476-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="00476-108">Overview</span></span>

- <span data-ttu-id="00476-109">`Main` Metoda je vstupním bodem spustitelného programu; je místo, kde se ovládací prvek program spouští a končí.</span><span class="sxs-lookup"><span data-stu-id="00476-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="00476-110">`Main`je deklarován uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="00476-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="00476-111">`Main`musí být [statický](../../language-reference/keywords/static.md) a nemusí být [veřejný](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="00476-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="00476-112">(V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.</span><span class="sxs-lookup"><span data-stu-id="00476-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="00476-113">`Main``void`může mít C# `Task` `Task<int>` buď,, nebo, počínaje 7,1, nebo návratovým typem. `int`</span><span class="sxs-lookup"><span data-stu-id="00476-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="00476-114">Pokud a pouze pokud `Main` `Task` vrátí `Task<int>` [nebo,`async`](../../language-reference/keywords/async.md) deklaraci můžeobsahovatmodifikátor.`Main`</span><span class="sxs-lookup"><span data-stu-id="00476-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="00476-115">Všimněte si, že to konkrétně vylučuje `async void Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="00476-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="00476-116">Metoda může být deklarována s `string[]` parametrem, který obsahuje argumenty příkazového řádku nebo bez něj. `Main`</span><span class="sxs-lookup"><span data-stu-id="00476-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="00476-117">Při použití sady <xref:System.Environment> Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít třídu k získání argumentů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="00476-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="00476-118">Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem.</span><span class="sxs-lookup"><span data-stu-id="00476-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="00476-119">Na rozdíl od jazyka C++C a se název programu nepovažuje za první argument příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="00476-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="00476-120">`async` Sčítání `Task` `Main` `await` a návratové typy zjednodušují kód programu, když aplikace konzoly potřebují spustit a asynchronní operace v. `Task<int>`</span><span class="sxs-lookup"><span data-stu-id="00476-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="00476-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="00476-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="00476-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00476-122">See also</span></span>

- [<span data-ttu-id="00476-123">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="00476-123">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="00476-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="00476-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="00476-125">Metody</span><span class="sxs-lookup"><span data-stu-id="00476-125">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="00476-126">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="00476-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
