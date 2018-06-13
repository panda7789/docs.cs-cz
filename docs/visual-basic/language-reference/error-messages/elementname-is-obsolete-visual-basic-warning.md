---
title: '&#39;&lt;Vlastnost elementname&gt; &#39; je zastaralé (upozornění Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 4dc2d0b8eace9bc411a344b4f2c4c79f7e09ac22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586767"
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="1f400-102">&#39;&lt;Vlastnost elementname&gt; &#39; je zastaralé (upozornění Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f400-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="1f400-103">Příkaz pokusí o přístup k programovací element, který byl označen s <xref:System.ObsoleteAttribute> atribut a direktiva považováno za upozornění.</span><span class="sxs-lookup"><span data-stu-id="1f400-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="1f400-104">Můžete označit jakékoli programovací element se už používá použitím <xref:System.ObsoleteAttribute> k němu.</span><span class="sxs-lookup"><span data-stu-id="1f400-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="1f400-105">Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost, která má buď `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="1f400-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="1f400-106">Pokud je nastavena na `True`, kompilátor zpracovává pokus o použití elementu za chybu.</span><span class="sxs-lookup"><span data-stu-id="1f400-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="1f400-107">Pokud je nastavena na `False`, nebo ho nechte výchozí `False`, kompilátor vydá upozornění, pokud dojde pokusu o použití elementu.</span><span class="sxs-lookup"><span data-stu-id="1f400-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="1f400-108">Ve výchozím nastavení, tato zpráva je upozornění, protože <xref:System.ObsoleteAttribute.IsError%2A> vlastnost <xref:System.ObsoleteAttribute> je `False`.</span><span class="sxs-lookup"><span data-stu-id="1f400-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="1f400-109">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1f400-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1f400-110">**ID chyby:** BC40008</span><span class="sxs-lookup"><span data-stu-id="1f400-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1f400-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1f400-111">To correct this error</span></span>  
  
-   <span data-ttu-id="1f400-112">Ujistěte se, že je odkaz na zdrojový kód pravopis název elementu správně.</span><span class="sxs-lookup"><span data-stu-id="1f400-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f400-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f400-113">See Also</span></span>  
 [<span data-ttu-id="1f400-114">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="1f400-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
