---
title: První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: debab4e495d05a05801dd11850d0665c8bd6b299
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834319"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="3efab-102">První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).</span><span class="sxs-lookup"><span data-stu-id="3efab-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="3efab-103">Prvním příkazem této 'Sub New musí být volání 'MyBase.New' nebo 'MyClass.New', protože základní třída\<basename > "z"\<derivedname >' nemá přístupné 'Sub New, kterou lze volat bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="3efab-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="3efab-104">V odvozené třídě, musí každý konstruktor volat konstruktor základní třídy (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="3efab-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="3efab-105">Pokud základní třída nemá konstruktor bez parametrů, který je přistupovat k odvozeným třídám `MyBase.New` může být automaticky volána.</span><span class="sxs-lookup"><span data-stu-id="3efab-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="3efab-106">V opačném případě musí být volána konstruktor základní třídy s parametry, a to nemůže udělat automaticky.</span><span class="sxs-lookup"><span data-stu-id="3efab-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="3efab-107">V tomto případě první příkaz každý konstruktoru odvozené třídy musí volat do parametrizovaného konstruktoru v základní třídě nebo volání jiného konstruktoru v odvozené třídě, která provádí volání konstruktoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="3efab-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="3efab-108">**ID chyby:** BC30148</span><span class="sxs-lookup"><span data-stu-id="3efab-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3efab-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3efab-109">To correct this error</span></span>  
  
-   <span data-ttu-id="3efab-110">Buď zavolat `MyBase.New` poskytnutí požadovaných parametrů, nebo volat konstruktor druhé strany, která provádí těchto volání.</span><span class="sxs-lookup"><span data-stu-id="3efab-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="3efab-111">Například, pokud základní třída nemá konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)`, první příkaz v odvozený konstruktor třídy může být `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="3efab-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3efab-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3efab-112">See also</span></span>

- [<span data-ttu-id="3efab-113">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="3efab-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
