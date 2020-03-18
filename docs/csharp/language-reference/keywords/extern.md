---
title: extern modifikátor - C# Reference
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713530"
---
# <a name="extern-c-reference"></a><span data-ttu-id="51eb3-102">extern (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="51eb3-102">extern (C# Reference)</span></span>

<span data-ttu-id="51eb3-103">Modifikátor `extern` se používá k deklarování metody, která je implementována externě.</span><span class="sxs-lookup"><span data-stu-id="51eb3-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="51eb3-104">Běžné použití modifikátoru `extern` `DllImport` je s atributem, když používáte služby Interop pro volání do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="51eb3-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="51eb3-105">V tomto případě musí být metoda `static`deklarována také jako , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="51eb3-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="51eb3-106">Klíčové `extern` slovo může také definovat alias externí sestavy, který umožňuje odkazovat na různé verze stejné součásti z jedné sestavy.</span><span class="sxs-lookup"><span data-stu-id="51eb3-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="51eb3-107">Další informace naleznete v tématu [extern alias](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="51eb3-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="51eb3-108">Je chyba použít [abstraktní](abstract.md) a `extern` modifikátory společně upravit stejný člen.</span><span class="sxs-lookup"><span data-stu-id="51eb3-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="51eb3-109">Použití `extern` modifikátoru znamená, že metoda je implementována `abstract` mimo kód Jazyka C#, zatímco použití modifikátoru znamená, že implementace metody není k dispozici ve třídě.</span><span class="sxs-lookup"><span data-stu-id="51eb3-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="51eb3-110">Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="51eb3-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="51eb3-111">Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="51eb3-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="51eb3-112">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="51eb3-112">Example 1</span></span>

<span data-ttu-id="51eb3-113">V tomto příkladu program obdrží řetězec od uživatele a zobrazí jej uvnitř okna se zprávou.</span><span class="sxs-lookup"><span data-stu-id="51eb3-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="51eb3-114">Program používá `MessageBox` metodu importovoz knihovny User32.dll.</span><span class="sxs-lookup"><span data-stu-id="51eb3-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="51eb3-115">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="51eb3-115">Example 2</span></span>

<span data-ttu-id="51eb3-116">Tento příklad ilustruje c# program, který volá do knihovny Jazyka C (nativní knihovna DLL).</span><span class="sxs-lookup"><span data-stu-id="51eb3-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="51eb3-117">Vytvořte následující soubor C `cmdll.c`a pojmenujte jej :</span><span class="sxs-lookup"><span data-stu-id="51eb3-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="51eb3-118">Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte `cmdll.c` soubor zadáním **souboru cl -LD cmdll.c** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="51eb3-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="51eb3-119">Ve stejném adresáři vytvořte následující soubor `cm.cs`Jazyka C# a pojmenujte jej :</span><span class="sxs-lookup"><span data-stu-id="51eb3-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="51eb3-120">Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte `cm.cs` soubor zadáním:</span><span class="sxs-lookup"><span data-stu-id="51eb3-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="51eb3-121">**csc cm.cs** (pro příkazový řádek x64) - nebo- **csc -platform:x86 cm.cs** (pro příkazový řádek x32)</span><span class="sxs-lookup"><span data-stu-id="51eb3-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="51eb3-122">Tím vytvoříte spustitelný `cm.exe`soubor .</span><span class="sxs-lookup"><span data-stu-id="51eb3-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="51eb3-123">Spusťte `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="51eb3-123">Run `cm.exe`.</span></span> <span data-ttu-id="51eb3-124">Metoda `SampleMethod` předá hodnotu 5 do souboru DLL, který vrátí hodnotu vynásobenou hodnotou 10.</span><span class="sxs-lookup"><span data-stu-id="51eb3-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="51eb3-125">Program vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="51eb3-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="51eb3-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="51eb3-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="51eb3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="51eb3-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="51eb3-128">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="51eb3-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="51eb3-129">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="51eb3-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="51eb3-130">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="51eb3-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="51eb3-131">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="51eb3-131">Modifiers</span></span>](index.md)
