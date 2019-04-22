---
title: Proměnná '<variablename>' skrývá proměnnou z vnějšího bloku.
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 15c35cbb829bec782771b584ea25b111b81b5e1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827130"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="de50d-102">Proměnná '\<NázevProměnné >' skrývá proměnnou v nadřízeném bloku</span><span class="sxs-lookup"><span data-stu-id="de50d-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="de50d-103">Proměnné v bloku má stejný název jako jiná místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="de50d-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="de50d-104">**ID chyby:** BC30616</span><span class="sxs-lookup"><span data-stu-id="de50d-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="de50d-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="de50d-105">To correct this error</span></span>  
  
-   <span data-ttu-id="de50d-106">Přejmenujte proměnnou v uzavřeném bloku tak, že není stejný jako další místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="de50d-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="de50d-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="de50d-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="de50d-108">Běžnou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="de50d-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="de50d-109">Pokud tomu tak, `Catch` proměnná bloku `ex` spíše než `e`.</span><span class="sxs-lookup"><span data-stu-id="de50d-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="de50d-110">Další běžné zdroje této chyby je pokus o přístup k místní proměnné deklarované v rámci `Try` blokovat v samostatném `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="de50d-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="de50d-111">Když to pokud chcete opravit, deklarujte proměnnou mimo `Try...Catch...Finally` struktury.</span><span class="sxs-lookup"><span data-stu-id="de50d-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de50d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de50d-112">See also</span></span>

- [<span data-ttu-id="de50d-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="de50d-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="de50d-114">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="de50d-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
