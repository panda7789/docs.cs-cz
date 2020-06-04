---
title: Název <membername> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 45c9332237dffc7311daeedaf36035d9e9958415
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397178"
---
# <a name="name-membername-is-not-cls-compliant"></a><span data-ttu-id="f498e-102">Název \<membername> není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="f498e-102">Name \<membername> is not CLS-compliant</span></span>
<span data-ttu-id="f498e-103">Sestavení je označeno jako, `<CLSCompliant(True)>` ale zpřístupňuje člena s názvem, který začíná podtržítkem ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="f498e-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="f498e-104">Programovací prvek může obsahovat jedno nebo více podtržítek, ale aby splňovaly [jazykovou nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), nesmí začínat podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="f498e-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="f498e-105">Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f498e-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="f498e-106">Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="f498e-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="f498e-107">Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f498e-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="f498e-108">Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="f498e-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="f498e-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="f498e-109">By default, this message is a warning.</span></span> <span data-ttu-id="f498e-110">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f498e-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f498e-111">**ID chyby:** BC40031</span><span class="sxs-lookup"><span data-stu-id="f498e-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f498e-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f498e-112">To correct this error</span></span>  
  
- <span data-ttu-id="f498e-113">Pokud máte kontrolu nad zdrojovým kódem, změňte název členu tak, aby nezačínal podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="f498e-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
- <span data-ttu-id="f498e-114">Pokud vyžadujete, aby název členu zůstal beze změny, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo ho označte jako `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="f498e-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="f498e-115">Můžete přesto označit sestavení jako `<CLSCompliant(True)>` .</span><span class="sxs-lookup"><span data-stu-id="f498e-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f498e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f498e-116">See also</span></span>

- [<span data-ttu-id="f498e-117">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="f498e-117">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="f498e-118">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f498e-118">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
