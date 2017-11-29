---
title: "Nelze volat funkce friend objekt, který není instancí definice – třída"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f1ac1ea14efb0cdf0d8ca03257e4da33d35e368
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="2c217-102">Nelze volat funkce friend objekt, který není instancí definice – třída</span><span class="sxs-lookup"><span data-stu-id="2c217-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="2c217-103">Buď jste se pokusili volání `Friend` postup třídy, nebo jste se pokusili získat přístup `Friend` vlastnosti nebo metody napříč procesy nebo mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="2c217-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="2c217-104">A `Friend` postup lze volat z modulu mimo třídu, ale je součástí projektu, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="2c217-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c217-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2c217-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2c217-106">Ujistěte se, že jsou volání nebo přístup k procesu z modul, který je součástí projektu, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="2c217-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c217-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c217-107">See Also</span></span>  
 [<span data-ttu-id="2c217-108">Friend</span><span class="sxs-lookup"><span data-stu-id="2c217-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
