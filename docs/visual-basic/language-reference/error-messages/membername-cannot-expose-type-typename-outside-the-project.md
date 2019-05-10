---
title: "'<membername>' nemůže vystavovat typ '<typename>' mimo projekt prostřednictvím <containertype> '<containertypename>'."
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: cb5191442ed8d3ee47c5116b10740e277ffa5bac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661916"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="658b0-102">"\<membername >' nemůže vystavovat typ '\<typename >' mimo projekt prostřednictvím \<containertype > '\<containertypename >"</span><span class="sxs-lookup"><span data-stu-id="658b0-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="658b0-103">Proměnná, parametr procedury nebo návratová hodnota funkce je vystaven vně svého kontejneru, ale je deklarován jako typ, který nesmí být vystaven vně kontejneru.</span><span class="sxs-lookup"><span data-stu-id="658b0-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="658b0-104">Následující kostrou kód ukazuje situaci, která vygeneruje tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="658b0-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="658b0-105">Typ, který je deklarován `Protected`, `Friend`, `Protected Friend`, nebo `Private` má omezený přístup mimo jeho deklarace kontextu.</span><span class="sxs-lookup"><span data-stu-id="658b0-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="658b0-106">Použití jako data typu proměnné s méně omezený přístup by vůbec nemělo tento účel.</span><span class="sxs-lookup"><span data-stu-id="658b0-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="658b0-107">V předchozím kódu kostru `exposedVar` je `Public` a by vystavovat `privateClass` kódu, který by neměl mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="658b0-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="658b0-108">**ID chyby:** BC30909</span><span class="sxs-lookup"><span data-stu-id="658b0-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="658b0-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="658b0-109">To correct this error</span></span>  
  
- <span data-ttu-id="658b0-110">Změna úrovně přístupu proměnná, parametr procedury nebo funkce vrátit se nejméně omezující jako úroveň přístupu jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="658b0-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658b0-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="658b0-111">See also</span></span>

- [<span data-ttu-id="658b0-112">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="658b0-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
