---
title: '&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 37a152da06a36756b86576bad9c6c5d6a392dc8d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="82f53-102">&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení &#39; &lt;assemblyname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="82f53-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="82f53-103">\<Zpráva > tuto chybu mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení '\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="82f53-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="82f53-104">V takovém případě zkuste vyměnit odkaz na soubor '\<assemblyfilename >' v projektu '\<projectname1 >' s odkaz na projekt se\<projectname2 > ".</span><span class="sxs-lookup"><span data-stu-id="82f53-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="82f53-105">Kód ve vašem projektu přistupuje členem jiného projektu, ale konfigurace řešení neumožňuje Visual Basic – kompilátor odkaz na řešení.</span><span class="sxs-lookup"><span data-stu-id="82f53-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="82f53-106">Chcete-li přistupovat k typu definovaný v jiném sestavení, Visual Basic – kompilátor musí mít odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="82f53-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="82f53-107">Toto musí být jeden jednoznačným odkaz, který nevyvolá Kruhové odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="82f53-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="82f53-108">**ID chyby:** BC30971</span><span class="sxs-lookup"><span data-stu-id="82f53-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="82f53-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="82f53-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="82f53-110">Určete, které projektu vytvoří doporučené sestavení pro svůj projekt tak, aby odkazovaly.</span><span class="sxs-lookup"><span data-stu-id="82f53-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="82f53-111">Pro toto rozhodnutí můžete použít kritérií, například snadný přístup k souborům a četnost aktualizací.</span><span class="sxs-lookup"><span data-stu-id="82f53-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="82f53-112">Ve vlastnostech projektu přidejte odkaz na projekt, který obsahuje sestavení, která definuje typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="82f53-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f53-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="82f53-113">See Also</span></span>  
 [<span data-ttu-id="82f53-114">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="82f53-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="82f53-115">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="82f53-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="82f53-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="82f53-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="82f53-117">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="82f53-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
