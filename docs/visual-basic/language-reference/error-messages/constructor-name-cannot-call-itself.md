---
title: Konstruktor '<name>' nemůže volat sám sebe.
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409800"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="fe3f5-102">Konstruktor '\<name>' nemůže volat sám sebe.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="fe3f5-103">`Sub New`Procedura ve třídě nebo struktuře volá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="fe3f5-104">Účelem konstruktoru je inicializace instance třídy nebo struktury při jejím prvním vytvoření.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="fe3f5-105">Třída nebo struktura může mít několik konstruktorů za předpokladu, že všechny mají jiný seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="fe3f5-106">Konstruktor je povolen pro volání jiného konstruktoru, aby se jeho funkce mohla provádět navíc.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="fe3f5-107">Nejedná se ale o stejný konstruktor, který by sám volal, a ve skutečnosti by to vedlo k nekonečné rekurzi, pokud je to povoleno.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="fe3f5-108">**ID chyby:** BC30298</span><span class="sxs-lookup"><span data-stu-id="fe3f5-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fe3f5-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fe3f5-109">To correct this error</span></span>  
  
1. <span data-ttu-id="fe3f5-110">Ověřte seznam parametrů volaného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="fe3f5-111">Měl by být jiný než konstruktor, který provádí volání.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="fe3f5-112">Pokud nechcete volat jiný konstruktor, odeberte `Sub New` volání zcela.</span><span class="sxs-lookup"><span data-stu-id="fe3f5-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3f5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe3f5-113">See also</span></span>

- [<span data-ttu-id="fe3f5-114">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="fe3f5-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
