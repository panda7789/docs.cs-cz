---
title: Proměnná '<variablename>' skrývá proměnnou z vnějšího bloku.
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592067"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="f1a4e-102">Proměnná ' \<variablename > ' skrývá proměnnou v ohraničujícím bloku</span><span class="sxs-lookup"><span data-stu-id="f1a4e-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="f1a4e-103">Proměnná uzavřená v bloku má stejný název jako jiná místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="f1a4e-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="f1a4e-104">**ID chyby:** BC30616</span><span class="sxs-lookup"><span data-stu-id="f1a4e-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1a4e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f1a4e-105">To correct this error</span></span>  
  
- <span data-ttu-id="f1a4e-106">Přejmenujte proměnnou v uzavřeném bloku tak, že se neshoduje s jinými místními proměnnými.</span><span class="sxs-lookup"><span data-stu-id="f1a4e-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="f1a4e-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f1a4e-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="f1a4e-108">Běžnou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="f1a4e-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="f1a4e-109">Pokud se jedná o tento případ, pojmenujte blokovou proměnnou `Catch` `ex` místo `e`.</span><span class="sxs-lookup"><span data-stu-id="f1a4e-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="f1a4e-110">Dalším běžným zdrojem této chyby je pokus o přístup k místní proměnné deklarované v bloku `Try` v samostatném bloku `Catch`.</span><span class="sxs-lookup"><span data-stu-id="f1a4e-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="f1a4e-111">Chcete-li tento problém opravit, deklarujte proměnnou mimo strukturu `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="f1a4e-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a4e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1a4e-112">See also</span></span>

- [<span data-ttu-id="f1a4e-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="f1a4e-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="f1a4e-114">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="f1a4e-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
