---
title: Člen <membername> nekompatibilní se specifikací CLS není povolen v rozhraní kompatibilním se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409397"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="4794b-102">Člen \<membername> nekompatibilní se specifikací CLS není povolen v rozhraní kompatibilním se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="4794b-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="4794b-103">Vlastnost, procedura nebo událost v rozhraní je označena jako, `<CLSCompliant(True)>` když je samotné rozhraní označeno jako `<CLSCompliant(False)>` nebo není označeno.</span><span class="sxs-lookup"><span data-stu-id="4794b-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="4794b-104">Aby rozhraní splňovalo [jazykovou nezávislost a součásti nezávislé na jazyce](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí být všechny jeho členy kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4794b-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="4794b-105">Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="4794b-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="4794b-106">Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4794b-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="4794b-107">Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4794b-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="4794b-108">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="4794b-108">By default, this message is a warning.</span></span> <span data-ttu-id="4794b-109">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4794b-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4794b-110">**ID chyby:** BC40033</span><span class="sxs-lookup"><span data-stu-id="4794b-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4794b-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4794b-111">To correct this error</span></span>  
  
- <span data-ttu-id="4794b-112">Pokud požadujete kompatibilitu se specifikací CLS a máte kontrolu nad zdrojovým kódem rozhraní, označte rozhraní jako, `<CLSCompliant(True)>` Pokud jsou všechny jeho členy kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4794b-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="4794b-113">Pokud požadujete kompatibilitu se specifikací CLS a nemáte kontrolu nad zdrojovým kódem rozhraní nebo pokud nesplňuje předpisy, definujte tohoto člena v jiném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4794b-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="4794b-114">Pokud vyžadujete, aby tento člen zůstal v rámci aktuálního rozhraní, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo ho označte jako `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="4794b-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4794b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4794b-115">See also</span></span>

- [<span data-ttu-id="4794b-116">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="4794b-116">Interface Statement</span></span>](../statements/interface-statement.md)
