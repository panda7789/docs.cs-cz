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
ms.openlocfilehash: 5de7e565560928b1867ba96c8937fd354c276806
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774121"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="4f61a-102">Argumenty Main () a příkazového řádku (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4f61a-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="4f61a-103">Metoda `Main` je vstupním bodem C# aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f61a-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="4f61a-104">(Knihovny a služby nevyžadují jako vstupní bod metodu `Main`.) Po spuštění aplikace je metoda `Main` první vyvolanou metodou.</span><span class="sxs-lookup"><span data-stu-id="4f61a-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="4f61a-105">V C# programu může být pouze jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="4f61a-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="4f61a-106">Pokud máte více než jednu třídu, která má metodu `Main`, je nutné zkompilovat program pomocí možnosti kompilátoru **/Main** a určit, která `Main` metoda, která má být použita jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="4f61a-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="4f61a-107">Další informace naleznete v tématu [-Main (C# možnosti kompilátoru)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4f61a-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="4f61a-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="4f61a-108">Overview</span></span>

- <span data-ttu-id="4f61a-109">Metoda `Main` je vstupním bodem spustitelného programu; je to místo, kde se spouští a končí ovládací prvek programu.</span><span class="sxs-lookup"><span data-stu-id="4f61a-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="4f61a-110">`Main` je deklarován uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="4f61a-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="4f61a-111">`Main` musí být [statické](../../language-reference/keywords/static.md) a nemusí být [veřejné](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="4f61a-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="4f61a-112">(V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.</span><span class="sxs-lookup"><span data-stu-id="4f61a-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="4f61a-113">`Main` může mít `void`, `int` nebo, počínaje C# 7,1, `Task` nebo `Task<int>` návratový typ.</span><span class="sxs-lookup"><span data-stu-id="4f61a-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="4f61a-114">Pokud a pouze pokud `Main` vrátí `Task` nebo `Task<int>`, deklarace `Main` může obsahovat modifikátor [`async`](../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="4f61a-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="4f61a-115">Všimněte si, že to konkrétně vylučuje metodu `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="4f61a-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="4f61a-116">Metodu `Main` lze deklarovat s nebo bez `string[]` parametr, který obsahuje argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4f61a-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="4f61a-117">Při použití sady Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít metodu <xref:System.Environment.GetCommandLineArgs> k získání [argumentů příkazového řádku](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4f61a-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="4f61a-118">Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem.</span><span class="sxs-lookup"><span data-stu-id="4f61a-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="4f61a-119">Na rozdíl od jazyka C++C a není název programu považován za první argument příkazového řádku v poli `args`, ale je prvním prvkem <xref:System.Environment.GetCommandLineArgs> metody.</span><span class="sxs-lookup"><span data-stu-id="4f61a-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="4f61a-120">Přidání `async` a `Task`, `Task<int>` návratové typy, zjednodušuje kód programu, když aplikace konzoly potřebují spustit a `await` asynchronní operace v `Main`.</span><span class="sxs-lookup"><span data-stu-id="4f61a-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4f61a-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4f61a-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4f61a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f61a-122">See also</span></span>

- [<span data-ttu-id="4f61a-123">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="4f61a-123">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="4f61a-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4f61a-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4f61a-125">Metody</span><span class="sxs-lookup"><span data-stu-id="4f61a-125">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="4f61a-126">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4f61a-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
