---
title: "Název &lt;parametr namespacename&gt; v kořenového oboru názvů &lt;fullnamespacename&gt; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7342c7e85cce6c0e5892c4ad1826907dc03ed808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="b2fdc-102">Název &lt;parametr namespacename&gt; v kořenového oboru názvů &lt;fullnamespacename&gt; není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="b2fdc-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="b2fdc-103">Sestavení je označena jako `<CLSCompliant(True)>`, ale element název kořenového oboru názvů začíná podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="b2fdc-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="b2fdc-104">Programovací element může obsahovat jeden nebo více podtržítka, ale aby byly kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/12a7a7h3) (CLS), se nesmí začínat podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="b2fdc-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="b2fdc-105">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b2fdc-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="b2fdc-106">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="b2fdc-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="b2fdc-107">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2fdc-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="b2fdc-108">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="b2fdc-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="b2fdc-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="b2fdc-109">By default, this message is a warning.</span></span> <span data-ttu-id="b2fdc-110">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b2fdc-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b2fdc-111">**ID chyby:** BC40039</span><span class="sxs-lookup"><span data-stu-id="b2fdc-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2fdc-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b2fdc-112">To correct this error</span></span>  
  
-   <span data-ttu-id="b2fdc-113">Pokud budete potřebovat souladu se specifikací CLS, změňte název kořenového oboru názvů tak, aby žádný z jejích elementů začíná podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="b2fdc-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="b2fdc-114">Pokud budete potřebovat, že název oboru názvů zůstanou beze změny, potom odeberte <xref:System.CLSCompliantAttribute> ze sestavení nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="b2fdc-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2fdc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2fdc-115">See Also</span></span>  
 [<span data-ttu-id="b2fdc-116">Namespace – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2fdc-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="b2fdc-117">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2fdc-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="b2fdc-118">/ RootNamespace</span><span class="sxs-lookup"><span data-stu-id="b2fdc-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [<span data-ttu-id="b2fdc-119">Stránka aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2fdc-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="b2fdc-120">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="b2fdc-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="b2fdc-121">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2fdc-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="b2fdc-122">\<PAVE přes > zápis kompatibilní se specifikací CLS kódu</span><span class="sxs-lookup"><span data-stu-id="b2fdc-122">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
