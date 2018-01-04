---
title: "Non kompatibilní se specifikací CLS &lt;membername&gt; není povolen v rozhraní, které je kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords: BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74744b89ad72b6fd051f83ba38354d0a277555c8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="18401-102">Non kompatibilní se specifikací CLS &lt;membername&gt; není povolen v rozhraní, které je kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="18401-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="18401-103">Vlastnost, postup nebo události v rozhraní je označena jako `<CLSCompliant(True)>` rozhraní samotné, když je označena jako `<CLSCompliant(False)>` nebo není označen.</span><span class="sxs-lookup"><span data-stu-id="18401-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="18401-104">Pro rozhraní splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí být všichni její členové v souladu.</span><span class="sxs-lookup"><span data-stu-id="18401-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="18401-105">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="18401-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="18401-106">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="18401-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="18401-107">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="18401-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="18401-108">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="18401-108">By default, this message is a warning.</span></span> <span data-ttu-id="18401-109">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="18401-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="18401-110">**ID chyby:** BC40033</span><span class="sxs-lookup"><span data-stu-id="18401-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18401-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="18401-111">To correct this error</span></span>  
  
-   <span data-ttu-id="18401-112">Pokud se vyžadují souladu se specifikací CLS a máte kontrolu nad zdrojový kód rozhraní, označit rozhraní jako `<CLSCompliant(True)>` Pokud předpisům všichni její členové.</span><span class="sxs-lookup"><span data-stu-id="18401-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="18401-113">Pokud vyžadují souladu se specifikací CLS a nemáte kontrolu nad zdrojový kód rozhraní, nebo pokud nesplňuje podmínky tak, aby vyhovoval, zadejte tento člen v rámci jiné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18401-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="18401-114">Pokud požadujete, aby tento člen zůstat v rámci jeho aktuální rozhraní, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="18401-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18401-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="18401-115">See Also</span></span>  
 [<span data-ttu-id="18401-116">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="18401-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
