---
title: Main () a argumenty příkazového řádku – Průvodce programováním v C#
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
ms.openlocfilehash: 190216b01ea416aedbca270a6d7a5acbf0c2e797
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200116"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="f41a4-102">Argumenty Main () a příkazového řádku (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f41a4-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="f41a4-103">`Main` Metoda je vstupním bodem aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="f41a4-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="f41a4-104">(Knihovny a služby nevyžadují `Main` metodu jako vstupní bod.) Po spuštění aplikace je `Main` metoda první vyvolanou metodou.</span><span class="sxs-lookup"><span data-stu-id="f41a4-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="f41a4-105">V programu v jazyce C# může být pouze jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="f41a4-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="f41a4-106">Pokud máte více než jednu třídu, která má `Main` metodu, je nutné zkompilovat program pomocí možnosti kompilátoru **/Main** a určit, kterou `Main` metodu použít jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="f41a4-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="f41a4-107">Další informace naleznete v části [-Main (možnosti kompilátoru C#)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f41a4-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="f41a4-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="f41a4-108">Overview</span></span>

- <span data-ttu-id="f41a4-109">`Main` Metoda je vstupním bodem spustitelného programu; je to místo, kde se spouští a končí ovládací prvek programu.</span><span class="sxs-lookup"><span data-stu-id="f41a4-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="f41a4-110">`Main`je deklarován uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="f41a4-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="f41a4-111">`Main`musí být [statický](../../language-reference/keywords/static.md) a nemusí být [veřejný](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="f41a4-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="f41a4-112">(V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.</span><span class="sxs-lookup"><span data-stu-id="f41a4-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="f41a4-113">`Main``void`může mít buď `int`, nebo, počínaje jazykem C# 7,1, `Task`nebo `Task<int>` návratový typ.</span><span class="sxs-lookup"><span data-stu-id="f41a4-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="f41a4-114">Pokud a pouze pokud `Main` vrátí `Task` nebo `Task<int>`, deklaraci `Main` může obsahovat [`async`](../../language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="f41a4-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="f41a4-115">Všimněte si, že to konkrétně vylučuje `async void Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="f41a4-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="f41a4-116">`Main` Metoda může být deklarována s `string[]` parametrem, který obsahuje argumenty příkazového řádku nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="f41a4-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="f41a4-117">Při použití sady <xref:System.Environment.GetCommandLineArgs> Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít metodu k získání [argumentů příkazového řádku](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="f41a4-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="f41a4-118">Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem.</span><span class="sxs-lookup"><span data-stu-id="f41a4-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="f41a4-119">Na rozdíl od jazyka C a C++ se název programu nepovažuje za první argument příkazového řádku v `args` poli, ale je prvním prvkem <xref:System.Environment.GetCommandLineArgs> metody.</span><span class="sxs-lookup"><span data-stu-id="f41a4-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="f41a4-120">Následuje seznam platných `Main` podpisů:</span><span class="sxs-lookup"><span data-stu-id="f41a4-120">The following is a list of valid `Main` signatures:</span></span>

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

<span data-ttu-id="f41a4-121">Předchozí příklady používají modifikátor veřejného přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="f41a4-121">The preceding examples all use the public accessor modifier.</span></span> <span data-ttu-id="f41a4-122">To je typické, ale není nutné.</span><span class="sxs-lookup"><span data-stu-id="f41a4-122">That is typical, but not required.</span></span>

<span data-ttu-id="f41a4-123">Sčítání `async` `Task`a `Task<int>` návratové typy zjednodušují kód programu, když aplikace konzoly potřebují spustit a `await` asynchronní operace v. `Main`</span><span class="sxs-lookup"><span data-stu-id="f41a4-123">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f41a4-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f41a4-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f41a4-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="f41a4-125">See also</span></span>

- [<span data-ttu-id="f41a4-126">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="f41a4-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="f41a4-127">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f41a4-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f41a4-128">Metody</span><span class="sxs-lookup"><span data-stu-id="f41a4-128">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="f41a4-129">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f41a4-129">Inside a C# Program</span></span>](../inside-a-program/index.md)
