---
title: <message> Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt do sestavení '<assemblyname>.
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 951f90a9209ff31896f4426ceb75f05b012897a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335144"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="cecf3-102">\<Zpráva > Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt do sestavení '\<assemblyname >!</span><span class="sxs-lookup"><span data-stu-id="cecf3-102">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>
<span data-ttu-id="cecf3-103">\<Zpráva > Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt do sestavení '\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="cecf3-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="cecf3-104">V takovém případě zkuste vyměnit odkaz na soubor "\<assemblyfilename >' v projektu"\<projectname1 >' s odkazem na projekt '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="cecf3-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="cecf3-105">Kód ve vašem projektu přistupuje k členem jiného projektu, ale konfigurace řešení není povoleno kompilátor jazyka Visual Basic přeložit odkaz.</span><span class="sxs-lookup"><span data-stu-id="cecf3-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="cecf3-106">Pro přístup k typ definovaný v jiném sestavení, musí mít kompilátoru jazyka Visual Basic odkazu na toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="cecf3-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="cecf3-107">Musí se jednat jednoznačnou, kompletní jeden odkaz, který nezpůsobí cyklické odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="cecf3-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="cecf3-108">**ID chyby:** BC30971</span><span class="sxs-lookup"><span data-stu-id="cecf3-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cecf3-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cecf3-109">To correct this error</span></span>  
  
1. <span data-ttu-id="cecf3-110">Určete, který projekt vytvoří nejlepší sestavení pro projekt tak, aby odkazovaly.</span><span class="sxs-lookup"><span data-stu-id="cecf3-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="cecf3-111">Pro toto rozhodnutí můžete použít kritéria, jako je například usnadnění přístupu k souborům a četnosti aktualizací.</span><span class="sxs-lookup"><span data-stu-id="cecf3-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="cecf3-112">Ve vlastnostech vašeho projektu přidejte odkaz na projekt, který obsahuje sestavení, které definuje typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="cecf3-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecf3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cecf3-113">See also</span></span>

- [<span data-ttu-id="cecf3-114">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="cecf3-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="cecf3-115">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="cecf3-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="cecf3-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="cecf3-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="cecf3-117">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="cecf3-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
