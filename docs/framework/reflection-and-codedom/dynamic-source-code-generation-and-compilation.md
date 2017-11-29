---
title: "Dynamické vytváření a kompilování zdrojového kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1eb17af8fef96f42973e65859bd17b1e835fa98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="1f914-102">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="1f914-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="1f914-103">Mechanismus volat Code Document Object Model (CodeDOM), která umožňuje vývojářům programy, které emitování zdrojového kódu ke generování zdrojového kódu ve více programovacích jazyků v době běhu na základě jednoho modelu, který představuje kód zahrnuje rozhraní .NET Framework k vykreslení.</span><span class="sxs-lookup"><span data-stu-id="1f914-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="1f914-104">Představují zdrojového kódu, CodeDOM elementy propojené s druhým k formuláři Datová struktura známé jako grafu modelu CodeDOM, který modelů strukturu některé zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1f914-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="1f914-105">`System.CodeDom` Obor názvů definuje typy, které může představovat logické struktury zdrojového kódu nezávislé na konkrétní programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="1f914-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="1f914-106">`System.CodeDom.Compiler` Obor názvů definuje typy pro generování zdrojového kódu z grafů CodeDOM a správu kompilace zdrojového kódu v podporovaných jazycích.</span><span class="sxs-lookup"><span data-stu-id="1f914-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="1f914-107">Dodavatelé kompilátoru a vývojářům můžete rozšířit sadu podporovaných jazyků.</span><span class="sxs-lookup"><span data-stu-id="1f914-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="1f914-108">Modelování nezávislé na jazyku zdrojového kódu může být užitečné, když program potřebuje ke generování zdrojového kódu pro model program v několika jazycích nebo neví cílový jazyk.</span><span class="sxs-lookup"><span data-stu-id="1f914-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="1f914-109">Například některé návrháři používají modelu CodeDOM jako jazyk abstrakce rozhraní k vytvoření zdrojového kódu ve správné programovací jazyk, pokud je k dispozici podpora CodeDOM pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="1f914-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="1f914-110">Rozhraní .NET Framework zahrnuje generátory kódu a kompilátory kódu pro <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="1f914-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f914-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1f914-111">In This Section</span></span>  
 [<span data-ttu-id="1f914-112">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f914-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="1f914-113">Popisuje běžná použití a ukazuje vytvoření jednoduchého objektu graf pomocí modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1f914-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="1f914-114">Generování zdrojového kódu a kompilace programu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f914-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="1f914-115">Popisuje, jak generovat zdrojový kód a kompilace generovaného kódu s externí kompilátoru pomocí třídy definované v `System.CodeDom.Compiler` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1f914-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="1f914-116">Postupy: vytváření souborů dokumentace XML pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f914-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="1f914-117">Popisuje postup generování kódu s XML – dokumentační komentáře a kompilace generovaného kódu tak, aby vytvoří výstupní dokumentace XML pomocí modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1f914-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="1f914-118">Postupy: vytváření třídy pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1f914-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="1f914-119">Popisuje, jak můžete vygenerovat třída obsahující pole, vlastností, metoda, konstruktor a vstupního bodu pomocí modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1f914-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1f914-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1f914-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="1f914-121">Definuje prvky, které představují elementy kódu v programovací jazyky cílených modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1f914-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="1f914-122">Definuje rozhraní pro generování a kompilace kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1f914-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f914-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1f914-123">Related Sections</span></span>  
 [<span data-ttu-id="1f914-124">Stručná referenční příručka modelu codeDOM</span><span class="sxs-lookup"><span data-stu-id="1f914-124">CodeDOM Quick Reference</span></span>](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 <span data-ttu-id="1f914-125">Poskytuje rychlý způsob pro vývojáře k vyhledání CodeDOM prvky, které představují elementy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1f914-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
