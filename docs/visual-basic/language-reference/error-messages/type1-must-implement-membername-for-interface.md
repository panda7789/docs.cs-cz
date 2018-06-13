---
title: '&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 0f93bd137bdc21268cbca139ae739843561350ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596743"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="4d22d-102">&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="4d22d-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="4d22d-103">'\<typename >' musí implementovat '\<členské jméno > "pro rozhraní '\<interfacename >'.</span><span class="sxs-lookup"><span data-stu-id="4d22d-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="4d22d-104">Implementace vlastností musí mít odpovídající "jen pro čtení, nebo specifikátory 'WriteOnly'.</span><span class="sxs-lookup"><span data-stu-id="4d22d-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="4d22d-105">Třídu nebo strukturu pro implementaci rozhraní deklarace identity, ale neimplementuje postupu, vlastnost nebo událostí, které jsou definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d22d-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="4d22d-106">Každý člen rozhraní musí být implementována.</span><span class="sxs-lookup"><span data-stu-id="4d22d-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="4d22d-107">**ID chyby:** BC30154</span><span class="sxs-lookup"><span data-stu-id="4d22d-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d22d-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4d22d-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="4d22d-109">Člena se stejným názvem a podpis definovaným v rozhraní deklarujte.</span><span class="sxs-lookup"><span data-stu-id="4d22d-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="4d22d-110">Je nutné zahrnout alespoň `End Function`, `End Sub`, nebo `End Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4d22d-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="4d22d-111">Přidat `Implements` klauzule na konec `Function`, `Sub`, `Property`, nebo `Event` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4d22d-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="4d22d-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4d22d-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="4d22d-113">Při implementaci vlastnost, ujistěte se, že `ReadOnly` nebo `WriteOnly` se používá stejným způsobem jako definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d22d-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="4d22d-114">Při implementaci vlastnost, deklarovat `Get` a `Set` postupy, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="4d22d-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d22d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d22d-115">See Also</span></span>  
 [<span data-ttu-id="4d22d-116">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="4d22d-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="4d22d-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d22d-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
