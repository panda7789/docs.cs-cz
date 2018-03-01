---
title: "&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení & č. 39;&lt; AssemblyName&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fcbcc48928b1b03487f31930e3d14051ddd990a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="8cc9d-102">&lt;zpráva&gt; této chyby mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení & č. 39;&lt; AssemblyName&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="8cc9d-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="8cc9d-103">\<Zpráva > tuto chybu mohou být také kvůli kombinování odkazu na soubor s projektu odkaz na sestavení '\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="8cc9d-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="8cc9d-104">V takovém případě zkuste vyměnit odkaz na soubor '\<assemblyfilename >' v projektu '\<projectname1 >' s odkaz na projekt se\<projectname2 > ".</span><span class="sxs-lookup"><span data-stu-id="8cc9d-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="8cc9d-105">Kód ve vašem projektu přistupuje členem jiného projektu, ale neumožňuje konfiguraci vašeho řešení [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru odkaz na řešení.</span><span class="sxs-lookup"><span data-stu-id="8cc9d-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="8cc9d-106">Pro přístup k typu definovaný v jiném sestavení, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru musí mít odkaz na tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="8cc9d-106">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="8cc9d-107">Toto musí být jeden jednoznačným odkaz, který nevyvolá Kruhové odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="8cc9d-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="8cc9d-108">**ID chyby:** BC30971</span><span class="sxs-lookup"><span data-stu-id="8cc9d-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8cc9d-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8cc9d-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="8cc9d-110">Určete, které projektu vytvoří doporučené sestavení pro svůj projekt tak, aby odkazovaly.</span><span class="sxs-lookup"><span data-stu-id="8cc9d-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="8cc9d-111">Pro toto rozhodnutí můžete použít kritérií, například snadný přístup k souborům a četnost aktualizací.</span><span class="sxs-lookup"><span data-stu-id="8cc9d-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="8cc9d-112">Ve vlastnostech projektu přidejte odkaz na projekt, který obsahuje sestavení, která definuje typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="8cc9d-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc9d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cc9d-113">See Also</span></span>  
 [<span data-ttu-id="8cc9d-114">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="8cc9d-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="8cc9d-115">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="8cc9d-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="8cc9d-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="8cc9d-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="8cc9d-117">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="8cc9d-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
