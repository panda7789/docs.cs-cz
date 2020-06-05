---
title: Proměnná '<variablename>' skrývá proměnnou z vnějšího bloku.
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 474a920c9cfdfba7a8157320d9c88b8677958425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406518"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="870d7-102">Proměnná '\<variablename>' skrývá proměnnou z vnějšího bloku.</span><span class="sxs-lookup"><span data-stu-id="870d7-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="870d7-103">Proměnná uzavřená v bloku má stejný název jako jiná místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="870d7-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="870d7-104">**ID chyby:** BC30616</span><span class="sxs-lookup"><span data-stu-id="870d7-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="870d7-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="870d7-105">To correct this error</span></span>  
  
- <span data-ttu-id="870d7-106">Přejmenujte proměnnou v uzavřeném bloku tak, že se neshoduje s jinými místními proměnnými.</span><span class="sxs-lookup"><span data-stu-id="870d7-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="870d7-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="870d7-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="870d7-108">Běžnou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="870d7-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="870d7-109">Pokud se jedná o tento případ, pojmenujte `Catch` blokovou proměnnou `ex` místo `e` .</span><span class="sxs-lookup"><span data-stu-id="870d7-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="870d7-110">Dalším běžným zdrojem této chyby je pokus o přístup k místní proměnné deklarované `Try` v bloku v samostatném `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="870d7-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="870d7-111">Chcete-li tento problém opravit, deklarujte proměnnou mimo `Try...Catch...Finally` strukturu.</span><span class="sxs-lookup"><span data-stu-id="870d7-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870d7-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="870d7-112">See also</span></span>

- [<span data-ttu-id="870d7-113">Try...Catch....Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="870d7-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="870d7-114">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="870d7-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
