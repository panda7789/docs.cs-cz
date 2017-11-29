---
title: "Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a0c54c6e62f9bdc7fe510500a486461d26636d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="d1795-102">Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání</span><span class="sxs-lookup"><span data-stu-id="d1795-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="d1795-103">Výchozí instance třídy se používá v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="d1795-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="d1795-104">To může vést k nekonečné rekurzivní volání, také známé jako nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="d1795-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1795-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d1795-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d1795-106">Výchozí instance odeberte z konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="d1795-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1795-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1795-107">See Also</span></span>  
 [<span data-ttu-id="d1795-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d1795-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
