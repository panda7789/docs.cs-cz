---
title: "& č. 39; &lt;– klíčové slovo&gt;& č. 39; je platná pouze v rámci metody instance"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords: BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="7cf2a-102">& č. 39; &lt;– klíčové slovo&gt;& č. 39; je platná pouze v rámci metody instance</span><span class="sxs-lookup"><span data-stu-id="7cf2a-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="7cf2a-103">`Me`, `MyClass`, A `MyBase` klíčová slova odkazovat na instancí určité třídy.</span><span class="sxs-lookup"><span data-stu-id="7cf2a-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="7cf2a-104">Proto je nelze použít uvnitř sdílenou `Function` nebo `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="7cf2a-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="7cf2a-105">**ID chyby:** BC30043</span><span class="sxs-lookup"><span data-stu-id="7cf2a-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7cf2a-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7cf2a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="7cf2a-107">Postup odebrání klíčové slovo nebo odebrat `Shared` – klíčové slovo z deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="7cf2a-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf2a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cf2a-108">See Also</span></span>  
 [<span data-ttu-id="7cf2a-109">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7cf2a-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="7cf2a-110">ME, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="7cf2a-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="7cf2a-111">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="7cf2a-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
