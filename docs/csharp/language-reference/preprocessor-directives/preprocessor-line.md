---
title: '#řádek – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: f4e3c3edbe1d542f9bf5c984c403e0486a9da61b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611975"
---
# <a name="line-c-reference"></a><span data-ttu-id="62172-102">#line (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="62172-102">#line (C# Reference)</span></span>

<span data-ttu-id="62172-103">`#line` Umožňuje upravit kompilátoru číslování řádků a (volitelně) název výstupního souboru pro chyby a upozornění.</span><span class="sxs-lookup"><span data-stu-id="62172-103">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="62172-104">Následující příklad ukazuje, jak ohlásit dvě upozornění související s čísly řádků.</span><span class="sxs-lookup"><span data-stu-id="62172-104">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="62172-105">`#line 200` Směrnice vynutí na další řádek číslo, které má být 200 (i když výchozí hodnota je #6) a až do další `#line` direktiv, název souboru se ohlásí jako "Speciální".</span><span class="sxs-lookup"><span data-stu-id="62172-105">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="62172-106">`#line default` – Direktiva vrátí řádku číslování na jeho výchozí čísla, která vrátí počet řádků, které se označuje jako předchozí direktivou.</span><span class="sxs-lookup"><span data-stu-id="62172-106">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

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

<span data-ttu-id="62172-107">Kompilace vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="62172-107">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="62172-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62172-108">Remarks</span></span>

<span data-ttu-id="62172-109">`#line` v jednom z automatizované, zprostředkující kroků v procesu sestavení, může se použít direktiva.</span><span class="sxs-lookup"><span data-stu-id="62172-109">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="62172-110">Například pokud řádky byly odebrány z původního souboru se zdrojovým kódem, ale stále chtěla kompilátor, aby generoval výstupní založené na původní řádek číslování v souboru, můžete odebrat řádky a potom simulovat původní řádek číslování s `#line`.</span><span class="sxs-lookup"><span data-stu-id="62172-110">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="62172-111">`#line hidden` – Direktiva skrývá po sobě jdoucích řádků z ladicího programu, takže když vývojář provede kód, některé řádky mezi `#line hidden` a dalších `#line` – direktiva (za předpokladu, že není jiné `#line hidden` – direktiva) bude se stupňovitým přes.</span><span class="sxs-lookup"><span data-stu-id="62172-111">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="62172-112">Tuto možnost lze také povolit ASP.NET k rozlišení mezi uživatelem a počítačem generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="62172-112">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="62172-113">I když je primární příjemce této funkce technologie ASP.NET, je pravděpodobnost, že další zdroje, které způsobí, že generátorů využije ho.</span><span class="sxs-lookup"><span data-stu-id="62172-113">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="62172-114">A `#line hidden` direktiva ovlivnit názvy souborů nebo čísla řádků v hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="62172-114">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="62172-115">To znamená pokud dojde k chybě v bloku skryté, že kompilátor nahlásí aktuální soubor název a číslo řádku chyby.</span><span class="sxs-lookup"><span data-stu-id="62172-115">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="62172-116">`#line filename` Direktiva Určuje název souboru, které se mají zobrazit ve výstupu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="62172-116">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="62172-117">Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="62172-117">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="62172-118">Název souboru musí být v dvojitých uvozovkách ("") a musí být předcházen číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="62172-118">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="62172-119">Soubor zdrojového kódu může mít libovolný počet `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="62172-119">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="62172-120">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="62172-120">Example 1</span></span>

<span data-ttu-id="62172-121">Následující příklad ukazuje, jak ladicí program ignoruje skryté řádky v kódu.</span><span class="sxs-lookup"><span data-stu-id="62172-121">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="62172-122">Při spuštění v příkladu se zobrazí tři řádky textu.</span><span class="sxs-lookup"><span data-stu-id="62172-122">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="62172-123">Ale při nastavení přerušení, jak je znázorněno v příkladu a stiskněte F10 a krokovat kód, si všimnete, že ladicí program ignoruje řádku skryté.</span><span class="sxs-lookup"><span data-stu-id="62172-123">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="62172-124">Všimněte si také, že i v případě, že jste nastavili přerušení na řádku skryté, ladicí program bude stále ho ignorovat.</span><span class="sxs-lookup"><span data-stu-id="62172-124">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="62172-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62172-125">See also</span></span>

- [<span data-ttu-id="62172-126">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62172-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="62172-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="62172-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="62172-128">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="62172-128">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
