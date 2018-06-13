---
title: '#řádek (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 08ba94ec3f1799f858e098bd2c0e059b7f45af2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289266"
---
# <a name="line-c-reference"></a><span data-ttu-id="b59c6-102">#line (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b59c6-102">#line (C# Reference)</span></span>
<span data-ttu-id="b59c6-103">`#line` Umožňuje změnit číslo řádku kompilátoru a (volitelně) název výstupního souboru chyby a upozornění.</span><span class="sxs-lookup"><span data-stu-id="b59c6-103">`#line` lets you modify the compiler's line number and (optionally) the file name output for errors and warnings.</span></span> <span data-ttu-id="b59c6-104">Tento příklad ukazuje, jak vytvářet sestavu dvě upozornění související s čísla řádků.</span><span class="sxs-lookup"><span data-stu-id="b59c6-104">This example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="b59c6-105">`#line 200` – Direktiva vynutí číslo řádku, které má být 200 (i když výchozí hodnota je #7) a dokud další #line – direktiva, název souboru budou hlášené jako "Zvláštní".</span><span class="sxs-lookup"><span data-stu-id="b59c6-105">The `#line 200` directive forces the line number to be 200 (although the default is #7) and until the next #line directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="b59c6-106">Směrnice výchozí #line vrátí číslování k jeho výchozí číslování, řádek, který zjistí, kolik řádků se označuje jako v předchozí direktivě.</span><span class="sxs-lookup"><span data-stu-id="b59c6-106">The #line default directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="b59c6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b59c6-107">Remarks</span></span>  
 <span data-ttu-id="b59c6-108">`#line` – Direktiva mohou být používány na automatické, zprostředkující krok v procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b59c6-108">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="b59c6-109">Například pokud řádky byly odebrány z původního souboru se zdrojovým kódem, ale přesto chtěli kompilátoru generovat výstup na základě původní řádku číslování v souboru, můžete odstranit řádky a pak simulovat původní řádek číslování s `#line`.</span><span class="sxs-lookup"><span data-stu-id="b59c6-109">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>  
  
 <span data-ttu-id="b59c6-110">`#line hidden` – Direktiva skryje po sobě jdoucích řádků ze ladicího programu, tak, že když vývojáři kroky prostřednictvím kód, všechny řádků mezi `#line hidden` a další `#line` – direktiva (za předpokladu, že není jiná `#line hidden` – direktiva) bude mít stupně přes.</span><span class="sxs-lookup"><span data-stu-id="b59c6-110">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="b59c6-111">Tuto možnost lze také povolit ASP.NET k rozlišení mezi kódu uživatelem definované a generované počítače.</span><span class="sxs-lookup"><span data-stu-id="b59c6-111">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="b59c6-112">I když primární příjemce této funkce je technologie ASP.NET, je pravděpodobné, že další zdroje, které budou generátory používat ho.</span><span class="sxs-lookup"><span data-stu-id="b59c6-112">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>  
  
 <span data-ttu-id="b59c6-113">A `#line hidden` – direktiva nemá vliv na názvy souborů nebo čísla řádků v zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="b59c6-113">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="b59c6-114">To znamená je-li k chybě v skrytá bloku, kompilátor zprávu aktuální soubor název a řádek číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="b59c6-114">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>  
  
 <span data-ttu-id="b59c6-115">`#line filename` – Direktiva Určuje název souboru, který se má zobrazit ve výstupu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b59c6-115">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="b59c6-116">Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="b59c6-116">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="b59c6-117">Název souboru musí být v uvozovkách ("") a musí předcházet číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="b59c6-117">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>  
  
 <span data-ttu-id="b59c6-118">Zdrojový soubor může mít libovolný počet `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="b59c6-118">A source code file can have any number of `#line` directives.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b59c6-119">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="b59c6-119">Example 1</span></span>  
 <span data-ttu-id="b59c6-120">Následující příklad ukazuje, jak ladicího programu ignoruje skryté řádky v kódu.</span><span class="sxs-lookup"><span data-stu-id="b59c6-120">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="b59c6-121">Při spuštění v příkladu, zobrazí se tří řádků textu.</span><span class="sxs-lookup"><span data-stu-id="b59c6-121">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="b59c6-122">Ale nastavit bod přerušení, jak je znázorněno v příkladu, a stiskněte tlačítko F10 procházet kód, si všimněte, že ladicí program ignoruje skrytá řádku.</span><span class="sxs-lookup"><span data-stu-id="b59c6-122">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="b59c6-123">Všimněte si také, že i v případě, že nastavíte bod zalomení na řádku Skrytá, ladicího programu bude stále ji ignorovat.</span><span class="sxs-lookup"><span data-stu-id="b59c6-123">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b59c6-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b59c6-124">See Also</span></span>  
 [<span data-ttu-id="b59c6-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b59c6-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b59c6-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b59c6-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b59c6-127">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="b59c6-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
