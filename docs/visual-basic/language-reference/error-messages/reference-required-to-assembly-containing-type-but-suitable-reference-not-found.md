---
title: Odkaz vyžadoval sestavení '<assemblyidentity>' obsahující typ '<typename>'. Nebylo však možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty '<projectname1>' a '<projectname2>'.
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 4b9f74f0627268752b0ba3c3816fe9d4cc8a231b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404820"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="41a0b-102">Odkaz vyžadoval sestavení '\<assemblyidentity>' obsahující typ '\<typename>'. Nebylo však možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty '\<projectname1>' a '\<projectname2>'.</span><span class="sxs-lookup"><span data-stu-id="41a0b-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>
<span data-ttu-id="41a0b-103">Výraz používá typ, jako je třída, struktura, rozhraní, výčet nebo delegát, které jsou definovány mimo váš projekt.</span><span class="sxs-lookup"><span data-stu-id="41a0b-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="41a0b-104">Nicméně máte odkazy na projekt na více než jedno sestavení, které definuje tento typ.</span><span class="sxs-lookup"><span data-stu-id="41a0b-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="41a0b-105">Citované projekty vytváří sestavení se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="41a0b-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="41a0b-106">Proto kompilátor nemůže určit, které sestavení se má použít pro typ, ke kterému přistupujete.</span><span class="sxs-lookup"><span data-stu-id="41a0b-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="41a0b-107">Pro přístup k typu definovanému v jiném sestavení musí mít kompilátor Visual Basic odkaz na toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="41a0b-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="41a0b-108">Musí se jednat o jediný nejednoznačný odkaz, který nezpůsobuje cyklické odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="41a0b-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="41a0b-109">**ID chyby:** BC30969</span><span class="sxs-lookup"><span data-stu-id="41a0b-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41a0b-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="41a0b-110">To correct this error</span></span>  
  
1. <span data-ttu-id="41a0b-111">Určete, který projekt vytváří nejlepší sestavení pro váš projekt k referenci.</span><span class="sxs-lookup"><span data-stu-id="41a0b-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="41a0b-112">Pro toto rozhodnutí můžete použít kritéria, jako je například snadné přístupu k souborům a četnost aktualizací.</span><span class="sxs-lookup"><span data-stu-id="41a0b-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="41a0b-113">Ve vlastnostech projektu přidejte odkaz na soubor, který obsahuje sestavení definující typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="41a0b-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a0b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="41a0b-114">See also</span></span>

- [<span data-ttu-id="41a0b-115">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="41a0b-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="41a0b-116">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="41a0b-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="41a0b-117">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="41a0b-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="41a0b-118">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="41a0b-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
