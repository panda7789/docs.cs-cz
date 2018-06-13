---
title: Proměnná &#39; &lt;NázevProměnné&gt; &#39; skryje proměnnou z vnějšího bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595089"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="08724-102">Proměnná &#39; &lt;NázevProměnné&gt; &#39; skryje proměnnou z vnějšího bloku</span><span class="sxs-lookup"><span data-stu-id="08724-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="08724-103">Proměnné v bloku má stejný název jako jiný místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="08724-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="08724-104">**ID chyby:** BC30616</span><span class="sxs-lookup"><span data-stu-id="08724-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08724-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="08724-105">To correct this error</span></span>  
  
-   <span data-ttu-id="08724-106">Přejmenujte proměnné v závorkách bloku tak, aby není stejná jako ostatní místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="08724-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="08724-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="08724-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="08724-108">Obvyklou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="08724-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="08724-109">Pokud je to tento případ, název `Catch` proměnná bloku `ex` místo `e`.</span><span class="sxs-lookup"><span data-stu-id="08724-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="08724-110">Další běžné zdroj této chyby je pokus o přístup k místní proměnné deklarované v rámci `Try` blokovat v samostatném `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="08724-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="08724-111">Chcete-li vyřešit tento problém, deklarovat proměnnou mimo `Try...Catch...Finally` struktura.</span><span class="sxs-lookup"><span data-stu-id="08724-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08724-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="08724-112">See Also</span></span>  
 [<span data-ttu-id="08724-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="08724-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="08724-114">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="08724-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
