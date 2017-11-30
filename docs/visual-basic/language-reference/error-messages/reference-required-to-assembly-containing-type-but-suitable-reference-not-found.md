---
title: "Odkaz vyžadoval sestavení & č. 39; &lt;assemblyidentity&gt;& č. 39; obsahující typ & č. 39;&lt; TypeName&gt;& č. 39; ale nebyl nalezen vhodný odkaz z důvodu nejednoznačnosti mezi projekty & č. 39;&lt; projectname1&gt;& č. 39; a & č. 39;&lt; projectname2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04a1b16a10d2a3945d1efbe3a2bd0850f1da39fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="05000-102">Odkaz vyžadoval sestavení & č. 39; &lt;assemblyidentity&gt;& č. 39; obsahující typ & č. 39;&lt; TypeName&gt;& č. 39; ale nebyl nalezen vhodný odkaz z důvodu nejednoznačnosti mezi projekty & č. 39;&lt; projectname1&gt;& č. 39; a & č. 39;&lt; projectname2&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="05000-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="05000-103">Výraz používá typu, například třída, struktura, rozhraní, výčet nebo delegáta, který je definován mimo projekt.</span><span class="sxs-lookup"><span data-stu-id="05000-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="05000-104">Máte ale odkazy na projekt k definování typu více než jednom sestavení.</span><span class="sxs-lookup"><span data-stu-id="05000-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="05000-105">Citovaný projekty vytvořit sestavení se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="05000-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="05000-106">Kompilátor proto nemůže určit sestavení, které použije pro typ přistupují.</span><span class="sxs-lookup"><span data-stu-id="05000-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="05000-107">Pro přístup k typu definovaný v jiném sestavení, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru musí mít odkaz na tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="05000-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="05000-108">Toto musí být jeden jednoznačným odkaz, který nevyvolá Kruhové odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="05000-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="05000-109">**ID chyby:** BC30969</span><span class="sxs-lookup"><span data-stu-id="05000-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05000-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="05000-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="05000-111">Určete, které projektu vytvoří doporučené sestavení pro svůj projekt tak, aby odkazovaly.</span><span class="sxs-lookup"><span data-stu-id="05000-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="05000-112">Pro toto rozhodnutí můžete použít kritérií, například snadný přístup k souborům a četnost aktualizací.</span><span class="sxs-lookup"><span data-stu-id="05000-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="05000-113">Ve vlastnostech projektu přidejte odkaz na soubor, který obsahuje sestavení, která definuje typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="05000-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05000-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="05000-114">See Also</span></span>  
 [<span data-ttu-id="05000-115">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="05000-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="05000-116">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="05000-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="05000-117">NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="05000-117">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="05000-118">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="05000-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="05000-119">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="05000-119">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
