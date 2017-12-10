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
ms.openlocfilehash: 2811958df5bd0b023a2ce3b02abf85b5a23c58f6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="c47f6-102">Non kompatibilní se specifikací CLS &lt;membername&gt; není povolen v rozhraní, které je kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="c47f6-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="c47f6-103">Vlastnost, postup nebo události v rozhraní je označena jako `<CLSCompliant(True)>` rozhraní samotné, když je označena jako `<CLSCompliant(False)>` nebo není označen.</span><span class="sxs-lookup"><span data-stu-id="c47f6-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="c47f6-104">Pro rozhraní splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), musí být všichni její členové v souladu.</span><span class="sxs-lookup"><span data-stu-id="c47f6-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="c47f6-105">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="c47f6-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="c47f6-106">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c47f6-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="c47f6-107">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="c47f6-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="c47f6-108">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="c47f6-108">By default, this message is a warning.</span></span> <span data-ttu-id="c47f6-109">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c47f6-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c47f6-110">**ID chyby:** BC40033</span><span class="sxs-lookup"><span data-stu-id="c47f6-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c47f6-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c47f6-111">To correct this error</span></span>  
  
-   <span data-ttu-id="c47f6-112">Pokud se vyžadují souladu se specifikací CLS a máte kontrolu nad zdrojový kód rozhraní, označit rozhraní jako `<CLSCompliant(True)>` Pokud předpisům všichni její členové.</span><span class="sxs-lookup"><span data-stu-id="c47f6-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="c47f6-113">Pokud vyžadují souladu se specifikací CLS a nemáte kontrolu nad zdrojový kód rozhraní, nebo pokud nesplňuje podmínky tak, aby vyhovoval, zadejte tento člen v rámci jiné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c47f6-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="c47f6-114">Pokud požadujete, aby tento člen zůstat v rámci jeho aktuální rozhraní, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="c47f6-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c47f6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c47f6-115">See Also</span></span>  
 [<span data-ttu-id="c47f6-116">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="c47f6-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="c47f6-117">\<PAVE přes > zápis kompatibilní se specifikací CLS kódu</span><span class="sxs-lookup"><span data-stu-id="c47f6-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
