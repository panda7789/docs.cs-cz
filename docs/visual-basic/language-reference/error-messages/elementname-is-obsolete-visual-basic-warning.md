---
title: Element '<elementname>' je zastaralý (upozornění jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 7914bc859966e17f3da41c9a13a01573b31baf91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409670"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="d2ba1-102">Element '\<elementname>' je zastaralý (upozornění jazyka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d2ba1-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="d2ba1-103">Příkaz se pokusí o přístup k programovacímu prvku, který byl označen <xref:System.ObsoleteAttribute> atributem a direktivou, aby byl považován za upozornění.</span><span class="sxs-lookup"><span data-stu-id="d2ba1-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="d2ba1-104">Můžete označit libovolný prvek programování, který se už nepoužívá, a to tak, že <xref:System.ObsoleteAttribute> se na něj aplikuje.</span><span class="sxs-lookup"><span data-stu-id="d2ba1-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="d2ba1-105">Pokud to uděláte, můžete vlastnost atributu nastavit <xref:System.ObsoleteAttribute.IsError%2A> na buď `True` nebo `False` .</span><span class="sxs-lookup"><span data-stu-id="d2ba1-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="d2ba1-106">Nastavíte-li na `True` , kompilátor považuje pokus o použití prvku jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d2ba1-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="d2ba1-107">Nastavíte-li na `False` nebo jako výchozí `False` , kompilátor vydá upozornění, pokud dojde k pokusu o použití prvku.</span><span class="sxs-lookup"><span data-stu-id="d2ba1-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="d2ba1-108">Ve výchozím nastavení je tato zpráva upozornění, protože <xref:System.ObsoleteAttribute.IsError%2A> vlastnost <xref:System.ObsoleteAttribute> je `False` .</span><span class="sxs-lookup"><span data-stu-id="d2ba1-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="d2ba1-109">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d2ba1-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d2ba1-110">**ID chyby:** BC40008</span><span class="sxs-lookup"><span data-stu-id="d2ba1-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2ba1-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d2ba1-111">To correct this error</span></span>  
  
- <span data-ttu-id="d2ba1-112">Zajistěte, aby měl odkaz na zdrojový kód pravopis názvu elementu správně.</span><span class="sxs-lookup"><span data-stu-id="d2ba1-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ba1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2ba1-113">See also</span></span>

- [<span data-ttu-id="d2ba1-114">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="d2ba1-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
