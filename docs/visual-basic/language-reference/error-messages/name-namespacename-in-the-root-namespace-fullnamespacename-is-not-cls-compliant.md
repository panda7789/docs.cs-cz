---
title: Název <namespacename> v kořenovém oboru názvů <fullnamespacename> není kompatibilní se specifikací.
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 821044d3ee359a052fa6a763e9c5a89da5d6f607
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775572"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="2b5a8-102">Název \<namespacename > v kořenovém oboru názvů \<fullnamespacename > není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="2b5a8-103">Sestavení je označeno jako `<CLSCompliant(True)>`, ale element názvu kořenového oboru názvů začíná podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="2b5a8-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="2b5a8-104">Programovací prvek může obsahovat jedno nebo více podtržítek, ale aby splňovaly [jazykovou nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), nesmí začínat podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="2b5a8-105">Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="2b5a8-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="2b5a8-106">Použijete-li <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte parametr `isCompliant` atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="2b5a8-107">Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="2b5a8-108">Pokud nepoužijete <xref:System.CLSCompliantAttribute> na prvek, považuje se za nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="2b5a8-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-109">By default, this message is a warning.</span></span> <span data-ttu-id="2b5a8-110">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2b5a8-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2b5a8-111">**ID chyby:** BC40039</span><span class="sxs-lookup"><span data-stu-id="2b5a8-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2b5a8-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2b5a8-112">To correct this error</span></span>  
  
- <span data-ttu-id="2b5a8-113">Pokud požadujete kompatibilitu se specifikací CLS, změňte název kořenového oboru názvů tak, aby žádný z jeho elementů nezačínal podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="2b5a8-114">Pokud vyžadujete, aby název oboru názvů zůstal beze změny, odeberte <xref:System.CLSCompliantAttribute> ze sestavení nebo jej označte jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="2b5a8-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b5a8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b5a8-115">See also</span></span>

- [<span data-ttu-id="2b5a8-116">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="2b5a8-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="2b5a8-117">Obory názvů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b5a8-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="2b5a8-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="2b5a8-118">-rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="2b5a8-119">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b5a8-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="2b5a8-120">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="2b5a8-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="2b5a8-121">Visual Basic konvence pojmenování</span><span class="sxs-lookup"><span data-stu-id="2b5a8-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
