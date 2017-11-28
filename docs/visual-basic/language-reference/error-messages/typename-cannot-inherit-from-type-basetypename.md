---
title: "& č. 39; &lt;typename&gt;& č. 39; nemůže Zdědit z &lt;typ&gt; & č. 39;&lt; basetypename&gt;& č. 39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords: BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="eb7bb-102">& č. 39; &lt;typename&gt;& č. 39; nemůže Zdědit z &lt;typ&gt; & č. 39;&lt; basetypename&gt;& č. 39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení</span><span class="sxs-lookup"><span data-stu-id="eb7bb-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="eb7bb-103">Třídy nebo rozhraní dědí vlastnosti ze základní třídy nebo rozhraní ale je méně omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="eb7bb-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="eb7bb-104">Například `Public` rozhraní dědí z `Friend` rozhraní, nebo `Protected` třída dědí z `Private` třídy.</span><span class="sxs-lookup"><span data-stu-id="eb7bb-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="eb7bb-105">To zpřístupňuje základní třídy nebo rozhraní pro přístup k mimo určený úroveň.</span><span class="sxs-lookup"><span data-stu-id="eb7bb-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="eb7bb-106">**ID chyby:** BC30910</span><span class="sxs-lookup"><span data-stu-id="eb7bb-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb7bb-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="eb7bb-107">To correct this error</span></span>  
  
-   <span data-ttu-id="eb7bb-108">Změníte úroveň přístupu tohoto odvozené třídy nebo rozhraní na omezující jako základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb7bb-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="eb7bb-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="eb7bb-109">-or-</span></span>  
  
-   <span data-ttu-id="eb7bb-110">Pokud budete potřebovat méně omezující úroveň přístupu, odeberte `Inherits` příkaz.</span><span class="sxs-lookup"><span data-stu-id="eb7bb-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="eb7bb-111">Nelze zdědit omezenější základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb7bb-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7bb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb7bb-112">See Also</span></span>  
 [<span data-ttu-id="eb7bb-113">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb7bb-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="eb7bb-114">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb7bb-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="eb7bb-115">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb7bb-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="eb7bb-116">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb7bb-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
