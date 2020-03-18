---
title: '#řádek – odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712491"
---
# <a name="line-c-reference"></a><span data-ttu-id="d6239-102">#line (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d6239-102">#line (C# Reference)</span></span>

<span data-ttu-id="d6239-103">`#line`umožňuje upravit číslování řádků kompilátoru a (volitelně) výstup názvu souboru pro chyby a upozornění.</span><span class="sxs-lookup"><span data-stu-id="d6239-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="d6239-104">Následující příklad ukazuje, jak nahlásit dvě upozornění přidružená k číslům řádků.</span><span class="sxs-lookup"><span data-stu-id="d6239-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="d6239-105">Směrnice `#line 200` vynutí číslo dalšího řádku na 200 (i když je `#line` výchozí hodnota #6) a až do další směrnice bude název souboru vykázán jako "Zvláštní".</span><span class="sxs-lookup"><span data-stu-id="d6239-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="d6239-106">Směrnice `#line default` vrátí číslování řádků na výchozí číslování, které počítá řádky, které byly přečíslovány předchozí směrnicí.</span><span class="sxs-lookup"><span data-stu-id="d6239-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

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

<span data-ttu-id="d6239-107">Kompilace vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d6239-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="d6239-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6239-108">Remarks</span></span>

<span data-ttu-id="d6239-109">Směrnice `#line` může být použita v automatizovaném, mezikroku v procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6239-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="d6239-110">Pokud byly například řádky odebrány z původního souboru zdrojového kódu, ale přesto jste chtěli, aby kompilátor generoval výstup na `#line`základě původního číslování řádků v souboru, můžete řádky odebrat a potom simulovat původní číslování řádků pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="d6239-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="d6239-111">Směrnice `#line hidden` skryje po sobě jdoucí řádky z ladicího programu, tak, že `#line hidden` když `#line` vývojář kroky prostřednictvím kódu, všechny řádky mezi a další směrnice (za předpokladu, že není další `#line hidden` směrnice) bude přešel.</span><span class="sxs-lookup"><span data-stu-id="d6239-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="d6239-112">Tuto možnost lze také použít k povolení ASP.NET rozlišovat mezi uživatelem definovaným a strojově generovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="d6239-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="d6239-113">Přestože ASP.NET je primárním spotřebitelem této funkce, je pravděpodobné, že ji využije více zdrojových generátorů.</span><span class="sxs-lookup"><span data-stu-id="d6239-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="d6239-114">Direktiva `#line hidden` nemá vliv na názvy souborů nebo čísla řádků v hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="d6239-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="d6239-115">To znamená, že pokud dojde k chybě ve skrytém bloku, kompilátor ohlásí aktuální název souboru a číslo řádku chyby.</span><span class="sxs-lookup"><span data-stu-id="d6239-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="d6239-116">Směrnice `#line filename` určuje název souboru, který se má zobrazit ve výstupu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d6239-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="d6239-117">Ve výchozím nastavení se používá skutečný název souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="d6239-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="d6239-118">Název souboru musí být v uvozovkách ("") a musí mu předcházet číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="d6239-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="d6239-119">Soubor zdrojového kódu může `#line` mít libovolný počet směrnic.</span><span class="sxs-lookup"><span data-stu-id="d6239-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="d6239-120">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="d6239-120">Example 1</span></span>

<span data-ttu-id="d6239-121">Následující příklad ukazuje, jak ladicí program ignoruje skryté řádky v kódu.</span><span class="sxs-lookup"><span data-stu-id="d6239-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="d6239-122">Při spuštění příkladu se zobrazí tři řádky textu.</span><span class="sxs-lookup"><span data-stu-id="d6239-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="d6239-123">Však při nastavení bodu přerušení, jak je znázorněno v příkladu a hit F10 krokovat kód, zjistíte, že ladicí program ignoruje skryté čáry.</span><span class="sxs-lookup"><span data-stu-id="d6239-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="d6239-124">Všimněte si také, že i v případě, že nastavíte bod přerušení na skryté čáry, ladicí program bude stále ignorovat.</span><span class="sxs-lookup"><span data-stu-id="d6239-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d6239-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6239-125">See also</span></span>

- [<span data-ttu-id="d6239-126">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d6239-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d6239-127">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d6239-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d6239-128">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d6239-128">C# Preprocessor Directives</span></span>](./index.md)
