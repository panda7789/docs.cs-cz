---
title: Main () a argumenty příkazového řádku – Průvodce programováním v C#
description: Přečtěte si o Main () a argumentech příkazového řádku. Metoda Main je vstupním bodem spustitelného programu.
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
ms.openlocfilehash: 95ec9d3dfebe4721d4b1822939f925aa37b9e9c4
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382071"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="4623b-104">Argumenty Main () a příkazového řádku (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4623b-104">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="4623b-105">`Main`Metoda je vstupním bodem aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="4623b-105">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="4623b-106">(Knihovny a služby nevyžadují `Main` metodu jako vstupní bod.) Po spuštění aplikace `Main` je metoda první vyvolanou metodou.</span><span class="sxs-lookup"><span data-stu-id="4623b-106">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

<span data-ttu-id="4623b-107">V programu v jazyce C# může být pouze jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="4623b-107">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="4623b-108">Pokud máte více než jednu třídu, která má `Main` metodu, je nutné zkompilovat program s `-main` možností kompilátoru pro určení, kterou `Main` metodu použít jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="4623b-108">If you have more than one class that has a `Main` method, you must compile your program with the `-main` compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="4623b-109">Další informace naleznete v části [-Main (možnosti kompilátoru C#)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4623b-109">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="4623b-110">Přehled</span><span class="sxs-lookup"><span data-stu-id="4623b-110">Overview</span></span>

- <span data-ttu-id="4623b-111">`Main`Metoda je vstupním bodem spustitelného programu; je místo, kde se ovládací prvek program spouští a končí.</span><span class="sxs-lookup"><span data-stu-id="4623b-111">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="4623b-112">`Main`je deklarován uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="4623b-112">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="4623b-113">`Main`musí být [statický](../../language-reference/keywords/static.md) a nemusí být [veřejný](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="4623b-113">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="4623b-114">(V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.</span><span class="sxs-lookup"><span data-stu-id="4623b-114">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="4623b-115">`Main`může mít buď `void` , `int` nebo, počínaje jazykem C# 7,1, `Task` nebo `Task<int>` návratový typ.</span><span class="sxs-lookup"><span data-stu-id="4623b-115">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="4623b-116">Pokud a pouze pokud `Main` vrátí `Task` nebo `Task<int>` , deklaraci `Main` může obsahovat [`async`](../../language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="4623b-116">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="4623b-117">Všimněte si, že to konkrétně vylučuje `async void Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="4623b-117">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="4623b-118">`Main`Metoda může být deklarována s `string[]` parametrem, který obsahuje argumenty příkazového řádku nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="4623b-118">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="4623b-119">Při použití sady Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít <xref:System.Environment.GetCommandLineArgs> metodu k získání [argumentů příkazového řádku](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4623b-119">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="4623b-120">Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem.</span><span class="sxs-lookup"><span data-stu-id="4623b-120">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="4623b-121">Na rozdíl od jazyka C a C++ se název programu nepovažuje za první argument příkazového řádku v `args` poli, ale je prvním prvkem <xref:System.Environment.GetCommandLineArgs> metody.</span><span class="sxs-lookup"><span data-stu-id="4623b-121">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="4623b-122">Následuje seznam platných `Main` podpisů:</span><span class="sxs-lookup"><span data-stu-id="4623b-122">The following is a list of valid `Main` signatures:</span></span>

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

<span data-ttu-id="4623b-123">Předchozí příklady používají modifikátor veřejného přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="4623b-123">The preceding examples all use the public accessor modifier.</span></span> <span data-ttu-id="4623b-124">To je typické, ale není nutné.</span><span class="sxs-lookup"><span data-stu-id="4623b-124">That is typical, but not required.</span></span>

<span data-ttu-id="4623b-125">Sčítání `async` a `Task` `Task<int>` návratové typy zjednodušují kód programu, když aplikace konzoly potřebují spustit a `await` asynchronní operace v `Main` .</span><span class="sxs-lookup"><span data-stu-id="4623b-125">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4623b-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4623b-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4623b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4623b-127">See also</span></span>

- [<span data-ttu-id="4623b-128">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="4623b-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="4623b-129">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4623b-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4623b-130">Metody</span><span class="sxs-lookup"><span data-stu-id="4623b-130">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="4623b-131">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4623b-131">Inside a C# Program</span></span>](../inside-a-program/index.md)
