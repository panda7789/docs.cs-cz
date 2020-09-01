---
description: extern – modifikátor – Referenční dokumentace jazyka C#
title: extern – modifikátor – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 25eb5e6642d8b608bedcb4e9adadde4d84c2bae9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138966"
---
# <a name="extern-c-reference"></a><span data-ttu-id="1898f-103">extern (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1898f-103">extern (C# Reference)</span></span>

<span data-ttu-id="1898f-104">`extern`Modifikátor slouží k deklaraci metody, která je implementována externě.</span><span class="sxs-lookup"><span data-stu-id="1898f-104">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="1898f-105">Běžné použití `extern` modifikátoru je s `DllImport` atributem, pokud používáte služby vzájemné spolupráce pro volání do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1898f-105">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="1898f-106">V tomto případě musí být metoda také deklarována jako `static` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1898f-106">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="1898f-107">`extern`Klíčové slovo může také definovat externí alias sestavení, který umožňuje odkazování na různé verze stejné součásti v rámci jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="1898f-107">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="1898f-108">Další informace najdete v tématu [extern alias](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="1898f-108">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="1898f-109">Použití [abstraktních](abstract.md) a `extern` modifikátorů pro změnu stejného člena je chybné.</span><span class="sxs-lookup"><span data-stu-id="1898f-109">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="1898f-110">Použití `extern` modifikátoru znamená, že metoda je implementována mimo kód jazyka C#, zatímco použití `abstract` modifikátoru znamená, že implementace metody není ve třídě k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1898f-110">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="1898f-111">Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="1898f-111">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="1898f-112">Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="1898f-112">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="1898f-113">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="1898f-113">Example 1</span></span>

<span data-ttu-id="1898f-114">V tomto příkladu program obdrží od uživatele řetězec a zobrazí jej v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="1898f-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="1898f-115">Program používá `MessageBox` metodu importovanou z knihovny User32.dll.</span><span class="sxs-lookup"><span data-stu-id="1898f-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="1898f-116">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="1898f-116">Example 2</span></span>

<span data-ttu-id="1898f-117">Tento příklad znázorňuje program v jazyce C#, který volá do knihovny jazyka C (nativní knihovna DLL).</span><span class="sxs-lookup"><span data-stu-id="1898f-117">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="1898f-118">Vytvořte následující soubor C a pojmenujte ho `cmdll.c` :</span><span class="sxs-lookup"><span data-stu-id="1898f-118">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="1898f-119">Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte `cmdll.c` soubor tak, že na příkazovém řádku zadáte **CL-ld cmdll. c** .</span><span class="sxs-lookup"><span data-stu-id="1898f-119">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="1898f-120">Ve stejném adresáři vytvořte následující soubor C# a pojmenujte ho `cm.cs` :</span><span class="sxs-lookup"><span data-stu-id="1898f-120">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

    ```csharp
    // cm.cs
    using System;
    using System.Runtime.InteropServices;
    public class MainClass
    {
        [DllImport("Cmdll.dll")]
          public static extern int SampleMethod(int x);

        static void Main()
        {
            Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
        }
    }
    ```

4. <span data-ttu-id="1898f-121">Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte `cm.cs` soubor tak, že zadáte:</span><span class="sxs-lookup"><span data-stu-id="1898f-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="1898f-122">**csc cm.cs** (pro příkazový řádek x64), nebo – **CSC-platform: x86 cm.cs** (pro příkazový řádek x32)</span><span class="sxs-lookup"><span data-stu-id="1898f-122">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="1898f-123">Tím se vytvoří spustitelný soubor `cm.exe` .</span><span class="sxs-lookup"><span data-stu-id="1898f-123">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="1898f-124">Spusťte `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="1898f-124">Run `cm.exe`.</span></span> <span data-ttu-id="1898f-125">`SampleMethod`Metoda předá hodnotu 5 souboru DLL, která vrací hodnotu vynásobenou 10.</span><span class="sxs-lookup"><span data-stu-id="1898f-125">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="1898f-126">Program vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1898f-126">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="1898f-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1898f-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1898f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1898f-128">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="1898f-129">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1898f-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1898f-130">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1898f-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1898f-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1898f-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1898f-132">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="1898f-132">Modifiers</span></span>](index.md)
