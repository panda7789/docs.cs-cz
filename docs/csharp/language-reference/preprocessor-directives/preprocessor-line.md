---
title: '#odkaz na C# řádek'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712491"
---
# <a name="line-c-reference"></a><span data-ttu-id="6be69-102">#line (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6be69-102">#line (C# Reference)</span></span>

<span data-ttu-id="6be69-103">`#line` umožňuje upravit číslování řádků kompilátoru a (volitelně) výstup názvu souboru pro chyby a upozornění.</span><span class="sxs-lookup"><span data-stu-id="6be69-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="6be69-104">Následující příklad ukazuje, jak ohlásit dvě upozornění spojená s čísly řádků.</span><span class="sxs-lookup"><span data-stu-id="6be69-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="6be69-105">Direktiva `#line 200` vynutí, aby číslo dalšího řádku bylo 200 (i když je výchozí hodnota #6) a do další `#line` direktivy, název souboru bude hlášen jako "Special".</span><span class="sxs-lookup"><span data-stu-id="6be69-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="6be69-106">Direktiva `#line default` vrací číslování řádků do výchozího číslování, což počítá řádky, které byly přečíslovány předchozí direktivou.</span><span class="sxs-lookup"><span data-stu-id="6be69-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="6be69-107">Kompilace generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6be69-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="6be69-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6be69-108">Remarks</span></span>

<span data-ttu-id="6be69-109">Direktiva `#line` může být použita v automatizovaném mezilehlém kroku procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6be69-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="6be69-110">Například pokud byly řádky odebrány z původního souboru zdrojového kódu, ale přesto jste chtěli, aby kompilátor vygeneroval výstup na základě originálního číslování řádků v souboru, mohli byste odebrat řádky a potom simulovat původní číslování řádků pomocí `#line`.</span><span class="sxs-lookup"><span data-stu-id="6be69-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="6be69-111">Direktiva `#line hidden` skrývá po sobě jdoucí řádky z ladicího programu, což znamená, že pokud kroky pro vývojáře procházejí kódem, všechny řádky mezi `#line hidden` a další `#line`ou direktivou (za předpokladu, že se nejedná o jinou direktivu `#line hidden`), se zvýší.</span><span class="sxs-lookup"><span data-stu-id="6be69-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="6be69-112">Tato možnost slouží také k tomu, aby ASP.NET bylo možné odlišit od uživatelsky definovaného a strojově generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6be69-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="6be69-113">I když je ASP.NET primárním spotřebitelem této funkce, je pravděpodobnější, že ji budou využívat více generátorů zdrojů.</span><span class="sxs-lookup"><span data-stu-id="6be69-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="6be69-114">Direktiva `#line hidden` neovlivňuje názvy souborů nebo čísla řádků při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="6be69-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="6be69-115">To znamená, že pokud ve skrytém bloku dojde k chybě, kompilátor oznámí aktuální název souboru a číslo řádku chyby.</span><span class="sxs-lookup"><span data-stu-id="6be69-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="6be69-116">Direktiva `#line filename` Určuje název souboru, který se má zobrazit ve výstupu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6be69-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="6be69-117">Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="6be69-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="6be69-118">Název souboru musí být v uvozovkách ("") a musí předcházet číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="6be69-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="6be69-119">Soubor se zdrojovým kódem může mít libovolný počet direktiv `#line`.</span><span class="sxs-lookup"><span data-stu-id="6be69-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="6be69-120">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="6be69-120">Example 1</span></span>

<span data-ttu-id="6be69-121">Následující příklad ukazuje, jak ladicí program ignoruje skryté řádky v kódu.</span><span class="sxs-lookup"><span data-stu-id="6be69-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="6be69-122">Když spustíte příklad, zobrazí se tři řádky textu.</span><span class="sxs-lookup"><span data-stu-id="6be69-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="6be69-123">Nicméně pokud nastavíte bod přerušení, jak je znázorněno v příkladu, a stisknutím klávesy F10 projdete kód, zjistíte, že ladicí program ignoruje skrytý řádek.</span><span class="sxs-lookup"><span data-stu-id="6be69-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="6be69-124">Všimněte si také, že i když nastavíte bod přerušení na skrytém řádku, ladicí program ho bude stále ignorovat.</span><span class="sxs-lookup"><span data-stu-id="6be69-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="6be69-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6be69-125">See also</span></span>

- [<span data-ttu-id="6be69-126">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="6be69-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6be69-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6be69-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6be69-128">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="6be69-128">C# Preprocessor Directives</span></span>](./index.md)
