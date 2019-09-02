---
title: extern modifikátor – C# referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 387ef707166705c4df501bd6740d438683aa2d69
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203014"
---
# <a name="extern-c-reference"></a><span data-ttu-id="6d9a3-102">extern (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6d9a3-102">extern (C# Reference)</span></span>

<span data-ttu-id="6d9a3-103">`extern` Modifikátor slouží k deklaraci metody, která je implementována externě.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="6d9a3-104">Běžné použití `extern` modifikátoru je `DllImport` s atributem, pokud používáte služby vzájemné spolupráce pro volání do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="6d9a3-105">V tomto případě musí být metoda také deklarována jako `static`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6d9a3-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="6d9a3-106">`extern` Klíčové slovo může také definovat externí alias sestavení, který umožňuje odkazování na různé verze stejné součásti v rámci jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="6d9a3-107">Další informace najdete v tématu [extern alias](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="6d9a3-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="6d9a3-108">Použití [abstraktních](abstract.md) a `extern` modifikátorů pro změnu stejného člena je chybné.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="6d9a3-109">Použití modifikátoru znamená, že metoda je implementována mimo C# kód `abstract` , zatímco použití modifikátoru znamená, že implementace metody není ve třídě k dispozici. `extern`</span><span class="sxs-lookup"><span data-stu-id="6d9a3-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="6d9a3-110">Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="6d9a3-111">Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="6d9a3-112">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="6d9a3-112">Example 1</span></span>

<span data-ttu-id="6d9a3-113">V tomto příkladu program obdrží od uživatele řetězec a zobrazí jej v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="6d9a3-114">Program používá `MessageBox` metodu importovanou z knihovny User32. dll.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="6d9a3-115">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="6d9a3-115">Example 2</span></span>

<span data-ttu-id="6d9a3-116">Tento příklad ilustruje C# program, který volá do knihovny jazyka C (nativní knihovna DLL).</span><span class="sxs-lookup"><span data-stu-id="6d9a3-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="6d9a3-117">Vytvořte následující soubor C a pojmenujte `cmdll.c`ho:</span><span class="sxs-lookup"><span data-stu-id="6d9a3-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="6d9a3-118">Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio `cmdll.c` a zkompilujte soubor tak, že na příkazovém řádku zadáte **CL-ld cmdll. c** .</span><span class="sxs-lookup"><span data-stu-id="6d9a3-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="6d9a3-119">Ve stejném adresáři vytvořte následující C# soubor a pojmenujte ho: `cm.cs`</span><span class="sxs-lookup"><span data-stu-id="6d9a3-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="6d9a3-120">Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio `cm.cs` a zkompilujte soubor tak, že zadáte:</span><span class="sxs-lookup"><span data-stu-id="6d9a3-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="6d9a3-121">**cm.cs CSC** (pro příkazový řádek x64), nebo – **CSC-Platform: x86 cm.cs** (pro příkazový řádek x32)</span><span class="sxs-lookup"><span data-stu-id="6d9a3-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="6d9a3-122">Tím se vytvoří spustitelný soubor `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="6d9a3-123">Spusťte `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-123">Run `cm.exe`.</span></span> <span data-ttu-id="6d9a3-124">`SampleMethod` Metoda předá hodnotu 5 souboru DLL, která vrací hodnotu vynásobenou 10.</span><span class="sxs-lookup"><span data-stu-id="6d9a3-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="6d9a3-125">Program vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6d9a3-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="6d9a3-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d9a3-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6d9a3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d9a3-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="6d9a3-128">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="6d9a3-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d9a3-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6d9a3-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6d9a3-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d9a3-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6d9a3-131">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="6d9a3-131">Modifiers</span></span>](modifiers.md)
