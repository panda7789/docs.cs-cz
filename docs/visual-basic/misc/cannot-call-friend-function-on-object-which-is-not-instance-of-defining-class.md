---
title: Nelze volat spřátelenou funkci pro objekt, který není instancí definující třídy
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a227e5761bacc36c0682844a833e70c34582a5d3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622596"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="a6ac9-102">Nelze volat spřátelenou funkci pro objekt, který není instancí definující třídy</span><span class="sxs-lookup"><span data-stu-id="a6ac9-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="a6ac9-103">Buď se snažíte volat `Friend` postup třídy, nebo jste se pokusili získat přístup `Friend` vlastnosti nebo metody procesy nebo mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="a6ac9-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="a6ac9-104">A `Friend` procedury lze volat z modulu vně třídy, ale je součástí projektu, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="a6ac9-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6ac9-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a6ac9-105">To correct this error</span></span>  
  
- <span data-ttu-id="a6ac9-106">Ujistěte se, že jsou volání nebo přístupu k postupu z modulu, který je součástí projektu, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="a6ac9-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ac9-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6ac9-107">See also</span></span>

- [<span data-ttu-id="a6ac9-108">Friend</span><span class="sxs-lookup"><span data-stu-id="a6ac9-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
