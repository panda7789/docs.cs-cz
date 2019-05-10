---
title: Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 1cad1e3cf3943e945d519aee061a877c91684b4a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623473"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="0984e-102">Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání</span><span class="sxs-lookup"><span data-stu-id="0984e-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="0984e-103">Byla použita výchozí instance třídy v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="0984e-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="0984e-104">To může vést k nekonečné rekurzivní volání, označované také jako nekonečná smyčka.</span><span class="sxs-lookup"><span data-stu-id="0984e-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0984e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0984e-105">To correct this error</span></span>  
  
- <span data-ttu-id="0984e-106">Odebrání výchozí instanci konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="0984e-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0984e-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0984e-107">See also</span></span>

- [<span data-ttu-id="0984e-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="0984e-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
