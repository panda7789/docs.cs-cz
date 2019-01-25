---
title: Proměnná &#39; &lt;NázevProměnné&gt; &#39; skrývá proměnnou v nadřízeném bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 23ec659535b71ee9af189f5c4fec0dec2bb1cd8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719427"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="2c1a1-102">Proměnná &#39; &lt;NázevProměnné&gt; &#39; skrývá proměnnou v nadřízeném bloku</span><span class="sxs-lookup"><span data-stu-id="2c1a1-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="2c1a1-103">Proměnné v bloku má stejný název jako jiná místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="2c1a1-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="2c1a1-104">**ID chyby:** BC30616</span><span class="sxs-lookup"><span data-stu-id="2c1a1-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c1a1-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2c1a1-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2c1a1-106">Přejmenujte proměnnou v uzavřeném bloku tak, že není stejný jako další místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="2c1a1-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="2c1a1-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2c1a1-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="2c1a1-108">Běžnou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="2c1a1-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="2c1a1-109">Pokud tomu tak, `Catch` proměnná bloku `ex` spíše než `e`.</span><span class="sxs-lookup"><span data-stu-id="2c1a1-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="2c1a1-110">Další běžné zdroje této chyby je pokus o přístup k místní proměnné deklarované v rámci `Try` blokovat v samostatném `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="2c1a1-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="2c1a1-111">Když to pokud chcete opravit, deklarujte proměnnou mimo `Try...Catch...Finally` struktury.</span><span class="sxs-lookup"><span data-stu-id="2c1a1-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1a1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c1a1-112">See also</span></span>
- [<span data-ttu-id="2c1a1-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="2c1a1-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="2c1a1-114">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="2c1a1-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
