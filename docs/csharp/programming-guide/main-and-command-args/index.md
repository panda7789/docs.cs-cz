---
title: Main () a argumenty příkazového řádku – C# Průvodce programováním
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
ms.openlocfilehash: 0571ec6dbc42f103ec922a6b2b13a52510640a78
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700598"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="ce012-102">Argumenty Main () a příkazového řádku (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ce012-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="ce012-103">Metoda `Main` je vstupním bodem C# aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce012-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="ce012-104">(Knihovny a služby nevyžadují jako vstupní bod metodu `Main`.) Po spuštění aplikace je metoda `Main` první vyvolanou metodou.</span><span class="sxs-lookup"><span data-stu-id="ce012-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="ce012-105">V C# programu může být pouze jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="ce012-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="ce012-106">Pokud máte více než jednu třídu, která má metodu `Main`, je nutné zkompilovat program pomocí možnosti kompilátoru **/Main** a určit, která `Main` metoda, která má být použita jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="ce012-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="ce012-107">Další informace naleznete v tématu [-Main (C# možnosti kompilátoru)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ce012-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="ce012-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="ce012-108">Overview</span></span>

- <span data-ttu-id="ce012-109">Metoda `Main` je vstupním bodem spustitelného programu; je to místo, kde se spouští a končí ovládací prvek programu.</span><span class="sxs-lookup"><span data-stu-id="ce012-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="ce012-110">`Main` je deklarován uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="ce012-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="ce012-111">`Main` musí být [statické](../../language-reference/keywords/static.md) a nemusí být [veřejné](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="ce012-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="ce012-112">(V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.</span><span class="sxs-lookup"><span data-stu-id="ce012-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="ce012-113">`Main` může mít `void`, `int`nebo, počínaje C# 7,1, `Task`nebo `Task<int>` návratový typ.</span><span class="sxs-lookup"><span data-stu-id="ce012-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="ce012-114">Pokud a pouze pokud `Main` vrátí `Task` nebo `Task<int>`, deklarace `Main` může obsahovat modifikátor [`async`](../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="ce012-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ce012-115">Všimněte si, že to konkrétně vylučuje metodu `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="ce012-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="ce012-116">Metodu `Main` lze deklarovat s nebo bez `string[]` parametr, který obsahuje argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ce012-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="ce012-117">Při použití sady Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít metodu <xref:System.Environment.GetCommandLineArgs> k získání [argumentů příkazového řádku](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="ce012-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="ce012-118">Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem.</span><span class="sxs-lookup"><span data-stu-id="ce012-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="ce012-119">Na rozdíl od jazyka C++C a není název programu považován za první argument příkazového řádku v poli `args`, ale je prvním prvkem <xref:System.Environment.GetCommandLineArgs> metody.</span><span class="sxs-lookup"><span data-stu-id="ce012-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="ce012-120">Následuje seznam platných signatur `Main`:</span><span class="sxs-lookup"><span data-stu-id="ce012-120">The following is a list of valid `Main` signatures:</span></span>

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

<span data-ttu-id="ce012-121">Přidání `async` a `Task`, `Task<int>` návratové typy, zjednodušuje kód programu, když aplikace konzoly potřebují spustit a `await` asynchronní operace v `Main`.</span><span class="sxs-lookup"><span data-stu-id="ce012-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ce012-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce012-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ce012-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce012-123">See also</span></span>

- [<span data-ttu-id="ce012-124">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="ce012-124">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="ce012-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ce012-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ce012-126">Metody</span><span class="sxs-lookup"><span data-stu-id="ce012-126">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="ce012-127">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ce012-127">Inside a C# Program</span></span>](../inside-a-program/index.md)
