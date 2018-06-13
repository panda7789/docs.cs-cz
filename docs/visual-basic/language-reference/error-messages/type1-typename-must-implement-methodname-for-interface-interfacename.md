---
title: '&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;methodname&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: daeeab853f6a7f582542fa15ffc09ce749731d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594380"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="27763-102">&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;methodname&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="27763-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="27763-103">Třídu nebo strukturu pro implementaci rozhraní deklarace identity, ale neimplementuje procedury definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27763-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="27763-104">Každý člen rozhraní musí být implementována.</span><span class="sxs-lookup"><span data-stu-id="27763-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="27763-105">**ID chyby:** BC30149</span><span class="sxs-lookup"><span data-stu-id="27763-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27763-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="27763-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="27763-107">Procedura se stejným názvem a podpis definovaným v rozhraní deklarujte.</span><span class="sxs-lookup"><span data-stu-id="27763-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="27763-108">Je nutné zahrnout alespoň `End Function` nebo `End Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="27763-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="27763-109">Přidat `Implements` klauzule na konec `Function` nebo `Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="27763-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="27763-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="27763-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="27763-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="27763-111">See Also</span></span>  
 [<span data-ttu-id="27763-112">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="27763-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="27763-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="27763-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
