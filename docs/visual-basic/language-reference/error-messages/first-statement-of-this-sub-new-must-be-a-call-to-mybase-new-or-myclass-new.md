---
title: První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 2b9d2568fb64e4af72733ad1f3dee58aaee650e5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402976"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="bbd5e-102">První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).</span><span class="sxs-lookup"><span data-stu-id="bbd5e-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="bbd5e-103">Prvním příkazem této metody Sub New musí být volání MyBase. New nebo MyClass. New, protože základní třída \<basename> pro \<derivedname> nemá přístupnou proceduru Sub New, kterou je možné volat bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="bbd5e-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="bbd5e-104">V odvozené třídě musí každý konstruktor volat konstruktor základní třídy ( `MyBase.New` ).</span><span class="sxs-lookup"><span data-stu-id="bbd5e-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="bbd5e-105">Pokud má základní třída konstruktor bez parametrů, který je přístupný pro odvozené třídy, `MyBase.New` může být volána automaticky.</span><span class="sxs-lookup"><span data-stu-id="bbd5e-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="bbd5e-106">V takovém případě musí být konstruktor základní třídy volán s parametry a tuto hodnotu nelze provést automaticky.</span><span class="sxs-lookup"><span data-stu-id="bbd5e-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="bbd5e-107">V tomto případě musí první příkaz každého konstruktoru odvozené třídy volat parametrizovaný konstruktor pro základní třídu nebo volat jiný konstruktor v odvozené třídě, která vytvoří volání konstruktoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bbd5e-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="bbd5e-108">**ID chyby:** BC30148</span><span class="sxs-lookup"><span data-stu-id="bbd5e-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bbd5e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="bbd5e-109">To correct this error</span></span>  
  
- <span data-ttu-id="bbd5e-110">Buď zavolejte `MyBase.New` , zadejte požadované parametry, nebo zavolejte rovnocenný konstruktor, který provádí takové volání.</span><span class="sxs-lookup"><span data-stu-id="bbd5e-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="bbd5e-111">Například pokud má základní třída konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)` , první příkaz v konstruktoru odvozené třídy může být `MyBase.New(100)` .</span><span class="sxs-lookup"><span data-stu-id="bbd5e-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd5e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbd5e-112">See also</span></span>

- [<span data-ttu-id="bbd5e-113">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="bbd5e-113">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
