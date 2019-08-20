---
title: -defineC# (možnosti kompilátoru)
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
ms.openlocfilehash: d56907493ed24e2ea9fa6568af7441fc81ba1a78
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606959"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="81a07-102">-defineC# (možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="81a07-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="81a07-103">Možnost **-define** definuje `name` jako symbol ve všech souborech zdrojového kódu váš program.</span><span class="sxs-lookup"><span data-stu-id="81a07-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81a07-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="81a07-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="81a07-105">Arguments</span></span>  
 <span data-ttu-id="81a07-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="81a07-106">`name`, `name2`</span></span>  
 <span data-ttu-id="81a07-107">Název jednoho nebo více symbolů, které chcete definovat.</span><span class="sxs-lookup"><span data-stu-id="81a07-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81a07-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81a07-108">Remarks</span></span>  
 <span data-ttu-id="81a07-109">Možnost **-define** má stejný účinek jako použití direktivy preprocesoru [#define](../preprocessor-directives/preprocessor-define.md) s tím rozdílem, že možnost kompilátoru je platná pro všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="81a07-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="81a07-110">Symbol zůstane definován ve zdrojovém souboru, dokud direktiva [#undef](../preprocessor-directives/preprocessor-undef.md) ve zdrojovém souboru definici odstraní.</span><span class="sxs-lookup"><span data-stu-id="81a07-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="81a07-111">Použijete-li možnost-define, `#undef` direktiva v jednom souboru nemá žádný vliv na jiné soubory zdrojového kódu v projektu.</span><span class="sxs-lookup"><span data-stu-id="81a07-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="81a07-112">Můžete použít symboly vytvořené pomocí této možnosti s [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)a [#endif](../preprocessor-directives/preprocessor-endif.md) ke podmíněnému kompilování zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="81a07-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="81a07-113">**-d** je krátká forma **definice**.</span><span class="sxs-lookup"><span data-stu-id="81a07-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="81a07-114">Můžete definovat více symbolů pomocí operátoru **-define** pomocí středníku nebo čárky pro oddělení názvů symbolů.</span><span class="sxs-lookup"><span data-stu-id="81a07-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="81a07-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="81a07-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="81a07-116">Samotný C# kompilátor nedefinuje žádné symboly nebo makra, které lze použít ve zdrojovém kódu; všechny definice symbolů musí být definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="81a07-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81a07-117">Nepovoluje, aby se k symbolu dostala hodnota, jako v jazycích, jako je C++například. C# `#define`</span><span class="sxs-lookup"><span data-stu-id="81a07-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="81a07-118">Například `#define` nelze použít k vytvoření makra nebo k definování konstanty.</span><span class="sxs-lookup"><span data-stu-id="81a07-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="81a07-119">Pokud potřebujete definovat konstantu, použijte `enum` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="81a07-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="81a07-120">Chcete-li vytvořit makro C++ stylu, zvažte alternativy jako obecné.</span><span class="sxs-lookup"><span data-stu-id="81a07-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="81a07-121">Vzhledem k tomu, že makra jsou obvykle odlaďuje náchylná k chybám, neumožňuje jejich použití, C# ale poskytuje bezpečnější alternativy.</span><span class="sxs-lookup"><span data-stu-id="81a07-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="81a07-122">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="81a07-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="81a07-123">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="81a07-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="81a07-124">Na kartě **sestavení** zadejte symbol, který má být definován v poli **symboly podmíněné kompilace** .</span><span class="sxs-lookup"><span data-stu-id="81a07-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="81a07-125">Například pokud používáte následující příklad kódu, stačí zadat `xx` do textového pole.</span><span class="sxs-lookup"><span data-stu-id="81a07-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="81a07-126">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="81a07-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81a07-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="81a07-127">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81a07-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81a07-128">See also</span></span>

- [<span data-ttu-id="81a07-129">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="81a07-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="81a07-130">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="81a07-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
