---
title: extern – modifikátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: aca1a9fa0b57e9b3b0a515a805039ade2fe0c2f1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027912"
---
# <a name="extern-c-reference"></a><span data-ttu-id="7b8c1-102">extern (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7b8c1-102">extern (C# Reference)</span></span>

<span data-ttu-id="7b8c1-103">`extern` Modifikátor se používá k deklaraci metodu, která je implementována externě.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="7b8c1-104">Běžně se používají `extern` se modifikátor s `DllImport` atributu při použití zprostředkovatele komunikace s objekty služby volat nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="7b8c1-105">V takovém případě metoda musí být deklarován také jako `static`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7b8c1-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="7b8c1-106">`extern` – Klíčové slovo můžete také definovat alias externí sestavení, která vám umožní tak, aby odkazovaly různé verze stejné komponenty z v rámci jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="7b8c1-107">Další informace najdete v tématu [extern alias](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="7b8c1-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="7b8c1-108">Jedná se o chybu používat [abstraktní](abstract.md) a `extern` modifikátory společně k úpravě stejného člena.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="7b8c1-109">Pomocí `extern` modifikátor znamená, že je metoda implementována mimo kód C# zatímco pomocí `abstract` modifikátor znamená, že není zadaný implementace metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="7b8c1-110">Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="7b8c1-111">Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="7b8c1-112">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="7b8c1-112">Example 1</span></span>

<span data-ttu-id="7b8c1-113">V tomto příkladu program od uživatele přijímá řetězec a zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="7b8c1-114">Program používá `MessageBox` metoda naimportované z knihovny User32.dll.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="7b8c1-115">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="7b8c1-115">Example 2</span></span>

<span data-ttu-id="7b8c1-116">Tento příklad ukazuje programu C#, který volá do knihovny jazyka C (nativní knihovny DLL).</span><span class="sxs-lookup"><span data-stu-id="7b8c1-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="7b8c1-117">Vytvoření následujícího souboru C a pojmenujte ji `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="7b8c1-117">Create the following C file and name it `cmdll.c`:</span></span>

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. <span data-ttu-id="7b8c1-118">Otevřete okno sady Visual Studio x64 (nebo x32) nativní nástroje pro příkazový řádek z instalačního adresáře nástroje Visual Studio a kompilaci `cmdll.c` souboru zadáním **cl -LD cmdll.c** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="7b8c1-119">Ve stejném adresáři, vytvořte následující soubor C# a pojmenujte ji `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="7b8c1-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

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

4. <span data-ttu-id="7b8c1-120">Otevřete okno sady Visual Studio x64 (nebo x32) nativní nástroje pro příkazový řádek z instalačního adresáře nástroje Visual Studio a kompilaci `cm.cs` souboru zadáním:</span><span class="sxs-lookup"><span data-stu-id="7b8c1-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

> <span data-ttu-id="7b8c1-121">**CSC cm.cs** (pro x64 příkazového řádku) – nebo – **csc-platformy: x 86 cm.cs** (pro x32 příkazového řádku)</span><span class="sxs-lookup"><span data-stu-id="7b8c1-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

<span data-ttu-id="7b8c1-122">Tím se vytvoří spustitelný soubor `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="7b8c1-123">Spustit `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-123">Run `cm.exe`.</span></span> <span data-ttu-id="7b8c1-124">`SampleMethod` Metoda předá hodnotu 5 soubor knihovny DLL, která vrátí hodnotu násobí hodnotou 10.</span><span class="sxs-lookup"><span data-stu-id="7b8c1-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="7b8c1-125">Program vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7b8c1-125">The program produces the following output:</span></span>

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a><span data-ttu-id="7b8c1-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b8c1-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b8c1-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b8c1-127">See also</span></span>

<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
[<span data-ttu-id="7b8c1-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b8c1-128">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="7b8c1-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7b8c1-129">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="7b8c1-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b8c1-130">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="7b8c1-131">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="7b8c1-131">Modifiers</span></span>](modifiers.md)  