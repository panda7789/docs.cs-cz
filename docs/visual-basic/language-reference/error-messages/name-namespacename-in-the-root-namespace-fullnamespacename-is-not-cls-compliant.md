---
title: Název <namespacename> v kořenovém oboru názvů <fullnamespacename> není kompatibilní se specifikací.
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: faed46eaf21513945ef4eb0c76d36780e960d380
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592027"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="11702-102">Název \<namespacename > v kořenovém oboru názvů \<fullnamespacename > není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="11702-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="11702-103">Sestavení je označen jako `<CLSCompliant(True)>`, ale element název kořenového oboru názvů začíná podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="11702-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="11702-104">Programovací element může obsahovat jeden nebo více podtržítka, ale chcete-li být kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), se nesmí začínat podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="11702-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="11702-105">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="11702-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="11702-106">Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="11702-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="11702-107">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="11702-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="11702-108">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="11702-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="11702-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="11702-109">By default, this message is a warning.</span></span> <span data-ttu-id="11702-110">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="11702-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="11702-111">**ID chyby:** BC40039</span><span class="sxs-lookup"><span data-stu-id="11702-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11702-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="11702-112">To correct this error</span></span>  
  
- <span data-ttu-id="11702-113">Pokud budete vyžadovat dodržování specifikace CLS, změňte název kořenového oboru názvů tak, aby žádný z jeho prvků začíná podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="11702-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="11702-114">Pokud budete vyžadovat, že název oboru názvů zůstanou beze změny, odstraňte <xref:System.CLSCompliantAttribute> ze sestavení nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="11702-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11702-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11702-115">See also</span></span>

- [<span data-ttu-id="11702-116">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="11702-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="11702-117">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11702-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="11702-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="11702-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="11702-119">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11702-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="11702-120">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="11702-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="11702-121">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11702-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
