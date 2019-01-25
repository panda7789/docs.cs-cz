---
title: Název &lt;membername&gt; není kompatibilní se Specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: b950be530eb80fd1c65b48e1625eb344c642d260
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626365"
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="5bab2-102">Název &lt;membername&gt; není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="5bab2-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="5bab2-103">Sestavení je označen jako `<CLSCompliant(True)>` ale zpřístupňuje člen s názvem, který začíná podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="5bab2-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="5bab2-104">Programovací element může obsahovat jeden nebo více podtržítka, ale chcete-li být kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), se nesmí začínat podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="5bab2-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="5bab2-105">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5bab2-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="5bab2-106">Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="5bab2-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5bab2-107">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5bab2-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5bab2-108">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="5bab2-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5bab2-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="5bab2-109">By default, this message is a warning.</span></span> <span data-ttu-id="5bab2-110">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5bab2-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5bab2-111">**ID chyby:** BC40031</span><span class="sxs-lookup"><span data-stu-id="5bab2-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5bab2-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5bab2-112">To correct this error</span></span>  
  
-   <span data-ttu-id="5bab2-113">Pokud budete mít kontrolu nad zdrojový kód, změňte název člena tak, aby nezačíná znakem podtržítka.</span><span class="sxs-lookup"><span data-stu-id="5bab2-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="5bab2-114">Pokud budete vyžadovat, že název člena zůstanou beze změny, odstraňte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="5bab2-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="5bab2-115">Stále můžete označit sestavení jako `<CLSCompliant(True)>`.</span><span class="sxs-lookup"><span data-stu-id="5bab2-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bab2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bab2-116">See also</span></span>
- [<span data-ttu-id="5bab2-117">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="5bab2-117">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="5bab2-118">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bab2-118">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

