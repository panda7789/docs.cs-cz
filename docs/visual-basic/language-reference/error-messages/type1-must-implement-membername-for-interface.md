---
title: <type1>'<typename>' musí implementovat '<membername>' pro rozhraní '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386851"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="81d77-102">\<type1>'\<typename>' musí implementovat '\<membername>' pro rozhraní '\<interfacename>'</span><span class="sxs-lookup"><span data-stu-id="81d77-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="81d77-103">' \<typename> ' musí implementovat ' \<membername> ' pro rozhraní ' \<interfacename> '.</span><span class="sxs-lookup"><span data-stu-id="81d77-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="81d77-104">Implementující vlastnost musí mít párové specifikátory ReadOnly a WriteOnly.</span><span class="sxs-lookup"><span data-stu-id="81d77-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="81d77-105">Deklarace třídy nebo struktury pro implementaci rozhraní, ale neimplementuje proceduru, vlastnost nebo událost definovanou rozhraním.</span><span class="sxs-lookup"><span data-stu-id="81d77-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="81d77-106">Je nutné implementovat všechny členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81d77-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="81d77-107">**ID chyby:** BC30154</span><span class="sxs-lookup"><span data-stu-id="81d77-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="81d77-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="81d77-108">To correct this error</span></span>  
  
1. <span data-ttu-id="81d77-109">Deklarujete člena se stejným názvem a signaturou, jak je definováno v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81d77-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="81d77-110">Nezapomeňte zahrnout alespoň `End Function` `End Sub` příkaz, nebo `End Property` .</span><span class="sxs-lookup"><span data-stu-id="81d77-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="81d77-111">Přidejte `Implements` klauzuli na konec `Function` `Sub` příkazu,, `Property` nebo `Event` .</span><span class="sxs-lookup"><span data-stu-id="81d77-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="81d77-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="81d77-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="81d77-113">Při implementaci vlastnosti se ujistěte, že `ReadOnly` nebo `WriteOnly` je použita stejným způsobem jako v definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81d77-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="81d77-114">Při implementaci vlastnosti, deklarujte `Get` a `Set` procedury podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="81d77-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d77-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="81d77-115">See also</span></span>

- [<span data-ttu-id="81d77-116">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="81d77-116">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="81d77-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="81d77-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
