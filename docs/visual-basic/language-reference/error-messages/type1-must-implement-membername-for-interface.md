---
title: <type1>"<typename>musí implementovat<membername>'pro rozhraní'<interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 485680a2984a29037b2836fcba13cf1aa1e2e699
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822749"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="6028e-102">\<Type1 >'\<typename >' musí implementovat '\<membername > "rozhraní"\<interfacename > "</span><span class="sxs-lookup"><span data-stu-id="6028e-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="6028e-103">"\<typename >' musí implementovat '\<membername >" rozhraní "\<interfacename >'.</span><span class="sxs-lookup"><span data-stu-id="6028e-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="6028e-104">Implementující vlastnost musí mít odpovídající 'ReadOnly' / specifikátory 'Jen pro zápis'.</span><span class="sxs-lookup"><span data-stu-id="6028e-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="6028e-105">Třída nebo struktura, deklarací identity pro implementaci rozhraní, ale neimplementuje proceduru, vlastnost nebo událost definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6028e-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="6028e-106">Musíte implementovat každého člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6028e-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="6028e-107">**ID chyby:** BC30154</span><span class="sxs-lookup"><span data-stu-id="6028e-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6028e-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6028e-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="6028e-109">Deklarujte člena se stejným názvem a signaturou, jak jsou definovány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6028e-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="6028e-110">Nezapomeňte uvést alespoň `End Function`, `End Sub`, nebo `End Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6028e-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="6028e-111">Přidat `Implements` klauzuli na konec objektu `Function`, `Sub`, `Property`, nebo `Event` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6028e-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="6028e-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6028e-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="6028e-113">Při implementaci vlastnost, ujistěte se, že `ReadOnly` nebo `WriteOnly` se používá stejným způsobem jako v definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6028e-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="6028e-114">Při implementaci vlastnost, deklarujte `Get` a `Set` postupy, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6028e-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6028e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6028e-115">See also</span></span>

- [<span data-ttu-id="6028e-116">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="6028e-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="6028e-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="6028e-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
