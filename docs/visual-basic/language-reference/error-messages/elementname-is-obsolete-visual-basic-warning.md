---
title: Element '<elementname>' je zastaralý (upozornění jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 545f0f4a56e72e32d2225217225d441a10f0e52e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836360"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="aeb3c-102">"\<elementname >' je zastaralý (upozornění jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aeb3c-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="aeb3c-103">Příkaz se pokusí o přístup k programový element, která byla označena atributem <xref:System.ObsoleteAttribute> atribut a směrnice s ní zacházet jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="aeb3c-104">Můžete označit libovolný programovací element jako se už používá použitím <xref:System.ObsoleteAttribute> k němu.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="aeb3c-105">Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost buď `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="aeb3c-106">Pokud ji nastavíte na `True`, kompilátor zpracovává pokus o použití prvku za chybu.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="aeb3c-107">Pokud ji nastavíte na `False`, nebo jej jako výchozí `False`, kompilátor vyvolá upozornění, pokud se pokus o použití elementu.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="aeb3c-108">Ve výchozím nastavení, je tato zpráva upozornění, protože <xref:System.ObsoleteAttribute.IsError%2A> vlastnost <xref:System.ObsoleteAttribute> je `False`.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="aeb3c-109">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="aeb3c-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="aeb3c-110">**ID chyby:** BC40008</span><span class="sxs-lookup"><span data-stu-id="aeb3c-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aeb3c-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aeb3c-111">To correct this error</span></span>  
  
-   <span data-ttu-id="aeb3c-112">Ujistěte se, že odkaz zdrojového kódu je správně kontroly pravopisu název elementu.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb3c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aeb3c-113">See also</span></span>

- [<span data-ttu-id="aeb3c-114">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="aeb3c-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
