---
title: -define (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 4a3622b6acc8ebe9c590b01b67074ae59396fc34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173741"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="ba530-102">-define (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ba530-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="ba530-103">Možnost **-define** definuje `name` jako symbol ve všech souborech zdrojového kódu, které váš program.</span><span class="sxs-lookup"><span data-stu-id="ba530-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba530-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba530-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba530-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ba530-105">Arguments</span></span>  
 <span data-ttu-id="ba530-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="ba530-106">`name`, `name2`</span></span>  
 <span data-ttu-id="ba530-107">Název jednoho nebo více symbolů, které chcete definovat.</span><span class="sxs-lookup"><span data-stu-id="ba530-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba530-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba530-108">Remarks</span></span>  
 <span data-ttu-id="ba530-109">Možnost **-define** má stejný účinek jako použití direktivy preprocesoru [#define](../preprocessor-directives/preprocessor-define.md) s tím rozdílem, že možnost kompilátoru je v platnosti pro všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="ba530-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="ba530-110">Symbol zůstane definován ve zdrojovém souboru, dokud [#undef](../preprocessor-directives/preprocessor-undef.md) direktiva ve zdrojovém souboru neodebere definici.</span><span class="sxs-lookup"><span data-stu-id="ba530-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="ba530-111">Při použití -define možnost, `#undef` směrnice v jednom souboru nemá žádný vliv na jiné soubory zdrojového kódu v projektu.</span><span class="sxs-lookup"><span data-stu-id="ba530-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="ba530-112">Symboly vytvořené touto volbou můžete použít s [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)a [#endif](../preprocessor-directives/preprocessor-endif.md) můžete podmíněně kompilovat zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="ba530-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="ba530-113">**-d** je krátká forma **-define**.</span><span class="sxs-lookup"><span data-stu-id="ba530-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="ba530-114">Můžete definovat více symbolů s **-define** pomocí středníku nebo čárky pro oddělení názvů symbolů.</span><span class="sxs-lookup"><span data-stu-id="ba530-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="ba530-115">Například:</span><span class="sxs-lookup"><span data-stu-id="ba530-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="ba530-116">Samotný kompilátor Jazyka C# nedefinuje žádné symboly nebo makra, které můžete použít ve zdrojovém kódu; všechny definice symbolů musí být definovány uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ba530-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba530-117">C# `#define` neumožňuje symbolu, který má být uveden hodnotu, jako v jazycích, jako je například C++.</span><span class="sxs-lookup"><span data-stu-id="ba530-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="ba530-118">Nelze například `#define` použít k vytvoření makra nebo k definování konstanty.</span><span class="sxs-lookup"><span data-stu-id="ba530-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="ba530-119">Pokud potřebujete definovat konstantu, `enum` použijte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="ba530-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="ba530-120">Pokud chcete vytvořit makro stylu C++, zvažte alternativy, jako jsou obecné typy.</span><span class="sxs-lookup"><span data-stu-id="ba530-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="ba530-121">Vzhledem k tomu, že makra jsou notoricky náchylné k chybám, C# zakazuje jejich použití, ale poskytuje bezpečnější alternativy.</span><span class="sxs-lookup"><span data-stu-id="ba530-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ba530-122">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ba530-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ba530-123">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="ba530-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ba530-124">Na kartě **Sestavení** zadejte symbol, který má být definován, do pole **Symboly podmíněné kompilace.**</span><span class="sxs-lookup"><span data-stu-id="ba530-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="ba530-125">Například pokud používáte příklad kódu, který následuje, stačí zadat `xx` do textového pole.</span><span class="sxs-lookup"><span data-stu-id="ba530-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="ba530-126">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="ba530-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba530-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba530-127">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba530-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba530-128">See also</span></span>

- [<span data-ttu-id="ba530-129">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ba530-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ba530-130">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ba530-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
