---
title: První příkaz tohoto &#39;Sub New&#39; musí být volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589457"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="2e106-102">První příkaz tohoto &#39;Sub New&#39; musí být volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)</span><span class="sxs-lookup"><span data-stu-id="2e106-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="2e106-103">Prvním příkazem 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New', protože základní třídy\<basename >' z '\<derivedname >' nemá k přístupné 'Sub New, kterou lze volat bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="2e106-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="2e106-104">V odvozené třídě, musí každý konstruktor volání konstruktoru základní třídy (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="2e106-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="2e106-105">Pokud má konstruktor bez parametrů, které je přístupné pro odvozené třídy základní třídy `MyBase.New` může být automaticky volána.</span><span class="sxs-lookup"><span data-stu-id="2e106-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="2e106-106">Pokud ne, konstruktoru základní třídy musí být volána s parametry, a to není možné automaticky.</span><span class="sxs-lookup"><span data-stu-id="2e106-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="2e106-107">V takovém případě první příkaz každých konstruktoru odvozené třídy musí volat parametrizované konstruktor pro základní třídu nebo volání jiného konstruktoru odvozené třídy, která vytváří volání konstruktoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2e106-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="2e106-108">**ID chyby:** BC30148</span><span class="sxs-lookup"><span data-stu-id="2e106-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e106-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2e106-109">To correct this error</span></span>  
  
-   <span data-ttu-id="2e106-110">Buď volání `MyBase.New` poskytnutí požadované parametry, nebo volejte sdílené konstruktor, který provede tyto volání.</span><span class="sxs-lookup"><span data-stu-id="2e106-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="2e106-111">Například, pokud základní třída má konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)`, první příkaz v odvozené třídy konstruktor může být `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="2e106-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e106-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e106-112">See Also</span></span>  
 [<span data-ttu-id="2e106-113">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="2e106-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
