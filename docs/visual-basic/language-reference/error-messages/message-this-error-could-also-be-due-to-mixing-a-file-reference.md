---
title: <message> Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt pro sestavení '<assemblyname>'.
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 263e30f992ef58b0053acb2fd749d0d9186ef6b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397256"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="ed9d8-102">\<message> Tato chyba mohla být také způsobena kombinováním odkazu na soubor s odkazem na projekt pro sestavení '\<assemblyname>'.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-102">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>
<span data-ttu-id="ed9d8-103">\<message>Tato chyba může být také způsobena kombinováním odkazu na soubor s odkazem na projekt na sestavení \<assemblyname> .</span><span class="sxs-lookup"><span data-stu-id="ed9d8-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="ed9d8-104">V takovém případě nahraďte odkaz na soubor \<assemblyfilename> v projektu ' \<projectname1> ' s odkazem na projekt ' \<projectname2> '.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="ed9d8-105">Kód v projektu přistupuje ke členu jiného projektu, ale konfigurace vašeho řešení neumožňuje kompilátoru Visual Basic vyřešit odkaz.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="ed9d8-106">Pro přístup k typu definovanému v jiném sestavení musí mít kompilátor Visual Basic odkaz na toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="ed9d8-107">Musí se jednat o jediný nejednoznačný odkaz, který nezpůsobuje cyklické odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="ed9d8-108">**ID chyby:** BC30971</span><span class="sxs-lookup"><span data-stu-id="ed9d8-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ed9d8-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ed9d8-109">To correct this error</span></span>  
  
1. <span data-ttu-id="ed9d8-110">Určete, který projekt vytváří nejlepší sestavení pro váš projekt k referenci.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="ed9d8-111">Pro toto rozhodnutí můžete použít kritéria, jako je například snadné přístupu k souborům a četnost aktualizací.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="ed9d8-112">Ve vlastnostech projektu přidejte odkaz na projekt, který obsahuje sestavení definující typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="ed9d8-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed9d8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed9d8-113">See also</span></span>

- [<span data-ttu-id="ed9d8-114">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="ed9d8-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="ed9d8-115">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="ed9d8-115">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="ed9d8-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ed9d8-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="ed9d8-117">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="ed9d8-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
