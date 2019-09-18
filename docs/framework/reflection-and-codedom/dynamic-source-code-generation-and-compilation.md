---
title: Dynamické vytváření a kompilování zdrojového kódu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fb95ab7ff4fcac7169238d90637d7b83078d6dd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046103"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="f1f46-102">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="f1f46-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="f1f46-103">.NET Framework obsahuje mechanismus nazvaný Code Document Object Model (CodeDOM), který umožňuje vývojářům programu generovat zdrojový kód pro generování zdrojového kódu v několika programovacích jazycích za běhu na základě jednoho modelu, který představuje kód. pro vykreslení.</span><span class="sxs-lookup"><span data-stu-id="f1f46-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="f1f46-104">Aby představoval zdrojový kód, prvky CodeDOM jsou vzájemně propojeny, aby tvořily datovou strukturu známou jako graf CodeDOM, který modeluje strukturu nějakého zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f1f46-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="f1f46-105">`System.CodeDom` Obor názvů definuje typy, které mohou představovat logickou strukturu zdrojového kódu, nezávisle na konkrétním programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="f1f46-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="f1f46-106">`System.CodeDom.Compiler` Obor názvů definuje typy pro generování zdrojového kódu z grafů CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích.</span><span class="sxs-lookup"><span data-stu-id="f1f46-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="f1f46-107">Dodavatelé a vývojáři kompilátoru můžou sadu podporovaných jazyků zvětšit.</span><span class="sxs-lookup"><span data-stu-id="f1f46-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="f1f46-108">Modelování zdrojového kódu nezávislého na jazyce může být užitečné, když program potřebuje vygenerovat zdrojový kód pro model programu v několika jazycích nebo v neurčitém cílovém jazyce.</span><span class="sxs-lookup"><span data-stu-id="f1f46-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="f1f46-109">Například někteří návrháři používají rozhraní CodeDOM jako rozhraní pro abstrakci jazyka k vytvoření zdrojového kódu ve správném programovacím jazyce, pokud je k dispozici podpora CodeDOM pro daný jazyk.</span><span class="sxs-lookup"><span data-stu-id="f1f46-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="f1f46-110">.NET Framework obsahuje generátory kódu a kompilátory kódu pro <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="f1f46-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1f46-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f1f46-111">In This Section</span></span>  
 [<span data-ttu-id="f1f46-112">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f1f46-112">Using the CodeDOM</span></span>](using-the-codedom.md)  
 <span data-ttu-id="f1f46-113">Popisuje běžné použití a ukazuje vytvoření jednoduchého grafu objektů pomocí CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="f1f46-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="f1f46-114">Generování zdrojového kódu a kompilování programu z grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f1f46-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="f1f46-115">Popisuje, jak generovat zdrojový kód a zkompilovat generovaný kód s externím kompilátorem pomocí tříd definovaných v `System.CodeDom.Compiler` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f1f46-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="f1f46-116">Postupy: Vytvoření souboru dokumentace XML pomocí CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f1f46-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="f1f46-117">Popisuje, jak použít CodeDOM k vygenerování kódu s dokumentačními komentáři XML a zkompilovat generovaný kód tak, aby vytvořil výstup dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="f1f46-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="f1f46-118">Postupy: Vytvoření třídy pomocí CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f1f46-118">How to: Create a Class Using CodeDOM</span></span>](how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="f1f46-119">Popisuje, jak použít CodeDOM k vygenerování třídy obsahující pole, vlastnosti, metodu, konstruktor a vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="f1f46-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1f46-120">Reference</span><span class="sxs-lookup"><span data-stu-id="f1f46-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="f1f46-121">Definuje prvky, které reprezentují prvky kódu v programovacích jazycích, které cílí na modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f1f46-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="f1f46-122">Definuje rozhraní pro generování a kompilaci kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f1f46-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f1f46-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f1f46-123">Related Sections</span></span>  
 <span data-ttu-id="f1f46-124">[Rychlá referenční příručka CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f1f46-124">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>  
 <span data-ttu-id="f1f46-125">Poskytuje vývojářům rychlý způsob, jak najít prvky CodeDOM, které představují prvky zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f1f46-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
