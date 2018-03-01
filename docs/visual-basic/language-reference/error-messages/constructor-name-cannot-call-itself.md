---
title: "Konstruktor & č. 39; &lt;název&gt;& č. 39; nelze volat sám sebe"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="7d08a-102">Konstruktor & č. 39; &lt;název&gt;& č. 39; nelze volat sám sebe</span><span class="sxs-lookup"><span data-stu-id="7d08a-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="7d08a-103">A `Sub New` postup ve třídě nebo struktuře volá sám sebe.</span><span class="sxs-lookup"><span data-stu-id="7d08a-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="7d08a-104">Účelem konstruktor je k inicializaci instance třídy nebo struktura při prvním vytvoření.</span><span class="sxs-lookup"><span data-stu-id="7d08a-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="7d08a-105">Třídu nebo strukturu může mít několik konstruktorů za podmínky, že všechny seznamy různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="7d08a-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="7d08a-106">Konstruktor může volat jiný konstruktor provést jeho funkčnost kromě vlastní.</span><span class="sxs-lookup"><span data-stu-id="7d08a-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="7d08a-107">Ale je smysl pro konstruktor volat sám a ve skutečnosti výsledkem by nekonečná rekurze Pokud povolena.</span><span class="sxs-lookup"><span data-stu-id="7d08a-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="7d08a-108">**ID chyby:** BC30298</span><span class="sxs-lookup"><span data-stu-id="7d08a-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d08a-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7d08a-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="7d08a-110">Zkontrolujte seznam parametr konstruktoru volána.</span><span class="sxs-lookup"><span data-stu-id="7d08a-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="7d08a-111">Musí být z konstruktoru uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="7d08a-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="7d08a-112">Pokud nemáte v úmyslu volat jiný konstruktor, odeberte `Sub New` zcela volání.</span><span class="sxs-lookup"><span data-stu-id="7d08a-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d08a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d08a-113">See Also</span></span>  
 [<span data-ttu-id="7d08a-114">Doba života objektu: Objekty vytváření a zničení</span><span class="sxs-lookup"><span data-stu-id="7d08a-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
