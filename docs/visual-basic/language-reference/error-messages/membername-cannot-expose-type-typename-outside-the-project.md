---
title: '&#39;&lt;MemberName&gt; &#39; nemůže vystavovat typ &#39; &lt;typename&gt; &#39; mimo projekt prostřednictvím &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 39d316aca5ec306de4b1e43e2eb2d1495f5525d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672341"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="6a146-102">&#39;&lt;MemberName&gt; &#39; nemůže vystavovat typ &#39; &lt;typename&gt; &#39; mimo projekt prostřednictvím &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="6a146-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="6a146-103">Proměnná, parametr procedury nebo návratová hodnota funkce je vystaven vně svého kontejneru, ale je deklarován jako typ, který nesmí být vystaven vně kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6a146-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="6a146-104">Následující kostrou kód ukazuje situaci, která vygeneruje tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="6a146-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="6a146-105">Typ, který je deklarován `Protected`, `Friend`, `Protected Friend`, nebo `Private` má omezený přístup mimo jeho deklarace kontextu.</span><span class="sxs-lookup"><span data-stu-id="6a146-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="6a146-106">Použití jako data typu proměnné s méně omezený přístup by vůbec nemělo tento účel.</span><span class="sxs-lookup"><span data-stu-id="6a146-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="6a146-107">V předchozím kódu kostru `exposedVar` je `Public` a by vystavovat `privateClass` kódu, který by neměl mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="6a146-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="6a146-108">**ID chyby:** BC30909</span><span class="sxs-lookup"><span data-stu-id="6a146-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a146-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6a146-109">To correct this error</span></span>  
  
-   <span data-ttu-id="6a146-110">Změna úrovně přístupu proměnná, parametr procedury nebo funkce vrátit se nejméně omezující jako úroveň přístupu jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="6a146-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a146-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a146-111">See also</span></span>
- [<span data-ttu-id="6a146-112">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a146-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
