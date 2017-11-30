---
title: "Název &lt;membername&gt; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords: BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7f574c2ebd71dbe06c4a687728e7812a18c8a949
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="5bf3a-102">Název &lt;membername&gt; není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="5bf3a-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="5bf3a-103">Sestavení je označena jako `<CLSCompliant(True)>` ale zveřejňuje člena s názvem, který začíná podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="5bf3a-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="5bf3a-104">Programovací element může obsahovat jeden nebo více podtržítka, ale aby byly kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/12a7a7h3) (CLS), se nesmí začínat podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="5bf3a-105">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5bf3a-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="5bf3a-106">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5bf3a-107">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5bf3a-108">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5bf3a-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-109">By default, this message is a warning.</span></span> <span data-ttu-id="5bf3a-110">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5bf3a-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5bf3a-111">**ID chyby:** BC40031</span><span class="sxs-lookup"><span data-stu-id="5bf3a-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5bf3a-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5bf3a-112">To correct this error</span></span>  
  
-   <span data-ttu-id="5bf3a-113">Pokud budete mít kontrolu nad zdrojový kód, změňte název člena tak, aby nezačíná znakem podtržítka.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="5bf3a-114">Pokud budete potřebovat, že název člena zůstanou beze změny, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="5bf3a-115">Přesto můžete označit sestavení jako `<CLSCompliant(True)>`.</span><span class="sxs-lookup"><span data-stu-id="5bf3a-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf3a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bf3a-116">See Also</span></span>  
 [<span data-ttu-id="5bf3a-117">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="5bf3a-117">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="5bf3a-118">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bf3a-118">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="5bf3a-119">\<PAVE přes > zápis kompatibilní se specifikací CLS kódu</span><span class="sxs-lookup"><span data-stu-id="5bf3a-119">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
