---
title: "'<membername>' nemůže vystavovat typ '<typename>' mimo projekt prostřednictvím <containertype> '<containertypename>'."
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 16f579a05236ba8977a071cb08068be8e98799f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921079"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="9ffe7-102">"\<membername >' nemůže vystavovat typ '\<typename >' mimo projekt prostřednictvím \<containertype > '\<containertypename >"</span><span class="sxs-lookup"><span data-stu-id="9ffe7-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="9ffe7-103">Proměnná, parametr procedury nebo návratová hodnota funkce je vystaven vně svého kontejneru, ale je deklarován jako typ, který nesmí být vystaven vně kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9ffe7-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="9ffe7-104">Následující kostrou kód ukazuje situaci, která vygeneruje tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="9ffe7-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="9ffe7-105">Typ, který je deklarován `Protected`, `Friend`, `Protected Friend`, nebo `Private` má omezený přístup mimo jeho deklarace kontextu.</span><span class="sxs-lookup"><span data-stu-id="9ffe7-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="9ffe7-106">Použití jako data typu proměnné s méně omezený přístup by vůbec nemělo tento účel.</span><span class="sxs-lookup"><span data-stu-id="9ffe7-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="9ffe7-107">V předchozím kódu kostru `exposedVar` je `Public` a by vystavovat `privateClass` kódu, který by neměl mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="9ffe7-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="9ffe7-108">**ID chyby:** BC30909</span><span class="sxs-lookup"><span data-stu-id="9ffe7-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ffe7-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9ffe7-109">To correct this error</span></span>  
  
- <span data-ttu-id="9ffe7-110">Změna úrovně přístupu proměnná, parametr procedury nebo funkce vrátit se nejméně omezující jako úroveň přístupu jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="9ffe7-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ffe7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ffe7-111">See also</span></span>

- [<span data-ttu-id="9ffe7-112">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ffe7-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
