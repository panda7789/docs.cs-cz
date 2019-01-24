---
title: '&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; rozhraní &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574739"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="c2d28-102">&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; rozhraní &#39; &lt;interfacename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="c2d28-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="c2d28-103">"\<typename >' musí implementovat '\<membername >" rozhraní "\<interfacename >'.</span><span class="sxs-lookup"><span data-stu-id="c2d28-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="c2d28-104">Implementující vlastnost musí mít odpovídající 'ReadOnly' / specifikátory 'Jen pro zápis'.</span><span class="sxs-lookup"><span data-stu-id="c2d28-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="c2d28-105">Třída nebo struktura, deklarací identity pro implementaci rozhraní, ale neimplementuje proceduru, vlastnost nebo událost definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c2d28-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="c2d28-106">Musíte implementovat každého člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c2d28-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="c2d28-107">**ID chyby:** BC30154</span><span class="sxs-lookup"><span data-stu-id="c2d28-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c2d28-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c2d28-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c2d28-109">Deklarujte člena se stejným názvem a signaturou, jak jsou definovány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c2d28-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="c2d28-110">Nezapomeňte uvést alespoň `End Function`, `End Sub`, nebo `End Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c2d28-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="c2d28-111">Přidat `Implements` klauzuli na konec objektu `Function`, `Sub`, `Property`, nebo `Event` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c2d28-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="c2d28-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c2d28-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="c2d28-113">Při implementaci vlastnost, ujistěte se, že `ReadOnly` nebo `WriteOnly` se používá stejným způsobem jako v definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c2d28-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="c2d28-114">Při implementaci vlastnost, deklarujte `Get` a `Set` postupy, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c2d28-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d28-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2d28-115">See also</span></span>
- [<span data-ttu-id="c2d28-116">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="c2d28-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="c2d28-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2d28-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
