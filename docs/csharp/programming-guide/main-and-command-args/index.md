---
title: Hlavní() argumenty a argumenty příkazového řádku - Průvodce programováním jazyka C#
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75700598"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="f7e65-102">Main() a argumenty příkazového řádku (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f7e65-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="f7e65-103">Metoda `Main` je vstupním bodem aplikace Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f7e65-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="f7e65-104">(Knihovny a služby `Main` nevyžadují metodu jako vstupní bod.) Při spuštění aplikace `Main` metoda je první metoda, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f7e65-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="f7e65-105">V programu Jazyka C# může být pouze jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="f7e65-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="f7e65-106">Pokud máte více než jednu `Main` třídu, která má metodu, musíte zkompilovat program s **parametrem /main** kompilátoru a určit, kterou `Main` metodu použít jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="f7e65-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="f7e65-107">Další informace naleznete [v tématu -main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f7e65-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="f7e65-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="f7e65-108">Overview</span></span>

- <span data-ttu-id="f7e65-109">Metoda `Main` je vstupním bodem spustitelného programu; to je místo, kde se spustí a končí ovládací prvek programu.</span><span class="sxs-lookup"><span data-stu-id="f7e65-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="f7e65-110">`Main`je deklarována uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="f7e65-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="f7e65-111">`Main`musí být [statická](../../language-reference/keywords/static.md) a nemusí být [veřejná](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="f7e65-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="f7e65-112">(V předchozím příkladu obdrží výchozí přístup [private](../../language-reference/keywords/private.md).) Ohraničující třída nebo struktura nemusí být statická.</span><span class="sxs-lookup"><span data-stu-id="f7e65-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="f7e65-113">`Main`může mít `void`, `int`, nebo počínaje C# 7.1 , `Task`nebo `Task<int>` návratový typ.</span><span class="sxs-lookup"><span data-stu-id="f7e65-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="f7e65-114">If a `Main` only `Task` if `Task<int>`returns a `Main` or [`async`](../../language-reference/keywords/async.md) , deklarace může obsahovat modifikátor.</span><span class="sxs-lookup"><span data-stu-id="f7e65-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="f7e65-115">Všimněte si, že `async void Main` to výslovně vylučuje metodu.</span><span class="sxs-lookup"><span data-stu-id="f7e65-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="f7e65-116">Metoda `Main` může být deklarována s parametrem `string[]` nebo bez něj, který obsahuje argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f7e65-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="f7e65-117">Při vytváření aplikací systému Windows pomocí sady Visual Studio můžete <xref:System.Environment.GetCommandLineArgs> parametr přidat ručně nebo použít metodu k získání [argumentů příkazového řádku](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="f7e65-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="f7e65-118">Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem.</span><span class="sxs-lookup"><span data-stu-id="f7e65-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="f7e65-119">Na rozdíl od C a C++ název programu není považován za první `args` argument příkazového řádku v <xref:System.Environment.GetCommandLineArgs> poli, ale je prvním prvkem metody.</span><span class="sxs-lookup"><span data-stu-id="f7e65-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="f7e65-120">Následuje seznam platných `Main` podpisů:</span><span class="sxs-lookup"><span data-stu-id="f7e65-120">The following is a list of valid `Main` signatures:</span></span>

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

<span data-ttu-id="f7e65-121">Přidání a `async` `Task`návratové `Task<int>` typy zjednodušuje programový kód, `await` když konzolové `Main`aplikace potřebují spustit a asynchronní operace v .</span><span class="sxs-lookup"><span data-stu-id="f7e65-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f7e65-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f7e65-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f7e65-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7e65-123">See also</span></span>

- [<span data-ttu-id="f7e65-124">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="f7e65-124">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="f7e65-125">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f7e65-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f7e65-126">Metody</span><span class="sxs-lookup"><span data-stu-id="f7e65-126">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="f7e65-127">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f7e65-127">Inside a C# Program</span></span>](../inside-a-program/index.md)
