---
title: Odkaz vyžadoval sestavení &#39; &lt;assemblyidentity&gt; &#39; obsahující typ &#39; &lt;typename&gt;&#39;, ale nebyl nalezen vhodný odkaz z důvodu nejednoznačnosti mezi projekty &#39; &lt;projectname1&gt; &#39; a &#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69b1184d47e427bd985c3b18135d4a0ac4d91410
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="40c8d-102">Odkaz vyžadoval sestavení &#39; &lt;assemblyidentity&gt; &#39; obsahující typ &#39; &lt;typename&gt;&#39;, ale nebyl nalezen vhodný odkaz z důvodu nejednoznačnosti mezi projekty &#39; &lt;projectname1&gt; &#39; a &#39; &lt;projectname2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="40c8d-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="40c8d-103">Výraz používá typu, například třída, struktura, rozhraní, výčet nebo delegáta, který je definován mimo projekt.</span><span class="sxs-lookup"><span data-stu-id="40c8d-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="40c8d-104">Máte ale odkazy na projekt k definování typu více než jednom sestavení.</span><span class="sxs-lookup"><span data-stu-id="40c8d-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="40c8d-105">Citovaný projekty vytvořit sestavení se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="40c8d-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="40c8d-106">Kompilátor proto nemůže určit sestavení, které použije pro typ přistupují.</span><span class="sxs-lookup"><span data-stu-id="40c8d-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="40c8d-107">Chcete-li přistupovat k typu definovaný v jiném sestavení, Visual Basic – kompilátor musí mít odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="40c8d-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="40c8d-108">Toto musí být jeden jednoznačným odkaz, který nevyvolá Kruhové odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="40c8d-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="40c8d-109">**ID chyby:** BC30969</span><span class="sxs-lookup"><span data-stu-id="40c8d-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40c8d-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="40c8d-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="40c8d-111">Určete, které projektu vytvoří doporučené sestavení pro svůj projekt tak, aby odkazovaly.</span><span class="sxs-lookup"><span data-stu-id="40c8d-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="40c8d-112">Pro toto rozhodnutí můžete použít kritérií, například snadný přístup k souborům a četnost aktualizací.</span><span class="sxs-lookup"><span data-stu-id="40c8d-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="40c8d-113">Ve vlastnostech projektu přidejte odkaz na soubor, který obsahuje sestavení, která definuje typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="40c8d-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c8d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="40c8d-114">See Also</span></span>  
 [<span data-ttu-id="40c8d-115">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="40c8d-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="40c8d-116">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="40c8d-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="40c8d-117">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="40c8d-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="40c8d-118">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="40c8d-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
