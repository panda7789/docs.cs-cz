---
description: -define (možnosti kompilátoru C#)
title: -define (možnosti kompilátoru C#)
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
ms.openlocfilehash: 3b7a1c6e92d2c60ce289f29044774c3aa42ca84f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125875"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="3106e-103">-define (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3106e-103">-define (C# Compiler Options)</span></span>
<span data-ttu-id="3106e-104">Možnost **-define** definuje `name` jako symbol ve všech souborech zdrojového kódu váš program.</span><span class="sxs-lookup"><span data-stu-id="3106e-104">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3106e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3106e-105">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3106e-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3106e-106">Arguments</span></span>  
 <span data-ttu-id="3106e-107">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="3106e-107">`name`, `name2`</span></span>  
 <span data-ttu-id="3106e-108">Název jednoho nebo více symbolů, které chcete definovat.</span><span class="sxs-lookup"><span data-stu-id="3106e-108">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3106e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3106e-109">Remarks</span></span>  
 <span data-ttu-id="3106e-110">Možnost **-define** má stejný účinek jako použití direktivy preprocesoru [#define](../preprocessor-directives/preprocessor-define.md) s tím rozdílem, že možnost kompilátoru je platná pro všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="3106e-110">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="3106e-111">Symbol zůstane definován ve zdrojovém souboru, dokud direktiva [#undef](../preprocessor-directives/preprocessor-undef.md) ve zdrojovém souboru definici odstraní.</span><span class="sxs-lookup"><span data-stu-id="3106e-111">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="3106e-112">Použijete-li možnost-define, `#undef` direktiva v jednom souboru nemá žádný vliv na jiné soubory zdrojového kódu v projektu.</span><span class="sxs-lookup"><span data-stu-id="3106e-112">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="3106e-113">Můžete použít symboly vytvořené pomocí této možnosti s [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)a [#endif](../preprocessor-directives/preprocessor-endif.md) ke podmíněnému kompilování zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="3106e-113">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="3106e-114">**-d** je krátká forma **definice**.</span><span class="sxs-lookup"><span data-stu-id="3106e-114">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="3106e-115">Můžete definovat více symbolů pomocí operátoru **-define** pomocí středníku nebo čárky pro oddělení názvů symbolů.</span><span class="sxs-lookup"><span data-stu-id="3106e-115">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="3106e-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3106e-116">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="3106e-117">Kompilátor jazyka C# sám nedefinuje žádné symboly nebo makra, které lze použít ve zdrojovém kódu; všechny definice symbolů musí být definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3106e-117">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3106e-118">Jazyk C# `#define` nepovoluje, aby se symbolu předala hodnota, jako v jazycích, jako je například C++.</span><span class="sxs-lookup"><span data-stu-id="3106e-118">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="3106e-119">Například `#define` nelze použít k vytvoření makra nebo k definování konstanty.</span><span class="sxs-lookup"><span data-stu-id="3106e-119">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="3106e-120">Pokud potřebujete definovat konstantu, použijte `enum` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="3106e-120">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="3106e-121">Chcete-li vytvořit makro stylu C++, zvažte alternativy jako obecné.</span><span class="sxs-lookup"><span data-stu-id="3106e-121">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="3106e-122">Vzhledem k tomu, že makra jsou obvykle odlaďuje náchylné k chybám, C# nepovoluje jejich použití, ale poskytuje bezpečnější alternativy.</span><span class="sxs-lookup"><span data-stu-id="3106e-122">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3106e-123">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3106e-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3106e-124">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="3106e-124">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3106e-125">Na kartě **sestavení** zadejte symbol, který má být definován v poli **symboly podmíněné kompilace** .</span><span class="sxs-lookup"><span data-stu-id="3106e-125">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="3106e-126">Například pokud používáte následující příklad kódu, stačí zadat `xx` do textového pole.</span><span class="sxs-lookup"><span data-stu-id="3106e-126">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="3106e-127">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A> .</span><span class="sxs-lookup"><span data-stu-id="3106e-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3106e-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="3106e-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3106e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="3106e-129">See also</span></span>

- [<span data-ttu-id="3106e-130">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="3106e-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3106e-131">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3106e-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
