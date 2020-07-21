---
title: Dynamické vytváření a kompilování zdrojového kódu
description: Zkompilujte a generujte dynamický zdrojový kód v rozhraní .NET pomocí Code Document Object Model (CodeDOM). Prvky CodeDOM jsou propojeny, aby tvořily graf CodeDOM.
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
ms.openlocfilehash: 3cdd89ac9745f6af133ca683afff64283f2727d1
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475096"
---
# <a name="compile-and-generate-dynamic-source-code"></a><span data-ttu-id="69de7-104">Kompilovat a generovat dynamický zdrojový kód</span><span class="sxs-lookup"><span data-stu-id="69de7-104">Compile and generate dynamic source code</span></span>

<span data-ttu-id="69de7-105">.NET Framework obsahuje mechanismus nazvaný Code Document Object Model (CodeDOM), který umožňuje vývojářům programu generovat zdrojový kód pro generování zdrojového kódu v několika programovacích jazycích za běhu na základě jednoho modelu, který představuje kód pro vykreslení.</span><span class="sxs-lookup"><span data-stu-id="69de7-105">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
<span data-ttu-id="69de7-106">Aby představoval zdrojový kód, prvky CodeDOM jsou vzájemně propojeny, aby tvořily datovou strukturu známou jako graf CodeDOM, který modeluje strukturu nějakého zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="69de7-106">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
<span data-ttu-id="69de7-107"><xref:System.CodeDom?displayProperty=fullName>Obor názvů definuje typy, které mohou představovat logickou strukturu zdrojového kódu, nezávisle na konkrétním programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="69de7-107">The <xref:System.CodeDom?displayProperty=fullName> namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="69de7-108"><xref:System.CodeDom.Compiler?displayProperty=fullName>Obor názvů definuje typy pro generování zdrojového kódu z grafů CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích.</span><span class="sxs-lookup"><span data-stu-id="69de7-108">The <xref:System.CodeDom.Compiler?displayProperty=fullName> namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="69de7-109">Dodavatelé a vývojáři kompilátoru můžou sadu podporovaných jazyků zvětšit.</span><span class="sxs-lookup"><span data-stu-id="69de7-109">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
<span data-ttu-id="69de7-110">Modelování zdrojového kódu nezávislého na jazyce může být užitečné, když program potřebuje vygenerovat zdrojový kód pro model programu v několika jazycích nebo v neurčitém cílovém jazyce.</span><span class="sxs-lookup"><span data-stu-id="69de7-110">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="69de7-111">Například někteří návrháři používají rozhraní CodeDOM jako rozhraní pro abstrakci jazyka k vytvoření zdrojového kódu ve správném programovacím jazyce, pokud je k dispozici podpora CodeDOM pro daný jazyk.</span><span class="sxs-lookup"><span data-stu-id="69de7-111">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
<span data-ttu-id="69de7-112">.NET Framework obsahuje generátory kódu a kompilátory kódu pro <xref:Microsoft.CSharp.CSharpCodeProvider> , <xref:Microsoft.JScript.JScriptCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider> .</span><span class="sxs-lookup"><span data-stu-id="69de7-112">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69de7-113">V této části</span><span class="sxs-lookup"><span data-stu-id="69de7-113">In this section</span></span>

- [<span data-ttu-id="69de7-114">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="69de7-114">Using the CodeDOM</span></span>](using-the-codedom.md)

  <span data-ttu-id="69de7-115">Popisuje běžné použití a ukazuje vytvoření jednoduchého grafu objektů pomocí CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="69de7-115">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
- [<span data-ttu-id="69de7-116">Generování zdrojového kódu a kompilace programu z grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="69de7-116">Generate Source Code and Compile a Program from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)  

  <span data-ttu-id="69de7-117">Popisuje, jak generovat zdrojový kód a zkompilovat generovaný kód s externím kompilátorem pomocí tříd definovaných v `System.CodeDom.Compiler` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="69de7-117">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
- [<span data-ttu-id="69de7-118">Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="69de7-118">How to: Create an XML Documentation File Using CodeDOM</span></span>](how-to-create-an-xml-documentation-file-using-codedom.md)  

  <span data-ttu-id="69de7-119">Popisuje, jak použít CodeDOM k vygenerování kódu s dokumentačními komentáři XML a zkompilovat generovaný kód tak, aby vytvořil výstup dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="69de7-119">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
- [<span data-ttu-id="69de7-120">Postupy: Vytváření třídy pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="69de7-120">How to: Create a Class Using CodeDOM</span></span>](how-to-create-a-class-using-codedom.md)  

  <span data-ttu-id="69de7-121">Popisuje, jak použít CodeDOM k vygenerování třídy obsahující pole, vlastnosti, metodu, konstruktor a vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="69de7-121">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="69de7-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="69de7-122">Reference</span></span>  

- <xref:System.CodeDom>  

  <span data-ttu-id="69de7-123">Definuje prvky, které reprezentují prvky kódu v programovacích jazycích, které cílí na modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="69de7-123">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
- <xref:System.CodeDom.Compiler>  

  <span data-ttu-id="69de7-124">Definuje rozhraní pro generování a kompilaci kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="69de7-124">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="69de7-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="69de7-125">Related sections</span></span>  

- <span data-ttu-id="69de7-126">[Stručný odkaz na CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) poskytuje vývojářům rychlý způsob, jak najít prvky CodeDOM, které představují prvky zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="69de7-126">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
