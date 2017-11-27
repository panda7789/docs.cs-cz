---
title: "Main() a argumenty příkazového řádku (C# Průvodce programováním)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab0b93a867ecf252bffd529d284ef9ddcc9163ba
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="03a3e-102">Main() a argumenty příkazového řádku (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="03a3e-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="03a3e-103">`Main` Metoda je vstupní bod aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="03a3e-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="03a3e-104">(Knihovny a služby nevyžadují `Main` metoda jako vstupní bod.) Při spuštění aplikace `Main` je první metody, která je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="03a3e-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="03a3e-105">Může existovat pouze jeden vstupní bod v programu v C#.</span><span class="sxs-lookup"><span data-stu-id="03a3e-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="03a3e-106">Pokud máte více než jednu třídu, která má `Main` metoda, je nutné kompilovat s vaším programem **/main** – možnost kompilátoru k určení, které `Main` metoda se má použít jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="03a3e-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="03a3e-107">Další informace najdete v tématu [/Main (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="03a3e-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a><span data-ttu-id="03a3e-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="03a3e-108">Overview</span></span>

- <span data-ttu-id="03a3e-109">`Main` Metoda je vstupní bod spustitelný program, je kde ovládacího prvku programu spuštění a ukončení.</span><span class="sxs-lookup"><span data-stu-id="03a3e-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="03a3e-110">`Main`je deklarovaná ve třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="03a3e-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="03a3e-111">`Main`musí být [statické](../../../csharp/language-reference/keywords/static.md) a nemusí být [veřejné](../../../csharp/language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="03a3e-111">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="03a3e-112">(V předchozím příkladu, obdrží přístup výchozí [privátní](../../../csharp/language-reference/keywords/private.md).) Nadřazených třídě nebo struktuře nemusí být statická.</span><span class="sxs-lookup"><span data-stu-id="03a3e-112">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="03a3e-113">`Main`mohou mít buď `void`, `int`, nebo, počínaje C# 7.1, `Task`, nebo `Task<int>` návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="03a3e-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="03a3e-114">Jenom v případě `Main` vrátí `Task` nebo `Task<int>`, deklaraci `Main` může zahrnovat [ `async` ](../../language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="03a3e-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="03a3e-115">Všimněte si, že konkrétně vyloučeny `async void Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="03a3e-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="03a3e-116">`Main` Metoda lze deklarovat, bez ohledu `string[]` parametr, který obsahuje argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03a3e-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="03a3e-117">Při použití [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] k vytvoření aplikace systému Windows, můžete můžete ručně přidat parametr jinak použít <xref:System.Environment> třída získat argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03a3e-117">When using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="03a3e-118">Parametry jsou přečíst jako nové indexované argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03a3e-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="03a3e-119">Na rozdíl od C a C++ nepovažuje se název programu jako první argument příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03a3e-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="03a3e-120">Přidání `async` a `Task`, `Task<int>` vrátit typy zjednodušuje kódu programu, když je potřeba spustit konzolové aplikace a `await` asynchronních operací v `Main`.</span><span class="sxs-lookup"><span data-stu-id="03a3e-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03a3e-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03a3e-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="03a3e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="03a3e-122">See also</span></span>
<span data-ttu-id="03a3e-123">[Sestavení příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[Průvodce programováním v C#](../../../csharp/programming-guide/index.md)
[metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
[uvnitř programu v C#](../../../csharp/programming-guide/inside-a-program/index.md)</span><span class="sxs-lookup"><span data-stu-id="03a3e-123">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[C# Programming Guide](../../../csharp/programming-guide/index.md)
[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md)
[Inside a C# Program](../../../csharp/programming-guide/inside-a-program/index.md)</span></span>
