---
title: Prvním příkazem této &#39;proceduru Sub New&#39; musí být volání konstruktoru &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 75832ae88908094c1cb74ce04ad84c0d2ae91e68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728892"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="e32c2-102">Prvním příkazem této &#39;proceduru Sub New&#39; musí být volání konstruktoru &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)</span><span class="sxs-lookup"><span data-stu-id="e32c2-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="e32c2-103">Prvním příkazem této 'Sub New musí být volání 'MyBase.New' nebo 'MyClass.New', protože základní třída\<basename > "z"\<derivedname >' nemá přístupné 'Sub New, kterou lze volat bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="e32c2-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="e32c2-104">V odvozené třídě, musí každý konstruktor volat konstruktor základní třídy (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="e32c2-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="e32c2-105">Pokud základní třída nemá konstruktor bez parametrů, který je přistupovat k odvozeným třídám `MyBase.New` může být automaticky volána.</span><span class="sxs-lookup"><span data-stu-id="e32c2-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="e32c2-106">V opačném případě musí být volána konstruktor základní třídy s parametry, a to nemůže udělat automaticky.</span><span class="sxs-lookup"><span data-stu-id="e32c2-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="e32c2-107">V tomto případě první příkaz každý konstruktoru odvozené třídy musí volat do parametrizovaného konstruktoru v základní třídě nebo volání jiného konstruktoru v odvozené třídě, která provádí volání konstruktoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e32c2-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="e32c2-108">**ID chyby:** BC30148</span><span class="sxs-lookup"><span data-stu-id="e32c2-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e32c2-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e32c2-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e32c2-110">Buď zavolat `MyBase.New` poskytnutí požadovaných parametrů, nebo volat konstruktor druhé strany, která provádí těchto volání.</span><span class="sxs-lookup"><span data-stu-id="e32c2-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="e32c2-111">Například, pokud základní třída nemá konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)`, první příkaz v odvozený konstruktor třídy může být `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="e32c2-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32c2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e32c2-112">See also</span></span>
- [<span data-ttu-id="e32c2-113">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="e32c2-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
