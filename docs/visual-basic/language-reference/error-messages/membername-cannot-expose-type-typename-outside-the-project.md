---
title: "& č. 39; &lt;membername&gt;& č. 39; nelze vystavit typ & č. 39;&lt; TypeName&gt;& č. 39; mimo projekt prostřednictvím &lt;containertype&gt; & č. 39;&lt; containertypename&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords: BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="160e6-102">& č. 39; &lt;membername&gt;& č. 39; nelze vystavit typ & č. 39;&lt; TypeName&gt;& č. 39; mimo projekt prostřednictvím &lt;containertype&gt; & č. 39;&lt; containertypename&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="160e6-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="160e6-103">Proměnnou, parametr procedury nebo funkce návratový je nezveřejní jejímu kontejneru, ale je deklarován jako typ, který nesmí být nezveřejní kontejneru.</span><span class="sxs-lookup"><span data-stu-id="160e6-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="160e6-104">Následující kód kostru ukazuje situaci, který generuje této chybě.</span><span class="sxs-lookup"><span data-stu-id="160e6-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="160e6-105">Typ, který je deklarován `Protected`, `Friend`, `Protected Friend`, nebo `Private` má mít omezený přístup mimo kontext jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="160e6-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="160e6-106">Použití jako data typ proměnné s méně omezený přístup by vůbec nemělo tento účel.</span><span class="sxs-lookup"><span data-stu-id="160e6-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="160e6-107">V předchozím kostru kódu `exposedVar` je `Public` a by vystavit `privateClass` na kód, který by neměl mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="160e6-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="160e6-108">**ID chyby:** BC30909</span><span class="sxs-lookup"><span data-stu-id="160e6-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="160e6-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="160e6-109">To correct this error</span></span>  
  
-   <span data-ttu-id="160e6-110">Změnit úroveň přístupu proměnnou, parametr procedury nebo funkce vrátí omezující jako úroveň přístupu datového typu.</span><span class="sxs-lookup"><span data-stu-id="160e6-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160e6-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="160e6-111">See Also</span></span>  
 [<span data-ttu-id="160e6-112">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="160e6-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
