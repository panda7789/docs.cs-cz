---
title: "&lt;Type1&gt;& č. 39;&lt; TypeName&gt;& č. 39; musí implementace & č. 39;&lt; MemberName&gt;& č. 39; pro rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords: BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05e0229d0259c519d4db265c017a5040b425c79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="6e62c-102">&lt;Type1&gt;& č. 39;&lt; TypeName&gt;& č. 39; musí implementace & č. 39;&lt; MemberName&gt;& č. 39; pro rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="6e62c-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="6e62c-103">'\<typename >' musí implementovat '\<členské jméno > "pro rozhraní '\<interfacename >'.</span><span class="sxs-lookup"><span data-stu-id="6e62c-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="6e62c-104">Implementace vlastností musí mít odpovídající "jen pro čtení, nebo specifikátory 'WriteOnly'.</span><span class="sxs-lookup"><span data-stu-id="6e62c-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="6e62c-105">Třídu nebo strukturu pro implementaci rozhraní deklarace identity, ale neimplementuje postupu, vlastnost nebo událostí, které jsou definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e62c-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="6e62c-106">Každý člen rozhraní musí být implementována.</span><span class="sxs-lookup"><span data-stu-id="6e62c-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="6e62c-107">**ID chyby:** BC30154</span><span class="sxs-lookup"><span data-stu-id="6e62c-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e62c-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6e62c-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="6e62c-109">Člena se stejným názvem a podpis definovaným v rozhraní deklarujte.</span><span class="sxs-lookup"><span data-stu-id="6e62c-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="6e62c-110">Je nutné zahrnout alespoň `End Function`, `End Sub`, nebo `End Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6e62c-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="6e62c-111">Přidat `Implements` klauzule na konec `Function`, `Sub`, `Property`, nebo `Event` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6e62c-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="6e62c-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6e62c-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="6e62c-113">Při implementaci vlastnost, ujistěte se, že `ReadOnly` nebo `WriteOnly` se používá stejným způsobem jako definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e62c-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="6e62c-114">Při implementaci vlastnost, deklarovat `Get` a `Set` postupy, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6e62c-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e62c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e62c-115">See Also</span></span>  
 [<span data-ttu-id="6e62c-116">Implements – příkaz</span><span class="sxs-lookup"><span data-stu-id="6e62c-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="6e62c-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e62c-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
