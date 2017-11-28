---
title: "Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; skryje proměnnou z vnějšího bloku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords: BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="0631c-102">Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; skryje proměnnou z vnějšího bloku</span><span class="sxs-lookup"><span data-stu-id="0631c-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="0631c-103">Proměnné v bloku má stejný název jako jiný místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="0631c-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="0631c-104">**ID chyby:** BC30616</span><span class="sxs-lookup"><span data-stu-id="0631c-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0631c-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0631c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="0631c-106">Přejmenujte proměnné v závorkách bloku tak, aby není stejná jako ostatní místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="0631c-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="0631c-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0631c-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="0631c-108">Obvyklou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0631c-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="0631c-109">Pokud je to tento případ, název `Catch` proměnná bloku `ex` místo `e`.</span><span class="sxs-lookup"><span data-stu-id="0631c-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="0631c-110">Další běžné zdroj této chyby je pokus o přístup k místní proměnné deklarované v rámci `Try` blokovat v samostatném `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="0631c-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="0631c-111">Chcete-li vyřešit tento problém, deklarovat proměnnou mimo `Try...Catch...Finally` struktura.</span><span class="sxs-lookup"><span data-stu-id="0631c-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0631c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0631c-112">See Also</span></span>  
 [<span data-ttu-id="0631c-113">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="0631c-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="0631c-114">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="0631c-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
