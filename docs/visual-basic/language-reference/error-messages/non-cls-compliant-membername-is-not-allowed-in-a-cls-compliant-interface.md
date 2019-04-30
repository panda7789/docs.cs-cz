---
title: Člen <membername> nekompatibilní se specifikací CLS není povolen v rozhraní kompatibilním se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: dbffe2bd196e798b90104aebb74269387660c794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918200"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="96e4e-102">Non-kompatibilní se Specifikací CLS \<membername > není povolené v rozhraní kompatibilním se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="96e4e-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="96e4e-103">Vlastnost, procedura nebo událost v rozhraní je označen jako `<CLSCompliant(True)>` samotným rozhraním, když je označena jako `<CLSCompliant(False)>` nebo není označen.</span><span class="sxs-lookup"><span data-stu-id="96e4e-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="96e4e-104">V rámci rozhraní má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), všechny její členy musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="96e4e-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="96e4e-105">Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="96e4e-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="96e4e-106">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="96e4e-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="96e4e-107">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="96e4e-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="96e4e-108">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="96e4e-108">By default, this message is a warning.</span></span> <span data-ttu-id="96e4e-109">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="96e4e-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="96e4e-110">**ID chyby:** BC40033</span><span class="sxs-lookup"><span data-stu-id="96e4e-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96e4e-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="96e4e-111">To correct this error</span></span>  
  
- <span data-ttu-id="96e4e-112">Pokud se vyžadovat dodržování specifikace CLS a máte kontrolu nad rozhraní zdrojového kódu, označte rozhraní jako `<CLSCompliant(True)>` Pokud všechny její členy jsou kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="96e4e-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="96e4e-113">Pokud vyžadovat dodržování specifikace CLS a nemáte kontrolu nad rozhraní zdrojového kódu, nebo pokud nesplňuje, aby vyhovovala, definujte tohoto člena v rámci jiné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96e4e-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="96e4e-114">Pokud budete vyžadovat, že tento člen zůstat v rámci svého aktuálního rozhraní, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="96e4e-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e4e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96e4e-115">See also</span></span>

- [<span data-ttu-id="96e4e-116">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="96e4e-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
