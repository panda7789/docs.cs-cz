---
title: Odkaz vyžadoval sestavení '<assemblyidentity>' obsahující typ '<typename>'. Nebylo však možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty '<projectname1>' a '<projectname2>'.
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 9868598b32ae17ef5bfb5dd738f8a7541515f5ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013743"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="6e196-102">Odkaz vyžadoval sestavení '\<assemblyidentity >' obsahující typ "\<typename >", ale nebylo možné najít vhodný odkaz z důvodu nejednoznačnosti mezi projekty\<projectname1 > "a"\< projectname2 > "</span><span class="sxs-lookup"><span data-stu-id="6e196-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>
<span data-ttu-id="6e196-103">Výraz používá typ, jako jsou třídy, struktury, rozhraní, výčet nebo delegáta, který je definován vně vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="6e196-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="6e196-104">Máte ale odkazy na více než jedno sestavení, definice typu.</span><span class="sxs-lookup"><span data-stu-id="6e196-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="6e196-105">Citovaný projekty vytváří sestavení se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="6e196-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="6e196-106">Proto kompilátor nemůže určit sestavení, které použije pro typ přistupují.</span><span class="sxs-lookup"><span data-stu-id="6e196-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="6e196-107">Pro přístup k typ definovaný v jiném sestavení, musí mít kompilátoru jazyka Visual Basic odkazu na toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e196-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="6e196-108">Musí se jednat jednoznačnou, kompletní jeden odkaz, který nezpůsobí cyklické odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="6e196-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="6e196-109">**ID chyby:** BC30969</span><span class="sxs-lookup"><span data-stu-id="6e196-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e196-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6e196-110">To correct this error</span></span>  
  
1. <span data-ttu-id="6e196-111">Určete, který projekt vytvoří nejlepší sestavení pro projekt tak, aby odkazovaly.</span><span class="sxs-lookup"><span data-stu-id="6e196-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="6e196-112">Pro toto rozhodnutí můžete použít kritéria, jako je například usnadnění přístupu k souborům a četnosti aktualizací.</span><span class="sxs-lookup"><span data-stu-id="6e196-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="6e196-113">Ve vlastnostech vašeho projektu přidejte odkaz na soubor, který obsahuje sestavení, které definuje typ, který používáte.</span><span class="sxs-lookup"><span data-stu-id="6e196-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e196-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e196-114">See also</span></span>

- [<span data-ttu-id="6e196-115">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="6e196-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="6e196-116">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="6e196-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="6e196-117">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="6e196-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="6e196-118">Řešení potíží s poškozenými odkazy</span><span class="sxs-lookup"><span data-stu-id="6e196-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
