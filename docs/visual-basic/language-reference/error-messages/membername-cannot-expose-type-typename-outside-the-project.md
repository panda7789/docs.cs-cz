---
title: "'<membername>' nemůže vystavovat typ '<typename>' mimo projekt prostřednictvím <containertype> '<containertypename>'."
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: ca67e74d7790352bd1842cb8a59fe1525af6e18c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700903"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="a3c5e-102">' \<membername > ' nemůže vystavovat typ ' \<typename > ' mimo projekt prostřednictvím \<containertype > ' \<containertypename > '</span><span class="sxs-lookup"><span data-stu-id="a3c5e-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="a3c5e-103">Proměnná, parametr procedury nebo návrat funkce jsou vystaveny mimo svůj kontejner, ale jsou deklarovány jako typ, který nesmí být vystaven mimo kontejner.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="a3c5e-104">Následující kostrový kód zobrazuje situaci, která tuto chybu generuje.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="a3c5e-105">Typ deklarovaný `Protected`, `Friend`, `Protected Friend` nebo `Private`, má mít omezený přístup mimo svůj kontext deklarace.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="a3c5e-106">Použije se jako datový typ proměnné s omezeným přístupem bez omezení.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="a3c5e-107">V předcházejícím kostrě kódu `exposedVar` je `Public` a vystavení `privateClass` kódu, který by k němu neměl mít přístup.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="a3c5e-108">**ID chyby:** BC30909</span><span class="sxs-lookup"><span data-stu-id="a3c5e-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a3c5e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a3c5e-109">To correct this error</span></span>  
  
- <span data-ttu-id="a3c5e-110">Změňte úroveň přístupu proměnné, parametru procedury nebo vraťte funkci tak, aby byla alespoň omezující jako úroveň přístupu jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c5e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3c5e-111">See also</span></span>

- [<span data-ttu-id="a3c5e-112">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3c5e-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
