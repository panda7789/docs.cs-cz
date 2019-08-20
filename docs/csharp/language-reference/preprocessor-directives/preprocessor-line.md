---
title: '#odkaz na C# řádek'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: b4ac4fd3277fb53251e87321500d1b8007458037
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608535"
---
# <a name="line-c-reference"></a><span data-ttu-id="b1e89-102">#line (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b1e89-102">#line (C# Reference)</span></span>

<span data-ttu-id="b1e89-103">`#line`umožňuje upravit číslování řádků kompilátoru a (volitelně) výstup názvu souboru pro chyby a upozornění.</span><span class="sxs-lookup"><span data-stu-id="b1e89-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="b1e89-104">Následující příklad ukazuje, jak ohlásit dvě upozornění spojená s čísly řádků.</span><span class="sxs-lookup"><span data-stu-id="b1e89-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="b1e89-105">Direktiva vynutí, aby číslo dalšího řádku bylo 200 (výchozí hodnota je #6), a až do další `#line` direktivy bude název souboru uveden jako "Special". `#line 200`</span><span class="sxs-lookup"><span data-stu-id="b1e89-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="b1e89-106">`#line default` Direktiva vrátí číslování řádků do výchozího číslování, což spočítá řádky, které byly přečíslovány předchozí direktivou.</span><span class="sxs-lookup"><span data-stu-id="b1e89-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

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

<span data-ttu-id="b1e89-107">Kompilace generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b1e89-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="b1e89-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1e89-108">Remarks</span></span>

<span data-ttu-id="b1e89-109">`#line` Direktiva může být použita v automatizovaném mezilehlém kroku procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1e89-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="b1e89-110">Například pokud byly řádky odebrány z původního souboru zdrojového kódu, ale přesto jste chtěli, aby kompilátor vygeneroval výstup na základě původního číslování řádků v souboru, mohli byste odebrat řádky a potom simulovat původní číslování `#line`řádků.</span><span class="sxs-lookup"><span data-stu-id="b1e89-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="b1e89-111">Direktiva skryje po sobě následující řádky z ladicího programu, což znamená, že když postupuje vývojář pomocí kódu, všechny řádky `#line hidden` mezi a a `#line` další direktivou (za předpokladu, `#line hidden` že se nejedná o jinou direktivu). `#line hidden` zvýší se.</span><span class="sxs-lookup"><span data-stu-id="b1e89-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="b1e89-112">Tato možnost slouží také k tomu, aby ASP.NET bylo možné odlišit od uživatelsky definovaného a strojově generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b1e89-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="b1e89-113">I když je ASP.NET primárním spotřebitelem této funkce, je pravděpodobnější, že ji budou využívat více generátorů zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b1e89-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="b1e89-114">`#line hidden` Direktiva nemá vliv na názvy souborů nebo čísla řádků při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="b1e89-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="b1e89-115">To znamená, že pokud ve skrytém bloku dojde k chybě, kompilátor oznámí aktuální název souboru a číslo řádku chyby.</span><span class="sxs-lookup"><span data-stu-id="b1e89-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="b1e89-116">`#line filename` Direktiva Určuje název souboru, který se má zobrazit ve výstupu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b1e89-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="b1e89-117">Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="b1e89-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="b1e89-118">Název souboru musí být v uvozovkách ("") a musí předcházet číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="b1e89-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="b1e89-119">Soubor zdrojového kódu může mít libovolný počet `#line` direktiv.</span><span class="sxs-lookup"><span data-stu-id="b1e89-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="b1e89-120">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="b1e89-120">Example 1</span></span>

<span data-ttu-id="b1e89-121">Následující příklad ukazuje, jak ladicí program ignoruje skryté řádky v kódu.</span><span class="sxs-lookup"><span data-stu-id="b1e89-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="b1e89-122">Když spustíte příklad, zobrazí se tři řádky textu.</span><span class="sxs-lookup"><span data-stu-id="b1e89-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="b1e89-123">Nicméně pokud nastavíte bod přerušení, jak je znázorněno v příkladu, a stisknutím klávesy F10 projdete kód, zjistíte, že ladicí program ignoruje skrytý řádek.</span><span class="sxs-lookup"><span data-stu-id="b1e89-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="b1e89-124">Všimněte si také, že i když nastavíte bod přerušení na skrytém řádku, ladicí program ho bude stále ignorovat.</span><span class="sxs-lookup"><span data-stu-id="b1e89-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b1e89-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1e89-125">See also</span></span>

- [<span data-ttu-id="b1e89-126">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b1e89-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b1e89-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b1e89-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b1e89-128">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="b1e89-128">C# Preprocessor Directives</span></span>](./index.md)
